# TONK 🛆
Homemade RC tank

## Description 

T84-120 Yatagan 
1/6th scale RC model

Two variants 
1) Electric
2) Electro-Diesel with turboprop

## Mechanical specs

### Propulsion

Chose from one of the two following options :

1) Electric
   Two AC or DC motors 

2) Electro-Diesel with turboprop
   Based on the Wren turboprop.
   Should produce a good amount of power, with two drawbacks :
   * consumption
   * noise

### Turret

The turret main movement is constrained around two axis :

* Rotation motor
* Elevation motor

### Others

* Lights
* Smoke
* Optics
* Dozer
* Coax MG

## Embedded solutions 

A gyro is placed on the main gun and obviously follows the rotation fo the gun/turret axis



## Software - Algoritms

### Hull 

Two configurations have to be available in the firmware :
1) One for the electric config   
   Simple input throttle come from the remote   
   They should be between -127 and +128, 0 meaning the track is not moving, the sign determining which direction the motor should rotate.
3) the other one for the turboprop config   
   work in progress
### Turret stabilization simple algorithm

The hull can rotate on the three axis, depending on the terrain and how the vehicle moves.   

The gimbal, however is only allowed to work on two axis :
* Azimuth angle (around z-axis)
* Elevation angle (around y-axis)

The sensors are 
* The three axis inclinometer
* Angles sensors from the turret ring and gun elevation

The algorithm is quite tricky because we work with 3D.

How it works :

1) Initial position  
At first, the hull and turret are facing random orientations. 
2) After moving the hull   
Both hull and gun have changed orientations.
3) Final position    
The correction is updated to the motors command to match the predicted angle on the azimuth and elevation

Of course, this algorithm works every time the loop starts



### Turret control algorithm

Each loop, the desired position modification is updated from the receiver and added to the turret motors.

### Turret general algorithm

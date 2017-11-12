# Report on PID project

#### Objective
The aim of this document is to discuss design decisions that went in while implementing PID project. This document also talks about how each of the hyper parameters affect algorithm and how they were chosen.

### PID Controller

PID controller's task is to continuously calculate error between desired output and measured value and applies correction based on proportional, integral and derivative terms. ([link](https://en.wikipedia.org/wiki/PID_controller)). Over period of time, PID controller attempts to minimize the error over time.

### Effect of P, I, D on algorithm

#### Proportional
The P part represents change proportional to error value. Increasing the proportional coefficient causes the system to be more responsive although too high value can create oscillations since PID algorithm minimizes the error over time.

#### Integral
The I (Integral) parts gives the algorithm a historical cumulative direction in which error propagates. I part integrates the error over time [1]. Additionally, I part also counts for system bias in system which remains constant over time.

#### Derivative
The D part of algorithm represents prediction based on rate of change in error value. The D part affects the rate of response of system and increasing D coefficient increases the rate of response to the control system.

### Choosing hyper-parameters

One of the task for this project is to approximately select values for P, I, D coefficients by either manual trial and error or using Twiddle.

I chose these hyper-parameters by way of manual experimentations. I started off with the values provided in Sebastian's class as P,I,D = 0.2, 0.004, 3.0.

Manually changing these values helped me understand how granular is the response to these factors. The P and D coefficients have a strong effect on car's behavior. Higher D coefficient makes the car to oscillate sharply on turns. Finally, after several rounds of tweaking, I settled for values of 0.3, 0.0020, 5.0.

These parameters suit lower speed and type of track in simulator. But taking this into a real world car would require more accurate coefficients which I believe would be possible after millions of miles of simulated driving on various types of tracks.

#### Reference
1. [NI White paper](http://www.ni.com/white-paper/3782/en/)
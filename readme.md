## AD525x - Arduino library for I<sup>2</sup>C communication with AD5253 and AD5254
This is a library for communication with AD5253 and AD5254 quad 64-/256-position I<sup>2</sup>C Nonvolatile Memory Digital Potentiometers. The features implemented are based on [the datasheet provided by Analog Devices](http://www.analog.com/static/imported-files/data_sheets/AD5253_5254.pdf). 

To use these, instantiate either an AD5253 or an AD5254 object (the main difference is in the error checking) and call `obj.initialize(AD_addr)` to initialize communication with the device. The AD525x series potentiometers have a 5 bits of their 7-bit I2C address hard-coded as `0x2C` (`0d44`), and the two lowest bits can be programmed by pulling the `AD0` (pin 4) and `AD1` (pin 16) lines either high or low. The `initialize` method of each AD525x object is instantiated with the 2-bit `AD1 AD0` address of the device - do not specify the hard-coded portion of the address, as that is already taken into account.

Due exception handling with `try` and `catch` are too costly to be used on microcontrollers, in the event of an error in a member function, the private variable `err_code` (which can be queried using `AD525x::get_err_code()`) is set to one of the error codes defined in `AD525x_Errors.h`. A small companion library, `AD525x_ErrorStrings.h` is provided for interpreting the error codes into human readable strings. It is separated out from the main library to minimize unnecessary resource costs.


### License
This code is licensed under the MIT license. If you would like to use it under a different license or you would like a waiver of the requirements of the MIT license, contact me.

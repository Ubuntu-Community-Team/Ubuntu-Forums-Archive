---
title: "rxtx serial port event problems with usb adapter"
date: 2009-03-28
forum: Programming Talk
---

### Post by siriyu on 2009-03-28
My java application communicates with datalogger via rs232. Rxtx library works fine on *linux and windows system using serial port. The problems come when I use an usb* adapter* FTDI chip-set based ([http://www.ftdichip.com/Products/EvaluationKits/US232R-10.htm](http://www.ftdichip.com/Products/EvaluationKits/US232R-10.htm)) on my lunux system (2.6.24 kernel), where there is no need of driver. On windows instead I have no problem. My program is event based; This adapter works correctly using Mincom. But in my program I use serialPort.notifyOnDataAvailable(true) and serialPort.notifyOnOutputEmpty(true)* calls.
My application send first message correctly but I get an error in response:

	at gnu.io.RXTXPort.sendEvent(RXTXPort.java:732) 
	at gnu.io.RXTXPort.nativeDrain(Native Method) 
	at gnu.io.RXTXPort$SerialOutputStream.flush(RXTXPort.java:1201) 

*If I comment flush() command after send first message I have no response and my time-out  exceeds. It seems there are problems when generating SerialPortEvent.DATA_AVAILABLE event.
How can I resolve this problems ?

Best regards.

Luca Catoni

---


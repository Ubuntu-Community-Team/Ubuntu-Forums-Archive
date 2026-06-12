---
title: "java serial communication problem"
date: 2010-04-15
forum: Programming Talk
---

### Post by ben72 on 2010-04-15
I'm developing a java program communicating with a device on a usb to serial converter. I'm using rxtx RXTX-2.2pre1.

When I connect the device (or really the simulator) to a real com port and open port /dev/ttyS0 in my program it works.

When I instead connect the device (real device or simulator) to /dev/ttyUSB0 it does not work! I can send data and it's received on the other end but I receive nothing back..

I've tried on the same usb port under WinXP/virtualbox and my program then works.

When I communicate between two usb to serial devices on /dev/ttyUSB0 and  /dev/ttyUSB1 with a serial terminal program like cutecom it works under Ubuntu. So it's not a hardware problem. It must be something with the combination java rxtx and usb to serial devices on Ubuntu?!

Thanks for any help!!

---

### Post by ben72 on 2010-04-16
The solution to this problem is to not call:
notifyOnOutputEmpty(true)

This seems to be a rxtx problem with serial to usb devcies on linux only.

---

### Post by Dmorente on 2010-08-18
Hi ben72 !

I have the same problem, but I don't use the notifyOnOutputEmpty method.

My code is:

CommPortIdentifier idPuerto = CommPortIdentifier.getPortIdentifier( "/dev/ttyUSB0" );
SerialPort puertoSerie = (SerialPort)idPuerto.open( "PuertoSerie",2000 );
puertoSerie.addEventListener(this);
puertoSerie.notifyOnDataAvailable(true);
puertoSerie.setSerialPortParams( 9600,SerialPort.DATABITS_8, SerialPort.STOPBITS_1,SerialPort.PARITY_NONE );
puertoSerie.setFlowControlMode(SerialPort.FLOWCONTROL_NONE);

salida = puertoSerie.getOutputStream();
entrada = puertoSerie.getInputStream();

Can you help me, please :)

Best Regards,

---


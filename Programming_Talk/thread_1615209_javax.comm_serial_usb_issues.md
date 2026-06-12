---
title: "javax.comm serial usb issues"
date: 2010-11-06
forum: Programming Talk
---

### Post by chris2634 on 2010-11-06
I am experiencing some strange behavior when communicating with an Arduino board from a Java program using the javax.comm library. I am running the Java program on a VIA Pico-ITX with Ubuntu 9.04 Server 32-bit Alternate Installation. The version of javax.comm is "comm3.0_u1_linux".

If I boot the computer and immediately run the Java program, I receive about 2 lines per second with every other line being blank. I am expecting roughly 20 lines per second. In this scenario the buffer also appears to be getting backed as events on the Arduino are not carried through the serial data for several seconds.

If I boot the computer and run Minicom, I am able to receive the full 20 lines per second without issue. My config is /dev/ttyUSB0, 9600 8N1, No HW control, No SW control.

If I run the Java program after running Minicom, it behaves differently. It receives the information at the correct rate, but will stop receiving data at least once or twice. If I keep restarting the program, eventually I can receive data at the correct rate indefinitely.

I have removed all sources of interference, including my DC motors, USB wireless module and physically separating the computer from the Arduino. I have also attached the Arduino to my Windows7 PC and the Java program works perfect there.


Here's my script for setting up the javax.comm libraries and USB Serial configuration:

```

#!/bin/sh

# constants
JAVA_HOME=/usr/lib/jvm/java-6-sun/jre

# ensure running as root
if [ `id -u` -ne 0 ] ; then
 echo error: you must be root to run this script
 echo error: no changes have been made to the system
 exit 1
fi

# install the library
cp commapi/lib/libLinuxSerialParallel.so $JAVA_HOME/lib/i386/
chmod 644 $JAVA_HOME/lib/i386/libLinuxSerialParallel.so
cp commapi/jar/comm.jar $JAVA_HOME/lib/ext/
cp commapi/jar/comm.jar `pwd`

# setup the javax.comm.properties file
cp commapi/docs/javax.comm.properties $JAVA_HOME/lib/
ln -s $JAVA_HOME/lib/javax.comm.properties `pwd`/javax.comm.properties

# SPECIAL add usb-to-serial device to properties file
sed -i -e '/serpath1 = \/dev\/ttyS1/aserpath2 = /dev/ttyUSB0' $JAVA_HOME/lib/javax.comm.properties

```


Here's the relevant part of the javax.comm.properties:

```

# Implementation specific driver
driver=com.sun.comm.LinuxDriver

# Paths to server-side serial port devices
serpath0 = /dev/ttyS0
serpath1 = /dev/ttyS1
serpath2 = /dev/ttyUSB0

# Paths to server-side parallel port devices
parpath0 = /dev/parport0
parpath1 = /dev/parport1

```


Here's the relevant part of the Java program:

```

CommPortIdentifier port_identifier = CommPortIdentifier.getPortIdentifier("/dev/ttyUSB0");
SerialPort serial_port = (SerialPort)port_identifier.open("Arduino", 2000);
serial_port.setSerialPortParams(9600, SerialPort.DATABITS_8, SerialPort.STOPBITS_1, SerialPort.PARITY_NONE);

InputStream input_stream = serial_port.getInputStream();
reader = new BufferedReader(new InputStreamReader(input_stream));

output_stream = serial_port.getOutputStream();

// THIS IS DONE IN A CONTINUOUS LOOP
String command = reader.readLine();
System.out.println("received=" + command);

```

I've tried a lot of things but haven't been able to solve this issue. I am hoping someone with more USB Serial experience will be able to point me in the right direction. Thanks for reading!

-Chris

---


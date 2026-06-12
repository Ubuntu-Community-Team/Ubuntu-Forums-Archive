---
title: "QT5 serial port open resource temporarily unavailable"
date: 2015-04-27
forum: Programming Talk
---

### Post by cihan2 on 2015-04-27
Hi,

i am a linux and raspberry Pi2 newbie, i have a device which uses FTDI chip, this device controls wave pumps in my aquarium.

in windows7, i can connect to this controller with its original program tunze 7096
[http://www.tunze.com/fileadmin/gebrauchsanleitungen/x7096.8888.pdf](http://www.tunze.com/fileadmin/gebrauchsanleitungen/x7096.8888.pdf)
 via usb port, and can change pump settings.

also i can change settings with c#, and qt5 in windows.

in raspbian and ubuntu, i can open the port with mono c# and write new settings successfully, but not with qt5, in QT5 when i open the port the device led turns off and i can not write the settings string to device.( devices led never turns off with c# mono, and qt5 in windows7 when successful open and write occurs)

i debug the code with raspbian and ubuntu, it  seems port opened ok, /dev/ttyUSB0 but i can't write data so i decide to trace if any error occurs after opening port.

serial.open(QIODevice::ReadWrite)
qDebug() << serial.errorString() , here it says

in raspbian "no such file or directory"
in ubuntu 14 -64bit , "resource temporarily unavailable"

and after opening the port i try to write string with qbytearray no errors but nothing happened, when i close the port device led again turns on.

But in mono c# code works perfect.. i can open and write in windows7 ubuntu14 and raspbian, nothing change with the led when i open the port. 

i also tried chmod 777 /dev/ttyUSB0 in ubuntu, raspbian but nothing changed

i am very pleased if you have an idea how to open /dev/ttyUSB0 successfully, and write string in cross compiled QT5 C++.

thanks.

---

### Post by cihan2 on 2015-04-30
here is  the code, is simple, i tried different baud rates and flowcontrol to  none but nothing is changed, also i tried open the port first and then  assigned port settings but no success :(
 also when i put waitForBytesWritten(1000) after write while debugging  with F10 after processing waitForBytesWritten debugger changed to line  again to serial.write command and again processed waitbyteswritten then  exits.
 by the way no locks exists, i tried minicom before it succeeds , port opened fine.


 #include <QCoreApplication>
#include <QSerialPort>
#include <QDebug>
 int main(int argc, char *argv[])
{
QCoreApplication a(argc, argv);
 QSerialPort serial;

               serial.setPortName("/dev/ttyUSB0");
               serial.setBaudRate(QSerialPort::Baud19200);
               serial.setStopBits(QSerialPort::OneStop);
               serial.setDataBits(QSerialPort::Data8);
               serial.setParity(QSerialPort::NoParity);
               serial.setFlowControl(QSerialPort::SoftwareControl);//xonxoff*/
 if (serial.open(QIODevice::ReadWrite))
//if (serial.open(QSerialPort::ReadWrite)) // both fails //writeonly fails
{
qDebug() << serial.errorString();
            bool success = true;
           qDebug() << "Connected to usb device: " << (success ? "OK" : "FAIL");

           serial.Write("tunze settings string");
           serial.Waitbyteswritten(1000);


            }

return a.exec();
 }

---


---
title: "3G modem e173 doesnt work"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by mike188 on 2014-05-08
Hello! Ive had so much trouble with this 3g modem. Right after installation of lubuntu when  i launched nm-applet and created a new mobile broadband connection in the choose device option it was identified as 'huawei device'. I made  new connection and everything worked well until after a while something happened and it stopped working. Now in that option theres only 'any device' , no 'huawei modem'. 
  I used this article [https://help.ubuntu.com/community/3GInternet](https://help.ubuntu.com/community/3GInternet) to fix it. I configured usb_modeswitch as instructed there, nothing happens. 
 
Then I tried wvdial, there are some outputs

```
$ lsusb
Bus 001 Device 005: ID 12d1:1436 Huawei Technologies Co., Ltd. E173 3G Modem (modem-mode)
```

device is connected

```
~$ sudo wvdialconf

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- ATQ0 V1 E1 S0=0
ttyUSB0<*1>: ATQ0 V1 E1 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```

then edited wvdialconf

```
sudo nano /etc/wvdial.conf

   [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = *99#
ISDN = 0
; Password = gdata
New PPPD = yes
; Username = gdata
Modem = /dev/ttyUSB0
Baud = 9600

```

then connect

```
~$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
```

When i start lubuntu in cd mode modem is identified and in a new broadband connection i have 'any device' and 'huawei modem'. 

1. What is the program responsible for identification of the modem in a new connection? Is it modeswitch? How to configure it properly? Why did they create new file usb-modeswitch.conf?
2. Why doesnt wvdial  connect and what should be written in password, name fields?
3. What are other possible solutions?

---

### Post by mike188 on 2014-05-10
I want to find out where the error is and then zero in on that area. I would like to clarify some points.
1. usb modeswitch; edit /etc/usb-modeswitch.conf, then sudo usb_modeswitch
Not clear: field 'message content', I read it's hex key from cat /etc/usb_modeswitch.d/vendor\product | grep MessageContent - 
doesnt work in my case. How can I check whether its been switched? Should i normally see the device in network manager now? 
2. Adding module setserial: edit /etc/modules, add usbserial vendor=0x... product=0x....
Need clarification here.

3. Trying wvdial. Configured file /etc/wvdial.conf with name, password received from provider. It either returns 
- 'modem not found' (most of the times). What should I do, which earlier commands it is related to? What about field modem= dev/tty.., how can I know which dev it is at?
or
- 'name, password not valid' What is meaning of these values? In windows it connected without  them, when modem was identified by network manager here it connected even with a wrong provider.

4. Sakis3g. Does it include all previous solutions in itself? Connects in 1 in 20 attempts. When its going to connect it prompts to choosing interface, provider, ect fields; most of the time when there's no success, I press 'connect 3g' - connection failed; all other options - fail, except 'set modem' - sets to 12d1:1436. Uninstalled network manager - nothing changed. If it fails once, rebooting OS many times, switching, unswitching the modem doesn't help. However next day it may  connect from the first attempt, then after disconnection it may fail and all cycle over again.

Are there any sources of technical information where i can read  in detail on how such 3g mobile connection process happens and those programs like nw manager, sakis work?

---

### Post by nadrach on 2014-05-16
Take a look at this thread from August 2013 (penultimate message):
 [http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173](http://ubuntuforums.org/showthread.php?t=2128479&page=2&highlight=E173)

To paraphrase ... usb_modeswitch is making the wrong product ID change ...
> The problem is that usb_modeswitch switches the device from its default operation (product id 1446 which is a storage device) to the incorrect product id of 1436. In fact, it should change it to product id 140c, which is the correct product id for the modem.

The post then describes a file edit to change the configuration message sent by usb_modeswitch ... unfortunately none of the configuration files that the post specifies for 12.04 are present in 14.04.

---


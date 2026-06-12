---
title: "Send AT commands via Bluetooth"
date: 2009-07-04
forum: Programming Talk
---

### Post by UbuKunubi on 2009-07-04
Hello!

I wish to send AT commands to my phone, connected over Bluetooth.

I found a code template, but it seems to fail!
Can anyone help please?

```

# -*- coding: utf-8 -*-
import bluetooth
import serial

#def SendViaBluetooth():

sockfd = bluetooth.BluetoothSocket(bluetooth.RFCOMM)
sockfd.connect(('00:12:40:XX:XX:XX', 1)) # BT Address
sockfd.send('ATZ\r')
sockfd.send('AT+CMGF=1\r')
sockfd.send('AT+CMGS=”+4478XXXXXXXX”\r') # TO PhoneNumber
sockfd.send('SMS over Bluetooth\n')
sockfd.send(chr(26)) # CTRL+Z
sockfd.close()

```

When run produces:
```

Traceback (most recent call last):
  File "/home/nigel/NDSPython/Btooth/SendSMS.py", line 8, in <module>
    sockfd.connect(('00:12:40:38:F6:75', 1)) # BT Address
  File "<string>", line 5, in connect
BluetoothError: (112, 'Host is down')

```

Yet the Bluetooth is on AND visable, and when I use the sdptool and hcitool I can view the phone in the visable list and sdptool can list the services on the phone - this also confirms that I am using the correct channel!

Thanks for any tips,
Ubu

---

### Post by monraaf on 2009-07-04
Cool I didn't even know there was a python bluetooth library, now I can convert all my bluetooth C code to python ;) Incredible, there are python libraries for almost anything!

Now regarding your question, the code works fine for me. I suggest looking at the bluetooth options of your phone, maybe you should also pair it with your PC if you haven't done so already.

---

### Post by Can+~ on 2009-07-04
> **monraaf said:**
> Cool I didn't even know there was a python bluetooth library, now I can convert all my bluetooth C code to python ;) Incredible, there are python libraries for almost anything!

```
-----@------:~$ apt-cache search python bluetooth
totem-plugins - Plugins for the Totem media player
python-bluez - Python wrappers around BlueZ for rapid bluetooth development
python-libbtctl - Python bindings for libbtctl Bluetooth library
python-lightblue - cross-platform Bluetooth API for Python
```

Awesome, I didn't knew either.

---

### Post by UbuKunubi on 2009-07-05
> **monraaf said:**
> Cool I didn't even know there was a python bluetooth library, now I can convert all my bluetooth C code to python ;) Incredible, there are python libraries for almost anything!

Now regarding your question, the code works fine for me. I suggest looking at the bluetooth options of your phone, maybe you should also pair it with your PC if you haven't done so already.

The phone is paired, as i use the 'browse phone' function a lot to transfer photos.

When I use sdptool I find the following:
```

Service Name: A2DP Source
Service RecHandle: 0x10000
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service Name: AVRCP Target
Service RecHandle: 0x10001
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: 
Service RecHandle: 0x10002
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Serial Port" (0x1101)

Service Name: AMOI FTP
Service RecHandle: 0x10003
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 16
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Voice Gateway
Service RecHandle: 0x10004
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: Voice Gateway
Service RecHandle: 0x10005
Service Class ID List:
  "Handsfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0105

Service Name: AMOI OPP
Service RecHandle: 0x10006
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 17
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

Service Name: AmoiBPPService
Service RecHandle: 0x10007
Service Class ID List:
  "Direct Printing Ref. Object" (0x1120)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 18
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Basic Printing" (0x1122)
    Version: 0x0100

Service Name: AmoiImageResponder
Service RecHandle: 0x10008
Service Class ID List:
  "Imaging Responder" (0x111b)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 19
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Imaging" (0x111a)
    Version: 0x0100

Service Name: QC Dial-up Networking
Service RecHandle: 0x10009
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 8
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

```

---

### Post by UbuKunubi on 2009-07-06
Bump!

HI Folks,
Seeing as some of your guys are keen to use the bluetooth for Python, perhaps I could have a pointer on how to READ data back from the device?

So I get my python code to send the command "AT+COPS", and then the reply is read back into whatever var, so I can do the required parsing......
Anyone......please?

---

### Post by monraaf on 2009-07-06
For receiving the data you just call the recv method.

BTW. Did you resolve the issue of not being able to connect to your phone? For future reference it would be nice if you post what was the problem and how you resolved it.

---

### Post by UbuKunubi on 2009-07-06
> **monraaf said:**
> For receiving the data you just call the recv method.

BTW. Did you resolve the issue of not being able to connect to your phone? For future reference it would be nice if you post what was the problem and how you resolved it.

aha - recv method - thanks for the pointer - I just wasnt sure of the method name. Thank you monraaf.

I did decide that the comms with the phone are ok, since I do witness the bluetooth icon change colour. The failure of sending a SMS indicated to me that the phone (3 Skypephone WP-S1) may not use text mode for compliling the SMS, and that I'll have to build a PDU encoder to do the task.
As soon as I get evidence to support either conclusion I will either edit or post as fit.

The uncertainty left me wondering if I should write (as I couldnt find one) a terminal chat program for bluetooth, so that I could manually send the commands and determine whether the phone was a)communicating as expected, and b) that it uses either text or PDU encoding for SMS.

All the best,
Ubu

---

### Post by gtr32 on 2009-07-06
> **UbuKunubi said:**
> So I get my python code to send the command "AT+COPS", and then the reply is read back into whatever var, so I can do the required parsing......
Anyone......please?

It's a socket so you will have to do write buffer + read buffer for the commands.

Set:

send(AT+COPS=[<mode>[,<format>[,<oper>]]])
response = recv(...)

Read:

send(AT+COPS?)
response = recv(...)

Test:

send(AT+COPS=?)
response = recv(...)

---

### Post by UbuKunubi on 2009-07-06
> **gtr32 said:**
> It's a socket so you will have to do write buffer + read buffer for the commands.


Thank you gtr32!

Your answer is the exact format I was hoping for! 
All the best,
Ubu

---

### Post by gtr32 on 2009-07-06
> **UbuKunubi said:**
> 
The uncertainty left me wondering if I should write (as I couldnt find one) a terminal chat program for bluetooth, so that I could manually send the commands and determine whether the phone was a)communicating as expected, and b) that it uses either text or PDU encoding for SMS.

I haven't tried it, yet, but maybe you could use gtkterm or minicom for that? I will try to find one of my test phones and try it in Ubuntu.

---

### Post by UbuKunubi on 2009-07-06
> **gtr32 said:**
> I haven't tried it, yet, but maybe you could use gtkterm or minicom for that? I will try to find one of my test phones and try it in Ubuntu.

Thanks again - In my 'google hunt', I did find and start to explore using gtkterm. 
Since it was an unknown program to me I decided that learning how to use it would detract from my goal of actually learning more about python and bluetooth.

Im eager to hear how you get along in your test!
Best Regards,
Ubu.

---

### Post by UbuKunubi on 2009-07-06
After a lot of searching, and a bit of playing I finally got to send the SMS by bluetooth commands from Python.

Im sorry, but with my playing I forgot where I found the original code sample.


Here is the working code:
```

# ATsend.py
#  
# Turn the phone bluetooth off and on each time you
# send the At commands to free up the DUN port
#
# Requires Pybluez from Google
# http://pybluez.googlecode.com
# PyBluez works on GNU/Linux and Windows XP (Microsoft and Widcomm Bluetooth stacks)
#
# Send At commands to mobile device via DUN
#
# Some code to show how to dial a number with
# AT commands also shown below
# 
# November 5, 2008
 
import sys
import bluetooth  #Pybluez http://pybluez.googlecode.com
 
deviceName = []
deviceAddress = None
foundDevices = bluetooth.discover_devices()
 
count = 0
while count == 0:
    print ""
    print ""
    for bdaddr in foundDevices:
        deviceName.append(bluetooth.lookup_name( bdaddr ))
        deviceAddress = bdaddr
        print "%2d  %-16s Address: %s" % (count +1, deviceName[count], deviceAddress) 
        count += 1  
    choice = raw_input("Choose Device or 0 to repeat scan")
 
    # Repeat scan to get more device names
    if (choice.isdigit() and int(choice) <= len(foundDevices)):
        count = int(choice) 
        if choice > "0": 
             
            print "\n-- Select device, 0 to repeat scan or q to quit --"
            print ""
            selected = deviceName[count -1]
            deviceAddress = foundDevices[count -1]
          
            if deviceAddress is not None:
                print ""
            else:
                print "Could not find a Bluetooth device"
                
    elif choice == 0: 
        count = choice  # Repeat the while loop and device scan again
    elif choice == "q" or choice == "Q":
        exit(0)
        
services = bluetooth.find_service(address=deviceAddress)
devicename = bluetooth.lookup_name(deviceAddress, timeout=10)
showProfiles = None
 
if len(services) > 0:
    print "Found %d services on %s\n" % (len(services), deviceAddress)
# 
else:
    print "No device found at address: %s" % deviceAddress
    print
    print "Did you turn on bluetooth?"
    print "Did you accept/authorize the connection?"
    print
    sys.exit(3)
 
dunPort = 0 # Not found yet   
# Get Service Details
# global showProfiles
showProfiles = raw_input("Show Bluetooth Profiles supported? y|n")
for svc in services:
     # Look for DUN port
    if  svc["name"] == "QC Dial-up Networking":
        dunPort = svc["port"]
    if  showProfiles == "y":
        print "BT Profile: %s"    % svc["name"]
        print "    Host:        %s" % svc["host"]
        print "    Description: %s" % svc["description"]
        print "    Provided By: %s" % svc["provider"]
        print "    Protocol:    %s" % svc["protocol"]
        print "    channel/PSM: %s" % svc["port"]
        print "    svc classes: %s "% svc["service-classes"]
        print "    profiles:    %s "% svc["profiles"]
        print "    service id:  %s "% svc["service-id"]
        print
                   
if dunPort != 0:
    print "Found Dial-Up Networking port = %d\n" % (dunPort)
        
    s = bluetooth.BluetoothSocket(bluetooth.RFCOMM)
 
    conn = s.connect((deviceAddress, dunPort))
 
    # A semicolon ";" at the of the number dialed
    # is necessary to make a voice call
    # with out the ";" this  command will try to
    # make a data call
 
    # Example to Dial a number using AT command
    
    #s.send('ATD +1650xxxxxxx;\r'),
    #print s.recv(1024),
    
 
# This next section has to expect the correct number of returns
# The first command "ATE1" gets a single "OK" response with a carrage return
# The next commands expects 2 lines returned.
# Each line return ends with \r
# The correct send/expect sequence must be followedd or you will get
# a hang or no response.
 
    #s.send("ATE1\r")
    #print s.recv(1024),
    s.send("AT\r")
    print s.recv(1024)

    s.send("AT+CMGF=1\r")
    print s.recv(1024)
    #print s.recv(1024)

    s.send('AT+CMGS="0784XXXXXXX"\r')
    print s.recv(1024)
    s.send("This is freds test!"+chr(26))
    print s.recv(1024)
    print s.recv(1024)
    
    #s.send("AT+GMI\r")
    #print s.recv(1024),
    #print s.recv(1024),
 
    #s.send("AT+CGMI\r")
    #print s.recv(1024),
    #print s.recv(1024),
 
    #s.send("AT+GMM\r")
    #print s.recv(1024),
    #print s.recv(1024),
 
    #s.send("AT+CGMM\r")
    #print s.recv(1024),
    #print s.recv(1024),
 
    s.close
    sys.exit(0)                 
    
else :
    print "Could not find Dial Up Networking port."
    print "Or DUN port is busy."
    print "Switch the target's Bluetooth off then on and retry"
    sys.exit(4)

```

and outputs (truncated):
```

Found Dial-Up Networking port = 8

AT


OK


AT+CMGF=1


OK


AT+CMGS="0784XXXXXXX"


> 



This is freds test!

```

---


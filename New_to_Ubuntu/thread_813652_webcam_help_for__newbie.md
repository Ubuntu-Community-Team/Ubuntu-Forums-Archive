---
title: "webcam help for  newbie"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by boywholinuxed on 2008-05-31
hi,
i got a creative webcam mini
its model no. is pd0040

i typed lsub and found out the driver is ov518.
thats pretty much all i know, 

i am a big time newbie to kubuntu so please help me by giving step by step instructions on how to install webcam on kubuntu

is there a kde alternative for camorama?

---

### Post by loell on 2008-05-31
you'll know what webcam driver is loaded you type or copy/paste in the command line,


```
lsmod | grep videodev
```

just use camorama in kubuntu if your webcam works, 

you can even use cheese if you like. ;)

---

### Post by boywholinuxed on 2008-05-31
i downloaded the driver and cheese from adept but when i run cheese,it says unable to find camera?



why does this error come?

---

### Post by loell on 2008-05-31
are you sure that the driver is used by your webcam? Where did you download the driver? 
what's the output of the command that i gave?

---

### Post by boywholinuxed on 2008-06-01
this is the out put i got

videodev               29312  1 ov511
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev



so i assume its the ov511 driver.

then i go to adept and install ov511 and cheese and when i try cheese the error which i mentioned above comes

---

### Post by loell on 2008-06-03
install **camorama** see if it can show your webcam, if it can then the issue would be cheese app.

---

### Post by boywholinuxed on 2008-06-03
no it doesnt come in camorama
this error comes

could not connect to video device(/dev/video0).Please check connection

---

### Post by loell on 2008-06-03
stange, can you do

```
lsusb
``` 

so we'll know what this webcam really is.

---

### Post by boywholinuxed on 2008-06-03
hi,
i love ubuntu and kubuntu except for the fact that there is no webcam support.

i mean for printer and scanners and for digicams,ubuntu and kubuntu is really helpful .it helps you with setting up of drivers and everything.but for webcams it both ubuntu and kubuntu is not that good.

is it just my opinion or a is it the truth?

---

### Post by Sef on 2008-06-03
> is it just my opinion or a is it the truth?

It depends on your webcam.  Mine (logitech communcative stx) worked out of the box with Hardy Heron.

---

### Post by ruffEdgz on 2008-06-03
Mine also worked with my on-board webcam from Dell (XPS M1530). 

I can only use the application Cheese (can be found in the Add/Remove Application window) which works well. The application don't record sound but the picture taking and video recording works well.

Here is a documentation about webcams :D

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by boywholinuxed on 2008-06-03
this is the output

Bus 002 Device 003: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam
Bus 002 Device 004: ID 04f3:0212 Elan Microelectronics Corp.
Bus 002 Device 002: ID 8086:1120 Intel Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by boywholinuxed on 2008-06-03
please take a look at this topic
[http://ubuntuforums.org/showthread.php?t=813652](http://ubuntuforums.org/showthread.php?t=813652)

---

### Post by loell on 2008-06-03
from [https://help.ubuntu.com/community/Ov51x](https://help.ubuntu.com/community/Ov51x)


i think you need to unload the driver ov511

```
sudo rmmod ov511
```

then load ov51x by doing

```
sudo modprobe ov51x
```

now lets test if camorama can pick up your webcam. if it can pickup then we'll have to load the module on startup.

---

### Post by avtolle on 2008-06-03
I notice there is a reply on your other thread suggesting an action you might take. BTW, you shouldn't open multiple threads on the same topic; be patient.

---

### Post by SunnyRabbiera on 2008-06-03
keep in mind that ubuntu is a community driven OS and we live in a MS ruled world, not all ebcams will work with linux...
this is not our fault.

---

### Post by bodhi.zazen on 2008-06-03
Threads merged.

@ boywholinuxed : Please do not start multiple threads on the same topic.

---

### Post by boywholinuxed on 2008-06-04
hi y'all,
@sunny :i'm not blaming anyone in fact i really appreciate the work ubuntu puts in for everyone.

@avtolle:i'm sorry but i've posted this webcam problem in another post and i've been waiting for a long time(a month at least!) to get an answer,so i got frustrated,once again i apologize and i assure you this wont happen again!

thanks everybody especially loell for your effort in helping me out!

---

### Post by boywholinuxed on 2008-06-04
hi y'all,
@sunny :i'm not blaming anyone in fact i really appreciate the work ubuntu puts in for everyone.

@avtolle:i'm sorry but i've posted this webcam problem in another post and i've been waiting for a long time(a month at least!) to get an answer,so i got frustrated,once again i apologize and i assure you this wont happen again!

thanks everybody especially loell for your effort in helping me out!

---

### Post by proevofanatik on 2009-08-02
hello i have a quickcam messenger plus webcam and im getting the error could not connect to video device(/dev/video0).Please check connection.

this is what i get on terminal

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 046d:08f6 Logitech, Inc. Quickcam Messenger Plus
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---


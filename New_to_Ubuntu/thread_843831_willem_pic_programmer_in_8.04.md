---
title: "willem pic programmer in 8.04?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by oisuxx on 2008-06-28
i am trying to get my willem programmer to work with no luck. i tried to even run it through vmware. this thing runs off the lpt port, but i have no luck on any end. i even installed piklab, but it just crashes when i try to search for it. i tried running a few programs through wine. but all just ends the same. no connection. 

is anyone familliar with these things and ubuntu? im really pulling my hair out with this. it worked perfect in windows, but i dont want to keep swapping hdds for this one thing. ](*,)

---

### Post by lank23 on 2008-06-28
You might have a access issue on the LPT port.  I have to be part of the scanner group to use the port. See below.

```

lank23@ubuntu-desktop:~$ ls -l /dev/parport0
crw-rw---- 1 lp scanner 99, 0 2008-06-27 17:45 /dev/parport0

```

---

### Post by oisuxx on 2008-06-28
bill@bill-desktop:~$ ls -l /dev/parport0ls -l /dev/parport0
ls: cannot access /dev/parport0ls: No such file or directory
crw-rw-rw- 1 lp scanner 99, 0 2008-06-26 22:27 /dev/parport0
bill@bill-desktop:~$

---

### Post by krlhc8 on 2008-06-28
I wish I could help, but I usually do in-system-programming and don't need a programmer, just a serial cable.  A MAX232 hooked up to txd and rxd and some caps could save you the trouble and money.

---

### Post by oisuxx on 2008-06-28
bill@bill-desktop:~$ ls -l /dev/parport0
crw-rw-rw- 1 lp scanner 99, 0 2008-06-26 22:27 /dev/parport0



got it, but it still wont detect it in piklab

---

### Post by lank23 on 2008-06-29
I looked in Piklab but did not find a predefined setting for your programmer.  So do you know what settings you should use?  If you are part of the scanner group, and you get the settings right it should work.

---

### Post by oisuxx on 2008-06-29
yea see i dont know the settings. i have a pre defined ini for winpic but i dont think i can import that into piklab. i am in the scanners group. ill have to knock my head around this some more. and learn more about ubuntu :)
TIME TO GET A BOOK!

---

### Post by oisuxx on 2008-06-29
so after looking at the ini file for willem on wimpic i found this

ProgrammerControlLines]

VppOnOff=str

PullMclrDown=nc

DataOut=D0

DataOutWhileReading=1

OutEnable=nc

DataIn=bsy

ClockOut=D1

ClkEnable=nc

VddOnOff=ini

Connect=nc

RedLed=nc

GreenLed=nc

OkButton=nc

i can get the lights to change but thats about it, cause some of these here dont have the values in piklab OR pikdev

---

### Post by lank23 on 2008-06-29
If you have lights, then you are close to getting it working. Looking at the INI file and what Piklab has, I think that the screen shot below will set it up to work.  You might have to play with the time delay some.

good luck.

---

### Post by oisuxx on 2008-06-29
every time i try to save the setup it just freezes now. lol. i cant WIN. i guess ill try to figure this out in pikdev instead

---

### Post by lank23 on 2008-06-29
open the configuration file ".kde/share/config/piklabrc" and edit instead of using the gui.  You might also want to post a question over at piklabs forums
[http://sourceforge.net/forum/?group_id=138852]("http://sourceforge.net/forum/?group_id=138852")

lank23

---

### Post by oisuxx on 2008-07-03
thanks for the link. i posted something there....hopefully it will work. i hate having to rip open my pc and plug in a hdd for ONE program DOH!

---


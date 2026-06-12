---
title: "Will not wake up properly after suspend (12.04)"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by carolin3 on 2013-04-19
Hello

My computer won't wake up properly after suspend, the screen just freezes. 
Also after my screen is locked, and I click switch user. I try to shut down and 
nothing happens?

now it became kinda two questions in one >.<  gomen ne

My computer is  Eeepc X101CH

---

### Post by pqwoerituytrueiwoq on 2013-04-19
have you checked for any BIOS updates?
this should be the latest bios for that system
[http://dlcdnet.asus.com/pub/ASUS/EeePC/X101CH/X101CH-ASUS-1203.zip](http://dlcdnet.asus.com/pub/ASUS/EeePC/X101CH/X101CH-ASUS-1203.zip) (version # 1203)
here is ht download page
[http://www.asus.com/Notebooks_Ultrabooks/Eee_PC_X101CH/#support_Download_8]("http://www.asus.com/Notebooks_Ultrabooks/Eee_PC_X101CH/#support_Download_8")

you could try a newer release (12.10/13.04) on a live usb flash drive and see if it works

---

### Post by carolin3 on 2013-04-19
How do I update BIOS ? I have never done such a thing before, is it difficult?

---

### Post by carolin3 on 2013-04-19
Also I had ubuntu 12.10 before on this computer but it made it slow :/ hence I switched to 12.04

---

### Post by edeneen on 2013-04-19
been there, done that, some machines do not support Ubuntu power management

---

### Post by pqwoerituytrueiwoq on 2013-04-19
depends on if your bios lets you flash from in the bios (often called easy flash or quick flash)
if it does not have that feature you have to flash from windows using asus's software, which will require you have the asus software sweet stuff installed or it will think you are trying to flash a system that was not made by asus

this info should be in the manual (see second link above)

you should be able to check your bios version using [hwinfo](apt:hwinfo)
```
sudo hwinfo --bios | grep -i version -B3
```
if you post the output of that i can tell what BIOS version you have currently installed

---

### Post by carolin3 on 2013-04-20
This is the output:

xxx@xxx-X101CH:~$ sudo hwinfo --bios | grep -i version -B3
process 3283: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
    OEM id: "A M I"
    Product id: "ALASKA"
    2 CPUs (0 disabled)
  SMBIOS Version: 2.7
  BIOS Info: #0
    Vendor: "American Megatrends Inc."
    Version: "X101CH.0701"
--
  System Info: #1
    Manufacturer: "ASUSTeK COMPUTER INC."
    Product: "X101CH"
    Version: "x.x"
--
  Board Info: #2
    Manufacturer: "ASUSTeK COMPUTER INC."
    Product: "X101CH"
    Version: "x.xx"
--
    Chassis: #3
  Chassis Info: #3
    Manufacturer: "ASUSTeK COMPUTER INC."
    Version: "x.x"
--
    Type: 0x03 (CPU)
    Family: 0x01 (Other)
    Manufacturer: "Intel"
    Version: "Intel(R) Atom(TM) CPU N2600   @ 1.60GHz"

---

### Post by pqwoerituytrueiwoq on 2013-04-20
your BIOS version is 701, there are 4 newer versions
instructions to flash the bios are in chapter 3 of your manual
[http://dlcdnet.asus.com/pub/ASUS/EeePC/X101CH/ENG6748.zip](http://dlcdnet.asus.com/pub/ASUS/EeePC/X101CH/ENG6748.zip) - English version, and i only see instructions for windows, you may not have a option in your bios for it

---

### Post by edeneen on 2013-04-20
> **carolin3 said:**
> How do I update BIOS ? I have never done such a thing before, is it difficult?

if you mess or use ethe wrong update you ruin the PC - period

---

### Post by Nixarter on 2013-04-20
The most common cause of this is not using a full install.  Did you use Wubi to install vs doing the partitions for a full install?  Due to the fundamental basics of how they work, suspend etc cannot work from a Wubi install.  If you are using wubi (installed ubuntu from within windows), then the only solution is to do a full install.  Otherwise, jsut disable the features because you may lose work if they get triggered.

This is step one.  if not, then read above for the next steps lolz

PS: do those functions work from within wondows?  If so, your firmware has nothing to do with the issue, esp your BIOS firmware.  leave it alone.

---

### Post by carolin3 on 2013-04-21
I have an full install , before when I had 12.10 on this computer suspend worked as it should, before that I had windows (the computer came with it) and hibernate worked :) but now it doesn't

---

### Post by pqwoerituytrueiwoq on 2013-04-21
if it worked on 12.10 and not on 12.04 it is probably the old kernel, i would suggest trying 13.04 and seeing if you like it, the daily iso will have all the updates on it
imo 12.04 was obsolete by the day it came out 12.10 was much better and 13.04 is full of fixes for 12.10

---

### Post by carolin3 on 2013-04-22
yes but the fancy animations when closing windows is too much for this computer, that's why I installed 12.04.
but yes I will probably try 13.04 :D

---


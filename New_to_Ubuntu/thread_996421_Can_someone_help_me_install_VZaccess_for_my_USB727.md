---
title: "Can someone help me install VZaccess for my USB727 network card?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by dblxx on 2008-11-28
I just got a dell mini-9 and want to use my USB727 network card.  The software downloads from the verizon site but it's for windows.

It's here:  [http://www.vzam.net/download/supported.aspx](http://www.vzam.net/download/supported.aspx)

I am new to linux and ubuntu..can anyone walk me through the steps to get the software on my laptop?

Thanks guys & gals.

---

### Post by Mason Whitaker on 2008-11-28
I don't completely understand, but you're trying to use your USB network card on Ubuntu, correct? and it's meant for Windows?

Well obviously there isn't a linux version availible, for you could using it in WINE, but I'm not positive it would work properly.

--Since you're a newbie--
1. go to applications -> add/remove
2. search for "WINE"
   - Make sure the "All available applications" is selected for the search
3. check the box next to "WINE Microsoft compatibility layer"
4. click apply changes on the box below
5. wait for the packages to download and compile
6. download the USB727 network card software if you haven't already
7. double click it, WINE should load it right up.

---

### Post by halitech on 2008-11-28
might be another way, depending on just what the software does. plug the card in and open the terminal and post back the results of
```
lsusb
```so we can at least see if it is recognized.

---

### Post by dblxx on 2008-11-28
david@david:~$ lsusb
Bus 001 Device 002: ID 0c45:63e5 Microdia 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1410:4100  
Bus 002 Device 001: ID 0000:0000  
david@david:~$

---

### Post by halitech on 2008-11-28
ok, no real help there. unplug the device and run the same command and post the output so we can see if there is any change

---

### Post by dblxx on 2008-11-28
david@david:~$ lsusb
Bus 001 Device 002: ID 0c45:63e5 Microdia 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 413c:02b0 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
david@david:~$

---

### Post by halitech on 2008-11-28
ok, there was a change
[COLOR="Red"]Bus 002 Device 003: ID 1410:4100 [/COLOR]

I would guess this is your usb card. Unfortunately it doesn't help out much :(

can you open the terminal again and type in
```
uname -r
```and post the results here

---

### Post by dblxx on 2008-11-28
david@david:~$ uname -r
2.6.24-19-lpia
david@david:~$

---

### Post by halitech on 2008-11-28
what version of Ubuntu do you have installed? from what I'm finding I think it should work if you have kernel version 2.6.27-8

---

### Post by dblxx on 2008-11-28
8.04  Came pre-installed on my Dell mini-9.

---

### Post by halitech on 2008-11-28
ok, I'm guessing you are looking at either upgrading to 8.10 or installing a new kernel

---

### Post by dblxx on 2008-11-28
You tell me, I am following your lead here.  Which one and how?

---

### Post by halitech on 2008-11-28
I guess both have their pros and cons. Check Synaptic and see if the linux-kernel-2.6.27 is there, if it is, check it and apply and that will install it. If not, we are going for an upgrade.

---

### Post by dblxx on 2008-11-28
How do I get to synaptic? (don't kill me):)

---

### Post by dblxx on 2008-11-28
Found it....looking now.

---

### Post by dblxx on 2008-11-28
I did a search for "linux-kernel-2.6.27" and nothing came up.  Was I suppose to put all that in?

---

### Post by jpeddicord on 2008-11-28
> **dblxx said:**
> I did a search for "linux-kernel-2.6.27" and nothing came up.  Was I suppose to put all that in?

2.6.27 isn't in 8.04. If you want the new kernel, your best bet is to upgrade to 8.10. See the following page for details.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I don't know if .27 has included support for VZW chips, but the new NetworkManager in 8.10 might let you configure it manually.

---

### Post by dblxx on 2008-11-28
Problem....when doing the software sources step....the 2 radio buttons in the picture under ubuntu updates are greyed out and I can't click them.

I tried it without changing those 2 and it says I have no updates...even when I changed the long term to normal release ?????

---

### Post by jpeddicord on 2008-11-28
> **dblxx said:**
> Problem....when doing the software sources step....the 2 radio buttons in the picture under ubuntu updates are greyed out and I can't click them.

I tried it without changing those 2 and it says I have no updates...even when I changed the long term to normal release ?????

Be sure to click the "Check" button in Update Manager to fetch the new updates. It will appear at the top of the window, above the list of packages.

If it still doesn't work, press Alt+F2 and enter the following:
```
gksu "update-manager -c"
```

It should then appear.

---

### Post by dblxx on 2008-11-28
Says I have all the latest updates.  I hit check 4 or 5 times now.

---

### Post by dblxx on 2008-11-28
Maybe I have 8.10.

---

### Post by jpeddicord on 2008-11-28
> **dblxx said:**
> Maybe I have 8.10.

Run `lsb_release -a` in a terminal (Applications > Accessories > Terminal); that will tell you your Ubuntu version.

---

### Post by dblxx on 2008-11-28
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
david@david:~$ 


In the system admin list, software sources, updates tab.... all 4 of the choices under ubuntu updates are greyed out and the instructions show I need to click the top 2.  Is that affecting my ability to update to 8.10?

---

### Post by jpeddicord on 2008-11-28
> **dblxx said:**
> In the system admin list, software sources, updates tab.... all 4 of the choices under ubuntu updates are greyed out and the instructions show I need to click the top 2.  Is that affecting my ability to update to 8.10?

Probably, could you paste the contents of the file /etc/apt/sources.list?

---

### Post by dblxx on 2008-11-28
> **jacobmp92 said:**
> Probably, could you paste the contents of the file /etc/apt/sources.list?

Put that in a terminal?

---

### Post by dblxx on 2008-11-28
david@david:~$ file /etc/apt/sources.list?
/etc/apt/sources.list?: ERROR: cannot open `/etc/apt/sources.list?' (No such file or directory)
david@david:~$

---

### Post by jpeddicord on 2008-11-28
> **dblxx said:**
> Put that in a terminal?

Sorry, I meant the just the file itself. You can run this in the terminal to view it quickly:```
cat /etc/apt/sources.list
```

Paste the output of that here. :)

---

### Post by dblxx on 2008-11-28
> **jacobmp92 said:**
> Sorry, I meant the just the file itself. You can run this in the terminal to view it quickly:```
cat /etc/apt/sources.list
```

Paste the output of that here. :)

david@david:~$ cat /etc/apt/sources.list
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
david@david:~$

---

### Post by sdowney717 on 2008-11-28
[http://ilearneditonline.wordpress.com/2008/04/06/how-to-use-usb727-with-pendrive-linux/](http://ilearneditonline.wordpress.com/2008/04/06/how-to-use-usb727-with-pendrive-linux/)

so it can be done, perhaps following along with what they did will work in ubuntu.

---

### Post by dblxx on 2008-11-28
> **sdowney717 said:**
> [http://ilearneditonline.wordpress.com/2008/04/06/how-to-use-usb727-with-pendrive-linux/](http://ilearneditonline.wordpress.com/2008/04/06/how-to-use-usb727-with-pendrive-linux/)

so it can be done, perhaps following along with what they did will work in ubuntu.

Do those commands go into a terminal?

---

### Post by jpeddicord on 2008-11-28
> **dblxx said:**
> david@david:~$ cat /etc/apt/sources.list
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
david@david:~$

Woah - what the.. since when does Dell get their own partner repository just for having a netbook? :-P

Anyway, that would be the problem - Intrepid (8.10) isn't yet supported for the Mini 9.

See these resources for information on the 727 and EVDO configuration:
[http://www.evdoforums.com/thread7379.html](http://www.evdoforums.com/thread7379.html)
[http://www.crystalnetworking.net/?p=17](http://www.crystalnetworking.net/?p=17)
[http://www.evdoforums.com/thread8270.html](http://www.evdoforums.com/thread8270.html)

(The post above was for Mandriva, so it isn't exactly the instructions you'll be looking for. The information in there is worth a read though.)

---

### Post by Michaelg14 on 2008-11-28
I have done what you are trying to do.  I will give you my method but I will also tell you that Intrepid will do it for you automaticly right out of the box.

To do it in Gutsy you will need to use wvdial. There is a graphic front end for it called gnome ppp you can download from symnaptic.  This is the data from my /etc/wvdial.conf file for my modem:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = /dev/ttyUSB0
Username = [email]XXXXXXXXXX@vzw3g.com[/email]
Password = vzw
Baud = 460800

XXXXX=your phone number

Open /etc/wvdial.config with a text editor and paste in that info.  from a terminal type wvdial and it should connect you.

Better yet upgrade to 8.10 and forget it.

There is a way to have etc/wvdial.conf configure itself by reading the information in your modem.  I have done it but don't remember how.  Maybe someone else can contribute that info.

---

### Post by sdowney717 on 2008-11-29
yes they do
you can simply sudo in front of the commands.

---

### Post by jpeddicord on 2008-11-29
> **sdowney717 said:**
> yes they do
you can simply sudo in front of the commands.

Umm... what now?

:)

---

### Post by THE TECH on 2008-12-01
> **Michaelg14 said:**
> I have done what you are trying to do.  I will give you my method but I will also tell you that Intrepid will do it for you automaticly right out of the box.

To do it in Gutsy you will need to use wvdial. There is a graphic front end for it called gnome ppp you can download from symnaptic.  This is the data from my /etc/wvdial.conf file for my modem:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = /dev/ttyUSB0
Username = [email]XXXXXXXXXX@vzw3g.com[/email]
Password = vzw
Baud = 460800

XXXXX=your phone number

Open /etc/wvdial.config with a text editor and paste in that info.  from a terminal type wvdial and it should connect you.

Better yet upgrade to 8.10 and forget it.

There is a way to have etc/wvdial.conf configure itself by reading the information in your modem.  I have done it but don't remember how.  Maybe someone else can contribute that info.

I am on 8.04 and it can't get this to work on mine.  I am also on the Dell mini.

---

### Post by Michaelg14 on 2008-12-02
I'm sorry, I took that info out of my notes on getting it set-up under 8.04 but I don't use it any more.  8.10 does not seem to use wvdial.  I did have a problem with Gutsy not assigning the same usb port everytime it booted up.  You might try

 sudo cat /proc/tty/driver/usbserial

The first listing for gsm modem will be the correct usb port to use.  Also put this line in your /etc/modules file

usbserial vendor=0x1410 product=0x4100

I am working from memory here so I hope this helps.

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> I'm sorry, I took that info out of my notes on getting it set-up under 8.04 but I don't use it any more.  8.10 does not seem to use wvdial.  I did have a problem with Gutsy not assigning the same usb port everytime it booted up.  You might try

 sudo cat /proc/tty/driver/usbserial

The first listing for gsm modem will be the correct usb port to use.  Also put this line in your /etc/modules file

usbserial vendor=0x1410 product=0x4100

I am working from memory here so I hope this helps.

I am a total noob, so I don't know if that was in response to my question or others'.

---

### Post by Michaelg14 on 2008-12-02
> I am a total noob, so I don't know if that was in response to my question or others'. 

That was to anyone trying to get a USB727 modem working in Unbuntu 8.04.

In a terminal type

> gksu gedit /etc/modules


Then enter as the last line in /etc/modules this line.

> usbserial vendor=0x1410 product=0x4100
 

save and exit.
Let me know if it works.

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> That was to anyone trying to get a USB727 modem working in Unbuntu 8.04.

Let me know if it works.

OK, then secondly, can you give a noob some more specific directions on how to setup what you listed.  I have never used Linux before.

---

### Post by Michaelg14 on 2008-12-02
> OK, then secondly, can you give a noob some more specific directions on how to setup what you listed. I have never used Linux before.


Sorry I edited my last message, try reloading and read it again.

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> That was to anyone trying to get a USB727 modem working in Unbuntu 8.04.

In a terminal type



Then enter as the last line in /etc/modules this line.

 

save and exit.
Let me know if it works.

Ok, I did all that.  What next?

---

### Post by Michaelg14 on 2008-12-02
> Ok, I did all that. What next? 


Reboot to get everything operating then in a terminal type "wvdial" without the quotes.  Start up a browser and see if you are connected.

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> Reboot to get everything operating then in a terminal type "wvdial" without the quotes.  Start up a browser and see if you are connected.

I must be missing something.

Do I still need to do all this:

[I]To do it in Gutsy you will need to use wvdial. There is a graphic front end for it called gnome ppp you can download from symnaptic. This is the data from my /etc/wvdial.conf file for my modem:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = /dev/ttyUSB0
Username = [email]XXXXXXXXXX@vzw3g.com[/email]
Password = vzw
Baud = 460800

XXXXX=your phone number

Open /etc/wvdial.config with a text editor and paste in that info. from a terminal type wvdial and it should connect you.
[/I]

When I try to edit the etc/wvdial.config file, it won't let me save the changes and tells me that I don't have permission to edit the file.

---

### Post by Michaelg14 on 2008-12-02
When you open a text editor is has to be opened with sudo or gksu to give it permission to alter files.  For example:

```
gksu gedit /etc/wvdial.conf
```

That will open a graphical text editor (gedit) and allow you to alter the wvdial.conf file.  Copy and past in the info below

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = /dev/ttyUSB0
Username = XXXXXXXXXX@vzw3g.com
Password = vzw
Baud = 460800
```

Make sure that the line username has the phone number of your device in it.  (The password for Verizon is vzw)

You will need to 
```
gksu gedit /etc/modules
``` 
the same way to add the line
```
usbserial vendor=0x1410 product=0x4100
```


Your /etc/modules file should look something like

```
fuse
lp
rtc
usbserial vendor=0x1410 product=0x4100
```

when you are done.

Again, reboot and in a terminal enter wvdial, it should connect you to the internet

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> When you open a text editor is has to be opened with sudo or gksu to give it permission to alter files.  For example:

```
gksu gedit /etc/wvdial.conf
```

That will open a graphical text editor (gedit) and allow you to alter the wvdial.conf file.  Copy and past in the info below

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = /dev/ttyUSB0
Username = XXXXXXXXXX@vzw3g.com
Password = vzw
Baud = 460800
```

Make sure that the line username has the phone number of your device in it.  (The password for Verizon is vzw)

You will need to 
```
gksu gedit /etc/modules
``` 
the same way to add the line
```
usbserial vendor=0x1410 product=0x4100
```


Your /etc/modules file should look something like

```
fuse
lp
rtc
usbserial vendor=0x1410 product=0x4100
```

when you are done.

Again, reboot and in a terminal enter wvdial, it should connect you to the internet

I guess I'm retarded.  I've done all of that but when I enter wvdial into terminal, all I get is this:

WvDial:  Internet dialer version 1.60
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory

---

### Post by Michaelg14 on 2008-12-02
Run this command and post what it gives you.

 ```
sudo cat /proc/tty/driver/usbserial
```

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> Run this command and post what it gives you.

 ```
sudo cat /proc/tty/driver/usbserial
```

0: module:usbserial name:"generic" vendor:1410 product:4100 num_ports:1 port:1 path:usb-0000:00:1d.3-2
1: module:usbserial name:"generic" vendor:1410 product:4100 num_ports:1 port:1 path:usb-0000:00:1d.3-2
2: module:usbserial name:"generic" vendor:1410 product:4100 num_ports:1 port:1 path:usb-0000:00:1d.3-2
3: module:usbserial name:"generic" vendor:1410 product:4100 num_ports:1 port:1 path:usb-0000:00:1d.3-2

---

### Post by cek on 2008-12-02
This is easier than it seems:

1. Unplug your USB727 card.
2. Plug in your USB727 card.
3. Open a terminal
4. In terminal type the command:  dmesg | grep tty

This will give you an output that shows the device name that you plugged the modem into like:  /dev/ttyUSB0

5.  In terminal type the command:  sudo gedit /etc/wvdial.conf

Double check the settings there:
[I][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = XXXXXXXXXXXXX  (this should be the device name from step 4)
Username = [email]XXXXXXXXXX@vzw3g.com[/email]
Password = vzw
Baud = 460800[/I]

6.  in the terminal, type the command:  wvdial

What is the output?  If it still says cannot open /dev/modem then it is not properly reading the /etc/wvdial.conf (since it should use the Modem entry there).

---

### Post by THE TECH on 2008-12-02
> **cek said:**
> This is easier than it seems:

1. Unplug your USB727 card.
2. Plug in your USB727 card.
3. Open a terminal
4. In terminal type the command:  dmesg | grep tty

This will give you an output that shows the device name that you plugged the modem into like:  /dev/ttyUSB0

5.  In terminal type the command:  sudo gedit /etc/wvdial.conf

Double check the settings there:
[I][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = XXXXXXXXXXXXX  (this should be the device name from step 4)
Username = [email]XXXXXXXXXX@vzw3g.com[/email]
Password = vzw
Baud = 460800[/I]

6.  in the terminal, type the command:  wvdial

What is the output?  If it still says cannot open /dev/modem then it is not properly reading the /etc/wvdial.conf (since it should use the Modem entry there).

This is what I get when I do the dmesg | grep tty

[    9.099108] console [tty0] enabled
[   18.806767] usb 5-2: generic converter now attached to ttyUSB0
[   18.806951] usb 5-2: generic converter now attached to ttyUSB1
[   18.807112] usb 5-2: generic converter now attached to ttyUSB2
[   18.807302] usb 5-2: generic converter now attached to ttyUSB3
[    3.487686] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[    3.488344] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[    3.488957] generic ttyUSB2: generic converter now disconnected from ttyUSB2
[    3.489589] generic ttyUSB3: generic converter now disconnected from ttyUSB3
[    4.012059] usb 5-2: generic converter now attached to ttyUSB0
[    4.015231] usb 5-2: generic converter now attached to ttyUSB1
[    4.017122] usb 5-2: generic converter now attached to ttyUSB2
[    4.019121] usb 5-2: generic converter now attached to ttyUSB3
[    2.793699] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[    2.794836] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[    2.796028] generic ttyUSB2: generic converter now disconnected from ttyUSB2
[    2.797160] generic ttyUSB3: generic converter now disconnected from ttyUSB3
[   24.318829] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
[   24.328462] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
[   24.331415] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB2
[   24.334049] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB3


I still get the same error when I try the wvdial in terminal

---

### Post by Michaelg14 on 2008-12-02
When you do that you will find that the USB727 uses four usb slots.  The lowest one is the one to use.

---

### Post by Michaelg14 on 2008-12-02
I am afraid I have used up all I know about it.  The only other thing I might suggest is to load Gnome-ppp from Synaptic.  It is a GUI for wvdial.  When I used 8.04 I also used Gnome-ppp and didn't have any trouble getting it to work.  

My only other suggestion would be to upgrade to 8.10.  Even if you tried a live CD it should work.  At least you could try it and see if you can connect.

Good luck

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> When you do that you will find that the USB727 uses four usb slots.  The lowest one is the one to use.

Huh?  Do I need to change a setting or something???

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> I am afraid I have used up all I know about it.  The only other thing I might suggest is to load Gnome-ppp from Synaptic.  It is a GUI for wvdial.  When I used 8.04 I also used Gnome-ppp and didn't have any trouble getting it to work.  

My only other suggestion would be to upgrade to 8.10.  Even if you tried a live CD it should work.  At least you could try it and see if you can connect.

Good luck

Thanks for all the help.  8.10 is not available for my machine apparantly.

---

### Post by Michaelg14 on 2008-12-02
> Huh? Do I need to change a setting or something???

As far as I can see /dev/ttyUSB0 is the correct entry for the modem. 


> 24.318829] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 24.328462] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 24.331415] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 24.334049] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB3


 It should say GSM Modem when it is recognised, when it said generic converter I don't think Ubuntu recognised it as a modem.

Try 
```
sudo cat /proc/tty/driver/usbserial
```
again.  When I do it I get a listing for GSM Modem not for a generic device.

You might have to unplug and replug the device.

---

### Post by cek on 2008-12-02
if wvdial is still giving you problems, try typing the following in a terminal:

sudo wvdial




I had this working in 8.04 (I have the exact card through Verizon) with both wvdial and Gnome-PPP.  If you can install Gnome-PPP do so and give it a try.

That said, I have since upgraded to 8.10.  In 8.10, this card is recognized automatically by the network manager, simply click on the network manager applet and select the device to connect.  No setup is necessary at all.

---

### Post by THE TECH on 2008-12-02
> **cek said:**
> if wvdial is still giving you problems, try typing the following in a terminal:

sudo wvdial




I had this working in 8.04 (I have the exact card through Verizon) with both wvdial and Gnome-PPP.  If you can install Gnome-PPP do so and give it a try.

That said, I have since upgraded to 8.10.  In 8.10, this card is recognized automatically by the network manager, simply click on the network manager applet and select the device to connect.  No setup is necessary at all.

I tried the sudo thing and it asks me for a password.  Is it the password for the computer or what?

8.10 is not available for the Dell Mini 9 so that's not an option for me.

Maybe I don't even have 8.04??  I can't seem to find info on which version I have installed on this thing.

I wonder why this is so difficult to get done??

My machine already has Gnome Desktop v2.22.2  Is that the same thing as the Gnome-PPP?

---

### Post by Michaelg14 on 2008-12-02
sudo refers to the password you use to log in to Ubuntu.

From your desktop go to system/administration/system monitor
select the system tab at the top and it will give you the version of Ubuntu and gnome you have.

gnome-ppp is a package downloaded from Synaptic package manager.

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> sudo refers to the password you use to log in to Ubuntu.

From your desktop go to system/administration/system monitor
select the system tab at the top and it will give you the version of Ubuntu and gnome you have.

gnome-ppp is a package downloaded from Synaptic package manager.

I downloaded the gnome-ppp.  I also confirmed that I am on 8.04.  How do I tell if the gnome prog will work?

Actually, I was able to find the gnome prog and tried it out.  I can tell that it's at least trying to connect, but I am still not able to get onto the internet.

Here is the log from my recent attempts:

GNOME PPP: Connecting...
GNOME PPP: STDERR: --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DT1,#777
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT1,#777
GNOME PPP: STDERR: NO CARRIER
GNOME PPP: STDERR: --> No Carrier!  Trying again.
GNOME PPP: STDERR: --> Maximum Attempts Exceeded..Aborting!!
GNOME PPP: STDERR: --> Disconnecting at Tue Dec  2 17:23:19 2008

I am using the settings from wvdial for gnome.  Not sure if that is correct or not.

---

### Post by Michaelg14 on 2008-12-02
It looks like Ubuntu found your modem but can't get a carrier from the wireless network.  You have to be in wireless range with a Verizon signal available. Are you sure it is working, have you tried it in windows.  You might also want to double check with Verizon on the phone number and password.  What I gave you works for me but I don't know where you are.  As I recall when I had 8.04 the modem had to be plugged in when the system booted up.  Plugging it in after booting didn't work for some reason.

Good Luck

---

### Post by THE TECH on 2008-12-02
> **Michaelg14 said:**
> It looks like Ubuntu found your modem but can't get a carrier from the wireless network.  You have to be in wireless range with a Verizon signal available. Are you sure it is working, have you tried it in windows.  You might also want to double check with Verizon on the phone number and password.  What I gave you works for me but I don't know where you are.  As I recall when I had 8.04 the modem had to be plugged in when the system booted up.  Plugging it in after booting didn't work for some reason.

Good Luck

Yes, I have signal and it works on my regular laptop, so I don't think that's the issue.

I am located in Southern California.  I will try calling Verizon tomorrow to see what they can tell me, but their customer service isn't that good IMO.  They told me that they don't support Linux, so the tech wasn't able to do anything for me when I was looking for a copy of the VZaccess which they used to have for Linux.

---

### Post by cek on 2008-12-03
> **THE TECH said:**
> I downloaded the gnome-ppp.  I also confirmed that I am on 8.04.  How do I tell if the gnome prog will work?

Actually, I was able to find the gnome prog and tried it out.  I can tell that it's at least trying to connect, but I am still not able to get onto the internet.

Here is the log from my recent attempts:

GNOME PPP: Connecting...
GNOME PPP: STDERR: --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DT1,#777
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT1,#777
GNOME PPP: STDERR: NO CARRIER
GNOME PPP: STDERR: --> No Carrier!  Trying again.
GNOME PPP: STDERR: --> Maximum Attempts Exceeded..Aborting!!
GNOME PPP: STDERR: --> Disconnecting at Tue Dec  2 17:23:19 2008

I am using the settings from wvdial for gnome.  Not sure if that is correct or not.

Try adding this line to the /etc/wvdial.conf file (editing it in the way described above)

Carrier Check = no

Just put that line in the [Dialer Defaults] section.

---

### Post by THE TECH on 2008-12-03
> **cek said:**
> Try adding this line to the /etc/wvdial.conf file (editing it in the way described above)

Carrier Check = no

Just put that line in the [Dialer Defaults] section.

Made no difference.

---

### Post by timcredible on 2008-12-03
to get a usb727 working with ubuntu 8.04, all you have to do is activate it using a windows machine and the vzmanager software (tools->activate), then connect once with windows to get it to download the cell tower info, then after it's activated, you can use gnome-ppp to run the modem in linux - check my sig link for a complete how-to with the setting, phone number, username, etc.  if you're using 8.10 (which installs easily on a dell mini 9, a friend has one), then you have to do nothing after the activation, just click on the network manager icon on the top panel bar and choose 'auto mobile broadband' connection, and it works.  me and 6 friends have these verizon usb cards (we have 4 different types - the 720, the 727, the 150, and the 175, they all work easily with linux, but we've all had to activate them with windows first.

so, my recommendation is to activate the 727 with a windows machine, then install 8.10 (it's very easy and straightforward), then choose 'auto mobile broadband', then right-click on the same icon and tell it to automatically connect every time you login, then you don't have to do anything from then on.  one caveat, 8.10 on the dell mini 9 requires a line to be added to a config file for sound to work - i forget what that file is, but i found that post on this forum.

---

### Post by THE TECH on 2008-12-03
> **timcredible said:**
> to get a usb727 working with ubuntu 8.04, all you have to do is activate it using a windows machine and the vzmanager software (tools->activate), then connect once with windows to get it to download the cell tower info, then after it's activated, you can use gnome-ppp to run the modem in linux - check my sig link for a complete how-to with the setting, phone number, username, etc.  if you're using 8.10 (which installs easily on a dell mini 9, a friend has one), then you have to do nothing after the activation, just click on the network manager icon on the top panel bar and choose 'auto mobile broadband' connection, and it works.  me and 6 friends have these verizon usb cards (we have 4 different types - the 720, the 727, the 150, and the 175, they all work easily with linux, but we've all had to activate them with windows first.

so, my recommendation is to activate the 727 with a windows machine, then install 8.10 (it's very easy and straightforward), then choose 'auto mobile broadband', then right-click on the same icon and tell it to automatically connect every time you login, then you don't have to do anything from then on.  one caveat, 8.10 on the dell mini 9 requires a line to be added to a config file for sound to work - i forget what that file is, but i found that post on this forum.

I've already activated it and it does work on my other computer.

I will check the link in your sig to see if that helps anything.

*edit* I just finished using your tutorial and it says that I'm connected but Firefox says I'm offline.  I try all sorts of sites and they all tell me that I'm offline.  I change the offline mode and it still says that it can't find any web addresses.

How/where do I download the 8.10?  When I try via the update manager, it says there are no updates.

---

### Post by cek on 2008-12-03
> **THE TECH said:**
> I've already activated it and it does work on my other computer.

I will check the link in your sig to see if that helps anything.

How/where do I download the 8.10?  When I try via the update manager, it says there are no updates.

You can get 8.10 here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I know this card will work in 8.04...  sorry we haven't been able to get it up for you.

In any case, here's the original link I used to get it working -- there's some very good info there, worth a read.

[http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)

One thing of interest there is the wvdial.conf that is used, I would try using it:

```

[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = ??????????@vzw3g.com
Password = vzw 
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
```

---

### Post by THE TECH on 2008-12-03
> **cek said:**
> You can get 8.10 here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I know this card will work in 8.04...  sorry we haven't been able to get it up for you.

In any case, here's the original link I used to get it working -- there's some very good info there, worth a read.

[http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)

One thing of interest there is the wvdial.conf that is used, I would try using it:

```

[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = ??????????@vzw3g.com
Password = vzw 
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh] 
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP
```

Yeah, those are the same settings I have.  I am now able to connect but I cannot get onto the web.  Every page I try to access I get the error "address not found".

---

### Post by cek on 2008-12-03
> **THE TECH said:**
> Yeah, those are the same settings I have.  I am now able to connect but I cannot get onto the web.  Every page I try to access I get the error "address not found".



It does connect though?  Click on the Applet that goes to the tray when Gnome-PPP connects.  It should bring up a window with a "Log" button on it.  Click on the log button and post up what the log says.

---

### Post by THE TECH on 2008-12-03
I didn't see any applet or log, but here is what it read in the terminal:

WVCONF: /home/thetech/.wvdial.conf
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATM0
GNOME PPP: STDERR: ATM0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM0L0DT#777
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM0L0DT#777
GNOME PPP: STDERR: CONNECT
GNOME PPP: STDERR: --> Carrier detected.  Starting PPP immediately.
GNOME PPP: STDERR: --> Starting pppd at Wed Dec  3 10:18:14 2008
GNOME PPP: STDERR: --> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
GNOME PPP: STDERR: --> --> PAP (Password Authentication Protocol) may be flaky.
GNOME PPP: STDERR: --> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
GNOME PPP: STDERR: --> --> CHAP (Challenge Handshake) may be flaky.
GNOME PPP: STDERR: --> Pid of pppd: 6347
GNOME PPP: STDERR: --> Using interface ppp0
GNOME PPP: STDERR: --> local  IP address 75.217.135.254
GNOME PPP: STDERR: --> remote IP address 66.174.209.64
GNOME PPP: STDERR: --> primary   DNS address 66.174.92.14
GNOME PPP: STDERR: --> secondary DNS address 69.78.96.14

---

### Post by cek on 2008-12-03
> **THE TECH said:**
> I didn't see any applet or log, but here is what it read in the terminal:

WVCONF: /home/thetech/.wvdial.conf
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> Ignoring malformed input line: ";Do NOT edit this file by hand!"
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.60
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATM0
GNOME PPP: STDERR: ATM0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM0L0DT#777
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM0L0DT#777
GNOME PPP: STDERR: CONNECT
GNOME PPP: STDERR: --> Carrier detected.  Starting PPP immediately.
GNOME PPP: STDERR: --> Starting pppd at Wed Dec  3 10:18:14 2008
GNOME PPP: STDERR: --> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
GNOME PPP: STDERR: --> --> PAP (Password Authentication Protocol) may be flaky.
GNOME PPP: STDERR: --> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
GNOME PPP: STDERR: --> --> CHAP (Challenge Handshake) may be flaky.
GNOME PPP: STDERR: --> Pid of pppd: 6347
GNOME PPP: STDERR: --> Using interface ppp0
GNOME PPP: STDERR: --> local  IP address 75.217.135.254
GNOME PPP: STDERR: --> remote IP address 66.174.209.64
GNOME PPP: STDERR: --> primary   DNS address 66.174.92.14
GNOME PPP: STDERR: --> secondary DNS address 69.78.96.14

This may be a simple drawback in 8.04 with dialup networking (anything that uses ppp is considered "dialup").  The network manager doesn't register the connection, and firefox communicates with the network manager to know if there is a valid internet route.

Open firefix, and click on the file menu.  Near the bottom, see if "Work Offline" is checked.  If it is, uncheck it, then try again.

---

### Post by THE TECH on 2008-12-03
> **cek said:**
> This may be a simple drawback in 8.04 with dialup networking (anything that uses ppp is considered "dialup").  The network manager doesn't register the connection, and firefox communicates with the network manager to know if there is a valid internet route.

Open firefix, and click on the file menu.  Near the bottom, see if "Work Offline" is checked.  If it is, uncheck it, then try again.

Yeah, I had turned off the work offline and it still thinks it's offline.

I'm downloading 8.10 now (it has taken all day so far and I'm only at 54% done downloading) so we'll see if that makes any difference.

---

### Post by timcredible on 2008-12-04
> **THE TECH said:**
> I've already activated it and it does work on my other computer.

I will check the link in your sig to see if that helps anything.

*edit* I just finished using your tutorial and it says that I'm connected but Firefox says I'm offline.  I try all sorts of sites and they all tell me that I'm offline.  I change the offline mode and it still says that it can't find any web addresses.

How/where do I download the 8.10?  When I try via the update manager, it says there are no updates.

you're online, but firefox only looks at the network manager to see if you're online, and since you're not using network manager in 8.04 with the 727 card, firefox thinks you're not connected.  so you have to go to into a network config file and fix that so that firefox doesn't ever check to see if you're online or not, but I don't remember what it is since i use 8.10.  you say you have 8.10 now?  just install that, you'll be glad you did, it'll be easier.

---

### Post by THE TECH on 2008-12-04
> **timcredible said:**
> you're online, but firefox only looks at the network manager to see if you're online, and since you're not using network manager in 8.04 with the 727 card, firefox thinks you're not connected.  so you have to go to into a network config file and fix that so that firefox doesn't ever check to see if you're online or not, but I don't remember what it is since i use 8.10.  you say you have 8.10 now?  just install that, you'll be glad you did, it'll be easier.

I downloaded the 8.10 directly to my Dell Mini, but it only gives me an option to write a cd and since there is no cd drive on the Mini, there is no way for me to do that.  Any idea how to install the 8.10 on my machine?

---

### Post by cek on 2008-12-04
> **THE TECH said:**
> I downloaded the 8.10 directly to my Dell Mini, but it only gives me an option to write a cd and since there is no cd drive on the Mini, there is no way for me to do that.  Any idea how to install the 8.10 on my machine?

That will be problematic....

let's try this first to rule out firefox issues:

Connect to the internet with the 727 card using GnomePPP (ensure you get primary and secondary DNS addresses shown as above)

Open terminal and type:
ping -c 3 [www.google.com](www.google.com)

---

### Post by THE TECH on 2008-12-04
> **cek said:**
> That will be problematic....

let's try this first to rule out firefox issues:

Connect to the internet with the 727 card using GnomePPP (ensure you get primary and secondary DNS addresses shown as above)

Open terminal and type:
ping -c 3 [www.google.com](www.google.com)

Ok, here's what I got:

PING [www.l.google.com](www.l.google.com) (209.85.173.103) 56(84) bytes of data.
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=1 ttl=239 time=106 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=2 ttl=239 time=98.8 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=3 ttl=239 time=104 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 98.837/103.396/106.472/3.288 ms

---

### Post by cek on 2008-12-04
> **THE TECH said:**
> Ok, here's what I got:

PING [www.l.google.com](www.l.google.com) (209.85.173.103) 56(84) bytes of data.
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=1 ttl=239 time=106 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=2 ttl=239 time=98.8 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=3 ttl=239 time=104 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 98.837/103.396/106.472/3.288 ms


Good news is -- you're up, connected to the net and able to get out.

Bad news is -- Firefox won't connect.

See this post, and make the suggested changes then try again:
[http://ubuntuforums.org/showpost.php?p=5060822&postcount=6](http://ubuntuforums.org/showpost.php?p=5060822&postcount=6)

---

### Post by THE TECH on 2008-12-04
> **cek said:**
> Good news is -- you're up, connected to the net and able to get out.

Bad news is -- Firefox won't connect.

See this post, and make the suggested changes then try again:
[http://ubuntuforums.org/showpost.php?p=5060822&postcount=6](http://ubuntuforums.org/showpost.php?p=5060822&postcount=6)

Thanks!!  It worked perfectly and I am now online with the 727.

I really appreciate all your help!!

---

### Post by jsmac8218 on 2008-12-04
> **timcredible said:**
> to get a usb727 working with ubuntu 8.04, all you have to do is activate it using a windows machine and the vzmanager software (tools->activate), then connect once with windows to get it to download the cell tower info, then after it's activated, you can use gnome-ppp to run the modem in linux - check my sig link for a complete how-to with the setting, phone number, username, etc.  if you're using 8.10 (which installs easily on a dell mini 9, a friend has one), then you have to do nothing after the activation, just click on the network manager icon on the top panel bar and choose 'auto mobile broadband' connection, and it works.  me and 6 friends have these verizon usb cards (we have 4 different types - the 720, the 727, the 150, and the 175, they all work easily with linux, but we've all had to activate them with windows first.

so, my recommendation is to activate the 727 with a windows machine, then install 8.10 (it's very easy and straightforward), then choose 'auto mobile broadband', then right-click on the same icon and tell it to automatically connect every time you login, then you don't have to do anything from then on.  one caveat, 8.10 on the dell mini 9 requires a line to be added to a config file for sound to work - i forget what that file is, but i found that post on this forum.

Hey Tim, I see above that you said a friend upgraded his Mini 9 to 8.10. I am trying to get my new mini 9 to show that an upgrade is available. I do NOT have an external DVD/CD drive so I need to do it as an upgrade. How did you do it? I'm also very new to Ubunutu/Linux and sould use a similar step by step approach that you've given in this chain. I have the step by step link from the getubunutu website but it descibes how ubunutu will see 8.10 as an upgrade, my mini is not doing that for me.

Thanks

PS: Your suggestion to use gnome-ppp worked perfectly for me. First try it recognized my card, usb727, and connected. I also had to uncheck the "work offline" selection, then restarted firefox and it worked great!

---


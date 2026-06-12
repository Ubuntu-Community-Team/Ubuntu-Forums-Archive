---
title: "need help with how to browse a camera's disk"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by holdie on 2008-06-22
Hey everybody, I'm using a Canon Powershot A560 and I'm trying to access my camera as though it were a hard disk.  Currently, when I turn on the camera and plug it in, ubuntu asks if I want to import photos...if I click yes, then it brings up Fspot, if I say no, then it essentially ignores the camera.  What I'd like is to access the camera outside of Fspot, but I don't see any icons that are associated with such as USB drives, devices, etc...

any ideas?

---

### Post by pytheas22 on 2008-06-22
If you say no when Ubuntu asks if it should open the photos in fspot, try going to the Places menu at the top of the desktop and see if the camera is listed there.  If it's not, open up a folder (any folder) and in the left pane, your camera should be listed.  If it's still not there, then please open a terminal and, with the camera plugged in, type:
```

ls /media
```

and please post the output here.

---

### Post by Happy_Man on 2008-06-22
Hm, check in /dev for anything that resembles your camera (eg sdb? or xcd? or something along those lines) and then enter this into your terminal (I'm going to assume xcd3 for this)

```
sudo mkdir /media/camera
sudo mount /dev/xcd3 /media/camera
```

Then go to /media/camera and see if it works.

---

### Post by holdie on 2008-06-23
I don't see any of the files that you mentioned (and it isn't mounted to /media)...

I have an sdb1 but that's only for my MyBook...other than that can't see anything except a bunch of usbdevice files.

---

### Post by wolfen69 on 2008-06-23
download gthumb and try that. just go to file>import photos. great app. then you can save your photos wherever you want.

---

### Post by indytim on 2008-06-23
Getting back to your original question (how do I browse the camera content?).... What happens if you just double click the icon of the mounted camera on the desktop?

IndyTim

---

### Post by holdie on 2008-06-23
@wolfen: I don't have a problem importing the photos, but I want to access them while they're still on the camera

@indytim: There isn't an icon of the camera on the desktop, that's what's weirding me out

---

### Post by pytheas22 on 2008-06-23
If you tell Ubuntu to open the photos in fspot after plugging in the camera, does it have an entry in /media while fspot is open?

Something strange is going on because obviously the system has a driver for your camera if you can open it using fspot, so it's weird that you don't seem to be able to mount it any other way...

---

### Post by philinux on 2008-06-23
I've had a thread here with the same thing. When you press ignore it's supposed to mount the memory card as a mass storage device. It did this in Gutsy. 

But now it don't.

[http://ubuntuforums.org/showthread.php?t=836189](http://ubuntuforums.org/showthread.php?t=836189)

So if anyone has an idea....

---

### Post by markbuntu on 2008-06-23
You can always change the media setting in nautilus/file management so fspot does not open when you plug in your camera. If you choose do noting it should just put an icon on your Desktop.

---

### Post by philinux on 2008-06-24
It should but it doesn't. :confused:

---

### Post by muguwmp67 on 2008-06-24
I'm having the same problem.  Although I can access the camera from fspot and gthumb, I cannot access it from nautilus.  I don't see anything in /media or /dev either.

I can access the pictures, but the camera's memory does not get mounted as a mass storage device.  This is kind of important, as I cannot access videos on the camera at the moment.

---

### Post by pytheas22 on 2008-06-25
muguwmp67,

what kind of camera do you have?

For both of you with this problem: does

```
lsusb
```

show any sign of your camera when it's plugged in?  And are you both absolutely positive that nothing is showing up in /dev?  Even when you're browsing photos in fspot, /dev doesn't include any entry for your camera?

Also, if possible, has either of you tried swapping the memory cards from your cameras into another camera or disk reader to see if you can mount them through that?  Maybe the problem isn't the camera itself so much as the memory card.

---

### Post by muguwmp67 on 2008-06-25
Its a Canon Powershot SD1100 IS Digital Elph.  
Do you need a serial number?

Yes, the camera is detected on the usb port.  I'm pretty sure fspot wouldn't be able to import images otherwise.  But here goes:

Before plugging in:
```
dell-laptop:~$ lsusb
Bus 001 Device 001: ID 0000:0000  

```

After:```

mcginnism@dell-laptop:~$ lsusb
Bus 001 Device 002: ID 04a9:3184 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000 
``` 

The only changes I see (that look remotely relevant) in /dev after I plug the camera in are a series of entries that look like "usbdev1.3_ep83", "..._ep80", "..._ep01", "..._ep00".  I also see an scd0 entry (my CD player), sd(1,2,5) entries (hard drive), no xcd entries.  

I really don't think you want me to post the full contents of my /dev directory.

I have 2 memory cards for the camera.  They both function properly in the camera.  One of them is a microSD that I can also use with my phone.  It works just fine in my phone.  I'm not rich (which is one reason why I use Ubuntu) and therefore, I do not have another camera.  My cell phone is bluetooth and my laptop does not support bluetooth.

---

### Post by pytheas22 on 2008-06-25
Thanks for the information.

You could try installing gtkam:
```

sudo apt-get install gtkam
```

I think it basically lets you browse your camera as if it were a disk.  I'm not sure if it will let you pull off video as well but it might.

I also admit that I'm sort of shooting in the dark here, as I've never personally trouble-shot a camera before on Ubuntu.  I'm just going off of what I'm reading online.  If anyone who knows more about cameras and Linux has suggestions, please jump in.

---

### Post by markbuntu on 2008-06-25
You could be having some sort of permissions problem which would prevent nautilus from seeing the camera. Try 

gksudo nautilus

to run nautilus as root and see if you can see your camera in /dev or somewhere else.

---

### Post by muguwmp67 on 2008-06-25
Here.  Tell me where the camera is:

```
dell-laptop:~$ lsusb
Bus 001 Device 004: ID 04a9:3184 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  
dell-laptop:~$ sudo ls /dev
adsp	   ptybb  ptyq9  ptyv7	ram13	    tty51  ttydd  ttys7  ttyx5
agpgart    ptybc  ptyqa  ptyv8	ram14	    tty52  ttyde  ttys8  ttyx6
audio	   ptybd  ptyqb  ptyv9	ram15	    tty53  ttydf  ttys9  ttyx7
bus	   ptybe  ptyqc  ptyva	ram2	    tty54  ttye0  ttysa  ttyx8
cdrom	   ptybf  ptyqd  ptyvb	ram3	    tty55  ttye1  ttysb  ttyx9
console    ptyc0  ptyqe  ptyvc	ram4	    tty56  ttye2  ttysc  ttyxa
core	   ptyc1  ptyqf  ptyvd	ram5	    tty57  ttye3  ttysd  ttyxb
disk	   ptyc2  ptyr0  ptyve	ram6	    tty58  ttye4  ttyse  ttyxc
dri	   ptyc3  ptyr1  ptyvf	ram7	    tty59  ttye5  ttysf  ttyxd
dsp	   ptyc4  ptyr2  ptyw0	ram8	    tty6   ttye6  ttyt0  ttyxe
fd	   ptyc5  ptyr3  ptyw1	ram9	    tty60  ttye7  ttyt1  ttyxf
fd0	   ptyc6  ptyr4  ptyw2	random	    tty61  ttye8  ttyt2  ttyy0
fd0u1040   ptyc7  ptyr5  ptyw3	rtc	    tty62  ttye9  ttyt3  ttyy1
fd0u1120   ptyc8  ptyr6  ptyw4	scd0	    tty63  ttyea  ttyt4  ttyy2
fd0u1440   ptyc9  ptyr7  ptyw5	sda	    tty7   ttyeb  ttyt5  ttyy3
fd0u1600   ptyca  ptyr8  ptyw6	sda1	    tty8   ttyec  ttyt6  ttyy4
fd0u1680   ptycb  ptyr9  ptyw7	sda2	    tty9   ttyed  ttyt7  ttyy5
fd0u1722   ptycc  ptyra  ptyw8	sda5	    ttya0  ttyee  ttyt8  ttyy6
fd0u1743   ptycd  ptyrb  ptyw9	sequencer   ttya1  ttyef  ttyt9  ttyy7
fd0u1760   ptyce  ptyrc  ptywa	sequencer2  ttya2  ttyp0  ttyta  ttyy8
fd0u1840   ptycf  ptyrd  ptywb	sg0	    ttya3  ttyp1  ttytb  ttyy9
fd0u1920   ptyd0  ptyre  ptywc	sg1	    ttya4  ttyp2  ttytc  ttyya
fd0u360    ptyd1  ptyrf  ptywd	shm	    ttya5  ttyp3  ttytd  ttyyb
fd0u720    ptyd2  ptys0  ptywe	snapshot    ttya6  ttyp4  ttyte  ttyyc
fd0u800    ptyd3  ptys1  ptywf	snd	    ttya7  ttyp5  ttytf  ttyyd
fd0u820    ptyd4  ptys2  ptyx0	sndstat     ttya8  ttyp6  ttyu0  ttyye
fd0u830    ptyd5  ptys3  ptyx1	sr0	    ttya9  ttyp7  ttyu1  ttyyf
full	   ptyd6  ptys4  ptyx2	stderr	    ttyaa  ttyp8  ttyu2  ttyz0
fuse	   ptyd7  ptys5  ptyx3	stdin	    ttyab  ttyp9  ttyu3  ttyz1
hpet	   ptyd8  ptys6  ptyx4	stdout	    ttyac  ttypa  ttyu4  ttyz2
initctl    ptyd9  ptys7  ptyx5	tty	    ttyad  ttypb  ttyu5  ttyz3
input	   ptyda  ptys8  ptyx6	tty0	    ttyae  ttypc  ttyu6  ttyz4
kmem	   ptydb  ptys9  ptyx7	tty1	    ttyaf  ttypd  ttyu7  ttyz5
kmsg	   ptydc  ptysa  ptyx8	tty10	    ttyb0  ttype  ttyu8  ttyz6
log	   ptydd  ptysb  ptyx9	tty11	    ttyb1  ttypf  ttyu9  ttyz7
loop0	   ptyde  ptysc  ptyxa	tty12	    ttyb2  ttyq0  ttyua  ttyz8
lp0	   ptydf  ptysd  ptyxb	tty13	    ttyb3  ttyq1  ttyub  ttyz9
MAKEDEV    ptye0  ptyse  ptyxc	tty14	    ttyb4  ttyq2  ttyuc  ttyza
mem	   ptye1  ptysf  ptyxd	tty15	    ttyb5  ttyq3  ttyud  ttyzb
mixer	   ptye2  ptyt0  ptyxe	tty16	    ttyb6  ttyq4  ttyue  ttyzc
net	   ptye3  ptyt1  ptyxf	tty17	    ttyb7  ttyq5  ttyuf  ttyzd
null	   ptye4  ptyt2  ptyy0	tty18	    ttyb8  ttyq6  ttyv0  ttyze
nvidia0    ptye5  ptyt3  ptyy1	tty19	    ttyb9  ttyq7  ttyv1  ttyzf
nvidiactl  ptye6  ptyt4  ptyy2	tty2	    ttyba  ttyq8  ttyv2  urandom
oldmem	   ptye7  ptyt5  ptyy3	tty20	    ttybb  ttyq9  ttyv3  usbdev1.1_ep00
parport0   ptye8  ptyt6  ptyy4	tty21	    ttybc  ttyqa  ttyv4  usbdev1.1_ep81
port	   ptye9  ptyt7  ptyy5	tty22	    ttybd  ttyqb  ttyv5  usbdev1.4_ep00
ppp	   ptyea  ptyt8  ptyy6	tty23	    ttybe  ttyqc  ttyv6  usbdev1.4_ep02
psaux	   ptyeb  ptyt9  ptyy7	tty24	    ttybf  ttyqd  ttyv7  usbdev1.4_ep81
ptmx	   ptyec  ptyta  ptyy8	tty25	    ttyc0  ttyqe  ttyv8  usbdev1.4_ep83
pts	   ptyed  ptytb  ptyy9	tty26	    ttyc1  ttyqf  ttyv9  vcs
ptya0	   ptyee  ptytc  ptyya	tty27	    ttyc2  ttyr0  ttyva  vcs1
ptya1	   ptyef  ptytd  ptyyb	tty28	    ttyc3  ttyr1  ttyvb  vcs2
ptya2	   ptyp0  ptyte  ptyyc	tty29	    ttyc4  ttyr2  ttyvc  vcs3
ptya3	   ptyp1  ptytf  ptyyd	tty3	    ttyc5  ttyr3  ttyvd  vcs4
ptya4	   ptyp2  ptyu0  ptyye	tty30	    ttyc6  ttyr4  ttyve  vcs5
ptya5	   ptyp3  ptyu1  ptyyf	tty31	    ttyc7  ttyr5  ttyvf  vcs6
ptya6	   ptyp4  ptyu2  ptyz0	tty32	    ttyc8  ttyr6  ttyw0  vcs7
ptya7	   ptyp5  ptyu3  ptyz1	tty33	    ttyc9  ttyr7  ttyw1  vcs8
ptya8	   ptyp6  ptyu4  ptyz2	tty34	    ttyca  ttyr8  ttyw2  vcsa
ptya9	   ptyp7  ptyu5  ptyz3	tty35	    ttycb  ttyr9  ttyw3  vcsa1
ptyaa	   ptyp8  ptyu6  ptyz4	tty36	    ttycc  ttyra  ttyw4  vcsa2
ptyab	   ptyp9  ptyu7  ptyz5	tty37	    ttycd  ttyrb  ttyw5  vcsa3
ptyac	   ptypa  ptyu8  ptyz6	tty38	    ttyce  ttyrc  ttyw6  vcsa4
ptyad	   ptypb  ptyu9  ptyz7	tty39	    ttycf  ttyrd  ttyw7  vcsa5
ptyae	   ptypc  ptyua  ptyz8	tty4	    ttyd0  ttyre  ttyw8  vcsa6
ptyaf	   ptypd  ptyub  ptyz9	tty40	    ttyd1  ttyrf  ttyw9  vcsa7
ptyb0	   ptype  ptyuc  ptyza	tty41	    ttyd2  ttys0  ttywa  vcsa8
ptyb1	   ptypf  ptyud  ptyzb	tty42	    ttyd3  ttyS0  ttywb  watchdog
ptyb2	   ptyq0  ptyue  ptyzc	tty43	    ttyd4  ttys1  ttywc  xconsole
ptyb3	   ptyq1  ptyuf  ptyzd	tty44	    ttyd5  ttyS1  ttywd  zero
ptyb4	   ptyq2  ptyv0  ptyze	tty45	    ttyd6  ttys2  ttywe
ptyb5	   ptyq3  ptyv1  ptyzf	tty46	    ttyd7  ttyS2  ttywf
ptyb6	   ptyq4  ptyv2  ram0	tty47	    ttyd8  ttys3  ttyx0
ptyb7	   ptyq5  ptyv3  ram1	tty48	    ttyd9  ttyS3  ttyx1
ptyb8	   ptyq6  ptyv4  ram10	tty49	    ttyda  ttys4  ttyx2
ptyb9	   ptyq7  ptyv5  ram11	tty5	    ttydb  ttys5  ttyx3
ptyba	   ptyq8  ptyv6  ram12	tty50	    ttydc  ttys6  ttyx4

```
While you are doing that, I'll continue googling, searching the ubuntu forums, trying to find workarounds and everything else that I've been doing to find an answer to this problem.  I've found a LOT of threads that describe similar problems with their cameras in Hardy.  None of them have helped so far.

---

### Post by pytheas22 on 2008-06-25
> Here. Tell me where the camera is:

A better way to do this (I think) and make sure no one is missing anything would be to use a little bash.  With the camera unplugged, type:
```

ls /dev > unplugged
```

then plug it in and type:
```

ls /dev > plugged
```

now:
```

diff unplugged plugged
```

the output is going to list differences in /dev before and after the camera is plugged in.  What is the output of the diff command?

It may also not hurt to see some dmesg.  What is the output of:

```
dmesg
```

after you plug the camera in and tell Ubuntu to mount it as a disk?  Maybe there's some driver issue or whatnot that this would reveal.

---

### Post by mc4man on 2008-06-26
I believe it's caused by the mode the camera is connecting by. Mine connects in PTP mode and won't been seen as a drive as such. I'm more disappointed a little script that I use in gutsy only half works in hardy 
(imports and sorts photos into dir's based on EXIF time and date, only imports in hardy, won't create dir's and sort)

Somewhat dated but decent info
[http://www.teaser.fr/~hfiguiere/linux/digicam.html](http://www.teaser.fr/~hfiguiere/linux/digicam.html)

---

### Post by muguwmp67 on 2008-06-26
Well, that certainly isn't the answer I wanted to hear, but it would explain a lot.  I think I'll try the camera out on someone's windows box tomorrow, and see if its the same way there.

---

### Post by mc4man on 2008-06-26
> certainly isn't the answer  Not really an answer, more observation
There are 3 questions that arise from this
Are both modes available and the Os is at fault?
Is only PTP available?  (SOL)
Can the mode be set on the camera? (maybe like PTP , Normal)

Edit: did you see your camera on list in link? (scroll way down)

---

### Post by muguwmp67 on 2008-06-26
I've just finished searching the manual and it says that it supports mtp/ptp.  I found the following thread and it looks like its ptp or nothing:
[http://ubuntuforums.org/showthread.php?t=592539&highlight=camera+mtp](http://ubuntuforums.org/showthread.php?t=592539&highlight=camera+mtp)

I'm still learning the camera and I found some good news.  The .avi files do appear in fspot.  I'll still get a card reader so I can access the card directly when I need to.

---

### Post by mc4man on 2008-06-26
> I'll still get a card reader When you do the action for that(card) is set in file management -> media, not in removable drives .....

---


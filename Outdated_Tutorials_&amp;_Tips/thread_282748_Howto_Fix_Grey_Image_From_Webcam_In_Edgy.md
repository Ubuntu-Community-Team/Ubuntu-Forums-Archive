---
title: "Howto: Fix Grey Image From Webcam In Edgy"
date: 2006-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by OffHand on 2006-10-23
The PWC webcam driver doesn't work anymore in Edgy. Webcams only show a grey image. Just follow this guide to install a PWC driver that does work.
It shouldn't be too hard. Good luck!

1] download [http://www.saillard.org/linux/pwc/files/pwc-10.0.12-rc1.tar.bz2](http://www.saillard.org/linux/pwc/files/pwc-10.0.12-rc1.tar.bz2)

2] extract in your home folder

- open your terminal- 

You have to install the Linux headers for your kernel:

3] Check what kind of kernel you use: ```
uname -r
```

4] ```
sudo apt-get install linux-headers-2.6.17-10-generic
```
(If you are running the 386 kernel replace generic with 386.)

5] You need build-essential to compile it.
```
sudo apt-get install build-essential
```

6] type: ```
cd pwc<tab><enter>
```
(<tab> represents the tab key on your keyboard, the same goes for <enter>. Do not use copy/paste.)

7] type: ```
make
```
8] type: ```
find /lib/modules/`uname -r`/ -name "pwc*.ko*"
```
9] type: ```
sudo rm <name of the file.ko>
``` 
(in my case: sudo rm /lib/modules/2.6.17-10-generic/kernel/drivers/media/video/pwc/pwc.ko)

10] type: ```
sudo cp ~/pwc-10.0.12-rc1/pwc.ko /lib/modules/2.6.17-10-generic/kernel/drivers/media/video/pwc/pwc.ko
```
11] type: ```
sudo depmod -a
```

reboot your computer

---

### Post by ersplus on 2006-10-25
Thanks a lot !!! :)

---

### Post by trash on 2006-11-03
worked for my logitech 3000 pro... Thanks!

---

### Post by spirit59fr on 2006-11-06
Hi,

I have the same problem, yet when trying the solution you gave, I got stuck while compiling :

> make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/laptop/pwc-10.0.12-rc1 modules
make: *** /lib/modules/2.6.17-10-386/build: Aucun fichier ou répertoire de ce type. Arrêt.
make: *** [all] Erreur 2

Any idea why ?

(By the way, how do you quote code here ? Can't find the icon for that in the message editor. Sorry, first time here !)

---

### Post by OffHand on 2006-11-06
> **spirit59fr said:**
> Hi,

I have the same problem, yet when trying the solution you gave, I got stuck while compiling :



Any idea why ?

(By the way, how do you quote code here ? Can't find the icon for that in the message editor. Sorry, first time here !)

you can make the code block with (code)actual code(/code); replace ( and ) for [ and ]. I do not speak French so I cannot read the error message. Did you install build-essential? 
```
sudo apt-get install build-essential
```

---

### Post by spirit59fr on 2006-11-06
Right... I apt-get installed the build-essential package and a few dependencies, yet when trying

```
make
```

it returns exactly the same message :

```
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/laptop/pwc-10.0.12-rc1 modules
make: *** /lib/modules/2.6.17-10-386/build: Aucun fichier ou répertoire de ce type. Arrêt.
make: *** [all] Erreur 2
```

which (for the French bits) roughly means : "No file or folder of that type. Stop.", then "Error 2".

Will that help you help me ?! lol

---

### Post by OffHand on 2006-11-06
> **spirit59fr said:**
> Right... I apt-get installed the build-essential package and a few dependencies, yet when trying

which (for the French bits) roughly means : "No file or folder of that type. Stop.", then "Error 2".

Will that help you help me ?! lol

Sorry I can't help you but I suppose it's just something missing you need to run 'make' properly. Maybe you should make a separate thread about this error in the General Help Section of the forum.

---

### Post by blkno1 on 2006-11-06
Worked perfect to fix my Logitech Quickcam Orbit.

Thanks

---

### Post by webfootedchicken on 2006-11-08
> **OffHand said:**
> you can make the code block with (code)actual code(/code); replace ( and ) for [ and ]. I do not speak French so I cannot read the error message. Did you install build-essential? 
```
sudo apt-get install build-essential
```
I get the same (I upgraded from Dapper to Edgy and this happened, was OK in Dapper) - in english it says:

myusername@mycomputer:~/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/myusername/pwc-10.0.12-rc1 modules
make: *** /lib/modules/2.6.17-10-386/build: No such file or directory.  Stop.
make: *** [all] Error 2

So then I tried creating a "build" directory in the /lib/modules folder, but now get the following error:

myusername@mycomputer:~/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/myusername/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/lib/modules/2.6.17-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-386/build'
make: *** [all] Error 2

Anyone got any ideas?

---

### Post by webfootedchicken on 2006-11-08
OK, got it working. Do *not* create the "build" folder manually like I did - D'Oh.

Go to Synaptic or use sudo and install "linux-headers-2.6.17-10-386" (Note my machine architecture is 386)

Then perform the "make" and follow the rest of the prompts in this faq. I actually followed a different/similar guide after installing the headers and all is working A-OK [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) "Edgy troubleshooting section".

HTH

Cheers,

WFC

---

### Post by OffHand on 2006-11-08
> **webfootedchicken said:**
> OK, got it working. Do *not* create the "build" folder manually like I did - D'Oh.

Go to Synaptic or use sudo and install "linux-headers-2.6.17-10-386" (Note my machine architecture is 386)

Then perform the "make" and follow the rest of the prompts in this faq. I actually followed a different/similar guide after installing the headers and all is working A-OK [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) "Edgy troubleshooting section".

HTH

Cheers,

WFC

Thnx webfootedchick, I will update my howto  :)

---

### Post by cosine7 on 2006-11-16
Worked for me too thanks.

---

### Post by ema85b on 2006-11-17
Thanks thousands I was driving crazy and finally I have found this post :mrgreen: :mrgreen:

---

### Post by roobarb! on 2006-11-22
I found that I was still getting problems with the "No such file or directory" error, but I was helpfully pointed in the right direction in [this thread]("http://www.ubuntuforums.org/showthread.php?t=300041").

---

### Post by leetrefz on 2006-11-28
I've got the generic kernel thing installed. Then this happens:
> $ cd pwc<tab><enter>
bash: syntax error near unexpected token `<'


I just cut and pasted it... I'm always getting bizarre errors.

---

### Post by OffHand on 2006-11-28
> **leetrefz said:**
> I've got the generic kernel thing installed. Then this happens:

$ cd pwc<tab><enter>
bash: syntax error near unexpected token `<' 

I just cut and pasted it... I'm always getting bizarre errors.

Hi. That part means that you have to press the tab key on your keyboard first  (to complete the name) and the enter key after that to enter that directory.
So in the terminal you type cd pwc first, then hit the tab key and after that the enter key.

---

### Post by WishMaster on 2006-11-28
Logitech Quickcam Zoom

In Camorama, the cam got recognized, but I had a grey image.
So I applied your 'patch'.
When I send my cam with aMSN, there is video, but is WAAAAAY to light.
When I try to config within aMSN, it says "no device connected".

When I open Camorama: "could not connect to video device (/dev/video0)
Please check connection"

*edit*
Just played around with it: it seems to me like he doesn't close the connection...
If I close all apps, and then run Camorama, I can adjust settings. But if I then close Camorama and send with aMSN --> no device.

Also the other way around: first aMSN, it works. I close the cam-session and open Camorama --> no device.
in aMSN it is still to bright...

I thought 6.10 was supposed to be 'cutting edge'. I was better of with Dapper...
How is it possible that they f*ck up something that used to work?

---

### Post by OffHand on 2006-11-28
> **WishMaster said:**
> Logitech Quickcam Zoom

In Camorama, the cam got recognized, but I had a grey image.
So I applied your 'patch'.
When I send my cam with aMSN, there is video, but is WAAAAAY to light.
When I try to config within aMSN, it says "no device connected".

When I open Camorama: "could not connect to video device (/dev/video0)
Please check connection"

*edit*
Just played around with it: it seems to me like he doesn't close the connection...
If I close all apps, and then run Camorama, I can adjust settings. But if I then close Camorama and send with aMSN --> no device.

Also the other way around: first aMSN, it works. I close the cam-session and open Camorama --> no device.
in aMSN it is still to bright...

I thought 6.10 was supposed to be 'cutting edge'. I was better of with Dapper...
How is it possible that they f*ck up something that used to work?

I agree this is something that shouldn't have to patch our selfs. I just checked my cam with both Camorama and aMSN: both pictures look good and are almost identical.

---

### Post by WishMaster on 2006-11-28
If I want to use the cam, I have to:
1. exit all programs
2. restart them
3. config brightness/contrast

Everytime again...

This sucks....

Oh well, many thanks for the fix 
and    [-(  ](*,)  [-( to the Edgy "programmers"

---

### Post by leetrefz on 2006-11-28
more stupid problems I'm afraid. 

chief@chief-toshiba:~/pwc-10.0.12-rc1$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by OffHand on 2006-11-29
> **leetrefz said:**
> more stupid problems I'm afraid. 

chief@chief-toshiba:~/pwc-10.0.12-rc1$ make
make: *** No targets specified and no makefile found.  Stop.
Try to install build-essential first, then try to run 'make' again.
```
sudo apt-get install build-essential
```

---

### Post by leetrefz on 2006-11-29
I had the folder like this:
/home/chief/pwc-10.0.12-rc1/pwc-10.0.12-rc1

not sure how it got that way. put it right & it worked!! maybe build-essential isn't 100% necessary after all?

feel like a bit of a hotshot watching all that code work right :cool:

---

### Post by OffHand on 2006-11-29
> **leetrefz said:**
> I had the folder like this:
/home/chief/pwc-10.0.12-rc1/pwc-10.0.12-rc1

not sure how it got that way. put it right & it worked!! maybe build-essential isn't 100% necessary after all?

feel like a bit of a hotshot watching all that code work right :cool:

I'm glad you got it working  :) Enjoy

P.S. build-essential is needed if you want to compile stuff ;)

---

### Post by leetrefz on 2006-12-05
after this is done can i delete pwc-10.0.12-rc1 from home?

---

### Post by OffHand on 2006-12-06
> **leetrefz said:**
> after this is done can i delete pwc-10.0.12-rc1 from home?
Yes you can.

---

### Post by webmadman on 2006-12-10
Thanks, worked like a charm!

---

### Post by AGM-86 on 2006-12-13
OffHand, thanks for the fix, 5 feet of snow in the driveway this November, and need to keep an eye out on the plow guy. :shock:   Worked great for me.

---

### Post by Kreuger on 2006-12-27
ARGH. I've done this twice now. Would've been once but I formatted my computer. Now I'm doing it a third time (and I didn't even format or anything it just went grey again) why does it keep doing it?

---

### Post by Shay Stephens on 2006-12-28
I gave this a whirl and it didn't help.  However, I am happy to report this is the first time I have successfully compiled **anything**.  So there is a bright spot out of all this :-)

---

### Post by OffHand on 2006-12-28
> **Kreuger said:**
> ARGH. I've done this twice now. Would've been once but I formatted my computer. Now I'm doing it a third time (and I didn't even format or anything it just went grey again) why does it keep doing it?

If the kernel gets updated you will have to re-install it.

---

### Post by OffHand on 2006-12-28
> **Shay Stephens said:**
> I gave this a whirl and it didn't help.  However, I am happy to report this is the first time I have successfully compiled **anything**.  So there is a bright spot out of all this :-)

Does your webcam use the pwc driver? If it does my guide should fix your broken webcam.

---

### Post by Shay Stephens on 2006-12-28
It should, it's a Philips SPC701NC webcam, but I can't get it to work for nothing.  I also have an intel easy pc webcam which give video, but it has a blue cast on it so everything looks like a blueberry hehehe.

Oddly, when I run the intel webcam in camorama, the color is more natural looking, but anything else, like ekiga gives me the blue cast.  And the philips webcam won't do anything at all.  I can see it with lsusb, but I can't get it to do anything else.

---

### Post by OffHand on 2006-12-29
> **Shay Stephens said:**
> It should, it's a Philips SPC701NC webcam, but I can't get it to work for nothing.  I also have an intel easy pc webcam which give video, but it has a blue cast on it so everything looks like a blueberry hehehe.

Oddly, when I run the intel webcam in camorama, the color is more natural looking, but anything else, like ekiga gives me the blue cast.  And the philips webcam won't do anything at all.  I can see it with lsusb, but I can't get it to do anything else.

So do you get a grey image or no image at all? Or do you get an error message?

---

### Post by Olav on 2006-12-31
This HOWTO saved my webcam. Because I would have literally thrown the poor little guy in the trashcan, thinking that it was kaput. :mrgreen: 

Did anyone already made a bug report about the pwc driver in Edgy? A working workaround like this is good. But I think the problem as such needs to be addressed upstairs, so to speak.

---

### Post by OffHand on 2006-12-31
> **Olav said:**
> This HOWTO saved my webcam. Because I would have literally thrown the poor little guy in the trashcan, thinking that it was kaput. :mrgreen: 

Did anyone already made a bug report about the pwc driver in Edgy? A working workaround like this is good. But I think the problem as such needs to be addressed upstairs, so to speak.

It's a known bug. Has been reported months ago  ](*,) 

[https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090)

---

### Post by Shay Stephens on 2006-12-31
> **OffHand said:**
> So do you get a grey image or no image at all? Or do you get an error message?

I don't remember how it behaved before the howto you posted.  But now it basically just doesn't get recognized.  I think it tried to work in the past, but the image was never usable.  I wish I could remember.

When I do a lsusb I get this:
Bus 003 Device 002: ID 0471:0328 Philips

When I run camorama, I get
Could not connect to video device (/dev/video0).
Please check the connection

When I run ekiga, there is no option to use the camera.  It does not get detected.  Same when I try using V4L2 or V4L.

I have two other cameras that do work, a logitech quick cam and an intel easy pc camera, but they have their own issues, but the philips and the IBM netcamera don't do a thing.

---

### Post by OffHand on 2007-01-01
> **Shay Stephens said:**
> I don't remember how it behaved before the howto you posted.  But now it basically just doesn't get recognized.  I think it tried to work in the past, but the image was never usable.  I wish I could remember.

When I do a lsusb I get this:
Bus 003 Device 002: ID 0471:0328 Philips

When I run camorama, I get
Could not connect to video device (/dev/video0).
Please check the connection

When I run ekiga, there is no option to use the camera.  It does not get detected.  Same when I try using V4L2 or V4L.

I have two other cameras that do work, a logitech quick cam and an intel easy pc camera, but they have their own issues, but the philips and the IBM netcamera don't do a thing.
I can't help you with that one I'm afraid.

---

### Post by Shay Stephens on 2007-01-01
> **OffHand said:**
> I can't help you with that one I'm afraid.

Not a problem, you helped me in being able to finally compile something successfully for the first time hehehe.  So thank you!

I am looking into just buying a webcam that is known to work in edgy out of the box.  I don't know if one exists.  The closest I have come is the Logitech QuickCam Chat.  I have read one person say it works in edgy out of the box, but I would like to get a little more confirmation before I plunck down the cash.

---

### Post by DarthTibault on 2007-01-03
> **Shay Stephens said:**
> 

When I do a lsusb I get this:
Bus 003 Device 002: ID 0471:0328 Philips

When I run camorama, I get
Could not connect to video device (/dev/video0).
Please check the connection


Try running Camorama from the terminal, and tell it to use video1 rather then video0:
```
camorama --device=/dev/video1
```
That's what I have to do, because my TV-card is on video0 (would be nice if camorama could detect this on its own).

@Offhand: btw, is it necessary that we complile this ourself, or could we use one of the debs available? [http://www.saillard.org/linux/pwc/debian/](http://www.saillard.org/linux/pwc/debian/)

---

### Post by OffHand on 2007-01-03
> **DarthTibault said:**
> @Offhand: btw, is it necessary that we complile this ourself, or could we use one of the debs available? [http://www.saillard.org/linux/pwc/debian/](http://www.saillard.org/linux/pwc/debian/)

I have never tried the deb files so I cannot say if they work. Probably they do. You can always give it a try.

---

### Post by marcopoloni on 2007-01-06
OffHand,
great job! :D 
Now I can finally video chat with my webcam.
Thanks a lot.
Marco

---

### Post by merry_meerkat on 2007-01-14
Another happy customer ;) 

Didn't follow the exact instructions given in this thread but rather a very similar set, see here for details: [http://boff.wordpress.com]("http://boff.wordpress.com/2007/01/14/solving-the-grey-image-problem/")

...can report that this fixes the grey-image problem on my Edgy machine with the Logitech QuickCam 4000 webcam.

---

### Post by newpants2003 on 2007-03-10
thanx a lot

---

### Post by silentme on 2007-03-12
Hi there, 
i need to get an step by step guide to install it, 
[-o<

here is the steps i do, when its not sucsessfull: :?:

~/test/Pwc$ tar jvxf pwc-10.0.12-rc1.tar.bz2

pwc-10.0.12-rc1/
pwc-10.0.12-rc1/pwc-dec1.c
pwc-10.0.12-rc1/pwc.h
pwc-10.0.12-rc1/pwc-uncompress.c
pwc-10.0.12-rc1/pwc-ioctl.h
pwc-10.0.12-rc1/pwc-nala.h
pwc-10.0.12-rc1/pwc-dec1.h
pwc-10.0.12-rc1/pwc-timon.c
pwc-10.0.12-rc1/pwc-kiara.c
pwc-10.0.12-rc1/pwc-timon.h
pwc-10.0.12-rc1/pwc-misc.c
pwc-10.0.12-rc1/pwc-kiara.h
pwc-10.0.12-rc1/pwc-dec23.c
pwc-10.0.12-rc1/pwc-if.c
pwc-10.0.12-rc1/pwc-uncompress.h
pwc-10.0.12-rc1/pwc-ctrl.c
pwc-10.0.12-rc1/Makefile
pwc-10.0.12-rc1/pwc-dec23.h
pwc-10.0.12-rc1/pwc-v4l.c

a:~/test/Pwc$ make
make: *** No targets specified and no makefile found. Stop.

i also installed this build-essential:
/test/Pwc$  sudo apt-get install build-essential
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold
Reading state information ... Ferdig
The following packages were automatically installed and are no longer required:
  libosp5 w3c-dtd-xhtml
Bruk «apt-get autoremove» for å fjerne dem.
Følgende ekstra pakker vil bli installert.
  g++ g++-4.1 libstdc++6-4.1-dev
Foreslåtte pakker:
  gcc-4.1-doc lib64stdc++6 libstdc++6-4.1-doc
Følgende NYE pakker vil bli installert:
  build-essential g++ g++-4.1 libstdc++6-4.1-dev
0 oppgraderte, 4 nylig installerte, 0 å fjerne og 62 ikke oppgradert.
1 pakker ikke fullt installert eller fjernet.
Må hente 4201kB med arkiver.
Etter utpakking vil 16,5MB ekstra diskplass bli brukt.
Vil du fortsette [Y/n]? y
Hent:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libstdc++6-4.1-dev 4.1.1-13ubuntu5 [1619kB]
Hent:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main g++-4.1 4.1.1-13ubuntu5 [2573kB]
Hent:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main g++ 4:4.1.1-6ubuntu3 [1434B]
Hent:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main build-essential 11.3 [6974B]
Hentet 4201kB på 21s (196kB/s)
Velger den tidligere fravalgte pakken libstdc++6-4.1-dev.
(Leser database ... 100446 filer og kataloger er installerte.)
Pakker ut libstdc++6-4.1-dev (fra .../libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb) ...
Velger den tidligere fravalgte pakken g++-4.1.
Pakker ut g++-4.1 (fra .../g++-4.1_4.1.1-13ubuntu5_i386.deb) ...
Velger den tidligere fravalgte pakken g++.
Pakker ut g++ (fra .../g++_4%3a4.1.1-6ubuntu3_i386.deb) ...
Velger den tidligere fravalgte pakken build-essential.
Pakker ut build-essential (fra .../build-essential_11.3_i386.deb) ...
etter opp libstdc++6-4.1-dev (4.1.1-13ubuntu5) ...
Setter opp g++-4.1 (4.1.1-13ubuntu5) ...
Setter opp g++ (4.1.1-6ubuntu3) ...

Setter opp build-essential (11.3) ...

(sorry that its norwegian , but it basicly says  Reading (leser), unpacking(pakker ut) and seting up (setter opp))

even thou i have done these steps, it wont work, ](*,)

i know that ive done this once before(around when edgy was released), but i dont remember how ..

Is there any other ways? :confused:

---

### Post by gabrielsaldana on 2007-12-02
I get the following errors when I try to run make:
```

gabriel@fenix:~/Desktop/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/gabriel/Desktop/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.o
In file included from /home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:69:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc.h:28:26: error: linux/config.h: No such file or directory
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:166: error: variable ‘pwc_template’ has initializer but incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:167: error: unknown field ‘owner’ specified in initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:167: warning: excess elements in struct initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:167: warning: (near initialization for ‘pwc_template’)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:168: error: unknown field ‘name’ specified in initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:168: warning: excess elements in struct initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:168: warning: (near initialization for ‘pwc_template’)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:169: error: unknown field ‘type’ specified in initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:169: warning: excess elements in struct initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:169: warning: (near initialization for ‘pwc_template’)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:170: error: unknown field ‘hardware’ specified in initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:170: warning: excess elements in struct initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:170: warning: (near initialization for ‘pwc_template’)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: error: unknown field ‘release’ specified in initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: error: ‘video_device_release’ undeclared here (not in a function)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: warning: excess elements in struct initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: warning: (near initialization for ‘pwc_template’)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:172: error: unknown field ‘fops’ specified in initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:172: warning: excess elements in struct initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:172: warning: (near initialization for ‘pwc_template’)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:173: error: unknown field ‘minor’ specified in initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:173: warning: excess elements in struct initializer
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:173: warning: (near initialization for ‘pwc_template’)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_isoc_init’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:921: warning: assignment from incompatible pointer type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘cd_to_pwc’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1019: warning: implicit declaration of function ‘to_video_device’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1019: warning: initialization makes pointer from integer without a cast
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1020: warning: implicit declaration of function ‘video_get_drvdata’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1020: warning: return makes pointer from integer without a cast
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_create_sysfs_files’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1062: warning: initialization makes pointer from integer without a cast
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1064: warning: implicit declaration of function ‘video_device_create_file’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_remove_sysfs_files’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1070: warning: initialization makes pointer from integer without a cast
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1072: warning: implicit declaration of function ‘video_device_remove_file’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_open’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1112: warning: implicit declaration of function ‘video_devdata’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1112: warning: initialization makes pointer from integer without a cast
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1117: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_close’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1231: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_read’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1292: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_poll’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1359: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_ioctl’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1375: warning: implicit declaration of function ‘video_usercopy’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_video_mmap’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1388: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘usb_pwc_probe’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1722: warning: implicit declaration of function ‘video_device_alloc’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1722: warning: assignment makes pointer from integer without a cast
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1730: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1731: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1732: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1733: warning: implicit declaration of function ‘video_set_drvdata’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1756: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: warning: implicit declaration of function ‘video_register_device’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: error: (Each undeclared identifier is reported only once
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: error: for each function it appears in.)
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1760: warning: implicit declaration of function ‘video_device_release’
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1765: error: dereferencing pointer to incomplete type
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function ‘usb_pwc_disconnect’:
/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.c:1819: warning: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/gabriel/Desktop/pwc-10.0.12-rc1/pwc-if.o] Error 1
make[1]: *** [_module_/home/gabriel/Desktop/pwc-10.0.12-rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

```

I already installed my kernel's headers and build essential packages. I'm using ubuntu gutsy.

Someone has a clue?

---

### Post by unprinted on 2008-04-06
It's not compiling for me under Hardy either:

```
Setting up build-essential (11.3ubuntu1) ...
me@nc4000:~$ cd pwc-10.0.12-rc1/
me@nc4000:~/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.24-15-generic/build SUBDIRS=/home/me/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-15-generic'
  CC [M]  /home/me/pwc-10.0.12-rc1/pwc-if.o
/home/me/pwc-10.0.12-rc1/pwc-if.c:171: error: unknown field ‘hardware’ specified in initialiser
/home/me/pwc-10.0.12-rc1/pwc-if.c:171: error: ‘VID_HARDWARE_PWC’ undeclared here (not in a function)
/home/me/pwc-10.0.12-rc1/pwc-if.c: In function ‘cd_to_pwc’:
/home/me/pwc-10.0.12-rc1/pwc-if.c:1020: warning: initialisation from incompatible pointer type
/home/me/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_create_sysfs_files’:
/home/me/pwc-10.0.12-rc1/pwc-if.c:1065: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/home/me/pwc-10.0.12-rc1/pwc-if.c:1066: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/home/me/pwc-10.0.12-rc1/pwc-if.c: In function ‘pwc_remove_sysfs_files’:
/home/me/pwc-10.0.12-rc1/pwc-if.c:1073: warning: passing argument 2 of ‘video_device_remove_file’ from incompatible pointer type
/home/me/pwc-10.0.12-rc1/pwc-if.c:1074: warning: passing argument 2 of ‘video_device_remove_file’ from incompatible pointer type
make[2]: *** [/home/me/pwc-10.0.12-rc1/pwc-if.o] Error 1
make[1]: *** [_module_/home/me/pwc-10.0.12-rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-15-generic'
make: *** [all] Error 2
me@nc4000:~/pwc-10.0.12-rc1$ 
```

This is after patching the 10.0.12-rc1 source as recommended on the pwc wiki ([here]("http://www.lavrsen.dk/twiki/bin/view/PWC/InstallationStandAloneModuleKernel2x6")).

---

### Post by Zookalicious on 2010-08-03
I get the exact same problems as the previous two posters under Lucid. Sorry to revive a dead thread but this still isn't fixed :S Does anybody know what we're doing wrong here?

---


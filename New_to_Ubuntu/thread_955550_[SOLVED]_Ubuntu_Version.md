---
title: "[SOLVED] Ubuntu Version"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by suncoolsu on 2008-10-22
I am new to Ubuntu. I have a Intel Core 2 Duo Processor. I have a few question about:
- which Ubuntu version to install.
  -x86 one or 64 bit one.
  
- I have burnt a ubuntu 8.04 LTS Desktop Edition(64 bit) cd and tried running ubuntu live but after boot screen no desktop appears :( instead a series of colored lines appear :(.
  - is it because of the wrong version (but the site says that the 64 bit version works for Intel and AMD)
  - some problem with my cd? (I checked for errors and it says no errors)

- Please help i need to install Linux on my laptop and preferably a 64 bit OS. Are there any other versions of Ubuntu I should look out for? (or a more fundamental question - is there a Ubuntu version for x86-64 bit architecture?)

Thanks for any help
B.

---

### Post by OldGrey on 2008-10-22
If it is a 64 bit processor the 64 bit version should work. However the 32bit version will work on 64 bit architecture no problem and in my experience with negligible effect on the performance. So you could try the 32bit and see if that works. If not it could be a graphics card problem.

---

### Post by Teamgeist on 2008-10-22
Since you have a core 2 duo processor the 64-bit Version will work on that.

Your Problem seems to be related to your graphics card.
What kind of graphics card do you have?

Try running the live cd in "save graphics mode mode" (<-- don't remember what it is called correctly, but it is an option in the menu, when the cd is inserted.

---

### Post by bodhi.zazen on 2008-10-22
You will likely need to install from the "alternate" CD. 

First try booting to "safe graphics" mode. If that fails -> alternate CD and post install we will need to install the drivers for your graphics card.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by suncoolsu on 2008-10-22
Intel® Integrated Graphics Media Accelerator X3100 is the video card. My processor in Intel Core 2 Duo T8100 2.1Ghz. My processor is 64 bit.

If i try to boot in the safe mode (after choosing the install in windows option) - then I can see the desktop but then I encounter errors like - root not set. etc. after this error message the ubuntu desktop wont load.

Thanks
B.

---

### Post by Teamgeist on 2008-10-22
ok, you're trying to install Ubuntu from within Windows using Wubi?


Try using the Live-CD and bootimg from it. Then try the Safe Graphics Mode from there.

[http://ubuntu-il.com/wiki/images/8/8f/Installguide3.jpg](http://ubuntu-il.com/wiki/images/8/8f/Installguide3.jpg)

You may have to enter your BIOS and tell it to boot from your CD-Rom drive first.

---

### Post by suncoolsu on 2008-10-22
thanks - in safe mode on a live cd - I am able to load ubuntu and work on it as well.

I have also checked most of my hardware.

My question is - 
should I install ubuntu now, without worrying worrying about the white screen to appear again? Or do i need to install drivers for my video card before installing ubuntu.. 

thanks guys for your speedy help - its highly appreciated

---

### Post by bodhi.zazen on 2008-10-22
> **suncoolsu said:**
> thanks - in safe mode on a live cd - I am able to load ubuntu and work on it as well.

I have also checked most of my hardware.

My question is - 
should I install ubuntu now, without worrying worrying about the white screen to appear again? Or do i need to install drivers for my video card before installing ubuntu.. 

thanks guys for your speedy help - its highly appreciated

You can install. If you have problems we need to fix them on the installation anyways ;)

---

### Post by suncoolsu on 2008-10-23
I have installed ubuntu as "commanded" and i still get the same white screen problem as before, please see the screens in the order of their occurance.

My Laptop is a recently launched Dell Studio 1535
configuration is as follows
Intel Core 2 Duo T8100 2.1 Ghz
Video Card - Intel® Integrated Graphics Media Accelerator X3100
OS - Windows Vista ( I tried installing UBuntu with Vista - though i plan to get rid of vista asap)

---

### Post by Ryadt on 2008-10-23
It looks like your laptop does not support the Live cd. Try installing with the alternate cd. You can download it from the Ubuntu homepage.

---

### Post by suncoolsu on 2008-10-23
I did.. I even burnt the Ubuntu given by Dell as well. I keep on getting the same screen for all of them :(. I dunno what is the problem, the only thing common for all these installation is the white screen. 

I tried installing kubuntu as well, but all lead to the same white screen.

pls help - very desperate to get rid of vista

---

### Post by Ryadt on 2008-10-23
First check the md5sum of the iso you downloaded.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If it passes the test, then check your cd for any errors.

---

### Post by suncoolsu on 2008-10-23
I had the ubuntu and kbuntu CD shipped via shipit. I checked for errors (with the check for errors option) while installing ubuntu. Do I still need to check the errors?

silly question but just curious..

thanks

---

### Post by suncoolsu on 2008-10-23
By the way I just checked using winMd5Sum - it say md5 sums are the same. ... :( :(

---

### Post by Ryadt on 2008-10-23
The md5sum of the shipped discs should be the same. The md5sum, you need to check is the one you downloaded.

---

### Post by suncoolsu on 2008-10-23
I am telling you about the downloaded one - the one from dell.

---

### Post by Ryadt on 2008-10-23
> **suncoolsu said:**
> I am telling you about the downloaded one - the one from dell.
Sorry but what do you mean by the one from dell?

---

### Post by suncoolsu on 2008-10-23
I used the shipped CD to install ubuntu.


I have a version of ubuntu provided by dell ([http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO))

I tried to check this version of ubuntu by running on Live CD. The md5 check sum is fine for this particular version. But it also gives the same white screen

---

### Post by Ryadt on 2008-10-23
This is a Live cd and it seems that your graphic card is not supported by the Live cd. So using this one won't solve anything.
There is an alternate way to install using the alternate cd. This cd can be downloaded from the Ubuntu homepage. [www.ubuntu.com](www.ubuntu.com)
Just make sure you check the option for the alternate cd before downloading.

---

### Post by bodhi.zazen on 2008-10-23
Installing from the alternate CD will not help. The difference with the alternate CD isit does not run a "live desktop" and the installer is more robust. The installed system will be the same.

You need to use the vesa drivers and find the drivers for your videocard.

To use the vesa driver, boot to recovery mode (it is an option at the boot menu).

You will have a command line only system.

I suggest you try :

```
dpkg-reconfigure -phigh xserver-xorg
```

Select defaults for everything (hit enter) , but when you are asked about which video driver to use, select (or enter) vesa.

You can test the new configuration by typing X (that is a large x)

This should give you a grey screen with a large black X. Hit Ctrl-Alt-Backspace to exit. If it is working enter:

```
telinit 2
```

---

### Post by suncoolsu on 2008-10-24
when I type
dpkg-reconfigure -phigh xserver-xorg

I get the following message:
Xserver-xorg postint warning: overwriting possible-customized config file backup etc/X11/xorg.conf ...

after that nothing happens ...

Which part did I miss?

---

### Post by bodhi.zazen on 2008-10-24
There is nothing wring with that, well you were not given a choice to select the vesa driver :(

I do not know if it will work, but if id does it is likely easier for you.

Try -plow

```
dpkg-reconfigure -plow xserver-xorg
```

You *should* be asked a lot of questions, again select the defaults for everything, but you need to use the "vesa" driver (without quotes) when asked about what driver you wish to use.

If that does not work, you will need to manually edit /etc/X11/xorg.conf and change the driver to vesa (which is not too hard, if you know what you are looking for).

---

### Post by suncoolsu on 2008-10-24
-plow didnt work...

But I reconfigured the xorg.cong file and changed the graphics driver to vesa ... and YAY!!! it worked :D .. 

What do I need to do next?

I am still in recovery mode...


Thanks a lot for you help guys!!

b.

---

### Post by SunnyRabbiera on 2008-10-24
you may wish to try the 32bit version, it will still work on your system
I know there are some hardwares that dont work with the 64bit version even if the processor supports it.

---

### Post by bodhi.zazen on 2008-10-24
> **suncoolsu said:**
> -plow didnt work...

But I reconfigured the xorg.cong file and changed the graphics driver to vesa ... and YAY!!! it worked :D .. 

What do I need to do next?

I am still in recovery mode...


Thanks a lot for you help guys!!

b.

Sweet, congrats :)

Either reboot or use the telinit command :

```
telinit 2
```

---

### Post by suncoolsu on 2008-10-24
So I rebooted and everything works fine.

How do I install drivers for my specific Intel Graphics accelerator X3100?

Currently my laptop runs Ubuntu without any any effects. I want to run it in the "more aesthetically pleasing set of effects mode" (in Visual Effects). When I click that option it gives me an error saying you cannot do that .. 

Any specific reasons for that ? is it because there are no specific video drivers for my type of Intel Graphics Accelrator ..

Please help .. also can anyone tell me how to activate wireless network?

-- Thanks

---

### Post by bodhi.zazen on 2008-10-24
Now you will have to do some searching.

For example, take a look at this thread :

[http://ubuntuforums.org/showthread.php?t=711014](http://ubuntuforums.org/showthread.php?t=711014)

And also a google search :

[http://www.google.com/search?q=ubuntu+Intel+Graphics+accelerator+X3100&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial](http://www.google.com/search?q=ubuntu+Intel+Graphics+accelerator+X3100&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial)

For your wireless you will need to use ndiswrapper and again using google find the driver you need.

Wish I could give you better advice :(

---


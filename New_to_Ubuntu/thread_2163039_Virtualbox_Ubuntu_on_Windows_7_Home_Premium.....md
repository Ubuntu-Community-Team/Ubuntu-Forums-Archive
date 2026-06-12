---
title: "Virtualbox Ubuntu on Windows 7 Home Premium...."
date: 2013-07-16
forum: New to Ubuntu
---

### Post by calc104 on 2013-07-16
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]HP 4430s Specs:[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Physical Memory: 4096 MB[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Processor: Intel64 Family 6 Model 42 Stepping 7 (this isfrom the Intel control panel) [/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]***Not sure if the information listed above and below arethe same*** [/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Processor: Intel Celeron CPU B810 @ 1.60GHz (this is fromDXDIAG information)[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Processor Speed: 1596 MHz  (yes its listed 2x, being as thorough as possible)[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Operating System: Windows 7 Home Premium (Service Pack 1)[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]DirectX Version: 10.1[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Graphics Memory: 1696 MB 

I am trying to run Ubuntu on VirtualBox inside of my Windows 7. At best I am a beginner as far knowing what I'm doing. 

Currently I have VirtualBox installed as well as Ubuntu version 13.04. When I try to run Ubuntu inside of VirtualBox only once have I got it to start running. 

The first thing I do before opening VirtualBox is use PowerIso to mount the image to H: so it htikns it has the CD to run from. 

Secondly I open VirtualBox and select Start on my Ubuntu inside of VirtualBox. After a few seconds of the purple'ish backscreen I get a error message that pops up:

"this kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel apptopriate for your CPU."

Since I have been able to properly run it once I have not been able to run it again. 
If there is a way to install Ubuntu in addition to my Windows 7 Home Premium and simply choose which OS I want to run upon starting up my computer, that will for now so I can use the program. 

Any help or advice would be greatly appreciated. If there is a post that already exists that has similar or the same problems, I did not mean to duplicate posts, please point me to that. 

Many Thanks, 
Calc104[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT]

---

### Post by yakinikku on 2013-07-16
To me it looks like your desktop CPU may only be 32bit and you are trying to run a 64bit OS in vbox, which won't work.  Can you verify?

---

### Post by calc104 on 2013-07-16
If the option was available to download the 64bit version I would have selected it. Im not sure where to look to verify the version I currently have. If the case is indeed that I have the 64 bit version would simply installing the 32bit version replace the 64bit and run smoothly? 

Many Thanks,

Calc104

---

### Post by waynefoutz on 2013-07-16
Also, you don't need to use the extra application to mount the .ISO image. Unnecessary step. Just point Virtual box to the .ISO file and it will do the rest.

---

### Post by su:bhatta on 2013-07-17
A bit strange, this Intel website lists that processor as 64bit, if i am not mistaken...
[http://ark.intel.com/products/55657](http://ark.intel.com/products/55657)

Also, second the comment from waynefoutz, you dont have to mount the image with any other application, VirtualBox does that for you... you have to select it from the setting page..

As for the other part of your post, Do you want to dual boot your computer?
If yes, then thatz easy, read up the forum posts and check if you have UEFI or Bios, U can Dual boot your systm and at the start up you get to choose which OS you want to load...

This page has a lot of details of dual booting Win7 & Ubuntu

[http://ubuntuforums.org/showthread.php?t=2145524&highlight=windows+home+basic+dual+boot](http://ubuntuforums.org/showthread.php?t=2145524&highlight=windows+home+basic+dual+boot)

---

### Post by mastablasta on 2013-07-17
have a look here: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

as others mentioned virtual box will mount the image. you can mark it as liveCD/DVD and it will boot from it. very handy for various security oriented distributions (e.g. Libre linux or Tails...)

also i think you need 32bit image for virtual box. at least i think it works better. not sure if that's true.

you might also need to enable PAE kernel support in virtual box. 

give it 1.5 GB of RAM and as much as possible graphics ram. i think you might need it.

otherwise you CPU is indeed 64 bit. they used to be called dual core celerons but are now basically Core i3 with soem disabled features so don't expect too much from them :-)

---

### Post by su:bhatta on 2013-07-17
> 

also i think you need 32bit image for virtual box. at least i think it works better. not sure if that's true.

you might also need to enable PAE kernel support in virtual box. 



Nah, I have used at least 5 distros (including Ubuntu Studio 64 bit) 64bit images on VirtualBox before settling for Ubuntu Studio. I dont think that is not the issue.

Seems like that PAE kernel support you are talking about, but i have no clue how that is to be done in Virtual Box...:confused:

---

### Post by mastablasta on 2013-07-17
ah good to hear 64bits work. never tried one (can dedicate abotu 1GB max to Vmand single core CPU, so i dont' want to overload it)....

PAE is ticked in one of the boxes in settings for virtual maschine. I think it might be off by default.

---

### Post by yakinikku on 2013-07-17
Double post.  DELETE ME!!!

---

### Post by yakinikku on 2013-07-17
> **calc104 said:**
> If the option was available to download the 64bit version I would have selected it. Im not sure where to look to verify the version I currently have. If the case is indeed that I have the 64 bit version would simply installing the 32bit version replace the 64bit and run smoothly? 

Many Thanks,

Calc104

Not sure what you mean.  x86-64 means you are using a 64bit ISO.  I would give the 32 bit version a go and see if you are able to get it working.

---

### Post by yakinikku on 2013-07-17
> **bhattabhishek said:**
> A bit strange, this Intel website lists that processor as 64bit, if i am not mistaken...
[http://ark.intel.com/products/55657](http://ark.intel.com/products/55657)

Also, second the comment from waynefoutz, you dont have to mount the image with any other application, VirtualBox does that for you... you have to select it from the setting page..

As for the other part of your post, Do you want to dual boot your computer?
If yes, then thatz easy, read up the forum posts and check if you have UEFI or Bios, U can Dual boot your systm and at the start up you get to choose which OS you want to load...

This page has a lot of details of dual booting Win7 & Ubuntu

[http://ubuntuforums.org/showthread.php?t=2145524&highlight=windows+home+basic+dual+boot](http://ubuntuforums.org/showthread.php?t=2145524&highlight=windows+home+basic+dual+boot)

Yes, but if the OS is 32 bit, that could be an issue.  Or this could be a BIOS limitation by the hardware MFG.  This is all speculation at this point because there are too many variables.

---

### Post by gbold on 2013-07-17
For your machine choose settings and make sure the following are set:
On the General->Basic tab of you machine you have to choose Ubuntu (64 bit)
System->Motherboard choose Enable IOAPIC
System->Processor choose Enable PAE/NX
System->Acceleration select both options

Most important for a 64-bit ISO is the first item so the machine knows your running 64-bit.  If it's selected and you use a 32-bit ISO there's no problem...
Greg

---

### Post by mastablasta on 2013-07-18
> **yakinikku said:**
> Yes, but if the OS is 32 bit, that could be an issue. 

no, because 64 bit CPU can run 64 bit OS or 32 bit OS. wile 32 bit CPU can run only 32 bit os (and probably 16bit and 8 bit).

---


---
title: "HP Pavillion g4 laptop"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by Jgranger on 2013-05-07
I recently dowloaded and installed Ubuntu 13.04 on my HP Pavillion g4 laptop ising a live CD, totally erasing my windows 7 os except for 8gbs worth of files which i saved to a usb stick.  i installed it just fine and then was told to restart my computer.  when i did all i got was a black screen with a white cursor in the corner whenever i try to boot from my harddrive.  I am a total newbie when it comes to any sort of linux based program, but i want to get better.  please help me out, i have absolutely no idea what Im doing! :p  any and all imput is appreciated :D

---

### Post by QIII on 2013-05-07
Hello and welcome to the forums.

There are a few common issues that may cause this, primarily related to hardware.

Since any given model of machine can have different hardware, could you let us know some more detail -- particularly the graphics adapter?

(If you wiped Windows but realized you wanted to keep some files, I wouldn't touch the machine just yet.  Let us know if you need to recover anything first.)

Best wishes.

---

### Post by Kopkins on 2013-05-07
> **QIII said:**
> 

(If you wiped Windows but realized you wanted to keep some files, I wouldn't touch the machine just yet.  Let us know if you need to recover anything first.)



He said except for 8GB of files that he put on a USB drive. 

Jgranger, Like QIII said, it's hard to tell what the issue is without more information about your computer. QIII is one of the most helpful people here, so they'll probably be able to help you out.

Good luck,

Kopkins

Oh! :) and welcome to Linux!

---

### Post by Jgranger on 2013-05-07
first and foremost, thank you guys for the speedy replies, the ubuntu community is awesome!  back on topic, i was sure to save my music, some papers i had written, phone numbers, etc onto a flash drive before i wiped.  as for hardware specifics, im not 100% sure what youre looking for, but this is from the hp website ([http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c02974953](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c02974953))

[TABLE="width: 540"]
[TR="bgcolor: #FFFFFF"]
[TD="align: left"]**Product Number**[/TD]
[TD="class: columnReducedMargin, align: left"]QE133UA#ABA[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="align: left"]**Microprocessor**[/TD]
[TD="class: columnReducedMargin, align: left"]2.5GHz/1.9GHz VISION A4 Technology from AMD with AMD Dual-Core A4-3300M Accelerated Processor [/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="align: left"]**Microprocessor Cache**[/TD]
[TD="class: columnReducedMargin, align: left"] 2MB L2 Cache[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="align: left"]**Memory**[/TD]
[TD="class: columnReducedMargin, align: left"]4GB DDR3 SDRAM (1 DIMM)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="align: left"]**Memory Max**[/TD]
[TD="class: columnReducedMargin, align: left"] Maximum supported = 8GB[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="align: left"]**Video Graphics**[/TD]
[TD="class: columnReducedMargin, align: left"]AMD Radeon HD 6480G Discrete-Class Graphics [/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="align: left"]**Video Memory**[/TD]
[TD="class: columnReducedMargin, align: left"]Up to 2037MB [/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="align: left"]**Hard Drive**[/TD]
[TD="class: columnReducedMargin, align: left"]320GB 5400RPM)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="align: left"]**Multimedia Drive**[/TD]
[TD="class: columnReducedMargin, align: left"]SuperMulti DVD burner [/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="align: left"]**Display**[/TD]
[TD="class: columnReducedMargin, align: left"]14.0-inch diagonal HD  BrightView LED-backlit Display (1366 x 768)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="align: left"]**Network Card**[/TD]
[TD="class: columnReducedMargin, align: left"]10/100 Ethernet LAN 
[/TD]
[/TR]
[/TABLE]

does that help?  i never installed any aftermarket hardware onto my comp.  if you need something additional or different from that, i might need some help on finding what you want.  thanks!

---

### Post by Jgranger on 2013-05-07
i fixed it!  it was a partician error that i managed to remedy!  thanks for the help guys, i am now a happy ubuntu user :)))  any recomendations on specific reading material whil im on here?  generally browing around now :)

---

### Post by Lightning Dragon on 2013-05-07
Hi,

Did you see any other screen before the black screen? If you can see any other screen before the black one appears, try following the steps here; [http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.tuxgarage.com/2011/01/ubuntumaverick-blank-screen-problem.html). If you don't get any other screen, could you try pressing the F6 key? When I was installing and got the black screen on two of my installs pressing F6 allowed me to get to the menus the above link I gave you talks about. However, having had this experience before, I think you if you can't get to the menu to perform those steps you are going to have to re-install Ubuntu. However, if you do, please make sure you follow the steps in the link above again. Depending on your type of GPU/Intergrated graphics, you will need to change what you are editing accordingly. At the bottom of the page in the link I gave, you will find this;

[QUOTE='nomodeset' Alternatives for other Graphics Devices]
According to *oldfred*, one of the senior members at *ubuntuforums.org*, if you are using an other graphics device than from Nvidia or ATI, or the *nomodeset* parameter doesn't work for your ATI device, you need to replace *"nomodeset"* with some other, corresponding parameters:
```

older Intel devices: i915.modeset=1 or i915.modeset=0
nVidia: nomodeset
Generic: xforcevesa or nouveau.modeset=0
Radeon: radeon.modeset=0


```
If you need to pop in this parameter in the Live CD environment, press F6 at the main boot menu but don't select *"nomodeset"*  then. Instead, just press <Esc> after that and you'll see a boot  parameter line at the bottom of your screen. At the end of that line,  you can type any of the parameters to boot with those.
[/QUOTE]

Also you could try booting to the Grub menu, which you can read about in the link under "First boot after installation is complete".

But I am curious, what partition type did you have it set on? Dynamic or basic? I have seen this issue being cured by having the partition set to basic, not dynamic (or vice-versa), when installing.

EDIT:

Oh, stupid connection! 11 minutes too late! Well, I am glad you have it fixed. What did you do to fix it? It could help other HP users who have had this problem, there are a lot of them. lol

---

### Post by DuckHook on 2013-05-07
> **Jgranger said:**
> ...any recomendations on specific reading material whil im on here?

"Linux is not Windows" intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

General Ubuntu Intro:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://owlcroft.com/ubuntu/](http://owlcroft.com/ubuntu/)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

Command line learning:

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---


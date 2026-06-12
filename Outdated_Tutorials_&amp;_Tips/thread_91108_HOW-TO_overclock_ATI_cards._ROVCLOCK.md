---
title: "HOW-TO overclock ATI cards. ROVCLOCK"
date: 2005-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by floyd27 on 2005-11-16
1- Download rovclock..
[http://freshmeat.net/projects/rovclock/](http://freshmeat.net/projects/rovclock/)

2- Extract to desktop
3- cd /home/yourname/Desktop/rovclock-0.6b
4- make
5- sudo ./rovclock -i 

This will give you the syntax and your current clock speeds.

OVERCLOCKING..

6- sudo ./rovclock -c(new mhz) -m(new mhz)
These are for core and mem respectively.

You can then do step 5 again to see if your changes took..
As for saving after a boot im not sure how to yet..

Its up to you to make sure its stable, as there is no "find max core/mem" or scanning for artifacts as in ATITool.....
I suggest that you google your card type and see what speeds others were able to reach as a guide.

Overclocking can kill your card/system so be careful....!!!!!!!
Im not responsible for any harm that may come to your system...Enjoy.

---

### Post by domino on 2005-11-17
First, thanks for this tool. I do OC my box and I already know my 9800Pro cpu/mem/Vagp limitations. But I have a question before I try this.

Do the ATI drivers actually support 3D games? If I purchase Point2Play, will the compatable games run "just like" expee (visual quality)?

---

### Post by floyd27 on 2005-11-17
ATI drivers do support 3d games, but you wont get performance just like xp...
I find the frame rate is much lower than in xp.. I have never used cedega or p2p however..
ATI's linux drivers are not the greatest. Its just a generic one. And openGL isnt as good as with Nvidia (which also have their own downfalls) 
Hopefully ATI will get their linux drivers in order soon..
With that said games are still playable, but probally not what your used to.

---

### Post by domino on 2005-11-18
Thanks for the info Floyd. Weighing these options, maybe it's not worth overclocking the card in Linux until we get better drivers for our cards. I run the 9800 Pro (OEM).

---

### Post by Zeroedout on 2005-11-18
[quote=domino]Thanks for the info Floyd. Weighing these options, maybe it's not worth overclocking the card in Linux until we get better drivers for our cards. I run the 9800 Pro (OEM).[/quote]

I personally love the fact we can finally overclock (or atleast i am now aware of the tool). Depending how far you can push your card, you can really get a nice performance increase. Ofcourse, the faster they write better drivers the better, but a performance jump is a jump.

---

### Post by floyd27 on 2005-11-18
With my 9700 pro i get around 4000+ glxgears.. When i overclock (the 9700 pro is a poor OCer) I move up to 4400+ glxgears..

With my 9600 323/203 stock overclocked to 400/250    (52fps in ATItool)
With my 9700 pro 325/310 stock overclocked to 370/330 (150fps in ATItool)

Better drivers will increase performance, but that takes time and people still want to play games now.. Its a small increase but most overclocking only gives a small increase anyway..Its when you add all the overclocking in the system together that you get some noticable increased performance..

Best thing to do is let ATI know you want better linux suppport.. I wrote a report to ATI asking for better linux drivers, but the responce was something like..."The ATI linux drivers are located in the drivers download section"....What a big help :confused:

---

### Post by domino on 2005-11-18
Yea, overclocking is rare now adays. Now that dual chips are available for both agp and mobo, and the P4 have reached it's maturity. I still have my main rig 2.8C clocked to 3.3GHz. I beleive that higher front side bus gaines overall system performance. That's where clocking the apg comes in. I hand picked the 2.8C and the 9800pro for one specific purpose. I think you know what that is :).

I guess, I'll stick with my expee until a comparable driver to expee is released. Who knows, Maybe I'll jump on the OSx86 bandwagon as soon as it's released to the general public. I also emailed ATI requesting better drivers since the ATI drivers for the 9800 and above are not open source.

---

### Post by floyd27 on 2005-11-18
Just because the drivers are not up to xp specs doesnt mean you can play games in linux..
Try out some linux native games and see what you think.. cedega and p2p use DX9 emulation so it should be better than openGl..But i dont know first hand..

With more people runnibg linux games and requesting better linux support, the more support that will come in the future...

---

### Post by Jingo on 2006-04-10
I am using rovclock to underclock my laptops radeon 7500 card. to gain battery life.

Under breezy this works perfectly...

Under Dapper it hangs my computer ! :cry: 

Any suggestion ? I am using the open source radeon driver.

---

### Post by ksugu2 on 2008-10-13
Hello all,

I am facing a problem with underclocking my HD3850 ATI card.
I installed rovclock but there seems to be a specific problem (as follows) ..
-------------------------------------------------------------------------------------- 
**sudo rovclock -i** 

gives the following error 

Found ATI card on 01:00, device id: 0x9515
I/O base address: 0xc800
Video BIOS shadow found @ 0xc0000
Invalid reference clock from BIOS: 0.0 MHz
Memory size: 0 kB
Memory channels: 0, CD,CH only: 0
tRcdRD:   3
tRcdWR:   1
tRP:      3
tRAS:     6
tRRD:     1
tR2W-CL:  1
tWR:      1
tW2R:     0
tW2Rsb:   0
tR2R:     1
tRFC:     13
tWL(0.5): 0
tCAS:     0
tCMD:     0
tSTR:     0
Floating point exception

-------------------------------------------------------------------------------------- 
Similarly, **sudo rovclock -c 100 -m 120** gives the following error ...

Radeon overclock 0.6e by Hasw (hasw@hasw.net)

Found ATI card on 01:00, device id: 0x9515
I/O base address: 0xc800
Video BIOS shadow found @ 0xc0000
Invalid reference clock from BIOS: 0.0 MHz


-------------------------------------------------------------------------------------- 
Is there any problem with my BIOS ?? I recently updated the BIOS as well -- its AMI V1.8, Dated : 11/02/2007
Any help would be greatly appreciated.
[B]
Additional Info:
AMD 64 bit -- Ubuntu 8.04
Driver : ati-driver-installer-8-9-x86.x86_64[/B]

---

### Post by Ravisher on 2008-12-27
I have this same problem  cept im using a 3870. Running Ubuntu 8.10 64 bit.
I have my 3870 bios flashed to the turbo because mine wasnt the turbo and used ati tools to throttle it back some during down time. 

I get the same thing you get :( someone help please!

---

### Post by Ravisher on 2008-12-27
Re: HOW-TO overclock ATI cards. ROVCLOCK
Hello all,

I am facing a problem with underclocking my HD3850 ATI card.
I installed rovclock but there seems to be a specific problem (as follows) ..
--------------------------------------------------------------------------------------
sudo rovclock -i

gives the following error

Found ATI card on 01:00, device id: 0x9515
I/O base address: 0xc800
Video BIOS shadow found @ 0xc0000
Invalid reference clock from BIOS: 0.0 MHz
Memory size: 0 kB
Memory channels: 0, CD,CH only: 0
tRcdRD: 3
tRcdWR: 1
tRP: 3
tRAS: 6
tRRD: 1
tR2W-CL: 1
tWR: 1
tW2R: 0
tW2Rsb: 0
tR2R: 1
tRFC: 13
tWL(0.5): 0
tCAS: 0
tCMD: 0
tSTR: 0
Floating point exception

--------------------------------------------------------------------------------------
Similarly, sudo rovclock -c 100 -m 120 gives the following error ...

Radeon overclock 0.6e by Hasw (hasw@hasw.net)

Found ATI card on 01:00, device id: 0x9515
I/O base address: 0xc800
Video BIOS shadow found @ 0xc0000
Invalid reference clock from BIOS: 0.0 MHz


--------------------------------------------------------------------------------------
Is there any problem with my BIOS ?? I recently updated the BIOS as well -- its AMI V1.8, Dated : 11/02/2007
Any help would be greatly appreciated.

Additional Info:
AMD 64 bit -- Ubuntu 8.04
Driver : ati-driver-installer-8-9-x86.x86_64



[COLOR="Red"]I have this same problem  cept im using a 3870. Running Ubuntu 8.10 64 bit.
I have my 3870 bios flashed to the turbo because mine wasnt the turbo and used ati tools to throttle it back some during down time. 

I get the same thing you get :( someone help please![/COLOR]

---

### Post by balcis on 2009-03-29
same problem here with my ati hd3650, any help??

---

### Post by WSmart on 2009-07-26
I'm getting just short of 1200 FPS with glxgears with the low end version AMD 9600, the 9600se version, which is only 64bits and 128MB, running Ubuntu 8.10 and Catalyst 9.3.   

With newer cards, you might want to try ATIpower.   Here's an article at [[COLOR="SeaGreen"][COLOR="DarkGreen"]Phoronix.com[/COLOR][/COLOR]]("http://www.phoronix.com/scan.php?page=article&item=675&num=1").  

I got my settings to load at startup by creating a script(adding some lines to a text file and ticking the run as program box in the properties for anyone that's not sure how that's done), and adding that script to Administration>sessions- the startup programs tab.  The script has two lines;  change directory and the command, as follows.
cd /rovclock-0.6e
sudo ./rovclock -c 482 -m 242

THANKS ALL! :popcorn:

---


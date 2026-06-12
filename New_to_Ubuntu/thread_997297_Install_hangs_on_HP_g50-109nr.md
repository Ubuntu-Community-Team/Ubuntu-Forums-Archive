---
title: "Install hangs on HP g50-109nr"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by jasex on 2008-11-29
Hey, just bought a HP G50 109NR and the install only gets partway through, before hanging at probably 20% on the loading bar.

It drops to busybox with 8.04.1 and freezes completely with 8.10

It is a x86_64 install disc, for both of them, and an x86_32 hangs as well.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01607591&lc=en&dlc=en&cc=us&lang=en&product=3808643](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01607591&lc=en&dlc=en&cc=us&lang=en&product=3808643)

This is the product specification sheet, could anyone give me some pointers; I.E. customized install disc, custom install arguments  to pass at the start-up command line? Any help... ?

This for my fiancee, and I stood out in front of Staples for about 16 hours to get this  for her, and she is pleading for me to put Linux on it. She's kind of frustrated that I can't get it on and is almost tempted to just keep windows at this point.

---

### Post by linuxguymarshall on 2008-11-29
on the live cd boot menu hit F6 and type : 
```
acpi=off noapic nolapic
```

that should fix it

---

### Post by jasex on 2008-11-29
So use all three extra options? I've only tried each seperately, I'll try this and get back to you.

---

### Post by linuxguymarshall on 2008-11-29
Ok. If that does not work then check the BIOS. Set Plug and Play OS to NO and if it is an option choose the onboard graphics over your PCI-E or PCI or whatever graphics card slot you have.

---

### Post by jasex on 2008-11-29
That did not work. I will try your second suggestion, except for one thing, this is a laptop.

---

### Post by linuxguymarshall on 2008-11-29
Yeah thats what I thought. The Plug and Play OS will probably be there but unless it is a high-end lappy then the second wont.

---

### Post by jasex on 2008-11-29
neither of those options were there and this was a cheap black friday special

---

### Post by linuxguymarshall on 2008-11-29
I would say call HP but they only offer Linux support to corporate customers....pigs...... Did you try the alternate CD?

---

### Post by jasex on 2008-11-29
i will see what i can do then. I did try the alternate cd and it gave me the same issues.

---

### Post by jasex on 2008-11-29
So it seems to be the CD after trying many different linuxes, I had this issue with another laptop sr0 buffer i/o error so... I dunno

the other laptop would install 7.04 fine, buuuut it wouldn't work for me because of the wireless card being incompatible, and updating it up from that would cause it to have even more issues. 

Anyone have any pointers...

---

### Post by jasex on 2008-11-29
Perhaps someone could link me to a tutorial to putting the iso on  athumb drive for installation... my only issue with that is, as is with the install on the other computer, running linux on it, the CD drive would fail to read a cd sometimes afterwards.

---

### Post by lkraemer on 2008-11-29
jasex,
Look over this information.  I know mine is a CQ50,
but the same type install should work.  HP can get you
the XP Drivers if you request them nicely.

http://ubuntuforums.org/showthread.php?t=996311

http://ubuntuforums.org/showthread.php?t=988691

lkraemer

---

### Post by jasex on 2008-11-30
Hey that just might work, but I am not going with the dual boot. I despise windows in all aspects, and am going to try to just do away with it. If not I do computer repair as a job, so coming by a recovery disc and just entering my serial if it comes down to that won't be too bad.

Anyhow trying from USB thumb disk first, seeing if that works.

---

### Post by jasex on 2008-11-30
Yeah, so no go... I just wasted my life by 36 H(our)P(oints) if that Laptop doesn't get linux installed. I'd rather use it as a paperweight.

HP only offers linux support to corporate people?! bullsnikeys I call. I might sell this thing, anyone want a 600 $ paperweight ;)

---

### Post by jasex on 2008-11-30
STATUS UPDATE: Cannot load HP Chat on Linux in Firefox on Ubuntu 8.04 64 bit, So can't even talk to the dirty bad men who don't want me to run OPEN SOURCE

---

### Post by jasex on 2008-11-30
Sadly so far all i've got to install is Mandriva sucessfully from an older DVD

---

### Post by jasex on 2008-12-01
:( If anyone bought this laptop, I recommend trading it.

---

### Post by itkeepsrepeating on 2008-12-02
Same laptop, same exact problem. Debian etch wont install. The funny thing about that is, it'll boot from cd, start the install process, and then ask for optical drive drivers via a floppy, which is not equipped on this model. 

Booooo. 

You paid 600 for yours? Mine was at staples for 400. I'll sell it to you for 600, though. It doesn't install ubuntu, however. :rolleyes:

---

### Post by jasex on 2008-12-02
mine was at 400 at staples too, but it is valued at 800 originally... I think that's including the vista premium price :)) but seriously, I got 32 bit 8.04.1 32 bit installed finally... and then boom updates killed it unless I reconfigured x server... but it would fail to properly use my nvidia card. so it would just remain black.

It is the optical drive on the install part... but there are other problems, i.e. the problems with the graphics card... the wireless card as well... it worked on mandriva fine, but after manual addition of access point. ubuntu detected it as well, but would refuse to let me configure it. THE BUTTON did not work at all.

---

### Post by itkeepsrepeating on 2008-12-22
> **jasex said:**
> I got 32 bit 8.04.1 32 bit installed finally... but it would fail to properly use my nvidia card.
It is the optical drive on the install part... but there are other problems, i.e. the problems with the graphics card... the wireless card as well... 

I have found out a few things that may help.
I did get one version to work, it was likely 8.04 32 bit, as well.

It's been suggested that Vista turns off the wifi card on shutdown, disabling somehow the ability for ubuntu to recognize it properly. There may be a setting in vista to stop this.

My video works, but ridiculously slow. You can tell the computer is running fine, but the screen is not updated immediately.

I agree much of the problems trying different distros that i've had all have to do with the optical drive. After reading the drive and loading the kernel, it usually asks for optical drivers.

I think we're just waiting on someone smarter/more linux savvy than us to get ahold of this thing and straighten us out. This is my first real exposure to vista, and it does become bearable after a coupla hours work stripping it. I wish to only use windows on occasion, but until I see some answers posted in the forums for this notebook, I'm dead in the water, or just using my desktop thru vnc.

Please post back any headway you've made.

---

### Post by s3a on 2008-12-27
I also tried to install Debian Etch x86_64 on this laptop (HP G50) and it also said that it needed to load modules from a floppy to get it to work. First of all, I also had it running off of a optical disc (DVD) and second, this laptop has no floppy drive!

Atleast Ubuntu 8.10 works on it and am using the live CD but I really need to use install Debian! As for the wireless Internet, I had to use my D-Link DWL-G122 (USB Device) to go online as the built-in wireless card didn't work and Ubuntu 8.04 LTS stopped loading at a busybox prompt.

I guess for you guys the solution would be to install Ubuntu 8.10 but I would like to use Debian because I only use Ubuntu on my mom's computer since it is supposedly easier to use.

And I think I read somewhere this laptop was made or revised or something like that in July so that could be why there are problems. Anyway if someone finds a solution (even a partial solution), please post.

---

### Post by jasex on 2009-01-02
I think hacking the BIOS will work for anyone still interested ;) I will release an edited winflash soon as I remember how to do it, that will enable the advanced Bios options... stay tuned. I'm not Linux "savvy" per se, but I am computer "savvy" ;)

---

### Post by darlykaiser on 2009-01-04
well, try to install the madwifi for the wifi issues

---

### Post by itkeepsrepeating on 2009-01-04
> **s3a said:**
> 
Atleast Ubuntu 8.10 works on it and am using the live CD but I really need to use install Debian! ... if someone finds a solution (even a partial solution), please post.

Since Ubuntu is based off debian, couldn't you do a minimal [e.g. server] install and add the gui?

For example, people with specific intentions have chose to install ubuntu server edition on their boxes, which is command-line only, then using apt-get, install gui of your choice. Not that this particular laptop needs a lighter one, but you could essentially be running xubuntu, thereby making it snappier than ever. 

If you don't mind my asking, what's the specific purpose you're etching [bad pun intended] for debian? I'm no guru, but I can't really see too many things debian can do, that *buntu can't. Though, I have a friend that scoffs at me for using ubuntu. He never seems to get his point across as to why, though.

---

### Post by itkeepsrepeating on 2009-05-08
Jaunty installs smoothly. I've had it running for some time now, without any major glitches. I'm having an issue with the wireless, but it's looking like faulty hardware, as when I get connection issues in Jaunty, I reboot into Vista, and the same problem remains. It seems to work fine again after leaving it off for an hour or so. Hopefully the warranty will cover it if, in fact, it is a hardware problem I'm having.

---

### Post by lkraemer on 2009-05-11
I am wondering if you have tried the LiveCD's on other computers to make
sure they were a good burn?  Also did you VERIFY the MD5SUM's of the
LiveCD's?  Burn them as Disk at Once (DAO) and at a slow speed?
I use K3B for burning all of mine.

Why not download and try a copy of PCLinuxOS 2009.1 as a test, to see
if that works?  I am running PCLinuxOS on a Compaq CQ50-139NR, and a
Compaq CQ60-210US and it works fine.

[http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm](http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm)
Compaq - Presario, Prolinea, Deskpro, Systempro, Portable

    * Press F10 while the cursor in the top right corner of the screen is blinking.
    * Older Compaq computers may use the F1, F2, F10, or Del key to give access to BIOS.


lkraemer

---


---
title: "Not at the starting line yet......"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by idgraham on 2008-11-15
I've dowloaded Ubuntu and burnt a CD. It doesn't have the the .eco on it - so far so good.
I've tried to boot from the CD, but (unless Linux is on a totally different timescale to Windows) it hangs - once at the rusty red pic screen, twice before that at the single or multiple white dots (talking 20 minutes in one case here). 

I opened the CD inside Windows and installed from there. rebooted and got the choice of whether to go into Windows or Unbuntu, chose the latter. This time i got farther than ever before - past the rusty screen to a 'Checking the installation' bar - but then no movement. Again, I'm fairly sure it's stalled, not just stone-age slow. 

Do I download and burn again ? Or is it my PC that's causing the problem ? Or what ?

I'd really like this to work.

Ian Graham
Wales.

---

### Post by idgraham on 2008-11-15
Not at the starting line yet...... 

--------------------------------------------------------------------------------

Sorry - terrible proof-reading !

I've downloaded Ubuntu and burnt a CD. It doesn't have just the the .eco on it - so far so good.
I've tried to boot from the CD, but (unless Linux is on a totally different timescale to Windows) it hangs - once at the rusty red pic screen, twice before that at the single or multiple white dots (talking 20 minutes in one case here). 

I opened the CD inside Windows and installed from there. rebooted and got the choice of whether to go into Windows or Unbuntu, chose the latter. This time i got farther than ever before - past the rusty screen to a 'Checking the installation' bar - but then no movement. Again, I'm fairly sure it's stalled, not just stone-age slow. 

Do I download and burn again ? Or is it my PC that's causing the problem ? Or what ?

I'd really like this to work.

Ian Graham
Wales.

---

### Post by shredder12 on 2008-11-15
are you able to reach the stage where you are asked for 4-5 things initially..if you are able to go there. then select the option to check for any errors in the cd..
may be it will clarify where is the problem...

---

### Post by oilchangeguy on 2008-11-15
you may want to read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
and please provide your computers specs.

---

### Post by aeiah on 2008-11-15
it could be a cd defect but the chances are there's something weird about your computer ;) its probably fixable. can you give us your computer specs? specifically your motherboard but also your ram and graphics card i suppose.

---

### Post by idgraham on 2008-11-15
At one stage I had a screen with options tagged to function keys. I didn't explore it beyond the choice of language. I'll try and re-run that.

Thanks

Ian G

---

### Post by idgraham on 2008-11-15
Thankyou for your various suggestions, which I have taken notice of.........

System info:  running (usually ) Win XP with AMD Sempron 2600 +1600 MHz processor on K8M800-8237 mainboard with 960Mb Ram. (And my mother's maiden name was Jones !) 

I've used the option from the Ubuntu setup to check the CD, and it found no problems. Likewise the various option choices all seem to respond. 

Since when I've tried to 'install Ubuntu', when I got through very quickly to an 'Install' box on the splash screen, with nothing in the frame except that little white dot with marks on - is it a paw ? I begin to associate that with 'freezing' - is that right, or is it part of a working boot process ?

That process having seemingly stalled, I rebooted again and this time chose to 'run from CD', and didn't even get to the Splash screen - again that dreaded 'paw' just sitting in the middle of the screen.

:confused:

Ian G.

---

### Post by shredder12 on 2008-11-15
well i think you are probably trying to install ubuntu 8.10 i haven't tried it yet so i don't know what shows up at the time of installation but that freezing thing seems to be worrying..
I am sorry but I don't really have any idea about such a problem..

---

### Post by idgraham on 2008-11-16
Yes, it is Ubuntu 8.10.

I tried the Alternative CD route, but got nervous (in the context of a well-established PC) of the partitiong implications.....

Thinking from first principles: 
the CD itself is OK (Ubuntu software says so)
it starts the boot process perfectly well
the process then gets stuck

My Windows installation can't be having any effect, by definition - the registry isn't even invoked?

The bios is happy enough to start running the boot / installation.

If Linux can't find some files on the CD (which is what the error message says) but they are presumably there (see above) 

surely the problem must be in the programming itself?

I'd be really grateful if one of the moderators would come in on this.....

Sincerely

Ian Graham:)

---

### Post by Peter09 on 2008-11-17
Just to confirm, you are unable to run the LiveCD (forget about installation). Or can you run the LiveCD but not install?

---

### Post by Ryadt on 2008-11-17
Did you check the md5sum of the iso you downloaded? If not check [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also please give time to the people helping you to get back to you. Do not create multiple threads on the same issue. If you don't get any response in 24hrs then bump your thread.

---

### Post by nhasian on 2008-11-17
try booting the liveCD with noapic

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by bennachie on 2008-11-17
Your computer system should be similar in power to my own desktop, so I would not have expected the kinds of delays you have been experiencing. 

While we don't absolutely need to know your mother's maiden name, it might be useful to know what(if any) graphics card you have installed - there is a known installation problem with some particular cards that require proprietary drivers.

---

### Post by Bucky Ball on 2008-11-17
> **bennachie said:**
>  it might be useful to know what(if any) graphics card you have installed - there is a known installation problem with some particular cards that require proprietary drivers.

K8M800-8237 motherboard

Maybe it has something to do with the motherboard. That is a Via chipset from memory and if I am not mistaken, has onboard video. This will not run with Nvidia drivers which means maybe you need to force feed the right drivers somehow. Just a hunch, but might be connected to this.

I have no idea what video drivers 8.10 loads to get the install GUI up and running but they may have changed from 8.04 (which installed and runs no problem on a desktop I have with Via chipset). As for the alternate install cd, back-up windoze and go for it. When you get to manual partitioning, have a plan as to what you are going to do and don't go anywhere near the partitions marked NTFS. That is windoze. Ubuntu uses EXT3 so there is no mistaking. Good luck.


* Update: Mainboard Gigabyte GA-K8VM800M K8M800/8237 1600 MHz FSB memorie DDR / 400 MHz **AGP 8x video integrat **Integrat ATA 133 SerialATA lan 10/100 Mbps audio AC97 micro ATX

Just a guess ...

---

### Post by tarps87 on 2008-11-17
If you can not load Ubuntu from the live cd I may also be due to the speed of your cd drive. If you want to install Ubuntu you can post your hard drive/partition details of what you have installed and where you want Ubuntu and we can guide you through partitioning using the alternative cd.

Another thought, when you run the live cd, at the point where it hangs can you press ctrl+alt+f1 ?

---

### Post by idgraham on 2008-11-17
Sincere thanks to all you guys for your various comments and suggestions. I've taken all of them on board to a greater or lesser extent......

My graphics card is a VIA/S3G Unichrome Pro1GP.

I have been again right through the process of trying to load Ubuntu from the (Live) CD. I have gone thoroughly around the various function key screens and the pre-tests. All of them seem to run OK. But when I try to actually 'try Ubuntu' (the first option) it starts and then a certain way in starts throwing up 'dos' type error messages along the lines of 
I/O error dev sr0 (or that last character might be theta?) with various sector and 'logical block' nos. 
(The interesting thing is that that's not how it was yesterday - then the problem was associated with an almost blank screens)

As for 'naopic' and 'check livesum' and boot options; I would regard myself as nothing of a duffer, IT-wise. But I download equal or greater quantities of programming for Windows, and it runs almost with fail,  without all this checking and vulnerability.
I've never seen a working Linux set-up. I'm just interested. I approve of the open source ethos, and I would be in the market for a more stable OS than Windows. But on my experience of the past 48 hours, I would say Linux has a long way to go before it saves the world. 

Sincerely

Ian Graham

---

### Post by jimv on 2008-11-17
I can never understand how people have so many problems installing Ubuntu.  I've installed varying versions of Ubuntu on dozens of machines, and the only one I ever had a problem on was my laptop (some kind of buggy ACPI implementation wouldn't let it boot with ACPI enabled till I patched the DSDT file).

If you're having a problems, especially IO problems, it's more than likely the problem is an old, broken, or odd piece of hardware that isn't communicating the way the drivers expect it to.

---

### Post by nhasian on 2008-11-18
I've also installed ubuntu successfully on many systems now.  i've had to blacklist the occasional driver now and then but thats the most difficult thing i've come across myself.  the problem arises when one tries to use incompatible or unsupported hardware, in this case the VIA/S3G Unichrome Pro1GP video card:

[http://ubuntuforums.org/showthread.php?t=76037](http://ubuntuforums.org/showthread.php?t=76037)

changing the video card would most likely resolve the installation problem :)

> **jimv said:**
> I can never understand how people have so many problems installing Ubuntu.

---

### Post by egalvan on 2008-11-18
> **idgraham said:**
> But I download equal or greater quantities of programming for Windows, and it runs almost with fail,  without all this checking and vulnerability.
I've never seen a working Linux set-up. I'm just interested. I approve of the open source ethos, and I would be in the market for a more stable OS than Windows. But on my experience of the past 48 hours, I would say Linux has a long way to go before it saves the world. 
Sincerely
Ian Graham

Well, I don't know if Linux will save the world, but it has managed to create and run the Internet, run Google, run the world's fastest computers (more than one peta-flop), and is responsible for the Mars Rovers. :)

Since Hardy 8.04 came out, I've installed it on some eight Dell desktops, one Dell laptop, four HP desktops (including one Media Center), two HP laptops, and five IBM Thinkpads.

From a lowly P-3 @ 733 with 256megs, Intel graphics w/ 4meg 
to a Dual-Core @ 2.8GHz with 8gigs, nVidia 7600 w/ 512meg

All dual-boot (XP & hardy 8.04.1), all run great.

All installs went smooth.

But I DID witness Feisty 7.10 crash on an HP laptop. Required the 'noapic' option. I don't know if the owner kept on with the install.


You MAY be experiencing bad RAM, or other bad hardware,
 and you are right, Windows doesn't do as much checking. At least in my experience.

A lot of manufacturers refuse to support Linux, and some also refuse to allow Linux to support their hardware.
And some are even antagonistic towards Gnu/Linux/BSD, deliberately coding against *nix.

But I seriously doubt you will find as great a forum devoted to Windows as this one is devoted to *buntu.

We may yet find an answer to your problem.

ErnestG

---

### Post by Peter09 on 2008-11-18
Why not have a go with the Alternate CD, if you feel reasonably competent then its not to much of an issue. Tell it to use the spare space on your drive (not the whole drive) and you will be ok.

---

### Post by Sianegad on 2009-02-15
> **Bucky Ball said:**
> K8M800-8237 motherboard

Maybe it has something to do with the motherboard. That is a Via chipset from memory and if I am not mistaken, has onboard video. This will not run with Nvidia drivers which means maybe you need to force feed the right drivers somehow. Just a hunch, but might be connected to this.



* Update: Mainboard Gigabyte GA-K8VM800M K8M800/8237 1600 MHz FSB memorie DDR / 400 MHz **AGP 8x video integrat **Integrat ATA 133 SerialATA lan 10/100 Mbps audio AC97 micro ATX

Just a guess ...

I'm having the same kind of trouble installing 8.10 on a ga-k8vm800m base system. Did you manage to install it?  I have found a few people mentioning trouble with that board and ubuntu, but no fix.  Would trying 8.04 be worthwhile?

---


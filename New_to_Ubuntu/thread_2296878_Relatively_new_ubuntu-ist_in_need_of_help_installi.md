---
title: "Relatively new ubuntu-ist in need of help installing and running stable"
date: 2015-09-29
forum: New to Ubuntu
---

### Post by sudohawk on 2015-09-29
Hey guys hope to learn a lot from this site.  I'm relatively new to Ubuntu. I have 14.04 which has progressed to 15.04 dual booting with windows 10 on my main laptop but that machine is showing its age and in fear of it dying on me while I still need a PC I picked up a laptop for a good price.  I initially set out to use Linux mint 17.2 cinnamon.  The install went well but I get periodic crashes and freezes.  The message on the console after the desktop environment closes out states something to the effect of cpu not syncing kernel panic.  I looked around and it looks like it might be nvidia driver related.  

In any case seeing as how I had good luck with Ubuntu on my old laptop I started looking at other Ubuntu flavors.  The one I'm most interested in is kubuntu 15.04 and thus would like help directed towards getting this up and running and running stable.

Machine is an MSI PX60 2qd 034us. It has a 5th gen i7. 16gb of memory and I've swapped out the included windows drive with a blank m.2 drive (Samsung evo 500gb).  It has integrated graphics (unsure what kind) and a gtx950. Problem is that every time I try to run the kubuntu live USB it goes to a black screen either immediately or after the kubuntu splash screen pulses once or twice.  

After much digging around it looks as though many USB live drive makers aren't equipped to install new kernels so according to a sites recommendation I gave mkusb a try and had some luck. Kubuntu installed but crashes before I can even update graphics drivers.

After more digging around it seems maybe I should install in fail safe mode with nomodeset and first boot also in failsafe mode with nomodeset to install the graphics drivers.  This is new territory for me. The crashes were frequent and I'm guessing timing of those crashes corrupted things along the way during updates so I put Linux mint back on just to have something running for the time being. I would prefer kubuntu to be the sole OS.

Can you guys help me with a detailed walkthrough or bullets on how I should go about making a new live USB. How to checksums. And how to install with failsafe and nomodeset if that is in fact my best course of action? Thanks in advance for any help. I'm really wanting to get fluent with Ubuntu and I'm liking what I've seen from kubuntu.  Let me know if any other info is needed in order to get up and running.

---

### Post by grahammechanical on 2015-09-29
I cannot help you much but I will offer this information.

1) intergrated graphics + GTX950 = hybrid graphics = Nvidia Optimus technology.
2) Nvidia Optimus technolgy = need for a proprietary (Nvida driver) to get switchable graphics but it will not be done automatically. The switch between the intergrated adapter and the discreet adapter is done manually using the Nvidia settings utility that is installed at the same time as the driver. Or, through Prime Indicator

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

3) During installation if we tick the box "Install third party software" we will get a proprietary video driver. But you are having video driver problems after installation. So, I suggest to install without ticking that box. Just to get a working installation. Maybe.
4) I have just checked the Nvidia web site and it recommends Nvidia Linux driver series 352 or 355 which are dated the last 2 weeks in August 2015 for the GTX 950.
5) I do not know if Ubuntu/Kubuntu 14.04.3 or 15.04 will offer those drivers by default. I do not know if the latest drivers offered by 14.04.3 or 15.04 support Nvidia GTX 950.
6) After installation you most likely will need to go to System Settings>Software & Updates>Other software and enable (tick) Officially supported Non-free drivers to get updated nvidia drivers.
7) After installation we can install the third party video and audio codecs by searching the Ubuntu Software Centre for Ubuntu Restricted Extras or Kubuntu Restricted Extras. Whichever is relevant.

Regards.

---

### Post by sudodus on 2015-09-29
Welcome to the Ubuntu Forums :-)

It might be worthwhile to try different versions of Kubuntu, 14.04.3, 15.04 and even Wily beta 2 (to become 15.10 four weeks from now). I suspect that you have problems with the graphics driver (which you mentioned in the beginning of your opening post).

Have you tried more than one version of the nvidia driver?

Checksum: run the following command in a terminal window (with the actual name of your ISO file)

```
md5sum file.iso
```

and compare to what you find via this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by mastablasta on 2015-09-30
and here is a how to do a nomodeset: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by oldfred on 2015-09-30
5th gen i7 - Broadwell
That could be part of the issue. You may need 15.10.
Intel does help Linux in adding kernel updates, support software updates & Intel driver updates. But those have to be accepted into the kernel, and then added to a distribution. Many testers of very new hardware use a ppa to update whatever install they have to the newest kernel & other software to get it to work.

When you boot are you using Intel video or nVidia? Many boot in low power mode or use Intel to boot.
The nomodeset would be correct if booting with nVidia.

Skylake is the 6th gen, yours is 5th gen, but may need other Intel boot parameters
       Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)
Xubuntu 14.04 - GRUB2 nomodeset brings wrong screen resolution - Acer TravelMate 4740 with Intel HD Graphics
[http://ubuntuforums.org/showthread.php?t=2240620](http://ubuntuforums.org/showthread.php?t=2240620)
kernel 3.19 which is implemented with all needed intel graphic stuff
[URL="http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951"]http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951

[/URL]
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

[URL="http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951"]

[/URL]

---

### Post by sudohawk on 2015-09-30
When it boots it boots in nvidia i believe.  From what Ive been able to gather if my power button lights orange its running in performance or nvidia mode and white if its in power saving/onboard graphics mode.  The power button starts white during the kubuntu splash screen but then switches over to orange shortly after.  I did try to install a newer nvidia driver but failed miserably.  It wouldnt load to the desktop environment afterwards and every tutorial I tried online to fix the issue resulted in no change.  Its able to get kubuntu running as ctrl alt f1 takes me to the ttyl terminal and i can navigate around (this is where i was forced to try to get my desktop back to no avail).  I'll give 15.10 a shot.  I didnt know that kernels were processor picky.  I didnt realize 15.10 was going to be out relatively soon.  I'm tempted to stick with mint which i gather is an ubuntu derivative until the kubuntu 15.10 releases then give that a shot.

In light of that is anyone familiar with how to manually install the nvidia driver in mint?  The highest driver available in the driver manager is 346.92 (iirc) and nvidia's site indicates that I should be running 352.41.  When i tried previously to get this running on mint before giving kubuntu a shot it appeared to have installed but then i was infinitely stuck in mint's fallback mode and couldnt get out of that.  Any tips would be appreciated.

---

### Post by oldfred on 2015-09-30
If you add the Ubuntu ppa, then your highest driver will be the newest between Ubuntu's repository or the ppa, or ppa will install the same way. Make sure if you installed any other way or from nVidia you totally purge that install or else you get conflicts.

       sudo apt-add-repository ppa:graphics-drivers/ppa
      
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)

---

### Post by sudohawk on 2015-10-02
much appreciated guys.  Oldfred, the [COLOR=#000000]i915.preliminary_hw_support=1 bit in the grub command seemed to be helpful in getting kubuntu 15.10 to actually boot.  It was hit and miss but that and nomodeset seemed to be the ones that my laptop liked to boot under.  15.10 installed well enough and to my pleasure it had the option to install the 352.41 nvidia drivers as an available option in the driver manager.  It appears though that things were too good to be true and the drivers resulted in not being able to boot into kubuntu.  I couldnt even get into the ttyl mode after restarting from the driver install.  I tried a few more times reinstalling it but the driver seemed to not be well configured well for 15.10.  

One other thing that I found online that was PARAMOUNT in getting kubuntu installed was to insert libata.force=noncq into the grub line after silent splash.  This had to be done upon installation and seeming should be done upon first boot and furthermore have the grub file modified to have this always run.  From what I was able to dig up on this is noncq was meant for standard drives but dont really apply for SSD (which is what I'm using in my laptop).  It appears that there are a number of cases where this resolves kernel panics due to synchronization issues between the solid state drive.

Having thrown up the white flag for now (till 15.10 kubuntu is officially released with hopefully better driver support for my hardware) I reinstalled linux mint 17.2 cinnamon using the libata.force=noncq line as described above.  So far so good and I hope I'm not going to have to put my foot in my mouth for saying it but I've been running it for a few hours now and no crashes.  Previously it would have crashed by now so hopefully the noncq line has fixed my issues for now till i decide to give the official kubuntu 15.10 a shot.  I did want to post up my findings on what worked.  I'll give it some more time before making it official that the libata.force=noncq line has fixed my issues for now but its pleasing me thus far.[/COLOR]

---

### Post by mastablasta on 2015-10-02
hmm out of curiousity ... re: the NVidia driver - did you get a blinking cursor?

---

### Post by sudohawk on 2015-10-02
In kubuntu 15.10 beta2 no after the driver update to 352.41 as provided by the driver manager it would flash the kubuntu splash screen on bootup and then go right to black.

---

### Post by mastablasta on 2015-10-05
ctrl+alt+F1 - F7 doe they bring up the virtual console interface (terminal)?

I am curious because I too read about some particular Kubuntu issues on NVidia. I could not get the fully supported card to work. card was good, mobo was good, card worked crappy with opensource drivers, but the proprietary ones gave a similar experience to your's and I never thought about changing the desktop interface to for example stock Ubuntu. had the card at home for about 2 weeks doing all sorts of tests, tried various BIOS commands, various Linux OS commands and boot sequences. nothing made it work. tried the card on a windows PC - worked well. tried another card in this motherboard (I though maybe the interface can't handle it) and it all worked reasonably well. but this NVidia just gave me blinking cursors. and all I wanted is for my son to be able to play Minecraft without crashes... :(

now later on (about a month later) I read about some specific bugs with NVidia and Kubuntu interface. and this is the second time I read a similar thing. so my take on this (but this could be a long shot) and If I still had that GPU card would now be to try a different desktop environment or perhaps only a windows manager and see if it get's me somewhere. 

mind you I don't know much about Optimus & Linux other than it needs bumblebee project files for it to work. I never had a dual GPU PC yet. so I don't know how much is that a factor here. but from what I understand system boots using one chip and the user can then manually force it to use another. it is not auto as on windows and it is all basically reverse engineered (i.e. hacked :) ).

---

### Post by sudohawk on 2015-10-05
When I tried kubuntu I didn't get a flashing cursor and I couldn't get into Ctrl alt f1 command line ttyl interface. It literally appeared frozen.  Mint seemed more forgiving both cinnamon and KDE versions and I bet the KDE version would be stable on my machine with the libata.force=noncq line in grub but I'm going to stick to cinnamon till kubuntu 15.10 stable comes out.  I read the main contributor or owner of kubuntu is parting ways though and this ming mean less support for kubuntu in the future which is a shame as its seemingly going to be my favored flavor of Linux.  In any case I'd definitely give other flavors a shot.  Not sure why mint was more stable for me as it too is Ubuntu based but in my case it is now stable where as similar fixes didn't help much for kubuntu and my setup.

---

### Post by mastablasta on 2015-10-06
mint has many patches done to ubuntu. while based on ubuntu it is still slightly different. i had another experience with it about 3 years ago where some KDE effects did not work at all on mint. same effects worked ok on version of Ubutnu on which mint kde was based on. in any case both are pretty solid distros.

still a very interesting info you provided. i just wish i still had that GPU to try it out. why i never tried another distro is beyond me. i made a mistake of being to focused on the problem to see possible solution. i too could not switch to TTY. booting into text only mode worked as i remember but that didn't help in troubleshooting as drivers didn't initialise propperly in that case.

---


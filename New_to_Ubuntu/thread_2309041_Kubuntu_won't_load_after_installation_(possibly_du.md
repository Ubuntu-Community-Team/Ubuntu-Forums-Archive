---
title: "Kubuntu won't load after installation (possibly due to Nvidia graphics card) &amp;&amp; ..."
date: 2016-01-07
forum: New to Ubuntu
---

### Post by allen17 on 2016-01-07
I am a complete noob and am having issues installing Ubuntu on my MSI laptop. Here's what happened:

1) I tried to boot Kubuntu on my MSI laptop from a liveUSB to no avail (it would get stuck at the Kubuntu logo screen) so i turned it off.
2) after reading forums I realized it was an nvidia driver issue.
3) I used my old HP laptop to boot into Kubuntu with the same liveUSB, installed drivers and everything else that included the word Nvidia in the software manager onto the liveUSB.
4) I then took the liveUSB and _successfully_ booted into Kubuntu on my MSI laptop (I'm assuming it was indeed a driver issue because it was after the installation of these drivers that i was able to boot Kubuntu with my MSI laptop).
5) I installed the OS thinking that the downloads I made onto the liveUSB would also be installed onto my disk (Sadly, it doesnt work that way).
6) after restart I am again stuck at the Kubuntu logo.

I'm not sure if it makes a difference when resolving the issue but please note that i am attempting to dual boot with WIN10.

Also, i was having issues with getting my WiFi to work correctly when using the liveUSB. if i plug in a WiFi dongle or use USB tethering i can successfully connect; however, using the internal Qualcomm Atheros AR8161 Gigabit didnt work. 

Laptop: MSI PE60-6QE-031US

Any help would be greatly appreciated! Thanks in advance!

---

### Post by yancek on 2016-01-07
You indiicate initially you are trying to install "Ubuntu" from a flash drive then boot another machine with "Kubuntu" on it and install nvidiadrivers.  How would that help, installing drivers to another system on another computer?  It isn't really clear what you did.  Did you actually install drivers on the Live system on the flash drive?  That won't work either because a Live system is read-only and any changes you make are lost on reboot.

Are you trying to install Ubuntu or Kubuntu and do you actually have Kubuntu installed?  Or do you have Ubuntu installed?  Or neither and just trying to install?  

As for dual booting with windows 10, you should probably read the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by allen17 on 2016-01-07
Sorry, that's a typo. I am trying to install Kubuntu. I have fixed the error and also tried to make it a little more clear. also, I have set 4GB on the liveUSB to save the changes I make. for instance I installed gedit and it is still there on reboot.

initially i tried to run the liveUSB on my MSI laptop with no luck. It would get the the Kubuntu logo and sit idle at the screen.
I removed the liveUSB from my MSI laptop and booted it from my HP laptop (successfully).
I installed everything in the software manager containing the string "nvidia".
after installing the drivers onto liveUSB with my HP laptop, I removed it from my HP laptop and placed the liveUSB  into my MSI laptop.
I booted from my MSI laptop. This time it booted successfully!!
After booting successfully, i began installation onto my HDD, with the proper partitions set. (the same way that is noted in the provided link: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI))
I restarted my MSI laptop and again was stuck at the Kubuntu logo. (same problem as before)

So my question is this - is there any way i can install the nvidia drivers onto the proper partition of my HDD from the liveUSB? if not, is there a way i can get past the kubuntu logo and into the terminal and install the necessary drivers (i would prefer a GUI, but if i have to use the command line so be it)?

I have set my linux partitions to 30GB root, 18GB swap (I was reading that its necessary to have a little more swap memory than physical memory), 60GB home directory. both root and home are EXT4

I hope this makes it clear enough to receive some guidance. Again, thanks for any assistance in this issue.

---

### Post by yancek on 2016-01-07
You could try a one time edit when booting Kubuntu from the hard drive.  When you see the Grub menu with Kubuntu highlighted, hit the e key on the keyboard and the screen should show the menuentry lines.  Use the down arrow on your keyboard to get to the line beginning with the word 'linux', then right arrow to the end of the line and enter 'nomodeset' (without the quotes).  You can try putting it before quiet splash -- or after it or replace them.  Can't remember which way will work.  If you are then able to boot, you will need to find system settings and look for an option to install additional drivers.

If you have a Recovery option on the boot menu, you might try that.

---


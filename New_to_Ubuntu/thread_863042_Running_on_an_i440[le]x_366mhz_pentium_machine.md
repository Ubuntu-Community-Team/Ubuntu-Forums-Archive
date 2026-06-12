---
title: "Running on an i440[le]x 366mhz pentium machine"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by afrodeity on 2008-07-18
Last night I installed Kubuntu on a Piii 366mhz with 256mb ram and 8gig harddrive.

Is this too small to run Kubuntu? Are there any alternatives? It freezes once I get into a session. Get a message to do with force= and guess I need to set noapic nolapic, but don't know how to set the startup mode preferences without getting into a session.

Tried doing a restore system after hitting the esc.

runs fine, except for this message: host smbus controller not enabled.

also gets a fatal error inserting battery message. does this mean the battery needs to be replaced?

---

### Post by kunixos on 2008-07-18
You should try the Kubuntu alternative CD and if that doesn't work Xubuntu's alternative CD will definately do the trick.

You have plenty of processor/ram/hdd space to make Kubuntu work as it should, but the Alternative CD will install with a smaller 'footprint' and ultimately make your computer run smooother.

Hope this helps!

---

### Post by bumanie on 2008-07-18
Ubuntu/kubuntu need a minimum of 384mb ram to run  - try xubuntu, it can run on 128mb ram

---

### Post by prshah on 2008-07-18
> **afrodeity said:**
> Last night I installed Kubuntu on a Piii 366mhz with 256mb ram and 8gig harddrive.

Is this too small to run Kubuntu? 


While the RAM is OK, the processor it very low. I get passable performance on a PIII 500 Mhz/196Mb/8Mb AGP, and I use Xubuntu. Applications are slow and switching is jerky, but running programs are smooth.

> **afrodeity said:**
> 
Are there any alternatives?

I'd suggest you use Xubuntu, with IceWM instead of XFCE, for such a slow processor. Also, if the graphics card shares system RAM, turn it down to 8Mb or thereabouts, if you screen resolution is less than 1024x768.

> **afrodeity said:**
> 
 It freezes once I get into a session. Get a message to do with force= and guess I need to set noapic nolapic, but don't know how to set the startup mode preferences without getting into a session.

force, noapic, lapic startup codes are to be added as kernel parameters; hit ESC during bootup to get the GRUB menu, then select (highlight) the kernel option you want to boot, press "e" to edit it, scroll down to the line where kernel options such as "ro splash" are mentioned, press "e" to edit the line, add the options you want to the end of the line, then press enter to save the line, and "b" to boot with the saved changes. Note that this is only temporary; to make it permanent, make the changes in your /boot/grub/menu.lst file, and then ```
sudo update-grub
```

> **afrodeity said:**
> 
also gets a fatal error inserting battery message. does this mean the battery needs to be replaced?

If this is a desktop (looks to be) then that message is normal because the battery module, though loading, cannot find a battery to manage, so it gives this error and stops further activities. This does not refer to your backup/CMOS/BIOS battery (usually CR2032, 3v)

---

### Post by hyper_ch on 2008-07-18
on that cpu I'd rather recommend DamnSmallLinux, FeatherLinux, PuppyLinux....

---

### Post by afrodeity on 2008-07-18
Sorry about the confusion in this thread. The tag should read Xubuntu. I installed Xubuntu and got the associated problem. Am going to try hitting e and editing. Otherwise it's gentoo or puppylinux

---

### Post by Canis familiaris on 2008-07-18
+1 for Puppy Linux

---

### Post by afrodeity on 2008-07-20
I partitioned my harddrive using the Puppy Linux boot disk. Then I installed Pup into the hd1, ran grub. It boots nicely and I have a small os and great looking desktop, sort of like an eMac. I have now intalled Xubuntu in partition hd2. Ran grubber again in pup and edited the menu.ls

Here is the problem when booting with Xubuntu:

#kernel maps protect is an unknown key  (error)
#vm.mmap.min.addr unknown key (error)

#could not load lib modules 2.6.21 fatal

got this fatal a number of times

It means that when I go into a session it freezes up.

How do I implement the IceWM solution? Since I can't get into Xubuntu, session freezes, what do I do?

---

### Post by afrodeity on 2008-07-22
Ok, here's there thing. So much for the community spirit. It seems I am talking to myself. I am now downloading the alternate CD for Kubuntu and Xubuntu and will give this a bash. It's clearly an install issue with regard to implementation on 686 machines and from what I can gather there seems to be a linux community on 686, question: Will this be an Ubuntu base or somebody else's problem?

---

### Post by kunixos on 2008-07-22
Do you still have the Puppy Linux installed?

I recommend not trying to get X/Kubuntu to work if Puppy is working. You can do all of the same things in Puppy as in X/Kubuntu just with different parameters and if it runs well with your hardware specs, then stick to it.

If you'd still like to get X/Kubuntu to work I'd say fresh install, select Puppy from the "list" of other OS's and then see if Grub sets it up for you. Honestly I don't see how that error exists if it's a clean install. It might have been a corrupted disk or something of that nature.

Also, If you're using this computer for fun (and you have another computer you use for daily use) I'd suggest using hda2 to install Gentoo or Slackware to get a better 'feel' for how Linux works. It could be a fun project-type thing!

Hope some of this helps!

---

### Post by afrodeity on 2008-07-22
Apparently, there's a fluxubuntu project, which offers a version of xubuntu which may actually work. This might be the solution, since, my download of the alt CD ended up being corrupted, and its only about 300mb, which is a lot better for me :-)

---

### Post by snowpine on 2008-07-23
> **afrodeity said:**
> Apparently, there's a fluxubuntu project, which offers a version of xubuntu which may actually work. This might be the solution, since, my download of the alt CD ended up being corrupted, and its only about 300mb, which is a lot better for me :-)

The correct spelling is Fluxbuntu, and the website is at [www.fluxbuntu.org](www.fluxbuntu.org). I think it will run quicker than Xubuntu on your computer (it is great on my PIII), though I would hesitate to recommend it to a beginner. :)

Edit: It is definitely *not* a "version of Xubuntu" however. It uses Fluxbox instead of Xfce as its windows manager, and a completely different set of applications.

Check out this thread for more info: [http://ubuntuforums.org/showthread.php?t=855596](http://ubuntuforums.org/showthread.php?t=855596)

---

### Post by afrodeity on 2008-09-06
Thought I should inform everyone that Dapper Drake is running just fine on the above machine. Its a little slow, but it's working alright. So +1 for ubuntu.

---


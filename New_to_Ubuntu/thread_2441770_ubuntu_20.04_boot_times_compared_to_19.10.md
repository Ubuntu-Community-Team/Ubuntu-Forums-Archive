---
title: "ubuntu 20.04 boot times compared to 19.10?"
date: 2020-04-26
forum: New to Ubuntu
---

### Post by tommylinux on 2020-04-26
Total Linux newbie here everyone, and really interested in converting to Linux full tilt boogie. But I have a couple of what are most likely newbie questions that hopefully the vets in here can answer for me;


[LIST]
[*]What is up with ubuntu 20.04's boot time compared to 19.10? I have both live versions on identical USB 3 drives, and 20.04 takes twice as long to boot on a Ryzen 7 3750? 
[*]And what is up with the lame dark mode? Meaning, enable dark mode, and then right click your desktop. The context menu isn't dark mode enabled? Is that a shell limitation? 
[/LIST]

Anyone else experiencing slooooooowwwwwwwwwwwwww boot times like that. And yes, that's taking into consideration disabling the drive check during boot.
Thanks for any help or guidance.

---

### Post by Autodave on 2020-04-26
I have installed Xubuntu 20.04 on 4 machines so far.  I can say w/o hesitation that it is quicker booting than 18.04 was.

Keep in mind that 19.10 is not a LTS (long term service) release, so you will have to upgrade to 20.04 very shortly if you install 19.10.  Don't go by boot times from a USB stick.  Install the 20.04 and be done with it.

---

### Post by tommylinux on 2020-04-26
Hey Autodave, ...thanks for the feedback. Why did you choose Xubuntu? Are all four of those old machines? I have an old dual core Pentium 2117U processor running ubuntu 19.10 better than my Asus ROG Ryzen 3750, and my HP Ryzen 1700 8-core can run unbuntu 20.04.

And what about my second question regarding dark mode and the desktop context menu? Any feedback there?

---

### Post by CelticWarrior on 2020-04-26
[https://www.omgubuntu.co.uk/2020/04/enable-full-dark-mode-in-ubuntu-20-04](https://www.omgubuntu.co.uk/2020/04/enable-full-dark-mode-in-ubuntu-20-04)

---

### Post by Autodave on 2020-04-26
They range from Pentium 4s to this machine: Ryzen 7 2700, 16 gig dual channel RAM, nVidia RTX 2070.  I originally tried Xubuntu on an old Asus EEEPC.  It worked great.  And I loved the simpler screen.  I don't really care what the desktop looks like because I don't sit here and stare at the desktop!  The desktop is simply a means to get to the program(s) that I want to use.  On some older machines, I need Xubuntu.  On this machine, I just like it.

As for the dark mode, I have no idea.  Again, the desktop is only visible to me for a second or two until my desired program is loaded.

---

### Post by tommylinux on 2020-04-26
Thanks CelticWarrior, I was able to use the info in the link you provided to decipher getting Yaru-Dark on my 19.10 installation as well :guitar:

---

### Post by oldfred on 2020-04-27
My screen comes up in about 6 sec after start of boot. Does not include UEFI time.
```
fred@Z170N-focal:~$ systemd-analyze 
Startup finished in 3.335s (kernel) + 5.700s (userspace) = 9.035s 
graphical.target reached after 5.690s in userspace

```

This is a Intel Z170 Intel with Skylake i5-6500. But I just installed a new NVMe drive which made it faster.
But I also tune system to reduce boot times.
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)

---

### Post by tommylinux on 2020-04-28
oldfred my friend if I may, you sir are truly a master of all you survey. The article you shared hit the nail on the head with what I am experiencing with v20.04 on my UEFI systems. Since creating this post initially, I chose to upgrade my old Pentium 2117U Gateway laptop vs. a fresh install, and low and behold, v20.04 not only runs, but runs as well as, if not better than v19.10.

The difference between this nearly seven year old Gateway touchscreen laptop purchased from a Staples store for $274.99 US back in December of 2013, and both my Ryzen systems, is of course their UEFI setup, which provides no option to be disabled vs. this Gateway's standard BIOS.

Because of the link you provided, I can now further troubleshoot this to find out why the UEFI on my Ryzen systems is causing 4-5 minute boots times to a flash drive.

Thank you oldfred

---

### Post by oldfred on 2020-04-28
Boot to a flash drive is always slower.

Years ago I gave up on DVDs, went to flash drives.
Then USB3 came out & even on USB2 port USB3 was faster. Then USB3 port with USB3 flash drive was a bit quicker.
But found using an old SSD on USB3 was almost as fast as internal HDD.
But I now normally load ISO from one drive into RAM and install to another drive using grub2's loopmount.

---

### Post by tommylinux on 2020-04-29
Thanks for the info and for the link my friend. Wow, RAM drive, man I haven't used one of those since my DOS days, but now I'm going to have to look into it. I used rEFInd years ago (2006-7?) when Apple converted OS X to x86, but that was only for Apple and Windows at the time. Neat to see its still around. I started with MS DOS, then Windows 3, then 95, then Unix (HP UX & DG/UX), then Windows 98, and then my first taste of Linux (harsh at the time), then back to Windows, converting to OS X toward the end of 2006 when they dropped Motorola for Intel. After Job's passed in 2011, OS X has been pretty stagnant. Got into VMs for awhile. It was cool on the Mac, because on the Mac you can run any VM, even Apple. However, I've watched Linux mature over the years, and now its my primary OS as of just recently. My 9-year old MacBook Pro died, and although I feel I got my money out of it over 9-years, Apple kills me with restrictions. Firmware updates that prohibit OS installs at certain intervals, etc. I friggin' love that I'm typing this message on a nearly 7-year old Gateway Pentium 2117U dual core laptop running the LATEST version of ubuntu faster than it ran the version of Windows that came preloaded on it nearly 7-years ago.

I first got introduced to ubuntu when I read that Jon Lech Johansen used it as his primary OS years ago. I tried it at the time however, and for me it simply didn't compare to what I had with OS X. I followed Jon for years until his online presence kind of faded away. I settled on ubuntu not only because of its stability and development, but also because of its hardware support. ubuntu and Fedora are my favorite, and I prefer Gnome over KDE. For very limited hardware, I really like Lubuntu with LXQt vs. the previous LXDE. Amazingly enough, this old dual core Pentium 2117U runs the standard ubuntu install just fine for most things like web browsing, email, etc. Of course I wouldn't run any kind of video editing on it, but for the most part, I can get most things done it.

I just recently broke over and purchased my ASUS Ryzen 7 3750H laptop, with an Nvidia 1660ti card no less, and I'm looking forward to getting this freakin' UEFI boot time issue resolved. It has a RGB keyboard that drives me nuts because the color can only be controlled through Windows, when in my opinion you should be allowed to control it through the UEFI as well. Gotta say, when it took nearly 5-minutes to boot ubuntu, it nearly crushed me. I was hoping for like sub 20-second boot times with the Ryzen processor and USB 3.1 drive. Hopefully I'll get it all figured out soon <fingers crossed>

Thanks for all the help my friend

---

### Post by oldfred on 2020-04-29
I retired my 2006 Toshiba laptop in 2012. Used fallback/gnome-panel.
I am retired and carted laptop back and forth to Florida for the Winters. Decided I preferred larger screen & separate keyboard, so built desktop.
I used gnome-panel originally as old desktop still has 4:3 monitor and bars on top & bottom work better than on side as with Unity & gnome. Gnome panel also is more lightweight, but not exactly same as Mate or Budgie. More like old Ubuntu before Unity.

But I installed 16.04 in laptop and Unity almost ran. Once gnome-panel added it ran well.
Just to test I installed 20.04 on laptop. Coin battery and main battery are both drained & I have to set clock each time I plug it in. I tried full Ubuntu but after a day or so, and install was still spinning. Was able to install server version in less than an hour & added gnome-panel. Quite a bit still missing & had to add bits & pieces.
But that old laptop now boots in less than a minute.  ;)

Just got new kernel. Manually counted seconds from shutdown, UEFI (fast boot still off), & boot. Bit less than 25 sec total.
Spoiled by new NVMe drive.

---


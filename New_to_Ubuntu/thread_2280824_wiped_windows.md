---
title: "wiped windows"
date: 2015-06-02
forum: New to Ubuntu
---

### Post by jake64 on 2015-06-02
So,  a while back I downloaded Ubunto. I accidentally wiped windows,  which is fine,  but now I want to dual boot another distro. I'm still fairly new with linux,  but I'd like to expand.
I chose a new distro, downloaded it, got unetbootin through the terminal,  and ran it. When I rebooted,  unetbootin popped up,  and I accidentally hit a key, which just logged me into Ubuntu. I assume I'm supposed to enter on default to bring up the installer etc.  
Now I can't get back to that.
I wiped my usb,  I formatted it to fat32,  I did everything again.  
Now I have a headache.  Any suggestions?

---

### Post by Bucky Ball on 2015-06-02
Welcome. If you were logged into a Ubuntu desktop, that is fine. You can have a look around or there should be an icon on the desktop that says 'Install Ubuntu'. 

When you boot from the Live USB to install Ubuntu, you should get a list of options. At the top (I think) is Try Ubuntu. Sounds like you accidentally hit that. Under that is 'Install Ubuntu'. 

You had it right the first time by the sounds. The 'Try Ubuntu' option simply runs Ubuntu 'live' from the USB without changing your hard drive in any way. A 'try before you buy' approach. ;)

---

### Post by jake64 on 2015-06-02
Yeah,  that's what I did the first time,  however I still couldn't find my windows 8. Then something happened,  and every time I logged into Ubuntu it started fresh.  Now it's persistent. Oh well with that.
The problem though I'm facing now is being unable to dual boot kali linux alongside Ubuntu.

---

### Post by mattharris4 on 2015-06-02
I have to make sure I understand what you are saying since how I understand your comment is different from what Bucky seems to understand.

Here is the rundown as I understand it:

1.  You are currently running Ubuntu (your post says Ubunto but I don't know of a distro by that name and a Google search comes up without any entries under Ubunto)
2.  You now wish to dual-boot with a second unnamed Linux distro
3.  You attempted to install this second distro and when you booted up to install it you ended up back into Ubuntu, possibly after hitting the wrong selection in the UNetbootin menu
4.  You then formatted and reinstalled the second distro onto your USB thinking that was the problem.

If I understand correctly I think your computer is set to boot first from the USB first already and it probably was fine to begin with.  However, if you cannot now get into the installer menu go into your BIOS and set the computer to first attempt to boot from a USB before moving on to the hard drive.  You will not need to go in and reset this after you are done installing the second distro to your computer, the computer will attempt to find a bootable USB before moving on to the hard drive but that only takes about one second when you first turn the computer on so resetting it back to first boot from the hard drive is unnecessary.  Instructions vary by computer make and model, usually you press an F key when the maker's logo shows up on screen directly after turning the computer on the follow the instructions to wade through the screens until you get to the boot order screen, there is usually a comment at the bottom of that logo screen with the F key to push -- you usually only have 1-2 seconds to press that key before the computer goes into boot mode and boots in whatever order the BIOS is set to boot in.  If your only issue is you selected the wrong selection on the installer screen you just need to use the USB copy you now have of whatever Linux distro to boot into the UNetbootin menu and either select Try (distro) or Install (distro).  I would try it first if you can, make sure that the basics work like any wireless card, your ethernet card, sound, trackpad (if a laptop), etc.  If all work and your computer did not originally come with Win 8 or 8.1 (if it did we need the make and model of your computer -- although since you were successful installing Ubuntu this is not likely an issue) after selecting the install icon you should be able to just follow the prompts to dual-boot (with the buntus it usually has an option that states essentially "Install Ubuntu with other OS", it might say "Ubuntu" even if you are installing another buntu), partition your hard drive into what appears to be two sections on the screen (actually you are partitioning the drive into at least four more sections including root, home, etc but that is done automatically by the installer unless you select "Something Else", you don't need to do that here) and install the second distro.  With Linux distros I have worked with you can go into the installer from the "try-it" screen, usually via an icon on the home screen.

If things do not work in the try-it screen, you need to research (Google is your friend here) whether the issue or issues can be easily rectified after install (or will be rectified by updated code installed during or directly after your install) before you install this distro.  Ask questions here in either this thread or the appropriate section of this forum if necessary.  Please also state what distro you are attempting to install so we can help you better.  A well-respected moderator has assured me that we can assist with issues here even if the distro is not a Canonical-endorsed distro (Ubuntu, Lubuntu, Xubuntu, Kubuntu, etc -- the buntus), the worst that can happen is the comment be moved to the appropriate section of the forum.  If we are discussing installing a mainline Linux distro (Linux Mint, Debian, any of the buntus, Fedora, etc) there is also assistance on their respective websites and sometimes a forum geared to that distro or line of distros to ask questions in (obviously with the buntus this is the right place).  If we are talking smaller distros such as Kolibri, Damn Small Linux, Tiny Core, etc assistance may be extremely limited.

Usually I would ask about your RAM, CPU, etc but if you are running Ubuntu successfully you should be OK spec-wise with the majority of Linux distros.  Be sure to select the appropriate bit version for your distro (32 or 64 bit depending on your CPU, Google your CPU like this "(CPU model) bits".

I wish you an easy install and hope you like whatever distro you are installing.

---

### Post by jake64 on 2015-06-02
It's an hp15 came stock with windows 8.  
I have the usb set to boot first. It takes me directly to Ubuntu. It's like the distro, kali linux, I am trying to install doesn't exist.  Unetbootin only showed up the one time when booted it up the first time after unetbootin extracted the iso. I enabled legacy mode,  which gave me a few extra options, but that didn't help either. I'm thinking my issue is unetbootin.

---

### Post by jake64 on 2015-06-02
Update:
I found unetbootin.  Once I switched the boots,  I then hit esc,  and my boot menu came up again.  I was able to select usb hard drive,  and then unetbootin popped up.

---

### Post by Bucky Ball on 2015-06-02
So your initial issue is solved? If so, please mark the thread as solved (see the second link in my signature) and post a new thread for any other issues with a title that tells us something about your support request rather than something generic. 

Thanks.

PS: If your new issue is about Kali Linux, please post in [Ubuntu/Debian based]("http://ubuntuforums.org/forumdisplay.php?f=452") as Kali is not an official member of the Ubuntu family. You may also like to try your luck on the [Kali forums]("http://forums.kali.org/").

---

### Post by cariboo on 2015-06-03
To add to what Bucky Ball said, if you have problems with the tools provided by Kali, please use their forums for support, as we don't support those tools here.

---


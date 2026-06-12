---
title: "Live CD restarts after a few seconds."
date: 2014-05-28
forum: New to Ubuntu
---

### Post by doctor2 on 2014-05-28
I am trying to install Ubuntu 14.04 on a desktop that already has Windows 7 on it. I've partitioned the drive to give Ubuntu 50 GB. From what I've read, it's better to install Windows 7, then Ubuntu afterward. The problem is that every time I boot the computer from my Ubuntu Live CD, it shows the Ubuntu load screen, then restarts and send me to the screen with four choices ("Try Ubuntu without Installing", "Install Ubuntu", "Factory Install (OEM)" and "Check disk for errors").

I've read that people have had this same problem with previous editions (12.04), and the fix they had for that one was to install the alternate version. But I would really like to install 14.04.

Also, I have had Ubuntu on this computer before. That was before I installed Windows and it was 13.04 32 bit. It's a new computer with 8 GB of ram and a 3.6 GHz processor and I'm running Windows 7 Ultimate 64 bit, so I think I should be able to run the 64 bit version of Ubuntu, right?

By the way, I've tried using two different Live CDs, and a few Live USBs. I've downloaded the ISO's via direct download and from the torrent. I'm not too sure what to do.

What can I do?

= = = 
Little update... When I put in the Ubuntu with Gnome live CD I made, while Windows is running, I can install Ubuntu from within Windows using wubi.exe, but then when it restarts it'll go into Ubuntu for a bit but then it says that it can't find the root folder.


I'm trying to reinstall it now with the root folder in a separate partition.


[COLOR=#000000]
[/COLOR]

---

### Post by doctor2 on 2014-05-29
Update 2:

Whenever I install Ubuntu via Wubi, when I restart later, it won't boot (not even into Windows) and says BOOTMGR is missing.

---

### Post by su:bhatta on 2014-05-29
Wubi is a project that has been abandoned. Please steer clear of it. Really sorry for giving such vital information this late.

Important: Please specify your computer hardware (Processor, Graphics, RAM) as much as you can.

> The problem is that every time I boot the computer from my Ubuntu Live  CD, it shows the Ubuntu load screen, then restarts and send me to the  screen with four choices ("Try Ubuntu without Installing", "Install  Ubuntu", "Factory Install (OEM)" and "Check disk for errors").
Did you try choosing 'Try Ubuntu' from that screen and was again rebooted?

Try Pressing F6 on that screen, it will open a small dialogue box, choose 'nomodeset' option from there and select "Try Ubuntu" see if you end up with a live session.
Look at [this page]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it?lq=1") with screenshots.

Does your machine have UEFI boot ?

---

### Post by doctor2 on 2014-05-29
My computer specs are...
3.6 GHz AMD with Radeon onboard graphics
MSI motherboard
and 8 GB ram
1 TB HHD

My machine does have UEFI boot.

I'm looking at that page now... Thank you for your help. :-) I'll be back with the results from your suggestions...

---

### Post by doctor2 on 2014-05-29
I have tried the "Try Ubuntu without installing" option, by the way. It goes to the purple loading screen, but then just goes back to the black screen where you choose the four options again (Try, install, OEM install, or check disk for errors).

Also, I've pressed F6 on the black choice screen, but nothing happens...

I'm still checking out that link you posted though...

---

### Post by doctor2 on 2014-05-29
I think the second thing (on that link you sent me) looks like it's working!!!! su:bhatta, I love you. I guess the video card drivers were the issue. :-/

I can now try Ubuntu without installing! :-D

One more question... When I try to install Ubuntu, it doesn't recognize my Windows 7 operating system. I used Gparted to set up a 20GB partition to install Ubuntu on...

So, on the installation type screen, I chose, "Something else"
On the next screen, should I select the partition I want to install Ubuntu on, then use as, "EFI boot partition"? I'm not too sure how the boot process will be effected. Will I still be able to boot into Windows after?

---

### Post by doctor2 on 2014-05-29
So I mounted the partition I'm installing Ubuntu on at "/" and selected EXT4 for the format. For the larger storage partition, I selected NTSF. I'm installing Ubuntu now... I'm wondering how the dual booting works...

---

### Post by su:bhatta on 2014-05-29
Again, I seem to be late with my response.
With Ubuntu dual booting, you will get a GRUB screen on start up which will list the available OS's in your HDD to which you can boot the system.
 Use arrow keys on the Grub screen to navigate to the OS of your choice.

NTFS for the larger partiton is the best idea as both Windows and Ubuntu can access it. 
Ext4 partitions are 'invisible' to Windows.

I am not at all well versed with UEFI, but here's some[ links]("https://help.ubuntu.com/community/UEFIBooting") that will [help]("https://help.ubuntu.com/community/UEFI") you.
In case the installation goes fine but you face problems when you reboot, start a new thread and mark this one as 'Solved' using the 'Thread Tools' at the top right of the page.
There are enough people here to help you for UEFI problems (am not naming any, but there will be assistance for sure)

What Radeon card do you have, the exact specs if provided will be helpful.
After installation, search from Dash (i.e. the first icon on the dock, or whatever they call it in Unity, left of your screen) 'Software and Updates' 
There one tab should be 'Additional Drivers' search for additional drivers(for your graphics card), will take some time and list you options available.
Choose the proprietory drivers and you should be good to go(generally fglrx-updates work nicely, never have failed me at least).

Welcome to the world of 'Linux for Humans'

---

### Post by doctor2 on 2014-05-29
Yeah, now it's only booting from Ubuntu. :-/

---

### Post by doctor2 on 2014-05-29
Okay... This issue is totally solved. Thank you again! You are awesome. I'm gonna mark it as solved now. :-)

---

### Post by su:bhatta on 2014-05-29
Do this first and see if it helps:
Boot Ubuntu, then open file manager it should list your Windows partition too, just click on it and it should mount i.e be ready for use and it will show your Windows Folders et al. Important : Dont make any changes whatsoever there.

Open a Terminal, Ctrl +T should open one (else find from Dash), then run ```
sudo update grub
```
It will ask for your password, it will not show, just type blindly and hit 'Enter'

It will do its task. While it does, you will be able to see if Windows is listed as an OS.
Then reboot and see if Grub finds the Windows entry.

---

### Post by doctor2 on 2014-05-29
it says "sudo: update: command not found".

---

### Post by su:bhatta on 2014-05-29
OOOps, my bad !!! Really sorry.
```
sudo update-grub
```
That should work

If you still cannot find Windows in Grub menu read up the links I gave in post#8 and open a new thread.
Glad to be of any help. Wish you will stay with us for long.

---

### Post by doctor2 on 2014-05-29
IT FOUND WINDOWS 7!!! :-D I think I might be all set! Now to learn how to code... And yeah, I chose the EXT4 specifically so Windows wouldn't know it's there. lol I can't thank you enough.

---

### Post by su:bhatta on 2014-05-29
Glad we got that sorted out before my bedtime (2 am) :)
Enjoy your work in Linux. It is awesome.

---

### Post by doctor2 on 2014-05-29
Oh man. I can't believe you're helping me out at this hour! Are you at least getting paid?

---

### Post by QIII on 2014-05-29
As this is a volunteer forum inhabited by normal Ubuntu users, none of us is getting paid.

---

### Post by doctor2 on 2014-05-29
Unbelievable! Man. I need to get good at this so I can repay the community. I was soooo frustrated. I tried for about a week (every day all day) to get this straightened out. bhatta, you are awesome.

---

### Post by su:bhatta on 2014-05-30
Paid, if I was, I wouldn't be half as enthusiastic about this and would have only been doing my 'dooty' !

Nope, I am only a part of a community that is awesome :) 
And am really really glad to be a part of it.

Anyways, wish you good times ahead !

---


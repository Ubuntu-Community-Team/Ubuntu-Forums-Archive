---
title: "blank windows until resized"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by ProntoAnthony on 2012-01-11
Typically I try to find solutions to problems myself. Often I find answers already written on the forum here, but this one is something I've never heard of before.

Suddenly whenever I open a new application by clicking on an icon a blank window will appear. Only if I make it smaller by resizing it can I see what is inside the window. This symptom includes when the application itself opens the window, like when I'm editing a document and I want to save it. The 'save as' dialog window comes up blank.

My thought is that I incorrectly set an option in CCSM but I just can't find it.

The problem exists both in Unity and Gnome shells. It happens in Nautilus consistently and CCSM, too. It is really strange.

More info:

It seems to be load related. For instance, if I close all apps and then open Nautilus then its window will not be blank.
I just added 4Gig memory to my system this week. I'm runnung the -pae version of the Linux.

---

### Post by arubislander on 2012-01-11
Hi,

You've started experiencing this behavior only *after* you added 4GB of memory to your system?

---

### Post by ProntoAnthony on 2012-01-11
> **arubislander said:**
> Hi,

You've started experiencing this behavior only *after* you added 4GB of memory to your system?


Yes.

---

### Post by ProntoAnthony on 2012-01-11
Given that I just installed the memory and did not re-install any applications after using synaptic to move to the -PAE kernal, I tried re-installing some applications today and have not run into the problem since then. It is a very unscientific test, but so far I'm quite pleased with the results.

---

### Post by ProntoAnthony on 2012-01-13
Darn. It is still happening intermittently. Both for loading applications, and for opening sub-windows, like an open file dialog.

This is a very strange problem indeed.

---

### Post by Ms. Daisy on 2012-01-13
I'm a big advocate of simple things first.  Have you removed the RAM you added to see if the problem resolves?

---

### Post by ProntoAnthony on 2012-01-13
I went into synaptics package manager and noticed that although
I installed linux generic-pae was installed as my kernel that linux-headers-generic was still installed, not linux-headers-generic-pae. So I took the bold step of installing the -pae headers and uninstalling the regular headers,

After rebooting there was no change. Blank windows are still intermittently coming up until I resize them. Text within thpse windows always become visible when I shrink down the window, and vanish again once I use my mouse to resize them bigger. The exact size of the windows vary before the contents of the windows become invisible.




Perhaps I need to re-install more libraries and utilities. How do I do this while keeping my settings and apps? I didn't do a complete re-install, just the applications that were (and still are) behaving badly.

---

### Post by ProntoAnthony on 2012-01-13
No I have not removed the new memory, but I hate to pull it out. If there were a problem with the hardware I cannot fathom how there would be no other symptoms.

---

### Post by Ms. Daisy on 2012-01-13
Only one way to find out...

---

### Post by ProntoAnthony on 2012-01-13
Thanks for the suggestion.


You are right in that I should test the memory, but removing it will leave the possibility that the -pae kernel is what is causing the problem. 

My thought is to run the memory test from the GRUB menu. It is running now and I've switched to my laptop so I can continue to do my other work.

---

### Post by wildmanne39 on 2012-01-13
Hi, also I had this kind of problem in 11.04, I had to change my nvidia card driver from the current to the old 173 and then it worked great.

---

### Post by ProntoAnthony on 2012-01-13
Yikes! My video adapter is integrated in the motherboard.

After over an hour running the video test and 1 complete pass, no errors have been found. Still, Ill let it run a little longer.

---

### Post by ProntoAnthony on 2012-01-13
> **wildmanne39 said:**
> Hi, also I had this kind of problem in 11.04, I had to change my nvidia card driver from the current to the old 173 and then it worked great.

The driver?

I mis-read your post. I am using the 173 nvidea driver.

---

### Post by wildmanne39 on 2012-01-13
Hi, please post the output of:
```
lspci | grep VGA
```
Thanks

---

### Post by ProntoAnthony on 2012-01-13
Stopped the mem test...


lspci | grep VGA produced:

anthony@anthony-Dimension-E521:~$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
anthony@anthony-Dimension-E521:~$ ^C
anthony@anthony-Dimension-E521:~$

---

### Post by wildmanne39 on 2012-01-13
Hi, that driver should work fine with that card unless there was an update to that driver that you do not know about.
Thanks

---

### Post by ProntoAnthony on 2012-01-13
Great...so the video driver is good and the memory tested good.

Where do I go from here?

---

### Post by Rainbow_Dash on 2012-01-13
> **ProntoAnthony said:**
> Great...so the video driver is good and the memory tested good.

Where do I go from here?

At worst you might have to do a reinstallation. You might want to try a different driver like the Noveau driver. In my experience the OSS drivers work better for Ubuntu 11.10 (the closed ones worked better for the previous versions).

---

### Post by wildmanne39 on 2012-01-13
Hi, there are two things to try, I recommend the first one first to confirm it is a nvidia driver ram issue.

Log out and into ubuntu no effects and see if that works, then you can go into your bios and increase the Frame Buffer Size in bios to 256MB or 512MB.
Thanks

---

### Post by ProntoAnthony on 2012-01-13
Decided to take out release CD and re-install.

In general it went well, but when I rebooted the system said:

FATAL:Module nvidia_173 not found.

(EE) NVIDIA (0) Failed to load the nvidia kernel module

It also said 281 packages needed upgrading so I keyed in:

sudo apt-get upgrade

that caused a lot of things to be downloaded and upgraded but not the nvidia driver. I cannot do a startx.

So I'm back on my laptop trying to figure out what to download to my usb stick and copy over to the desktop.

---

### Post by wildmanne39 on 2012-01-13
Hi, you should be able to get back to the desktop by doing:
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
did you just install over the top of your old ubuntu or did you do a clean install?

Just installing over could create more issues.
Thanks

---

### Post by ProntoAnthony on 2012-01-13
I just installed over the old.

At this point I've spent enough time attempting to save the old. I'm taking your advice and doing a complete fresh install since I have all my important data on Ubuntu One and DropBox.

---

### Post by wildmanne39 on 2012-01-13
Hi, I would try what is in my last post before you reinstall and just to be clear the person that recommended the reinstall in the first place was someone else that is also a new user.
Thanks

---

### Post by ProntoAnthony on 2012-01-13
> **wildmanne39 said:**
> Hi, you should be able to get back to the desktop by doing:
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
did you just install over the top of your old ubuntu or did you do a clean install?

Just installing over could create more issues.
Thanks

Tried doing the remove and reconfig without success. That's why I am doing the clean install.

---

### Post by wildmanne39 on 2012-01-13
Hi, okay.
Thanks

---

### Post by ProntoAnthony on 2012-01-13
Clean install done. System says there are drivers available for the video, but why do I need them if I'm running fine now?

---

### Post by wildmanne39 on 2012-01-13
Hi, it installs the open source driver which works fine for normal users if you do not want 3D capabilities or better 3D capabilities.

If you are happy with it leave it as it is.
Thanks

---

### Post by ProntoAnthony on 2012-01-13
I found that out quite quickly, so I installed the nvidia driver.

---

### Post by ProntoAnthony on 2012-01-14
Darn.

After the clean install, I have been installing applications again. Everything was going swimmingly...until I installed Eclipse. Manually, not from a repository. Perhaps a coincidence, but I observed a blank--until resized--window again.

Will keep going. What else can I do?

---

### Post by wildmanne39 on 2012-01-14
Hi, you might remove Eclipse completely with the purge command to see if that fixes the issue.
Thanks

---

### Post by ProntoAnthony on 2012-01-14
I'm thinking that since it only happened once and I haven't been able to reproduce it that I'll keep installing and leave Eclipse alone.

If it continues to happen I'll see about un-installing.

---

### Post by wildmanne39 on 2012-01-14
Hi, Ok but if it was me I would wait a little while and see if it happens again that way it is possible that it is one program you installed and not hundreds at once making it impossible to tell what caused the problem.
Thanks

---

### Post by ProntoAnthony on 2012-01-14
Yep. Still happening.


Installed using manually using this guide:

[http://colinrrobinson.com/technology/install-eclipse-ubuntu/](http://colinrrobinson.com/technology/install-eclipse-ubuntu/)

Problems began, so I di this:

rm /opt/eclipse/
rm /usr/share/applications/eclipse.desktop
rm /usr/bin/eclipse

Now I'll wait and see...

---

### Post by wildmanne39 on 2012-01-14
Hi, it says that it is under development so there is likely to be bugs in it, this is how to use the purge command to get rid of configuration files too.
```
sudo apt-get --purge remove eclipse* or whatever the packagename is.
```
Remember capitalization matters.
Thanks

---

### Post by ProntoAnthony on 2012-01-14
Thanks.

Did both 

sudo apt-get --purge remove eclipse*

and 

sudo apt-get --purge remove Eclipse*

Nothing was found either time.

---

### Post by wildmanne39 on 2012-01-14
Hi, ok that is good.

---

### Post by ProntoAnthony on 2012-01-16
looks like its working fine now.

Thanks everybody!

---

### Post by wildmanne39 on 2012-01-16
Hi, your welcome!

---

### Post by Geezer60 on 2012-06-11
I've got the same problem, random blank windows until i shrink them a bit.  I'm using an old laptop HP Pavillion dv6000, have made no changes to the computer in the 5 years i've had it, recently upgraded to 11.10 (32 bit) clean install on formatted drive.  I find it happens more when I have 3 or more windows open, but what application seems totally random.

And by the way I don't now, nor have I ever had eclipse installed.

---

### Post by wilee-nilee on 2012-06-11
> **Geezer60 said:**
> I've got the same problem, random blank windows until i shrink them a bit.  I'm using an old laptop HP Pavillion dv6000, have made no changes to the computer in the 5 years i've had it, recently upgraded to 11.10 (32 bit) clean install on formatted drive.  I find it happens more when I have 3 or more windows open, but what application seems totally random.

And by the way I don't now, nor have I ever had eclipse installed.

If you want help you need to start your own thread and describe the problem.

---


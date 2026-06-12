---
title: "How to stop opening the Mate-Terminal window the  moment I log in xubuntu?"
date: 2019-04-17
forum: New to Ubuntu
---

### Post by vacuous on 2019-04-17
I edited the .bashrc file and inserted usr/bin/Mate-Termial. Now,the next time I log into the system, it keeps opening the terminal all over the place and not letting me to even stop or kill it or do anything else. 

So How can I stop opening the terminal the moment I log in without re-flashing the image?


Because with ubuntu/xubuntu deskto system, If I want to run any application(x-sharedlib) the moment I log in through the bashrc file, I have to manually open the Mate-Terminal. I believe the right way of doing it is using the systemd management system as pstree -p command spits out what process was run as the first application. 

So any hint on how to run user-defined application as the first application without the desktop log-in prompt would be helpful. 

Thanks

---

### Post by TheFu on 2019-04-17
Don't put any interactive program inside startup files that aren't meant for it. .profile, .bashrc - don't put GUI programs into those.
Boot from any desktop install disk, mount the HDD storage and edit the file to remove that line.

There are many different sorts of logins on Unix. Batch local, batch remote, interactive local, interactive remote, GUI, no GUI.  The .bashrc is for non-interactive and internactive non-GUI local and remote logins.  Don't put GUI programs into there.

If you want any GUI program to be launched after login, then your WM or DE will have a way to do it. Each is a little different.  I use openbox, so there is an **autostart** file that goes into **$HOME/.config/openbox/** directory.

Don't touch systemd stuff for anything GUI.

You cannot run any DESKTOP GUI application until after the X/Session is up.  The X/session is required to display something on a local or remote display.  If you want to run something that is a GUI, but not have it display anywhere, then you can use xvfb.  You'll never be able to click on anything on that program.

Or you could setup an automatic login, which is terrible for security, and have the DE or WM run it automatically.

---

### Post by vacuous on 2019-04-17
Hello, TheFu,
first of all, thanks a lot for your reply. 

I am running an eMMC module of 32GB containing 64-bit xubuntu linux image with an embedded ARM-based board called odroid-xu4. So when you said "[COLOR=#000000]Boot from any desktop install disk, mount the HDD storage and edit the file to remove that line", I don't know how much I can make use of that. 

[/COLOR]would you please elaborate what you really mean by "[COLOR=#000000]Boot from any desktop install disk, mount the HDD storage and edit the file to remove that line" so that I can utilize that knowledge on a desktop machine.[/COLOR]


All I really want to do is to run an executable/x-sharedlib as an application that captures images by a machine-vision camera (after being triggered by an external trigger with a certain frequency ) and store the images on an external hard-disk. The camera has its own software development kit (SDK) with many APIs;And through a header file from that SDK, I can use those APIs in a c++ program and once I compile that program, it gives an executable or x-sharedlib which I'm trying to run as the first application after all the required system initialization. 

The images starts being stored at the location from where I run the that executable. So I thought I can have a bash-script to run this application from .bashrc file and this is how I got into this trouble.

So what would be your thoughts to run this application and to remove gui-desktop environment? 


Looking forward to your answer. Thanks a ton in advance.

---

### Post by TheFu on 2019-04-18
I have a few ARM devices, but not that model and none use eMMC.  I would pull the SDHC boot media, connect it to a different PC, then mount the storage and modify the file(s).  If you cannot pull the eMMC, that won't work.

On a normal x86 PC, you can switch to a different console using <ctl><alt>-F1, <ctl><alt>-F2, <ctl><alt>-F4 then login with a different account and modify files too. No idea if any ARM device supports alternate consoles.

Really you need a different userid to login under if you cannot mount the storage from some other system. Or you need to wipe the $HOME or OS and start over.  Hopefully, you have automatice, daily, versioned, backups working and it is a 15 min effort to put things back.

Nothing else is jumping out at me, but perhaps I'm missing something trivial that ARM supports from my lack of knowledge?


BTW, whenever posting questions here, we will assume an AMD/Intel CPU setup, so please say clearly that you are using ARM. They are different beasts and can't do a few of the things commonly handled by the mainstream hardware.  For example, the remote desktop tool that I use doesn't work on ARM. It has never been ported and isn't likely to ever be ported.

---

### Post by yetimon_64 on 2019-04-19
> **TheFu said:**
> ...On a normal x86 PC, you can switch to a different console using <ctl><alt>-F1, <ctl><alt>-F2, <ctl><alt>-F4 then login with a different account and modify files too. No idea if any ARM device supports alternate consoles...

The raspberry pi 3 as an ARM device definitely does with the Raspbian image I am using, I have three of them two of which I boot to a console rather than the GUI. Though after a bit of searching on Google for the Odroid, I still don't know for sure if it will support logging into a console.

It would be a good idea for the OP to try the Ctrl + Alt +F? (? being 1,2,3,4,5,or 6) from the login screen and check if a console can be accessed in my opinion. Fixing the .bashrc file in nano would be a simple task IF the odroid allows access to the linux consoles. One video I watched on setting up the Odroid gives me the feeling it may be a possibility.

---


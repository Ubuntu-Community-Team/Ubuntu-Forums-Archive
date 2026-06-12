---
title: "Login failure on new install of ubuntu-14.04.1-desktop"
date: 2015-02-21
forum: New to Ubuntu
---

### Post by Richard_Adams on 2015-02-21
I'm a newbie, and have been searching for similar issues, but haven't found any - so I'm posting here in hopes that someone may have some insight. My apologies if this isn't the correct forum. I've been trying to successfully install ubuntu on a Dell Dimension 9200 using a usb stick, which I configured with the Universal-USB-Installer-1.9.5.9.
I've worked through various issues getting the system to actually boot properly. I think most of those issues have been dealt with, however this login issue continues to plague me. I've actually had the system running, have loaded and executed software in the desktop and everything seems to be running ok. However, when I shut down the system, and reboot, I can't log in again. I can ctrl-alt-F1 into the system command mode. I can use that mode to force a reboot. I can execute recovery, etc. 

If I do execute a recovery, I can log into the guest account - and then log into a real account, but never directly into a real account.

For some reason, this just seems a bit bizarre to me - I can't imagine why I would be able to log into a guest account, and then cross into a regular account and have things run ok. After I've logged in this way I can log out - then log in without problem. But, once I cycle the system, the mess starts all over again and I can't get in unless I log into guest first - then log into a regular account.

Any ideas, help or suggestions would be most appreciated!

Thank you!

---

### Post by v3.xx on 2015-02-21
What are your specs (ram, cpu, video)?  Your model varies.
[http://support.us.dell.com/support/systemsinfo/document.aspx?~file=/systems/dim9200/en/sm_en/specs.htm](http://support.us.dell.com/support/systemsinfo/document.aspx?~file=/systems/dim9200/en/sm_en/specs.htm)

I ask because if your trying to run the Unity desktop you may not have the resources for it.

That said.  
At the login screen, is there a icon to click on?  Maybe you have switched desktop.

Also
Go back to console (CtrlAltF1) and enter:
```
startx
```
Did that take you to desktop?

LightDM is the package that takes care of login.
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by Richard_Adams on 2015-02-21
Hi,

Thank you for responding! I have 2GBRAM, 2-1.86GHz Intel 6300 CPU's and a VESA G72Board - p280h18, if that helps.

I tried the "startx" from the command prompt and .... it was interesting. I got as far as having a background image display, then nothing. When I cancelled out of that screen back to the prompt, it appeared to have hung up on "Loading extension GLX".

In order to get back to a working desktop, I rebooted, ran the "recover" option in the boot process and once again had to log in to the "guest" account before I could log into my own account.

Any ideas, comments or suggestions would be most welcome!

Thanks again!

---

### Post by v3.xx on 2015-02-21
I think I would try nomodeset.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Richard_Adams on 2015-02-22
Thank you for responding!

Ok, I followed the instructions on the link you provided and set "nomodeset" in the grub editor. 
When I booted, I was able to log in, but the screen resolution is wrong and I can no longer modify it to the correct resolution. Eg: it comes up in 1280x1024 and my physical screen won't go beyond 1024x780. So, I can't view the entire display on my monitor. Without the nomodeset, I can change the monitor resolution, but can't log in without going through the guest account first.
Maybe there's a file where I could change the terminal parameters for screen resolution?

Thanks in advance for any ideas.

---

### Post by v3.xx on 2015-02-22
Ok, one step forward :)

Check this out.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Richard_Adams on 2015-02-22
Thanks again for your response.

That didn't work. When I entered the command: xandr 
all I got was: "Can't open display", but what seems to have helped is a line in /etc/default/grub which was originally commented out:
      #GRUB_GFXMODE=600x480

I changed this line to:
       GRUB_GFXMODE=1024x768

Then I ran the command: sudo update-grub

Then, when I rebooted, the screen came up in the correct resolution.

I am not sure this is the complete resolution to the problems I've been having, but it's far enough along that at least I can be reasonably functional on the system until I can figure out some of the other stuff. I REALLY appreciate your kind response to the problem, and hopefully, I can bump along for now. I wouldn't have gotten this far without your help. So, Thank you!

Best!

Rich.

---

### Post by v3.xx on 2015-02-22
You got it working, thats what counts.

One last thought ..
You may find it useful to install an alternate desktop for testing purposes.  The "Flashback (Metacity)' desktop can be added to your current system.
```
sudo apt-get install gnome-panel
```
Desktops can be switched at the login screen by clicking on the icon.  Both desktops are gnome, but flashback uses the metacity window manager instead of compiz (Unity).  May be of some help.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


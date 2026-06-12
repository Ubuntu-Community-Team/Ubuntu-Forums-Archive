---
title: "[SOLVED] Unable to resolve screen resolution issue"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Nutbar on 2008-08-04
I've recently installed Ubuntu on my older desktop computer, and I'm having an issue that I cannot seem to resolve. Every time I logout or restart, my screen resolution defaults back to 800x600, and each time I change my settings back to 1024x768, or 1280x1024. 
I've tried various things:

[INDENT][LIST]
[*]I've enabled the nvidia drivers in the hardware panel.
[*]I've installed the nvidia-settings, and run them via "gksudo nvidia-settings".
[*]I've tried "gksudo desktop-gtk" and setting things there, but it ends up with an overly large ubuntu logo at the login screen (where I cannot see the login prompt).
[*]I've tried to edit the Monitor setting in /etc/X11/xorg.conf
[*]I installed Envy, to no avail.
[/LIST][/INDENT]

From what I can gather, each time I login, the system tries to auto detect my monitor, and sets it to a generic "Samsung SyncMaster" profile. In "gksudo desktop-gtk" I can see that a profile for my monitor exists, but when I enable it, I get the monster login screen. My monitor is a Samsung SyncMaster 997MB.

I'm lost, and I've spent too much time trying to figure this out, and I ask for your help. I'm not sure if I've gotten all the terms correct, but I hope this all makes some sense.

Thanks,

Terry

---

### Post by iaculallad on 2008-08-04
Try to post whatever outputs when your issue the command below on your terminal:

```
lspci | grep VGA
```

Also, do post the content of your /etc/X11/xorg.conf.

```
cat /etc/X11/xorg.conf
```

EDIT: Just a question: When you tried to manually change your screen resolution on your xorg.conf file, had you used:

```
gksudo gedit /etc/X11/xorg.conf
```

or

```
sudo nano /etc/X11/xorg.conf
```
?

---

### Post by jimv on 2008-08-04
Are you changing the resolution in the nvidia-settings control panel?  If you are, make sure that you click the "Save to Xorg.conf" (or something like that) button.

---

### Post by MaindotC on 2008-08-04
From experience I'm telling you you'll never have your video settings right if you don't get it right on the first install.  If you've messed around w/ the settings (like using displayconfig-gtk) you're in for a lot of posts.  I've had an issue similar to yours and I'm also using a Synchmaster and I've posted and posted and it never really goes back to normal.  I think the time you spend trying to understand and fix the problem will outweigh a fresh, clean install.  I really hate saying that because I know how bad it makes Ubuntu look, but I've just learned how to do a quick recovery in the event of a modification to the unbelievably sensitive video driver and video settings of Ubuntu.  Once I have it set properly, I leave it alone and don't mess around with it.  I'm reinstalling the 64-bit version and going to try downloading and compiling/installing the ATI driver from the ATI site with the help of a few other guys monitoring my progress on a different thread.

Again, I hate to tell you that, but I advise you learn how to create a custom install cd w/ the latest updates, an image of your perfect setup that can be quickly restored, and putting /home on a separate partition.  I really hope the others can help you fix the problem but I sincerely doubt it will end in anything other than a re-install.  Good luck to you.

---

### Post by JoshuaRL on 2008-08-04
> **strAlan said:**
> From experience I'm telling you you'll never have your video settings right if you don't get it right on the first install.  If you've messed around w/ the settings (like using displayconfig-gtk) you're in for a lot of posts.  I've had an issue similar to yours and I'm also using a Synchmaster and I've posted and posted and it never really goes back to normal.  I think the time you spend trying to understand and fix the problem will outweigh a fresh, clean install.  I really hate saying that because I know how bad it makes Ubuntu look, but I've just learned how to do a quick recovery in the event of a modification to the unbelievably sensitive video driver and video settings of Ubuntu.  Once I have it set properly, I leave it alone and don't mess around with it.  I'm reinstalling the 64-bit version and going to try downloading and compiling/installing the ATI driver from the ATI site with the help of a few other guys monitoring my progress on a different thread.

Again, I hate to tell you that, but I advise you learn how to create a custom install cd w/ the latest updates, an image of your perfect setup that can be quickly restored, and putting /home on a separate partition.  I really hope the others can help you fix the problem but I sincerely doubt it will end in anything other than a re-install.  Good luck to you.

Unfortunately I think I agree.  In the past you could change settings in xorg.conf or do a dpkg--reconfigure -phigh xserver-xorg to fix issues like this.  But Hardy ships with the new version of X11, and it is made to autodetect your hardware for the most part.  A few things still are given attention in the xorg.conf (the keyboard, mouse, and stuff like that) but for the moniter and video card especially, no dice.  So I would suggest you do one thing, then if that doesn't work, the reinstall.

```

gksu displayconfig-gtk

```
Mess with settings there, save, and reboot.  See if that helps.  If you go a few rounds and nothing, then try reinstalling.  But unfortunately, that may not work either.  I'm sorry for the bad news.

---

### Post by MaindotC on 2008-08-04
I'm sure somewhere out there, there's a guy (or girl) who lives and breathes driver writing and display configurations that has the ultimate display setup and resolves any issues and is a master of xorg.conf and could view this thread and say "all you have to do is this and this and edit this and insert this line and modify this and reboot and you're good to go" but I've yet to find him or her.  Again, nothing against Linux but in my experience (and it seems Josh's too) the video driver is just really sensitive and you need to get it right the first time and never change anything.  Especially, do not download and install the latest driver from Nvidia if everything you currently have is working properly.  Not that you've done that, but just advice for the future.

---

### Post by JoshuaRL on 2008-08-04
> **strAlan said:**
> I'm sure somewhere out there, there's a guy (or girl) who lives and breathes driver writing and display configurations that has the ultimate display setup and resolves any issues and is a master of xorg.conf and could view this thread and say "all you have to do is this and this and edit this and insert this line and modify this and reboot and you're good to go" but I've yet to find him or her.  Again, nothing against Linux but in my experience (and it seems Josh's too) the video driver is just really sensitive and you need to get it right the first time and never change anything.  Especially, do not download and install the latest driver from Nvidia if everything you currently have is working properly.  Not that you've done that, but just advice for the future.

Well, for most setups autodetect works great.  I think the issue here is the monitor, not so much the video driver.  That seems to not be the problem so much.  So what we're looking for here is either a forced config or a correct autodetect of the monitor.  Or maybe you can set it as a generic LCD monitor with the right specs and maybe it will work.

---

### Post by Nutbar on 2008-08-04
Thanks for the help!

After messing around all this time I think I've got it working. Since it was a fairly fresh install, I decided to reinstall the whole works. After the installation, I enabled the restricted nvidia driver and rebooted. I think that the last time I installed, I did not reboot before installing nvidia-settings and messing with them. I installed the nvidia-settings; however, I have made no changes with it.

As of right now, the system is set to auto resolution, which appears to default to 1280x1024 @ 85hz, for which I am very happy. I don't know if I dare try to mess with the resolution again for fear of screwing things up yet again. 

Thanks again,

Terry

---

### Post by Nutbar on 2008-08-04
I just changed my resolution to 1024x768, rebooted, and the resolution held... yay!

Thanks again =)

---

### Post by JoshuaRL on 2008-08-04
> **Nutbar said:**
> I just changed my resolution to 1024x768, rebooted, and the resolution held... yay!

Thanks again =)

Cool.  Don't forget to go to Thread Tools and Mark As Solved.

---

### Post by MaindotC on 2008-08-04
Be sure you go to System -> Preferences -> Main Menu and remove "Screens & Graphics".  Also, check out psychocats tutorials about quick system recovery like having a custom install cd w/ all of your updates and packages installed, or an image of your current installation that can be quickly restored.  It helps to know these things.

---


---
title: "Nvidia Driver 180"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by chris062689 on 2008-11-26
Does EnvyGT allow for the easy installation of Nvidia 180 driver?
Is there a repo I can use to add the drivers to the Hardware Manager?

I have a 64bit OS, so it's a real pain to install.

---

### Post by Peter09 on 2008-11-26
Any time I have used Envy it has been straight forward. Just go with the defaults.

What version of Ubuntu are you using. Hardy and Later will install 3rd Party stuff using the Hardware manager.

Look in

System->Administration->Hardware Drivers 

see if there is a driver waiting to be enabled.

---

### Post by chris062689 on 2008-11-26
I'm using 8.10
The problem is, only the nvidia 177 driver and (one of the older ones) is listed.
I didn't see anything about Nvidia 180.

---

### Post by cariboo on 2008-11-26
It is pretty easy to install the Nvidia driver. Download the driver from Nvidia.

Step 1. Completely remove any nvidia related programs using Synaptic
Step 2: Press Ctrl-Alt-F1
Step 3: Type:  
```
sudo /etc/init.d/gdm stop
```
Step 4: cd to the directory you stored the driver file in.
Step 5. sudo ./*run, answer yes to all the questions
Step 4. type
 ```
sudo /etc/init.d/gdm start
```

If you have done everything right, you  should be running the new driver.

Note: you must be running the latest kernel which currently is 2.6.27-10

I would suggest you wait until Alberto submits it to the repositories.

Jim

---

### Post by kernelhaxor on 2008-11-26
> **chris062689 said:**
> 
I didn't see anything about Nvidia 180.

I think that is because the 180 is still in beta

---

### Post by chris062689 on 2008-11-26
I remember installing nvidia drivers last time manually on a 64bit system, and it asked me something about creating the 32bit libraries or something like that.
Is that necessary? ^

---

### Post by Amorget on 2008-11-26
I always do it and have never had a problem.

---

### Post by geoffw35 on 2008-12-04
> **cariboo907 said:**
> It is pretty easy to install the Nvidia driver. Download the driver from Nvidia.

Step 1. Completely remove any nvidia related programs using Synaptic
Step 2: Press Ctrl-Alt-F1
Step 3: Type:  
```
sudo /etc/init.d/gdm stop
```
Step 4: cd to the directory you stored the driver file in.
Step 5. sudo ./*run, answer yes to all the questions
Step 4. type
 ```
sudo /etc/init.d/gdm start
```

If you have done everything right, you  should be running the new driver.

Note: you must be running the latest kernel which currently is 2.6.27-10

I would suggest you wait until Alberto submits it to the repositories.

Jim

I could use some help here. I'm fairly new to linux and haven't installed drivers yet. I need this new one due to random loss of all video described in bug report 234292. I did steps 1 up through 4 listed above. But step 5 didn't work for me. I see 2 *run files in the untarred directory:  NVIDIA-Linux-x86-180.11-pkg0.run and NVIDIA-Linux-x86_64-180.11-pkg2.run. They are not executable files. What steps am I missing here. Is it just a chmod +x on the two files before running step 5? Thanks for any help.

---

### Post by Amorget on 2008-12-04
> **geoffw35 said:**
> I could use some help here. I'm fairly new to linux and haven't installed drivers yet. I need this new one due to random loss of all video described in bug report 234292. I did steps 1 up through 4 listed above. But step 5 didn't work for me. I see 2 *run files in the untarred directory:  NVIDIA-Linux-x86-180.11-pkg0.run and NVIDIA-Linux-x86_64-180.11-pkg2.run. They are not executable files. What steps am I missing here. Is it just a chmod +x on the two files before running step 5? Thanks for any help.

Instead type:

sudo sh NVIDIA-Linux-x86_64-180.11-pkg2.run


Oh, and another trick... if you cd into the directory you have the file saved in, you can start typing, then press Tab and it will fill in the rest for you.  Since I had two version in there, I typed NVIDIA and it filled in all the way to the version, I put in 11, hit tab again and it filled in the rest.  Very handy.

---

### Post by geoffw35 on 2008-12-04
> **Amorget said:**
> Instead type:

sudo sh NVIDIA-Linux-x86_64-180.11-pkg2.run


Oh, and another trick... if you cd into the directory you have the file saved in, you can start typing, then press Tab and it will fill in the rest for you.  Since I had two version in there, I typed NVIDIA and it filled in all the way to the version, I put in 11, hit tab again and it filled in the rest.  Very handy.

Since I'm using 32 bit and not 64, I assume the other *run file is the one I want. Now it tells me that I need to exit X. I'll try to figure out how to do that. Aren't newbees fun?

---

### Post by Amorget on 2008-12-04
Ah, sorry about that!

Not a problem :)

What you need to type to exit X is the

sudo /etc/init.d/gdm stop


I should of been more clear, you need to do all the steps that you quoted, however you need to substitute the correct .run file for the *run that he listed.

---

### Post by geoffw35 on 2008-12-04
> **geoffw35 said:**
> Since I'm using 32 bit and not 64, I assume the other *run file is the one I want. Now it tells me that I need to exit X. I'll try to figure out how to do that. Aren't newbees fun?

Maybe that is what sudo /etc/init.d/gdm stop does. But when I come back up, X is restarted. So I need to find out how to boot to the console. I'll check the man page for gdm.

---

### Post by geoffw35 on 2008-12-04
The gdm man page is pretty thin. Can you help with the gdm option that prevents the X restart?

---

### Post by Paqman on 2008-12-04
> **cariboo907 said:**
> 
I would suggest you wait until Alberto submits it to the repositories.


So would I.

Installing 180 manually means your system *will* break whenever there's a new kernel in the updates.

Luckily, there's an extremely good chance that the driver will be making it into backports soon, as I believe it fixes a lot of KDE window decoration nastiness.

---

### Post by Amorget on 2008-12-04
> **geoffw35 said:**
> The gdm man page is pretty thin. Can you help with the gdm option that prevents the X restart?

You don't need to do that

Press Cntl + Alt + F1

Login

change to the directory that the NVIDIA files are in

type:

sudo /etc/init.d/gdm stop

type:
sudo sh NVIDIA-Linux-x86-180.11-pkg0.run

Follow the prompts

When done, type:

sudo /etc/init.d/gdm start

---

### Post by geoffw35 on 2008-12-04
> **Paqman said:**
> So would I.

Installing 180 manually means your system *will* break whenever there's a new kernel in the updates.

Luckily, there's an extremely good chance that the driver will be making it into backports soon, as I believe it fixes a lot of KDE window decoration nastiness.

Sounds like good advice. Thanks to both of you. I got to the point where I figured I needed to understand the gdm.conf file to do what I want to do. I sure hope you are right about the driver being available soon. This loss of my video from time to time is really annoying!

BTW, could you tell me what backport means?

---

### Post by Paqman on 2008-12-04
> **geoffw35 said:**
> 
BTW, could you tell me what backport means?

Normally the versions of software are pretty much locked for each version of Ubuntu. The updates you get are security and bugfixes only, so if a new version of a program comes out that has cool new features, well too bad. 

That's where backports comes in. New versions of important packages are put into backports so that old versions of Ubuntu don't miss out on the new features. You can enable backports through System > Admin > Software Sources.

Of course, since this driver includes large bugfixes I suppose it might go into the regular repos rather than backports.

---

### Post by geoffw35 on 2008-12-04
Thanks for the info on backports.

Amorget:
sudo /etc/init.d/gdm stop doesn't seem to work for me the way you say--most likely due to my ignorance. What happens when I enter this command is the screen goes black with no ability to type anything. So I need to press the power key which reboots and the config file restarts X.

---

### Post by Amorget on 2008-12-04
> **geoffw35 said:**
> Thanks for the info on backports.

Amorget:
sudo /etc/init.d/gdm stop doesn't seem to work for me the way you say--most likely due to my ignorance. What happens when I enter this command is the screen goes black with no ability to type anything. So I need to press the power key which reboots and the config file restarts X.

You need to press Ctrl + Alt + F1, which will take you to a terminal/command line, where you will need to login again.  You can't just open Terminal inside of GNOME :)  If you are already doing that then... that is really weird.

---

### Post by geoffw35 on 2008-12-04
> **Amorget said:**
> You need to press Ctrl + Alt + F1, which will take you to a terminal/command line, where you will need to login again.  You can't just open Terminal inside of GNOME :)  If you are already doing that then... that is really weird.

Nope, not doing that. I was talking about instructions I read on the nvidia site for installation: "Before beginning the driver installation, you should exit the X server. In addition you should set your default runlevel so you will boot to console and not start up X"

I don't know whether that means to edit the gdm.conf file or to do something else that prevents it from being used at startup.

So thank you again. I'll try it what you recommend.

---

### Post by Amorget on 2008-12-04
> **geoffw35 said:**
> Nope, not doing that. I was talking about instructions I read on the nvidia site for installation: "Before beginning the driver installation, you should exit the X server. In addition you should set your default runlevel so you will boot to console and not start up X"

I don't know whether that means to edit the gdm.conf file or to do something else that prevents it from being used at startup.

So thank you again. I'll try it what you recommend.

Follow the instructions that you quoted, you'll be must better off then the nVidia ones.

---

### Post by stefangr1 on 2008-12-04
> **Amorget said:**
> Follow the instructions that you quoted, you'll be must better off then the nVidia ones.

It means you should, when the logon screen appears, choose "console login" from the menu. You can't install the new driver from the gui.

---

### Post by geoffw35 on 2008-12-04
> **Amorget said:**
> Follow the instructions that you quoted, you'll be must better off then the nVidia ones.

I used your instructions. Sorry I missed the cntl-alt-f1 the first time through. It seemed to be successful. I'm not sure how I check, since the nvidia control gui is not under system/Administration anymore. Should it be? Maybe I missed something else.

In any case, thanks for taking the time to help me through this. In time, I hope to learn enough to be able to help others.

---

### Post by fooman on 2008-12-04
> **geoffw35 said:**
> I'm not sure how I check, since the nvidia control gui is not under system/Administration anymore. Should it be? Maybe I missed something else.


look in applications > system tools

---

### Post by geoffw35 on 2008-12-04
> **fooman said:**
> look in applications > system tools

As far as I can tell, this install worked. Now I wait to see whether the video problem where I see only garbage on the screen forcing a reboot is fixed.

Paqman: 
I figure the kernel update problem can be resolved or those who have done this manual install would not have done so. I can take an "I told you so", when the time comes. :) But this problem I'm experiencing is very serious and has been a problem for a long time, so I had to try to fix it. None of the Options recommended in #234292 worked for my M90 laptop.

---

### Post by Amorget on 2008-12-05
> **geoffw35 said:**
> As far as I can tell, this install worked. Now I wait to see whether the video problem where I see only garbage on the screen forcing a reboot is fixed.

Paqman: 
I figure the kernel update problem can be resolved or those who have done this manual install would not have done so. I can take an "I told you so", when the time comes. :) But this problem I'm experiencing is very serious and has been a problem for a long time, so I had to try to fix it. None of the Options recommended in #234292 worked for my M90 laptop.

Seriously, the kernel update is easy.  I did it today.

You just reinstall the drivers... simple as that.  Once you've done it a couple times it doesn't take more then 10 minutes.

---

### Post by geoffw35 on 2008-12-05
> **Amorget said:**
> Seriously, the kernel update is easy.  I did it today.

You just reinstall the drivers... simple as that.  Once you've done it a couple times it doesn't take more then 10 minutes.

Glad to hear it. I really appreciate you helping me learn this.

---

### Post by Cybso on 2008-12-07
Had anybody success in using 180.11 (or .06) in conjunction with Suspend to Disk (swsusp or TuxOnIce)? I [installed the driver](http://www.blogs.uni-osnabrueck.de/rotapken/2008/12/05/nvidia-intrepid-install-linux-driver-version-180/), but X crashes when resuming from disk.

I'm running 2.6.27-9-tuxonice on a Dell E6400 with nVidia NVM 160M. I've tried all the things from [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend) like NvAGP=1 (or 0), changing POST_VIDEO etc in acpi-support, and even tried some tricks that [seems to work](http://david.goodlad.ca/2008/3/14/suspend-hibernate-on-lenovo-t61) for Lenovi T61. Resuming works fine with 173 (but the performance is poor).

---

### Post by waspinator on 2009-02-05
any updates on 180 comming into backports? Also I read somewhere that Ubuntu should soon be able to install video drivers without worrying about messing up the kernel? Is that still happening?

---

### Post by cariboo on 2009-02-05
Running Intrepid, the nvidia drivers installed from the repositories get recompiled every time a new kernel gets installed.

If you manually install the drivers, you will have to reinstall them every time there is kernel upgrade.

Jim

---

### Post by iIgor on 2009-03-01
> **chris062689 said:**
> I'm using 8.10
The problem is, only the nvidia 177 driver and (one of the older ones) is listed.
I didn't see anything about Nvidia 180.

To see nvidia 180 driver in hardware drivers, install nvidia-180-modaliases.
To do this you can type in terminal sudo apt-get install nvidia-180-modaliases . Or you can use synaptic.

---

### Post by devmage on 2009-03-01
> **iIgor said:**
> To see nvidia 180 driver in hardware drivers, install nvidia-180-modaliases.
To do this you can type in terminal sudo apt-get install nvidia-180-modaliases . Or you can use synaptic.

The packages for nvidia-glx-180 and nvidia-180-kernel-source are already in Restricted.  Enable that repository through Synaptic, and you should be able to install them without issue.  The nvidia-glx-180 package will replace nvidia-glx-177 (and presumably other previous versions).

I'll post back if there *are* issues, though.  Installing now.  :P

Edit: after reboot and loading with 180.11, the NVIDIA splash screen now says "Beta Driver" in big red font underneath the nv logo.  Just a cosmetic thing, really.  The Restricted Drivers Manager will alert you to the fact that you're using a driver from Restricted, as it is supposed to do.  Finally, the nvidia-settings config tool seems to work fine, despite being versioned for 177 in the repositories.

Hope this helps!

---

### Post by ReisceakaLP on 2009-04-08
I seem to be having an issue. I activated the 180 driver and restarted my laptop. After signing in the screen goes dark. I can still hear the login music its just the display light goes out and I can't see anything.

---

### Post by nowhere@cox.net on 2009-04-09
FYI, I had to revert to the 177 driver on my Lenovo T61 laptop with nvidia discrete graphics. When I enabled the 180 driver that was pushed recently, it broke suspend to RAM. The laptop would go into suspension fine but nothing would wake it up.

This is a little different than other problems I have seen and had where the laptop would freeze after waking with black screen. In this case it would not even wake up at all (ie no backlight nothing). I had to hold the power button to force it to hard power off, then power it back on.

Reverting to 177 fixed it...

Hope this helps...

---

### Post by cylon33 on 2009-04-10
Same problem here with 180 driver... It goes to standby and never comes back. Fixed with 177 driver... 

I sure hope someone reported this bug, cuz it's a big one. :)

---

### Post by batjew_beyond on 2009-04-27
How can I switch back to 177?
I enabled 180 from the Hardware Manager, and now when I turn on my machine, It posts, and goes directly to a black screen.  I can't log in or anything.
Help much appreciated, I'm stuck on a Windows partition until someone saves me!

---

### Post by batjew_beyond on 2009-04-27
Saved myself...
I think...
Rebooted in Recovery mode.
Now it seems to be working with the 180 driver.
I'm so very very confused as to why, but I'm not gonna complain.

---

### Post by riQeh on 2009-06-21
> **Amorget said:**
> Instead type:

sudo sh NVIDIA-Linux-x86_64-180.11-pkg2.run


Oh, and another trick... if you cd into the directory you have the file saved in, you can start typing, then press Tab and it will fill in the rest for you.  Since I had two version in there, I typed NVIDIA and it filled in all the way to the version, I put in 11, hit tab again and it filled in the rest.  Very handy.

When i do this i get 
Verifying archive integrity... Error in check sums 3075395718 4155808496

ant ideas?

---


---
title: "What am I doing wrong?? NVIDIA horror!"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by AppState09 on 2008-05-11
I never imagined I would have so much trouble with this! Newbie here, so please bear with me....

I started with a fresh install of Hardy and wrote down everything I did. Basically, I enabled the NVIDIA driver through the hardware drivers manager. It prompted me to restart, which I did. It went to the GRUB menu, never made it to the login, but looped back to the GRUB menu again. Then it froze and I had to do a hard reboot, selected recovery mode, then fix X server. It got to the login screen, I logged in and the driver was in use, but not enabled (how is that even possible?!). So, I enabled it again, rebooted again, it again went to the GRUB menu twice, but this time when I got to log in, my driver was enabled and in use. However, my screen was all messed up. Text wouldn't show up until I had my pointer over it and when I tried to enable my desktop effects, I got this insane screen of what looked similar to static (blue bars and garbage). My resolution was: 1024x768 and 53hz. From that point it kept rebooting itself until finally I got to this point where once again, my driver is in use, but not enabled. 

I've tried using Envy to install the driver and it seemed to work, but when rebooting it got stuck at the NVIDIA splash screen. 

I'm not sure what I should post from terminal that would be of any use, but please tell me and I will put it up! This is just getting so frustrating!](*,)] 

Oh, my card is a GeForce 2mx. Obviously an old card; could that be the problem? I REALLY hope not! That's why I didn't want Vista!

---

### Post by MaindotC on 2008-05-11
Ok let's start with the basics - what is the name, type, model, and quantity of each piece of your hardware?

---

### Post by AppState09 on 2008-05-11
> **strAlan said:**
> Ok let's start with the basics - what is the name, type, model, and quantity of each piece of your hardware?

I'm not entirely sure. This computer was given to me by a friend of a friend. I know the graphics card is a GeForce2 MX integrated card. That probably isn't of much use. Sorry, I'm just REALLY new to all of this!

---

### Post by bumanie on 2008-05-11
With a card that old, you will probably have to go to the nvidia site and download the 'legacy driver' for linux. You then have to install it via command line in console mode. My previous machine had an mx4000 and after feisty fawn distro., that was the only way I could get my graphics card working in that machine. Post back if you need more information.

---

### Post by MaindotC on 2008-05-11
Thanks, bumanie - didn't know that.  If that doesn't work, is this a pre-built computer like a dell or gateway laptop and if so, can you find any stickers that identify the model?

---

### Post by jrusso2 on 2008-05-11
Actually Envy and the restricted driver manager is able to identify that card and install the right driver.

I have had problems running compiz with that card however starting with Gutsy.

---

### Post by AppState09 on 2008-05-11
> **bumanie said:**
> With a card that old, you will probably have to go to the nvidia site and download the 'legacy driver' for linux. You then have to install it via command line in console mode. My previous machine had an mx4000 and after feisty fawn distro., that was the only way I could get my graphics card working in that machine. Post back if you need more information.

I think I've already tried that. Someone posted this reply to a previous post of mine trying to help me out. I followed this guide and got a frozen screen again and had to start over. 

1) Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) sudo gedit /etc/modules
4.a) Add "nvidia" without quotes to the list.
4.b) Save and Exit

5) sudo gedit /etc/default/linux-restricted-modules-common
5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
-------------------------------------------------------------------------------------------------------
If you used Envy to attempt a previous nvidia install please run this command now before you go on:

sudo dpkg -P envy

-------------------------------------------------------------------------------------------------------
If you have some old Ubuntu repository attempts installed please run this command before you go on:

sudo apt-get remove --purge nvidia*

-------------------------------------------------------------------------------------------------------
If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

sudo nvidia-installer --uninstall

-------------------------------------------------------------------------------------------------------
################################################## ##################################
##................................................ ................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................ ................................##
################################################## ##################################

8.) CTRL-ALT-F1
8.a) Okay were in Command Line only now, we have a little left to do in here.
8.b)login:
8.c)Password:

9) sudo /etc/init.d/gdm stop
9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
11.a) Answer to the affirmative for all questions.
11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
11.c) If you somehow answered incorrectly on the last question in the installer then:
c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.

---

### Post by AppState09 on 2008-05-11
> **strAlan said:**
> Thanks, bumanie - didn't know that.  If that doesn't work, is this a pre-built computer like a dell or gateway laptop and if so, can you find any stickers that identify the model?

Yes, it is a Compaq Presario 6000 Series

---

### Post by onero on 2008-05-11
Be sure to uninstall the old drivers before you install the new ones; I had some trouble with that before. Every time I change my kernel I run into Nvidia driver problems ^^ It wouldn't be such a hassle if they didn't keep offering their drivers as binary blobs.

Also, if the legacy drivers are indeed what you need, they're in the repositories; look for the nvidia-glx-legacy package.

---

### Post by bumanie on 2008-05-11
Essentially the output of the post you pointed to was what I was thinking. Are you sure you downloaded the legacy driver? Nvidia have always supported debian systems well and there are a number of .run files one can download, but which one you need, depends on your card, ie, the latest driver won't work with that card.

---

### Post by AppState09 on 2008-05-11
> **onero said:**
> Be sure to uninstall the old drivers before you install the new ones; I had some trouble with that before. Every time I change my kernel I run into Nvidia driver problems ^^ It wouldn't be such a hassle if they didn't keep offering their drivers as binary blobs.

Also, if the legacy drivers are indeed what you need, they're in the repositories; look for the nvidia-glx-legacy package.

Ok; I removed the nvidia-glx and installed the nvidia-glx-legacy
  umm....now what? lol..I know, sounds nuts, but I have NO CLUE about this stuff as I'm just starting to learn.

---

### Post by AppState09 on 2008-05-11
> **bumanie said:**
> Essentially the output of the post you pointed to was what I was thinking. Are you sure you downloaded the legacy driver? Nvidia have always supported debian systems well and there are a number of .run files one can download, but which one you need, depends on your card, ie, the latest driver won't work with that card.

The driver I downloaded was here: [http://www.nvidia.com/object/linux_display_x86_96.43.05.html](http://www.nvidia.com/object/linux_display_x86_96.43.05.html)

I haven't downloaded it again since I did the fresh install of Hardy.

---

### Post by akshayas1986 on 2008-05-11
Hi everyone

Thanks a ton to Appstate09. It worked for me!!

Just being curious, any reason why we disable nv and put nvidia in modules file?

---

### Post by AppState09 on 2008-05-11
> **akshayas1986 said:**
> Hi everyone

Thanks a ton to Appstate09. It worked for me!!

Just being curious, any reason why we disable nv and put nvidia in modules file?

Oh, that wasn't me! I can't figure any of this out to save my life!! haha

That guide was posted here: [http://ubuntuforums.org/showthread.php?t=781717](http://ubuntuforums.org/showthread.php?t=781717)

It was a reply by 'starcannon' to a previous post about my NVIDIA troubles. People here are wonderful and trying to help, but I'm not having any luck at all....

---

### Post by AppState09 on 2008-05-11
Ugh...once again I cannot get into Ubuntu at all...

It is 4:40am where I am now, so I am going to sleep but I HOPE that someone can help me!!! 

This board is really great! Some others I have visited looking for solutions have been full of very mean posts including some telling people they had no business trying to use Linux! Glad it isn't like that here! ~Samantha

---

### Post by Tomatz on 2008-05-11
Just login at the cli (black screen with text) and type this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Follow the prompts

then

```
sudo shutdown -r now
```

That should at least get your gui back up and running by reconfiguring your graphics drivers.

---

### Post by MaindotC on 2008-05-20
App what's the status on this?  Are you still having issues?

---

### Post by metasolaris on 2008-05-20
> **AppState09 said:**
> I never imagined I would have so much trouble with this! Newbie here, so please bear with me....

I started with a fresh install of Hardy and wrote down everything I did. Basically, I enabled the NVIDIA driver through the hardware drivers manager. It prompted me to restart, which I did. It went to the GRUB menu, never made it to the login, but looped back to the GRUB menu again. Then it froze and I had to do a hard reboot, selected recovery mode, then fix X server. It got to the login screen, I logged in and the driver was in use, but not enabled (how is that even possible?!). So, I enabled it again, rebooted again, it again went to the GRUB menu twice, but this time when I got to log in, my driver was enabled and in use. However, my screen was all messed up. Text wouldn't show up until I had my pointer over it and when I tried to enable my desktop effects, I got this insane screen of what looked similar to static (blue bars and garbage). My resolution was: 1024x768 and 53hz. From that point it kept rebooting itself until finally I got to this point where once again, my driver is in use, but not enabled. 

I've tried using Envy to install the driver and it seemed to work, but when rebooting it got stuck at the NVIDIA splash screen. 

I'm not sure what I should post from terminal that would be of any use, but please tell me and I will put it up! This is just getting so frustrating!](*,)] 

Oh, my card is a GeForce 2mx. Obviously an old card; could that be the problem? I REALLY hope not! That's why I didn't want Vista!

Hi,

I have an old Pentium 4 1.5MHz PC with a Geforce 2 MX400 which I use as a spare computer.

I had exactly the same problem as you with the 'legacy' drivers. I could never get them to work with my old GF2 so I just use the OpenSource free drivers that come preinstalled with Hardy. 

They seem to work fine as long as I dont do anything graphically intensive. Net surfing, playing DVD's, downloaded videos from Miro are fine, streaming video is ok, games are a non starter!

meta

---

### Post by Bruegger on 2008-06-17
Hi,
You are rite mate!Getting a older gpu to work in new Ubuntu releases is a true-blue horror and a never ending ordeal.
I have a Geforce2 Integrated GPU and i am facing the same random freezing, black screens at log-in since Edgy-Eft.
I did a fresh install of Hardy Heron and then used the restricted drivers - no good, used envy to no avail.
Then installed 96.43.05 from Nvidia site. SOmetimes i can log in and then the system freezes. At other times, if i go to recovery mode and start gdm, the system boots up fine and then freezes after some time.
Using an older gpu is becoming progressively difficult with each upgrade of Ubuntu and has come to a point it's putting me off completely.
I spend half my time on Ubuntu trying to fix the driver issues so i can put the pc to use.
It seems with every Ubuntu upgrade i have to experiment endlessly to set the driver up for any use.
Have to use the drivers as thats what fixes my resolution and frequency perfectly otherwise using nv just screws up the display configs.
As an average pc user, windows handles my old gpu just fine and investing in a new set of hardware just so Ubuntu can handle it easily doesn't really sound a prudent reason to me.
Is there any fix to these driver issues with older gpu's at all?

Thx.

---


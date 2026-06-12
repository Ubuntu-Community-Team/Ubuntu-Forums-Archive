---
title: "I broke Xorg"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by CircuitFisted on 2008-09-19
Well, I believe it would be Xorg that I've broken in two. Now I've searched through the forums and I've been given the same command on each search, which is actually the thing that broke it. I can't remember the command exactly but it put me through a auto-configure that scrambled my monitor completely.

What's worse is that it told me that I had copied over my original custom settings. Now my monitor is scrambled. Completely. When I turn the laptop on, a Dell Inspiron 6000, it displays the text normally, the Ubuntu loading bar in clear vision. Then when it loads up the X GUI to log in the screen begins simply tearing apart and makes it impossible for me to see what I'm doing. Worse part is that there are files I want to save but can't due to not being able to see what's going on.

Is there a way I can restore the display settings to what they originally were? I tried booting in recovery mode, it didn't do much of anything. Nothing at all that I noticed because the display was still broken.

Now you may wonder as to why I had to throw a wrench into Xorg to begin with. Answer is I didn't. I was trying to get Xorg to refresh it self because some times it becomes unresponsive. It's done this before and I usually just saved if possible and then rebooted.

I entered the Restore Xorg (or something to that effect) and then my display went belly up. Any time I try to boot from a live distro the same thing happens to me. I tried booting Ubuntu live and Knoppix, but both did the same thing.

So again, I reiterate, can someone help me? I've been using Ubuntu for some time now, but am still some what a heavy nubcake to it and linux as a whole, but felt comfortable to be able to use the system. In fact I feel much more secure and the usual from using a better OS that seems to give my laptop another 25 minuets battery life that Windows robbed from it.

So my system specs (without complete details by a long shot) are:
Dell Inspiron 6000
1g RAM
Ubuntu 8.04 with all updates

---

### Post by philinux on 2008-09-19
Have a look in /etc/X11 for your old xorg.conf, the system may have made a backup for you which you can use.

Places>computer then browse to the above folder.

---

### Post by CircuitFisted on 2008-09-19
> **philinux said:**
> Have a look in /etc/X11 for your old xorg.conf, the system may have made a backup for you which you can use.

Places>computer then browse to the above folder.

So when I go to root terminal would I just type in /etc/X11/xorg.conf?

When I type in /etc/X11/xorg.conf it tells me that permission is denied.

When I do sudo su /etc/X11/xorg.conf it just tells me unknown id.

---

### Post by Nepherte on 2008-09-19
To open the file with a terminal based text editor:
```
sudo nano /etc/X11/xorg.conf
```

To open it with a graphical editor:
```
gksudo gedit /etc/X11/xorg.conf
```

There might be a backup of the file too. You can find out this way:
```
ls -l /etc/X11/
```
They are typically named "xorg.conf.backup or xorg.conf followed by a timestamp.

You can reconfigure the xorg configuration file in the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by CircuitFisted on 2008-09-19
> **Nepherte said:**
> To open the file with a terminal based text editor:
```
sudo nano /etc/X11/xorg.conf
```

To open it with a graphical editor:
```
gksudo gedit /etc/X11/xorg.conf
```

There might be a backup of the file too. You can find out this way:
```
ls -l /etc/X11/
```
They are typically named "xorg.conf.backup or xorg.conf followed by a timestamp.

You can reconfigure the xorg configuration file in the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

The only way I'm able to do anything currently is through GRUB. So any form of visual GUI is pretty much not going to work for me. Well, at least not from my experience.

I looked into the 

```
nano /etc/X11/xorg.conf
```

And it brought me to a page where I assume I could edit the packages and everything, but I didn't see any xorg.conf[insertnumbershere] file that I could edit to bring back to an older state.

---

### Post by gjoellee on 2008-09-19
[http://www.kshoster.net/index.php?c=tipsandtricks&h=xfix](http://www.kshoster.net/index.php?c=tipsandtricks&h=xfix) I think it will be the easiest way...:) I am not 100% sure it will work, but this is supposed to fix xorg

---

### Post by CircuitFisted on 2008-09-19
> **gjoellee said:**
> [http://www.kshoster.net/index.php?c=tipsandtricks&h=xfix](http://www.kshoster.net/index.php?c=tipsandtricks&h=xfix) I think it will be the easiest way...:) I am not 100% sure it will work, but this is supposed to fix xorg

XFIX is actually what put me in this mess. After I had ran that trying to reboot X to begin with (it seemed like a good idea at the time) it had scrambled the screen. It looks like my screen is constantly jumping up and down while shaking left to right very rapidly.

I also feel like a jerk requesting so much help and not really being able to offer anything in return. =/

---

### Post by gjoellee on 2008-09-19
> **CircuitFisted said:**
> XFIX is actually what put me in this mess. After I had ran that trying to reboot X to begin with (it seemed like a good idea at the time) it had scrambled the screen. It looks like my screen is constantly jumping up and down while shaking left to right very rapidly.

I also feel like a jerk requesting so much help and not really being able to offer anything in return. =/

because xfix doesn't work it seams like you have saved some changes in the xorg config file. You may have to reinstall ubuntu, or xorg. Or find a default xorg config file and replace it.

And by the way. We are just glad to help you :D

---

### Post by madcow72 on 2008-09-19
> 

I looked into the 

```
nano /etc/X11/xorg.conf
```

And it brought me to a page where I assume I could edit the packages and everything, but I didn't see any xorg.conf[insertnumbershere] file that I could edit to bring back to an older state.

What Nepherte said is correct.  If you're at the command line (not GRUB, that's the bootloader) and you do: ```
sudo nano /etc/X11/xorg.conf
``` then you'll be able to edit the document.  If you leave out "sudo" then you will not be able to edit the document.  That would be your problem.

Please state what your video card is, because that sounds like it's the problematic peripheral.  Regardless, however, you should be able to issue the command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and choose the correct video card driver (or just use "vesa" to be safe).  After that's done, you can restart the X-server by typing:
```
sudo /etc/init.d/gdm restart
``` (assuming you're using Ubuntu, not Kubuntu.) and you should be able to get back into X.

---

### Post by CircuitFisted on 2008-09-19
> **gjoellee said:**
> because xfix doesn't work it seams like you have saved some changes in the xorg config file. You may have to reinstall ubuntu, or xorg. Or find a default xorg config file and replace it.

And by the way. We are just glad to help you :D

Well, heck, is there a way to just install xorg? I also don't know how I'd go back to replace a previous version of the xorg settings. 

After XFIX ran the first time it said it was going to replace the previous custom version and didn't even give me the option to say no. Just kind of assumed that was what I wanted.

Any chance there's a step-by-step of rolling back to the original configuration?

---

### Post by madcow72 on 2008-09-19
> **CircuitFisted said:**
> 

Any chance there's a step-by-step of rolling back to the original configuration?

Yeah, the full-blown step-by-step is:
```
sudo dpkg-reconfigure xserver-xorg
```
The simpler version to only reconfigure your video card is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Let us know what happens when you try one of these.

---

### Post by nkri on 2008-09-19
Before you go to drastic measures, try this:
```
sudo dpkg-reconfigure xserver-xorg
```

It's the interactive way of reconfiguring X.

Good luck!
-nkri

PS: Madcow, you forgot the hyphen in that command.  It has to be
```
dpkg-reconfigure
```
 instead of
```
dpkg reconfigure
```

---

### Post by madcow72 on 2008-09-19
> 
PS: Madcow, you forgot the hyphen in that command.

Thanks nkri!  I noticed that and edited my earlier posts.  Cheers!

---

### Post by CircuitFisted on 2008-09-19
> **madcow72 said:**
> Yeah, the full-blown step-by-step is:
```
sudo dpkg-reconfigure xserver-xorg
```
The simpler version to only reconfigure your video card is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Let us know what happens when you try one of these.

I've tried both those commands as suggested before. Again, nothing happened. I tried with the swap thing on and with it off. Same keyboard setup and everything.

When I was going through those steps neither one fixed my problem. It's starting to look more and more bleak to me.

Then again I could just be borking this and ignoring some obvious path I could be taking to fix this thing all together short of formatting.

When I start the computer I hit the escape key>Ubuntu 8.04 Kernel 2.6.24-16-generic recovery mode (puts me in root user mode). From there I've been entering the commands and trying everything short of reformatting the system.

Again, that's the only way I can possibly enter commands. I can't get into Ubuntu regularly and enter the terminal in there, I have to enter root terminal mode from the get-go, so the 
```
gksudo gedit /etc/X11/xorg.conf
``` code won't even bother to run. Says it is unable to due to graphical reasons.

My videocard is also a 64 MB ATi Mobility Radeon X300 built in to the laptop's motherboard.

---

### Post by b0b138 on 2008-09-19
Boot to the live cd and copy the xorg file from the live session.

---

### Post by CircuitFisted on 2008-09-19
> **b0b138 said:**
> Boot to the live cd and copy the xorg file from the live session.

I'll try that. But last time I tried to use a live session it displayed the same faults; crazy screen and all. However if I load up another version of Linux aside from Ubuntu and Knoppix, it shows up fine.

Supposing I can't be helped, that's fine. I've been using the OS for a year and a half now and this is the first time I've encountered this. The only files I'd want saved are on my desktop and I've got a USB drive I can put the files on. 

What would the CP command look like to copy something from my desktop to the usb in the terminal?

---

### Post by bikeboy on 2008-09-19
From my quick skim of the thread I didn't see this suggested, though it may have been. The easiest way to get a usable Xorg is to start fresh.

```
cd /etc/X11/
sudo cp xorg.conf xorg.conf.broken
```

As far as I remember, you don't even have to create a blank xorg.conf, it will happen automatically upon the next restart of X or reboot. Worth a try, because if it works it's a lot easier than messing with the LiveCD etc.

---

### Post by Bucky Ball on 2008-09-19
Have you tried:

**startx**

In a terminal?

---

### Post by iansane on 2008-09-19
hmm... last time I had probs with xorg the command "sudo dpkg-reconfigure xserver-xorg" didn't have video options anymore. Had to revert to old version and lock it to be able to use that. Just throwin that in there.

---

### Post by jemate18 on 2008-09-19
> **CircuitFisted said:**
> Well, I believe it would be Xorg that I've broken in two. Now I've searched through the forums and I've been given the same command on each search, which is actually the thing that broke it. I can't remember the command exactly but it put me through a auto-configure that scrambled my monitor completely.

What's worse is that it told me that I had copied over my original custom settings. Now my monitor is scrambled. Completely. When I turn the laptop on, a Dell Inspiron 6000, it displays the text normally, the Ubuntu loading bar in clear vision. Then when it loads up the X GUI to log in the screen begins simply tearing apart and makes it impossible for me to see what I'm doing. Worse part is that there are files I want to save but can't due to not being able to see what's going on.

Is there a way I can restore the display settings to what they originally were? I tried booting in recovery mode, it didn't do much of anything. Nothing at all that I noticed because the display was still broken.

Now you may wonder as to why I had to throw a wrench into Xorg to begin with. Answer is I didn't. I was trying to get Xorg to refresh it self because some times it becomes unresponsive. It's done this before and I usually just saved if possible and then rebooted.

I entered the Restore Xorg (or something to that effect) and then my display went belly up. Any time I try to boot from a live distro the same thing happens to me. I tried booting Ubuntu live and Knoppix, but both did the same thing.

So again, I reiterate, can someone help me? I've been using Ubuntu for some time now, but am still some what a heavy nubcake to it and linux as a whole, but felt comfortable to be able to use the system. In fact I feel much more secure and the usual from using a better OS that seems to give my laptop another 25 minuets battery life that Windows robbed from it.

So my system specs (without complete details by a long shot) are:
Dell Inspiron 6000
1g RAM
Ubuntu 8.04 with all updates



to be able to have your xorg in its initial state...

type ```
sudo dexconf
```

it will create a default xorg file in your /etc/X11

---

### Post by CircuitFisted on 2008-09-20
> **jemate18 said:**
> to be able to have your xorg in its initial state...

type ```
sudo dexconf
```

it will create a default xorg file in your /etc/X11

Well, I've tried that. I've tried every option to me. Right now I've Ubuntu mounted in Safe Mode Live from my CD. Everything is displayed fine here. 

I figured while I was in here saving things to my USB stick I'd pretty much delete the 17 configurations that were created today leaving only the original files in their place.

Now I've encountered the problem of not being able to delete them because I'm  not root on the mounted drive. I can't figure out how to log in as root, either.

So, uh, now that I'm (still) grasping straws, does anyone know how to log on as root on a mounted drive..?

Sorry none of the solutions are working. Think it might not just be my day today.

---


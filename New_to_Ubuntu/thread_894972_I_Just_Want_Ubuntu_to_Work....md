---
title: "I Just Want Ubuntu to Work..."
date: 2008-08-19
forum: New to Ubuntu
---

### Post by mquest724 on 2008-08-19
Hello All,
Today is a dark day for me my friends, a dark day indeed.  I have received my Ubuntu Live CD in the mail and attempted to install it thinking that my previous woes (see my past thread) were due in some part to the disk I was using.  Unfortunately, it is completely and utterly useless.  I just want it to work and I've been patient and diligent in my attempts.  Basically my problem is this.  I am attempting to install Ubuntu on an Averatec 3200 series PC.  
The specs are as follows:  
  Mobile AMD Athalon XP-M 1.66 GHz processor
  480 MB RAM
  VIA/S3G UniChrome Graphics Card

I have tried a lot of different things and I don't know exactly what to do now. I have tried alternate boot ups changing the preferences with the F6 button and tried all the possible configurations with that and I got no where.  Is there a way to get a driver for that video card that will work with Ubuntu but somehow put it into the installation so that I will be able to install it.  Also could it be a problem with the monitor itself since my previous attempts have said things such as "Screen Failed". I don't know what kind of screen I'm using, it was installed already when I bought this computer so I don't even know if it's talking about screen as in monitor or screen as in it was processing things and something popped up it didn't like.  
I just want to know what it's like to be one of the chosen ones who can freely enjoy Ubuntu.  I want to smell the sweet air of Linux in my nose when I awake in the morning.  I want to look up to the heavens and see all the clouds lining up to say "Ubuntu Loves You" and I'll sigh to myself and respond "I love you too, Ubuntu".
Please help.

Thank you

---

### Post by brandoncolorado on 2008-08-19
Hey Mquest,

I read through most of your other post.  It is a bit lengthy though, so maybe there are some things I will repeat here.

1)  The most simple thing to try is a complete reformat of the hard drive and downloading/burning the iso on a different computer with a different type of media.

2)  If you are using windows to burn the iso, i recommend CdBurnerXP  [http://cdburnerxp.se/](http://cdburnerxp.se/)

3)  If you have another computer, try the disc to see if it is the computer or the disc.  Could your cd drive be giving you problems so that the installation isn't finishing correctly?

4)  What happened after you tried safe mode, can you copy/paste the actual error message here (I just saw you mentioned a portion of it in your last post).

Best,

Jayhawk

---

### Post by mquest724 on 2008-08-20
Ok, I have good news and I have bad news.  First the good news is I found a thread on here that had the exact same problem as me and he was able to fix it.  Very promising indeed.

The bad news is that I feel as though I am considerably less experienced than this gentleman (or gentlewoman) and I don't quite know how they got to where they are.  

The thread that was posted is located here:
[http://ubuntuforums.org/showthread.php?p=5625017#post5625017]("http://ubuntuforums.org/showthread.php?p=5625017#post5625017")

I got as far as installing with Wubi and getting to the removing "quiet" and "splash" but i didn't know where to put the word "single" and I also didn't know how to save the line like that because I went back to the menu and then went back in to see if what I had typed was still there and the changes were gone, but I don't know if that's because it just goes back to default or not.

Anywho, if anyone out there knows where to put "single" so I can get into the recovery mode thing so I can edit my xorg.conf it would be greatly appreciated.  

Though this has been a long and arduous process, I feel like I'm learning quite a bit and I want to thank everyone in advance for helping/reading/responding.  I would in no way call this process "fun" because it makes me want to set myself on fire not being able to do this stuff, but I'm sure the fun will come when I'm rocking Ubuntu.

---

### Post by BGFG on 2008-08-20
Hi,
Do you need the graphics card ? If not try the onboard connection. I'm no expert but i've seen posts where a graphics card messed up an install.

---

### Post by tangibleorange on 2008-08-20
> **mquest724 said:**
> Ok, I have good news and I have bad news.  First the good news is I found a thread on here that had the exact same problem as me and he was able to fix it.  Very promising indeed.

The bad news is that I feel as though I am considerably less experienced than this gentleman (or gentlewoman) and I don't quite know how they got to where they are.  

The thread that was posted is located here:
[http://ubuntuforums.org/showthread.php?p=5625017#post5625017]("http://ubuntuforums.org/showthread.php?p=5625017#post5625017")

I got as far as installing with Wubi and getting to the removing "quiet" and "splash" but i didn't know where to put the word "single" and I also didn't know how to save the line like that because I went back to the menu and then went back in to see if what I had typed was still there and the changes were gone, but I don't know if that's because it just goes back to default or not.

Anywho, if anyone out there knows where to put "single" so I can get into the recovery mode thing so I can edit my xorg.conf it would be greatly appreciated.  

Though this has been a long and arduous process, I feel like I'm learning quite a bit and I want to thank everyone in advance for helping/reading/responding.  I would in no way call this process "fun" because it makes me want to set myself on fire not being able to do this stuff, but I'm sure the fun will come when I'm rocking Ubuntu.

well i can certainly help you get to a recovery prompt. you say you can delete the 'quiet' and 'splash' options. that is good. where you deleted them, simply add 'single', so the old line looks similar to this:
```
/boot/vmlinuz-2.6.24-19-generic root=UUID=75421f84-559e-496d-ac4a-3fb544331416 ro quiet splash
```
and the one you just edited looks similar to this:
```
/boot/vmlinuz-2.6.24-19-generic root=UUID=75421f84-559e-496d-ac4a-3fb544331416 ro single
```
then press enter to save the changes, and then 'b' to boot. this should get you to a recovery console. you can the proceed to edit your xorg.conf. be aware that when the kernel options are not permanent when added in this way - you will need to repeat the process on each boot.

good luck.

---

### Post by Zill on 2008-08-20
mquest724:  FWIW, I always like to see if I can run the live CD *before* I try to install the system ;-)

If the live CD runs OK then the chances are that it should install OK, if not then there may be problems with the hardware.

Does your live CD seem to run correctly?

---

### Post by mquest724 on 2008-08-20
Ok, so I was able to get into the recovery mode, but when I tried to edit the xorg.conf it wouldn't work.  I don't know if I'm doing it wrong or what the deal is.  When I got to the recovery mode, I followed the instructions off the link that I posted of someone with the exact same computer as mine getting this to work.  I went to the root menu.  From there there were no instructions as to how to edit my xorg.conf, only that that person had done it and I looked up some things as to how to edit it, and at the root signal I typed in:  gksudo gedit xorg.conf

Once I typed that in I got the message:
(gksudo:7692):Gtk-WARNING **: cannot open display:

and then it brings me back to the root prompt....
I'm beginning to lose patience as I have been at this for quite some time.  If anyone knows how to get to the point where you can edit the xorg.conf it would be greatly appreciated.

Thank you in advance.

---

### Post by rossjman1 on 2008-08-20
to edit the file at the command prompt:
sudo vim xorg.conf

Vim is pretty complicated and hard to use for a new user. Check [http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html) for all of the commands available. I would print it out.

---

### Post by mquest724 on 2008-08-20
Ok, tried to do the sudo vim xorg.conf. When I did that it just brought me to an all black screen with a bunch of blue ~'s along the left edge and at the bottom of the screen it said:
"xorg.conf" [New File]

That didn't seem right to me so I figured that I would post back here again to make sure that I'm doing it right because that doesn't seem to be what the person who posted on the other thing did.  Or like I said, maybe they're just way more advanced than I am.  All I know is that the link that I posted with the person who got it to work is what I need to do and if anyone knows how to do that, it would be awesome to let me know how.  I can get to the point where I have the root prompt and I'm just trying to get over that last hurdle.

---

### Post by rossjman1 on 2008-08-21
do sudo vim /etc/X11/xorg.conf
The command I told you earlier assumes that you were in the same directory as xorg.conf, this one doesn't. Please note that this is not the solution to your initial problem, but the last post you made (the one above my first post) made it clear that you were trying to edit the xorg.conf file from the command line with gedit (which is a graphical text editor, which obviously wont work in a command line). Vim is a text only text editor, but it is complicated, please use the Vim cheat sheet that I linked to.

---

### Post by raydeen on 2008-08-21
I would recommend using Nano as your editor. It doesn't have all the bells and whistles that Vim has but is a good Notepad like editor and a bit simpler for newbs (like me).


sudo nano /etc/X11/xorg.conf

You'll be able to open the file, make the changes and then use the keyboard shortcuts listed at the bottom to save your file and exit the program. I believe it's Ctrl+o to save (file out) and then Ctrl+x to exit. I'm typing on a Mac right now so I'm not real sure. :)

---

### Post by tangibleorange on 2008-08-21
> **raydeen said:**
> I would recommend using Nano as your editor. It doesn't have all the bells and whistles that Vim has but is a good Notepad like editor and a bit simpler for newbs (like me).


sudo nano /etc/X11/xorg.conf

You'll be able to open the file, make the changes and then use the keyboard shortcuts listed at the bottom to save your file and exit the program. I believe it's Ctrl+o to save (file out) and then Ctrl+x to exit. I'm typing on a Mac right now so I'm not real sure. :)

yeah nano is far better for new users:

```
sudo nano /etc/X11/xorg/conf
```

and edit your file. to save, it's Ctrl+X, Y, and the Enter.

good luck.

---


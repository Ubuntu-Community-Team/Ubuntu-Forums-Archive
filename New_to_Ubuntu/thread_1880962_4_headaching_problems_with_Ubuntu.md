---
title: "4 headaching problems with Ubuntu"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by shadowdth on 2011-11-14
Dear Ubunters,

this is my very first time in my life Ive tried Ubuntu so naturally I have faced some to me unsolvable problems. 

I have a Dell Inspiron 17nch with 8gb Ram, I7 2g processor and a nvidia geforce 525M 2Gb video. I am running Windows 7 Pro 64bits and I have Ubuntu 11.10 installed alongside also 64 bits.

Current problems: 
1)Bluetooth not working on Ubuntu. Ive completely updated Ubuntu, after update my computer is at least visible (it wasnt before updating ubuntu), but cannot send/ receive files. On windows everyth working right.

2) Banshee music player is crashing all the time. 

3) Low battery life

4) this is the most important to me. Installed apps from app center dont start. They appear starting app and then disappear. This happend with cheese and all games Ive tested and an app used for interstellar space observation.

thank You guys!

---

### Post by MG&amp;TL on 2011-11-14
> **shadowdth said:**
> Dear Ubunters,

this is my very first time in my life Ive tried Ubuntu so naturally I have faced some to me unsolvable problems. 

I have a Dell Inspiron 17nch with 8gb Ram, I7 2g processor and a nvidia geforce 525M 2Gb video. I am running Windows 7 Pro 64bits and I have Ubuntu 11.10 installed alongside also 64 bits.

Current problems: 
1)Bluetooth not working on Ubuntu. Ive completely updated Ubuntu, after update my computer is at least visible (it wasnt before updating ubuntu), but cannot send/ receive files. On windows everyth working right.

2) Banshee music player is crashing all the time. 

3) Low battery life

4) this is the most important to me. Installed apps from app center dont start. They appear starting app and then disappear. This happend with cheese and all games Ive tested and an app used for interstellar space observation.

thank You guys!

Never say unsolvable, it usually doesn't apply. :)

bluetooth I can't help with, never used it. Somebody else might, though.

To help debug banshee, can you open a terminal and run:

```
banshee
``` in it.

Then put the output here in CODE tags.

Low battery life is something the linux kernel team are working on, I think it should be fixed soon. (correct me, please, something I read second-hand off an RSS)

installed apps...can you pick one, then post that particular one here, so we can give you commands to debug.

Sorry you've had a rough time, normally users would not have these problems (apart from maybe the battery life).

You have installed the driver for your card? Search for 'drivers' in the Unity bar and click on 'additional drivers', then follow the GUI, and reboot.

---

### Post by chenr1 on 2011-11-14
So bluetoooth does work on windows 7 right?what program are u using bt with?

---

### Post by shadowdth on 2011-11-15
none of the my installed apps from app center are working

apps ive tried are:Celestia, Cheese. All fail to load up. They start loading and disappear.

As for the BT am using inbuilt app on win7 and it works perfectly.
Same with Ubuntu, but its not working. 

I am starting to look for motivation and inspiration cuz first i fell in love with ubuntu now I can feel a divorce. Ubuntu caused my fans spin pretty much always also on Windows, it s asking me to do things manually things which windows can do automatically. For example they told me to check a log file on a some kind of an error. How would i find that log file. Windows gives an option to check the log file everytime pretty much automatically. Ubuntu is beautiful, i luw the sheer design but it fails in unforgivable things which users should not encounter. Every step is soo frustrating. I feel no respect from developers for new users.

As if they said: yea we finished it yea it s a bit clunky but suit yourself. 

But i havent given up. Help me guys with apps and bluetooth please. Even if idecide to quit Ubuntu i could tell to myself that i figured the errors and overcame them with a help of community which gives a little + to this non user friendly energy absorbing but beautiful OS.

---

### Post by Chronon on 2011-11-15
The message that tells you to check the log file should also tell you where it is located.  Probably this is what we need to do first, since it may hold clues as to why applications aren't running correctly.  Once we have addressed that issue we can move on to configuring bluetooth.

---

### Post by dniMretsaM on 2011-11-15
What do you get when you run the command MG&TL gave you? As for the apps that are crashing, post the output (in CODE tags) of these commands:
```
cheese
```
```
celestia
```

Note that I'm just guessing at these commands from the application names as I've never used either. If you get [FONT=Courier New]command not found[/FONT] as the output, that's my bad.

> **MG&TL said:**
> Low battery life is something the linux kernel team are working on, I think it should be fixed soon. (correct me, please, something I read second-hand off an RSS)

As far as I know that has been fixed in version 3.1 of the kernel, but Ubuntu hasn't pushed it yet (shouldn't be too long, though).

---

### Post by MG&amp;TL on 2011-11-16
^^ about kernel, just got latest, battery life much improved.

---

### Post by shadowdth on 2011-11-16
ok this is what the terminal gave me:

typed in celestia

outcome:Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Xlib: extension "GLX" missing on display ":0"

GdkGLext-WARNING **: Window system doesnt support OpenGL 

the first GTk error goes with Firefox as well but its working so I think errors below the Gtk error causes Celestia and Cheese to close. Same error displayed on an attempt to launch Cheese.

---

### Post by thatguruguy on 2011-11-16
Do you have the proprietary drivers installed for your video card?

...wait... do you have nVidia Optimus on your notebook?

You may want to look [here]("http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/") and [here]("http://ubuntuforums.org/showthread.php?t=1871226").

---

### Post by thatguruguy on 2011-11-16
With regards to bluetooth, what steps have you taken to get it set up?

I can walk you through a few things, if I know your starting point.

Also, you might want to install Rhythmbox if you're having trouble with Banshee.  Rhythmbox will replace Banshee as the default media player in Ubuntu 12.04.

---

### Post by shadowdth on 2011-11-17
all i did was installed ubuntu and updated which steps should i take next to fix these problems?

By the way I noticed that probably when I ve installed Ubuntu alongside win 7 pro both windows and ubuntu have increased cooling. Even if am only using word documents fans spinning hearably almost all the time. 

Is it normal?

---

### Post by MG&amp;TL on 2011-11-17
Generally, when you install ubuntu, it will work perfectly out of the box. However, some hardware will require tweaking.

So, as mentioned beforehand, can you follow the links thatguruguy gave , look in 'additional drivers' for drivers, then come back here for any question you might have.

Unfortunately, ubuntu is free, and to keep it that way, we can't afford to employ too many people, nor can we pay hardware manufacturers to integrate with ubuntu, as windows can. I suspect the increased cooling is part of the kernel bug descibed, although I can't be certain.

---


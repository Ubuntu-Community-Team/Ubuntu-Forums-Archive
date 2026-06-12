---
title: "Completely new linux user, I just want to do basic things like install drivers-"
date: 2019-07-28
forum: New to Ubuntu
---

### Post by no-win10 on 2019-07-28
So I am completely new to linux. I got sick of microsoft and wanted to learn something new. So here I am.
To start of I just want to do some basic things like install some AMD motherboard chipset and video card drivers and probably steam.

I tried to find some tutorials or instruction online but they all kind of sucked. They basically told you too do it as apose to "how" to do it.

So it seems to me that in order to do anything in linux you have to open up a command line menu of some sort? And then manually input the necessary commands to run and install the program you want?

I just need some kind of jump start here.

Thanks

---

### Post by Autodave on 2019-07-28
Most things just work now in Linux: rarely do you have to install any drivers.  Cutting edge drives, tablets, keyboards, etc may need help installing, but generally everything will install themselves when you install the Linux operating system.

Is there something that you are having problems with?  Something not working properly?

Please give us the specs on your equipment and what version of 'buntu that you installed.

---

### Post by CatKiller on 2019-07-28
As already noted by Autodave, installing drivers isn't something that one generally needs to do. Linux is very different to Windows.

> **no-win10 said:**
> So it seems to me that in order to do anything in linux you have to open up a command line menu of some sort?

This is a common misconception. It is not true.

What *is* true is that the Internet in general, and this forum in particular, is text-based. It is way, way, *way* easier to communicate instructions as text in this text-based medium. Text-based commands which give text output, which can also be simply copied-and-pasted into this text-based medium, is *significantly* more helpful than, "I clicked on a wobbly purple icon and it didn't work."

Discovering and using the OS in general is going to be exactly the same sort of menus and clicking on stuff that you're already used to. Getting help with stuff, especially here, is going to be predominately text-based.

---

### Post by no-win10 on 2019-07-28
I would like to install steam on my pc. I did an internet search and the info I found said that I could find steam in the ubuntu software center.
I searched for it but could not find it.

Also I would like to install the latest AMD drivers for my graphics card.
Also do I need the mother board chipset drivers?

---

### Post by Autodave on 2019-07-28
AMD drivers: should already be installed unless you need the pro driver.  Unless you have need of that driver for something special, there is no advantage to installing it.  Your gaming should be the same with or without it.

Motherboard chip set drivers?  Again, should either already be installed or you don't need anything special.

Steam installer is in the software center.  Search for "steam" and then scroll down to the bottom of the list.  If it does not appear, you may need to make sure that all updates have been installed.  In a terminal, type: sudo apt-get update.  It will then ask for your user password.  type it in and then hit the ENTER key.  PLEASE NOTE: you will NOT see the password getting entered onto the screen, but it is.

We would still like to know the specs on your machine: that may tell us if you need to do anything else right now.  And we really need to know what version of Ubuntu you are running!

---

### Post by CatKiller on 2019-07-28
In reverse order:

> **no-win10 said:**
> Also do I need the mother board chipset drivers?

No.

> Also I would like to install the latest AMD drivers for my graphics card.

There essentially *aren't* any AMD graphics drivers in the sense that you're thinking of. The functionality of your graphics card is handled through the kernel (for the hardware side) and Mesa (for the software side). Are you having a particular problem?

> I would like to install steam on my pc. I did an internet search and the  info I found said that I could find steam in the ubuntu software  center.
I searched for it but could not find it. 

I've never used the Ubuntu Software Centre. ```
sudo apt install steam
``` should install Steam.

---

### Post by no-win10 on 2019-07-28
My spec are:

AMD Ryzen 1500x
Aorus x470 ultra gaming motherboard
Gigabyte RX570 4g video card

---

### Post by no-win10 on 2019-07-28
> **CatKiller said:**
> In reverse order:



No.



There essentially *aren't* any AMD graphics drivers in the sense that you're thinking of. The functionality of your graphics card is handled through the kernel (for the hardware side) and Mesa (for the software side). Are you having a particular problem?



I've never used the Ubuntu Software Centre. ```
sudo apt install steam
``` should install Steam.

sudo apt install steam dose nothing. It says could not locate package steam.

What is mesa and were can I get it?

I am not having any particular problems. I am just used to windows needing all of those hardware specific drivers to function at peak performance.

---

### Post by CatKiller on 2019-07-28
> **no-win10 said:**
> sudo apt install steam dose nothing. It says could not locate package steam.

See? Instantly much more information than either your initial post ("I couldn't find it in Software Centre") or your description of the problem now ("it does nothing"). The error message shows that, for you, the **multiverse** repository (software that can't be freely distributed) isn't yet enabled; that's where the steam package resides. You can use the Software Sources screen to enable that. Then you'll need to refresh the list of available packages either from that screen or by using ```
sudo apt update
```

> What is mesa and were can I get it?

You already have it. It translates graphics calls from applications into graphics calls to the hardware. You can [read about it on Wikipedia](https://en.wikipedia.org/wiki/Mesa_(computer_graphics)) if you're interested, but it's not necessary to know much about it.

> I am not having any particular problems. I am just used to windows needing all of those hardware specific drivers to function at peak performance.

Newly supported hardware or specific new features are the only reason to get newer versions. Security fixes are already backported to earlier versions. Having to use the newest version of stuff for best performance isn't a general rule for Linux like it might be for Windows, and all the hardware side of things is just part of the OS and its frameworks.

---

### Post by no-win10 on 2019-07-28
Fantastic thank you. I enabled the multiverse software repository. I found steam in the list. How ever I am met with another error.
"unable to install steam installer" the following packages have unmet dependencies. 

So I am assuming there is another piece of software I need to run steam?

---

### Post by CatKiller on 2019-07-28
> **no-win10 said:**
> Fantastic thank you. I enabled the multiverse software repository. I found steam in the list. How ever I am met with another error.
"unable to install steam installer" the following packages have unmet dependencies. 

So I am assuming there is another piece of software I need to run steam?

That is one of the reasons why I've never used the Software Centre - it's been simplified so much that it's not terribly helpful.

Since you needed to enable the multiverse repository manually, I suspect that you'll also need to enable multiarch manually; it lets you run, for example, 32-bit applications on a 64-bit OS.

```
sudo dpkg --add-architecture i386
```

should do that. Then ```
sudo apt update
```

If that isn't sufficient, post back the output when you try installing steam with apt, and we'll see if we can help.

---

### Post by no-win10 on 2019-07-28
That work flawlessly. But now I have a new problem. When I go to install a game it tells me there is insufficient disk space. This also happens in the Good old game galaxy application. How ever in the good old game application the file path for the download is a windows file path, C: program files x86 ect. . .  So is this an issue of the game was not written to be installed in a linux environment and it is still trying to operate as if it is in windows?

Any fixes for this?

And just fyi I have a 2 terrabyte firecuda hard drive installed. I have no idea how ubuntu partitions things during the install, could it be related to the insufficient disk space?

EDIT: I just did some searching. I opened the disk usage analyser and saw that there are two partitions one labelled ubuntu, 1.2 gb available, 8.4 total. And another labelled 2.0 TB volume, 2.0 available.
 I tried to create a new folder in the 2.0tb volume but it told me that it was read only. 

How do I changeit so I can create a new folder?

EDIT: So I found the properties menu for the 2.0 partition. I tried to change the permissions but it told me I am not the owner so I could not. The owner is root. So how do I become root?

---

### Post by CatKiller on 2019-07-28
> **no-win10 said:**
> That work flawlessly. But now I have a new problem. When I go to install a game it tells me there is insufficient disk space. This also happens in the Good old game galaxy application. How ever in the good old game application the file path for the download is a windows file path, C: program files x86 ect. . .  So is this an issue of the game was not written to be installed in a linux environment and it is still trying to operate as if it is in windows?

Any fixes for this?

And just fyi I have a 2 terrabyte firecuda hard drive installed. I have no idea how ubuntu partitions things during the install, could it be related to the insufficient disk space?

There is no native version of GOG Galaxy: you're running it in Wine, which makes a pretend C: drive in your Home directory. I have no idea how well, or otherwise, GOG Galaxy works in Wine, since I've never used it. I only install the Linux-native games from GOG.

Steam installs games into your Home directory.

Unless you specifically changed things during your Ubuntu install, your Home directory will be part of your / partition, and your external drive would not be used at all.

Your drive space/partitioning question should go in a different thread, with as much information as you can provide, so that someone able to help with that specific thing can help you with it, and so that someone with the same kind of problem will be able to find the solution that you hit upon.

---

### Post by Autodave on 2019-07-29
For the third time, will you please tell us what version of Ubuntu you installed?

---

### Post by oldrocker99 on 2019-07-30
Did you type this?```
sudo apt install steam installer
```

No packages have spaces in the name; it would, if needed (and it isn't) be steam**-**installer.

You should only type this:```
sudo apt install steam
```
This will also install all the dependencies that are needed for steam to run, automagically.

---

### Post by Autodave on 2019-07-30
He has never said what version that he is running.....I am hoping it isn't something like 14.04 or worse.......

---


---
title: "Sirius Radio player help wanted"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by M Baker on 2008-07-19
Hi I'm struggling to get Sirius Internet Radio to play on my Ubuntu 8.04. I've tried the existing threads and installed gxine and some kind of python thing along with sipie. I think that sipie has gotten installed but I don't understand how to run it. I believe that it has to be run through a terminal although there was some mentions of a GUI. I followed the install instructions for that too but cannot find it on my machine. As a new user, I am not adept at locating downloaded and newly installed files.

Here are the instructions that I don't understand:

QUOTE:
"To run just copy sipie somewhere in your path 
cd TheDirectoryYouDownloadedTo
sudo chmod a+x sipie
sudo cp sipie /usr/bin

Then Run it, and it will ask for your username, password 
and if your a subscriber or a guest."[/I][/I]"
END QUOTE


In reference to the above, what does "copy sipie somewhere in your path" mean? 

What does "cd TheDirectoryYouDownloadedTo" mean exactly?

Apparently I'm to "copy" "sipie" into a "path". I thought that sipie was an application.

What does it mean to copy "sipie"? And how can I identify the directory that it was downloaded into?

How exactly do I "run it" (meaning run sipie)?

Thanks for any help.

AMD 64
Ubuntu 8.04
Flash installed
Java installed
Pandora Internet Radio works
National Weather Service animated radar works

---

### Post by cariboo on 2008-07-19
> In reference to the above, what does "copy sipie somewhere in your path" mean?

When you download a file where does it end up? most people seem to download files to there desktop

> What does "cd TheDirectoryYouDownloadedTo" mean exactly?

cd stands for change directory. so in a terminal:

```
cd /directoryyoudownloadedthefile to
```

if it is on your desktop:

```
cd /home/<user>/Desktop
```

where <user> is your username

> sudo chmod a+x sipie
sudo cp sipie /usr/bin

Once you are in the directory that you downloaded the file to you have to make it executable:

```
sudo chmod a+x sipie
```

then copy it to /usr/bin

```
sudo cp sipie /usr/bin
```

to run sipie, in a terminal

```
./sipie
```

If you see a command you don't under stand in a terminal type:

```
man <command>
eg: man cp
```

Jim

---

### Post by M Baker on 2008-07-21
Hey thanks cariboo907. I'll give that a good try. It's a little embarrassing to say this but thumbing through my new book "Ubuntu Linux Toolbox", I happened upon a section that mentioned that "directories" are called "folders" in the graphical interface. It was a revelation. A small one OK, but there you have it. Plus I've found that my AMD 64 is not fully supported in some instances. It's little things like that that are bogging me down.

I'm starting to wonder if Ubuntu is the best Linux starting place for me. I'm running it as a Wubi install in XP right now. I looked on newegg and found I can get a second hard drive and another gig of ram for not too much. I'm thinking to dual boot with two hard drives so I'm not so nervous about experimenting. I've already installed a lot of extra Linux stuff that I don't know much about. The command line is intimidating for me right now, but the GUI tools are starting to feel like a crutch (one that I can't always find in the dark).

Now I'm thinking about starting with Debian and accepting the learning curve and possible re-installs. I prefer the look and feel of Ubuntu over XP but I want my regular system to "just work". Ubuntu is close but not right there yet. Flash, and Java all took a while to figure out. And figuring out how to play Pandora Internet Radio is a high priority for me as far a my main system is concerned.

For now, XP will be my main system. I like Macs - I have Xubuntu on my old 266 iMac (yow!). But a new Mac is too expensive and I can't upgrade the hardware. So maybe now Linux will be my hobby. It's very interesting and entertaining and I'm learning a lot more about computers in general.

Any thoughts on learning from Debian? And thanks a lot for your response. I'm going to give it a whack before setting up the dual-boot, two hard drive system.

---

### Post by obtel29 on 2008-11-16
Got it to work!!!!

If you are using Firefox on 8.10 I got sirius radio to work and believe you can too.

add the new plugin "Amazing Media Browser"

login to sirus player and make your selection. open the "Amazing Media Browser" and double click the media link.... give it a second or 10 and it WORKS!!!

Remember to leave the sirius player page open. You can still browse from another tab.

---

### Post by squid68 on 2008-12-17
I am still using Gusty and running Firefox 2.0.0.18. I installed gxine to get the Sirius Internet Radio to play. Installed the gxine file and the plugin and they work fine. Just have to deal with the are you listening confirmation every 90 minutes.  

Sirius used to work with Sirius Internet Radio Plugin for Firefox but Sirius did some kind of update a year ago and it stopped working, so I had to go with the gxine to make it work. That works fine. But Sipie with Gui is better.

I was using Sipie with gui to play Sirius when I was with 7.04 and when I upgraded to Gusty I had to modify an .egg file which finally got it to work again.  But several weeks ago Sipie stopped working and I do not know what is wrong or how to fix it.

Does anyone know how to wipe out sipie and reinstall it. I need detailed instructions as I am still new with this and do not completely understand the file system. Please help get sipie running again. Thanks.

---


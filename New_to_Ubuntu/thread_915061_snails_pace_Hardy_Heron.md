---
title: "snails pace Hardy Heron"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by dennycraig on 2008-09-09
I am running Ubuntu 8.04 -the Hardy Heron and have been loving it. But now it has slowed down to a snails pace. I am not sure what to do. If this was a Microsoft system I would be defragging it by now. But I do not get the sense that this is done with linex. So how does one clean up their system so it will run faster. I do have a virus scanner (ClamTk) and have run that a few times. Yet I'm not sure if it ever gets updated. Whenever I try to update it myself it says I must do that in root. And I have not figures out to root update the virus scanner. 

I'm not sure where to start here could someone please point me in the right direction out of snails hollow? 

Thanks

---

### Post by philinux on 2008-09-09
Open a terminal from the accessories menu and use the command 

```
top
```

See if anything is hogging your cpu etc.

---

### Post by bobnutfield on 2008-09-09
If you are not connected to a netwrok serving files to a Windows computer, there is really no need to have CLAMAV on your computer.  

What are your system specs? Processor?  Memory?  Graphics?

---

### Post by vikram on 2008-09-09
In the command line type "top" to view the processes which are hogging system resources. You may be running multiple processes which you may not require.

what are your system specs ? if you have an older system try XFCE instead of GNOME or KDE

fyi you shouldnt have to defrag linux systems.

---

### Post by billgoldberg on 2008-09-09
> **dennycraig said:**
> I am running Ubuntu 8.04 -the Hardy Heron and have been loving it. But now it has slowed down to a snails pace. I am not sure what to do. If this was a Microsoft system I would be defragging it by now. But I do not get the sense that this is done with linex. So how does one clean up their system so it will run faster. I do have a virus scanner (ClamTk) and have run that a few times. Yet I'm not sure if it ever gets updated. Whenever I try to update it myself it says I must do that in root. And I have not figures out to root update the virus scanner. 

I'm not sure where to start here could someone please point me in the right direction out of snails hollow? 

Thanks

Dump the Anti-Virus scanner.

Post outcome of "top"

And give us your computer specs while you are at it.

--

Did you do something special before it slowed down (upgrade to new kernel?).

--

It seems you do not really have an idea of how Ubuntu works. You should do some reading on the internet about how Ubuntu works. Start here:

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

### Post by dennycraig on 2008-09-10
The only thing I have been doing is downloading torrents. 

I attached a screenshot of terminal after I put in "top"

As to the information on my computer you want: it is only about a year old and I have not had any problems so far with it and Hardy Heron. I think it is a 64. Do I have to look inside my computer to find out the type of info you want? Or can I get that sort of info by looking in systems or something? 

Sorry about not having that information ready at hand. I do not generally get asked for it. 

Thanks for your help:)

---

### Post by hyper_ch on 2008-09-10
(1) install htop
```

sudo apt-get htop

```

(2) run htop

(3) press F6 to order the display, select with the arrow keys "MEM%" and press enter

(4) make a screenshot and post it

---

### Post by dennycraig on 2008-09-10
> **hyper_ch said:**
> (1) install htop
```

sudo apt-get htop

```

(2) run htop

(3) press F6 to order the display, select with the arrow keys "MEM%" and press enter

(4) make a screenshot and post it
when I tried to do sudo apt-get htop I got as a responce: "E: Invalid operation htop"

---

### Post by GepettoBR on 2008-09-10
> **dennycraig said:**
> when I tried to do sudo apt-get htop I got as a responce: "E: Invalid operation htop"

the command is ```
sudo apt-get install htop
```

And btw, adding "sudo" before a command is how you run something "as root".

---

### Post by dennycraig on 2008-09-10
Thanks. so far so good. Here is what I done so far:

gene@gene-desktop:~$ sudo apt-get install htop
[sudo] password for gene:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/52.2kB of archives.
After this operation, 197kB of additional disk space will be used.
Selecting previously deselected package htop.
(Reading database ... 271018 files and directories currently installed.)
Unpacking htop (from .../htop_0.6.6+svn20070915-1_amd64.deb) ...
Setting up htop (0.6.6+svn20070915-1) ...

---

### Post by neurostu on 2008-09-10
Next time your system starts slowing down open htop and take a screen shot, then post that screen shot!

---

### Post by dennycraig on 2008-09-10
I entered htop on the command line and attached is a screen shot of what came up..

---

### Post by dennycraig on 2008-09-10
here is another shotattached.

---

### Post by hyper_ch on 2008-09-11
hmmm, seems totem and ktorrent use a lot of cpu.

---

### Post by dennycraig on 2008-09-11
Things are still slow even when i turn off ktorrent. I can try downloading fewer torrents though if that would help. 

I am not quite sure what totem is or what it does or how to turn it off or on if tht is an option.

---

### Post by GepettoBR on 2008-09-11
Totem appears in the menus as "Movie Player".

---

### Post by dennycraig on 2008-09-11
OH Thanks. Why would totem be taking up cpu space if I have no movies running? And how would I keep it from doing so?

---

### Post by hyper_ch on 2008-09-11
maybe it crashed... just kill it

---

### Post by dennycraig on 2008-09-11
I turned on thw movie player and then clicked quit on it. But I still see totem playing on my htop. I did notice that when it mentions totem on htop it says "totem-video-indexer". Does it have some sort of indexing program which runs when the movie player is off? How else would I "Kill it"?

---

### Post by GepettoBR on 2008-09-11
just type ```
pkill totem-video-indexer
``` in a terminal. If that doesn't do it, try simply "pkill totem". You should also make sure that it isn't starting up automatically when you log in. In GNOME, you'd control that through System>Preferences>sessions, but it looks like you run KDE from the screenshots. Sorry, but I don't know where the KDE menus are hidden ;) Certainly someone else here will tell you.

---

### Post by dennycraig on 2008-09-11
I tried your suggestions withough any effect with the totem video indexer. NOt sure what to do next of how to get into KDE.

---

### Post by skymera on 2008-09-11
```
 killall <process name> 
```

Should sucessfully kill any pesky processes.

That is an epic amount of RAM used. 650MB~ RAM and 400MB Swap?? That's not far off my mums Vista to be honest, a few hundred MB maybe.

Find what apps are using a LOT of memory by using htop and sorting.

---

### Post by dennycraig on 2008-09-11
sofar my kill comands have had no effect on the "totem-video-indexer" "totem" operation it still shows up on the htop. I'm scratching my head here.

---

### Post by barney385 on 2008-09-11
Open htop, and determine the exact process name for totem.

open terminal: killall *process name*

Done

---

### Post by neurostu on 2008-09-12
What you need to do is get the *** PID *** or the Process ID, this can be found by looking at htop or with:

```

ps -A | grep totem

```

Then use:
```

sudo kill -9 <pid>

```
This will kill the process. It isn't as nice to the process as killall is, this one forces the process to close.

---

### Post by Antlers on 2008-12-03
Hi I am having the same problem.  MY CPU is running almost constantly at 100% (dual core, both constantly at or near 100%).  I looked at systems monitor, top, and htop, and totem-video-ind is running at 100% any given second.  If I kill totem-video-ind, this helps, but it starts again (I assume because I have transmission running).  
If I am downloading torrents I need totem-video-ind right?  I'm assuming I do.
I also noticed  a post: totem-video-indexer, 100% cpu usage, 3 load...
November 5th 2007, where the same thing was happening. They seemed to think it was a bug...
I am running an HP pc, 4gs of ram, Intel Core 2Duo Processor E6320 
Help, thankyou.

---

### Post by GepettoBR on 2008-12-04
you don't actually need anything related to totem unless you're playing  a video *with totem* (if you use VLC or MPlayer for example, you also don't need these processes). Try reinstalling totem, that might help.

---

### Post by Rizzen Virnn on 2008-12-23
Hi,

I have the same problem.
I don't know when it's started but I just notice that. I was doing some tests with thunderbird and lighting.
Totem isn't my preferred application for multimedia (which is VLC) so I don't understand why totem shows up :confused:

thanks

---

### Post by CraigPaleo on 2009-01-01
> **dennycraig said:**
> sofar my kill comands have had no effect on the "totem-video-indexer" "totem" operation it still shows up on the htop. I'm scratching my head here.

Try the graphical way. Go to System, Administration, System Monintor. 
Click "processes" Then right click on the processes you want to kill and choose "Kill process."

---


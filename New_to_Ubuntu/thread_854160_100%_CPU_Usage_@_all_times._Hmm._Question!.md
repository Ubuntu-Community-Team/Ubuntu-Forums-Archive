---
title: "100% CPU Usage @ all times. Hmm. Question!"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Phjil on 2008-07-09
Hello again forum.

Many months ago you kindly helped me set up my dual booting desktop, and it all works just fine, although I do have an interesting issue.

From startup, my CPU, according to System Monitor, is constantly running at 100%, sometimes it might dip to... 95%, but even with no apps running other than System Monitor, the CPU is clocking away like it's being thrashed with video or a massive TIFF file!

Any thoughts?

My machine isn't that new ( AMD 1500+, with 2GB Ram, brand new and formatted HD with no partitions (WinXP boots from a totally separate hard disk). I've got all bells and whistles turned off, so no desktop FX running. Memory runs at a fairly consistent 42% usage. Swap History is... 1.4%.

I'm stumped!

Cheers
Phjil

---

### Post by Cypher on 2008-07-09
From the command line type "top" to see what process is consuming all the CPU power. Tell us the process name and we can help further..

---

### Post by Tatty on 2008-07-09
Try running ```
top
``` or use the system monitor in System->Administration->System monitor, and click the CPU tab to order the processes according to cpu useage.

Have a look at what seems to be taking up the resources.

---

### Post by Phjil on 2008-07-09
OK. It seems that XORG (whatever that may be!) is using a lot of CPU time (58%) followed by Firefox - another 38% - then gnome-system-mo and gnome-panel and gnome-system.

Metacity? What's that?

After that there's some other things using 1-3%.

---

### Post by AndyCooll on 2008-07-09
> **Phjil said:**
> OK. It seems that XORG (whatever that may be!) is using a lot of CPU time (58%) followed by Firefox - another 38% - then gnome-system-mo and gnome-panel and gnome-system.

Metacity? What's that?

After that there's some other things using 1-3%.
Essentially Xorg and metacity are the apps which handle and render your desktop gui environment.

:cool:

---

### Post by Tatty on 2008-07-09
Thats really odd, Xorg should obviously not be running that high.

Is there anything you did before this started happening?  Or has it been like this ever since install?

Also, what graphics card do you have, and what drivers are you using for it?

---

### Post by Phjil on 2008-07-09
Okay... perhaps it's time I got a new computer, eh? I thought this thing was running a little slow, and I guess that if most of the cpu run-time is being used to making it just run, then anything I try and do... whoooh!

It's like, when I spin the wheel on my mouse, it thinks about it for a second, and then scrolls the window down.

Sloooooowly.

---

### Post by Phjil on 2008-07-09
> **Tatty said:**
> Thats really odd, Xorg should obviously not be running that high.

Is there anything you did before this started happening?  Or has it been like this ever since install?

Also, what graphics card do you have, and what drivers are you using for it?

It's been like that since the day I installed it, but the whole computer seems much slower since I upgraded to the 8.04 distribution.

Not sure what the graphics card is - I got this machine as a part payment for fixing a windows box! Where will I find something like... device manager (sorry to use windows terms!)

Phjil

---

### Post by Tatty on 2008-07-09
```
lshw -C display
``` should tell you your graphics card.

lshw is the command to list hardware, and -C display will give you just the graphics card.

Alternatively lspci will list all pci cards in your machine.

---

### Post by Phjil on 2008-07-09
root@phil-desktop:~# lshw -C display
  *-display
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: driver=prosavage_smbus latency=32 maxlatency=255 mingnt=4 module=i2c_prosavage
root@phil-desktop:~

Hows that? Does this help you?

---

### Post by Tatty on 2008-07-09
I was half hoping you had a Nvidia card, because then it may have just been an issue of the incorrect drivers being used.

But VIA drivers should come out the box and work fine i believe.

I feel fairly certain that you problem is fixable, but i dont really know what to try next.  Hopefully someone more knowledgeable/with better ideas could come along and help.

Your comp isnt that old... I really hope you can sort this problem.

---

### Post by jamesrfla on 2008-07-09
I have a old AMD Athlon XP processor and it seems like the CPU usage is up all the time. Not to 100% but like 40%. I am doing a clean install of Ubuntu  and that might help me.

---

### Post by Darkchef on 2008-07-09
> **jamesrfla said:**
> I have a old AMD Athlon XP processor and it seems like the CPU usage is up all the time. Not to 100% but like 40%. I am doing a clean install of Ubuntu  and that might help me.

You should try to use a lighter version of ubuntu such as xubuntu and see if that has an impact on your cpu usage. My brothers PC also has this problem, with xp and ubuntu which is quite weird.

---

### Post by philinux on 2008-07-09
Dont worry it's a known bug in system monitor.

Shrink the window horizontally and you'll find xorg settles down.

It only happens on the processes tab visual display.

---

### Post by jamesrfla on 2008-07-09
> **Darkchef said:**
> You should try to use a lighter version of ubuntu such as xubuntu and see if that has an impact on your cpu usage. My brothers PC also has this problem, with xp and ubuntu which is quite weird.
It is a AMD Athlon XP preccesor. I don't have a dual boot just Ubuntu on one hard drive

---

### Post by Phjil on 2008-07-09
Interesting you say that... I just switched back into system monitor, and the cpu was down to about 40%, but as soon as I started to shrink the window... bang back up to 100%!

And it's still there.

Funnies.

---

### Post by philinux on 2008-07-09
> **Phjil said:**
> Interesting you say that... I just switched back into system monitor, and the cpu was down to about 40%, but as soon as I started to shrink the window... bang back up to 100%!

And it's still there.

Funnies.

I've got mine shrunk to about half the screen width and cpu's idle at 6%. As soon as you do anything cpu scaling will kick in and use the cpu's to full advantage. But should settle back again.

Post a screen shot of

top

---

### Post by Phjil on 2008-07-09
> **philinux said:**
> I've got mine shrunk to about half the screen width and cpu's idle at 6%. As soon as you do anything cpu scaling will kick in and use the cpu's to full advantage. But should settle back again.

Post a screen shot of

top

Can do... here the system has been idle for about 3 mins.
As you can see... memory's OK, but CPU is running like crazy!

---

### Post by philinux on 2008-07-09
Close system monitor and run the command

top

in a terminal post the output

---

### Post by Phjil on 2008-07-09
I couldn't copy, so I snapshotted.

Looking at this... all seems pretty normal. Shall I just ignore what System Monitor says? Perhaps drawing all those lines in real(ish) time just hammers the video card and the CPU?

It seems a little pathetic, but this ain't no sumer computer!

---

### Post by philinux on 2008-07-09
Yes use system monitor for the info other than resources and use top instead

---

### Post by Phjil on 2008-07-09
Thanks for that Phil (one Phil to another!)

I'm a total Linux virgin, but learning all these commands to use in terminal really is something that I've got to get a handle on, but I never thought that something so simple like a command line could be such a powerful tool for diagnosis of problems and installing software from repositories that aren't in the usual Ubuntu Add/Remove - like Gnome-do (I'm a fan of app launchers and keyboard shortcuts!)

Many thanks for all your help chaps. I guess this old war-horse get to live for another day - all it really does is internet and the occasional use as the office digital radio / CD player / MP3 player through some big speakers.

Cheers.
See you all the next time i've got a problem, but as I learn, maybe I'll be able to help someone else with something - as long as it's realting to System Monitor playing funny with readings!

Phjil

---


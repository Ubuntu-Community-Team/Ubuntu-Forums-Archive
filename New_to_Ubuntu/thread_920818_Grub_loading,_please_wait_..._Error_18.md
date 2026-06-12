---
title: "Grub loading, please wait ... Error 18"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by dESAI on 2008-09-15
Greetings good people,

I'm really impressed with Ubuntu. But I've had a lot of problems. And after after installing it, or attempting to install it over 20 times. I finally succeeded and had a system which I would consider a pretty good replacement for the more common one which I have to use now.

This morning I booted up and got this:

Grub loading, please wait ... 
Error 18

The error just had to come on the first boot after I downloaded system back up software.... but before I had a chance to use it! :P

I think the only think I changed was an Icon label in folder "Computer". I was there customizing the icons of my external HD's, and applied a read only label to the the system disk. Now I thought it was just a label, but could this some how have caused the Error? 

Yes, still a noob, but making progress. I just wish it'd work for longer than a week. It's quite distressing... 

Do I need to reinstall, again?

Thanks guys!

---

### Post by kansasnoob on 2008-09-15
I have never seen an error 18 so I had to look:

> 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

Sounds rather odd:confused: I mean you have a 500GB drive!

Can you give us more information on the machine?

If you're able to run the live CD can you post the output of:

```
sudo fdisk -l
```

Is this a dual boot?

Are you installed to the internal drive or the external drive?

---

### Post by k33bz on 2008-09-15
I've seen it before, on my desktop. I had to re-install. BUt i think there was another option for me, might take me a minute to find it in all my post.

---

### Post by bobnutfield on 2008-09-15
Check your BIOS and see if you have an option called "IDE Translation".  If you do, disable it.

---

### Post by caljohnsmith on 2008-09-15
Since you have such a large HDD and got that Grub error 18, you might want to consider making a really small partition near the beginning of your HDD dedicated to Grub. That might be enough to prevent any problems with Grub's system files (menu.lst, stage2, etc) from being out of reach due to a BIOS limitation, which could be your problem. 

First though, if you want to back up your files, you could boot your Live CD and most likely can still mount your Ubuntu partition. Just go to the Places menu and pull up Gnome's file browser, Nautilus. That way you can save important files before going further. 

If you want to give a dedicated Grub partition a shot, let me know and I can give you specifics of how to do it. Also if you need help accessing your Ubuntu partition, let me know.

And one last thought: do you have a HDD diagnostics CD that came with your HDD? I would definitely check your HDD in case it is having problems. If you don't have a diagnostics CD, you could try the [Ultimate Boot CD]("http://www.ultimatebootcd.com/"), as it has lots of good HDD diagnostics tests you can run.

---

### Post by k33bz on 2008-09-15
do you have any other errors or just that one?

---

### Post by dESAI on 2008-09-16
> **k33bz said:**
> do you have any other errors or just that one?

Just the one, until this everything was going great :)

---

### Post by dESAI on 2008-09-16
> **kansasnoob said:**
> I have never seen an error 18 so I had to look:



Sounds rather odd:confused: I mean you have a 500GB drive!

Can you give us more information on the machine?

If you're able to run the live CD can you post the output of:

```
sudo fdisk -l
```

Is this a dual boot?

Are you installed to the internal drive or the external drive?

more information on the machine:
Pentium 4 3.0GHz x2, 2.0Gb DDR2, Geforce 6 256Mb (AGP), 1x 180Gb HD (Ubuntu 8.04 - I love it!), 1x 500Gb HD (win), 1x 500Gb external HD.

When I installed Ubuntu I disconnected all other HD's and did a new install. Then I reconnected the Win HD and everything was cool. 

There was one thing... because I didn't have the Win HD connected it did not give me any OS options during booting. So someone on this forum kindly helped by providing the code to add the menu. 2 boots later I got this problem.

---

### Post by dESAI on 2008-09-16
> **caljohnsmith said:**
> Since you have such a large HDD and got that Grub error 18, you might want to consider making a really small partition near the beginning of your HDD dedicated to Grub. That might be enough to prevent any problems with Grub's system files (menu.lst, stage2, etc) from being out of reach due to a BIOS limitation, which could be your problem. 

First though, if you want to back up your files, you could boot your Live CD and most likely can still mount your Ubuntu partition. Just go to the Places menu and pull up Gnome's file browser, Nautilus. That way you can save important files before going further. 

If you want to give a dedicated Grub partition a shot, let me know and I can give you specifics of how to do it. Also if you need help accessing your Ubuntu partition, let me know.

And one last thought: do you have a HDD diagnostics CD that came with your HDD? I would definitely check your HDD in case it is having problems. If you don't have a diagnostics CD, you could try the [Ultimate Boot CD]("http://www.ultimatebootcd.com/"), as it has lots of good HDD diagnostics tests you can run.

Thanks for the tip :) I'll try the live CD and see if I can do anything.

Cheers!

---

### Post by dESAI on 2008-09-16
> **kansasnoob said:**
> I have never seen an error 18 so I had to look:



Sounds rather odd:confused: I mean you have a 500GB drive!

Can you give us more information on the machine?

If you're able to run the live CD can you post the output of:

```
sudo fdisk -l
```

Is this a dual boot?

Are you installed to the internal drive or the external drive?

It's installed on a 180gb internal :)

---


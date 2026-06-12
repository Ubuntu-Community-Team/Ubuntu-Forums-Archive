---
title: "[SOLVED] Stuck with upgrade reboot destroyed my linux?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Betziana on 2008-08-12
Well, since no one answered anymore I went and did windows and restarted the machine. Whops, my linux has lost my graphic card, home partition and all my settings. it cannot find home, it lets me log in root as my home, but the screen stays orange/light brown. 

Neither of the top or bottom bars appear. 

See more info about this in thread Upgrading Ubuntu by me.

---

### Post by skymera on 2008-08-12
You restarted during an upgrade?

Why?

---

### Post by Betziana on 2008-08-12
As I said earlier, for more info see my earlier thread. Nobody answered anymore and I knew it was a bad idea, but I tried if windows trick would work but instead it seems I destroyed the whole thing. 

This is the error message it gives me when logging in to Ubuntu: 

"Your home directory is listed as:'/home/zorbet' but it does not appear to exist. Do you want to log in with the /(root) as your home directory? It is unlikely anything will work unless you use a failsafe session." Then choises yes and no. yes -> orange screen. no -> stay in log in screen.

---

### Post by alzie on 2008-08-12
It appears the upgrade hung with only 3 minutes to go.

Original thread: [http://ubuntuforums.org/showthread.php?t=887888](http://ubuntuforums.org/showthread.php?t=887888)

Unfortunately I don't know if there is any way to recover your lost files.  It looks like you'll have to reinstall Ubuntu.

---

### Post by LowSky on 2008-08-12
[here the link to your last thread ]("http://ubuntuforums.org/showthread.php?t=887888")
People did try to help but you cant expect mircles from us?

Now what are the specs of the computer? In other words What kind of Processor, how much RAM, Size of the hard drive, What graphics card, Who makes it, What Model?
we might be able to save your /home directory
if you have an old Live CD and a flash drive

---

### Post by Betziana on 2008-08-12
yeah... did I destroy my home partition? 

F*ck, I hate all kinds of upgrades and updates, they bring only trouble! :'< 

And at that 3 minutes, it was stuck for over an hour, so I'm not just impatient.

---

### Post by LowSky on 2008-08-12
we might be able to save your /home directory
if you have an old Live CD and a flash drive

---

### Post by Betziana on 2008-08-12
What is a flash drive?

My boyfriend has the cd for installing ubuntu, originally he installed it. Man, this is the third time I have to install it.. 1) Get it on PC in the first place. 2) I had to reinstall windows -> grub bootloader broken -> any tips on the forum didn't work even tried by my bf, -> install Linux again. 3) This.. 

I must be the most unluckiest computerloving-person in the world with computers.

---

### Post by Betziana on 2008-08-12
Yeah, people did try to help me and I appreciate it but then they suddenly didn't say anything anymore and one of them told me to return on the forums if it didn't go away by itself in 10 minutes I thought maybe he meant new thread.. 

I've got 2gb RAM (kingston, for hard core playing or other tough use of computer), CPU Athlon dual core something, graphic card Nvidia 8600GTS. Mother board MSI K9VGM-V. I think that was the most important out of my machine. Hard drive I believe is normal memory, I think it was 120gb. Don't remember the brand. 

However my computer is one year and 3 months or so old and my bro picked up the components to it, RAM and graphic card have been updated later due to hardware damage and original ones not working properly.

---

### Post by Betziana on 2008-08-12
I ran a recovery mode on my linux as well. It gave a lot of fail, but it seems to me that the ultimate stop to everything is the same and single file.. The one listed last in my attachment. en_AU.UTF-8

The recovery mode got stuck there too. Maybe there's something wrong with that file? :S 

(However I'm off to bed for today.)

---

### Post by pirate_tux on 2008-08-12
> **Betziana said:**
> I ran a recovery mode on my linux as well. It gave a lot of fail, but it seems to me that the ultimate stop to everything is the same and single file.. The one listed last in my attachment. en_AU.UTF-8

The recovery mode got stuck there too. Maybe there's something wrong with that file? :S 

(However I'm off to bed for today.)

As far as I can see it seems you have very little knowledge about computers.

I think the better aproach for you is this:
Take some time (may be one or two months) and learn as much as you can about computers and the operating systems you want to use.

Google is your friend and you can obtain all information you need (and much more) on the web.

Then you will see you no longer need much help. :)

---

### Post by Betziana on 2008-08-13
Okay well thread over, I reinstalled Ubuntu. The newest version, no need for any upgrade anymore(for now). 

Thank you for help anyway!

Yeah I know I don't know much about computers and I admit I'm a total idiot with Linux, true true. But this is the absolute beginner forum, right? ;) 

I guess I try to learn more.

---

### Post by P235 on 2008-08-16
Hello, before you become comfortable with your shiny, new Ubuntu installation I suggest you read a little about partitioning from Psychocats site:  [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

You may want to install Ubuntu again with a separate '/home' and '/' partition to make future upgrades more convenient.

---


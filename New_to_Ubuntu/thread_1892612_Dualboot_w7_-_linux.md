---
title: "Dualboot w7 - linux"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by travolter on 2011-12-08
Hey,

Beware: noob talking. ^^

Now I've had the idea of dualbooting my 1gb ram pc with linxu (probs ubuntu) and w7 with the idea of having more ram when I use linux since it uses less ram leaving me with more ram then w7 would. Now I was wondering a couple things:

1. Does having both linux and w7 on my pc influence performance in any way? I mean is my reasoning correct of having more ram left?

2. How does it work with 2 screens?


3. Is it possible to install this dualboot when I have w7 preinstalled? In other words, can I just keep everything I already have on my pc.

4. Is it possible to install this dualboot without a disk drive?

5. Can I, after making the partition, just remove the linux partition when I want to and just merge them back together (and also the other way around).

6. When I was thinking about the whole partition thing I was wondering if I could just use an external hdd to run linux on. Is this possible and does it work just as smooth? 

7. Following up on 3. : I have used a flash drive before for booting ubunt. Now is there a difference between booting from a flash drive and an external hdd?

8. Are there any things I should be fully aware of?


I hope this isn't too much (or too stupid).

grtzz

---

### Post by Basher101 on 2011-12-08
> 1. Does having both linux and w7 on my pc influence performance in any way? I mean is my reasoning correct of having more ram left?
yes in general Ubuntu uses less RAM by default.
> 2. How does it work with 2 screens? no experience on Dualscreen, but it is possible.
> 3. Is it possible to install this dualboot when I have w7 preinstalled? In other words, can I just keep everything I already have on my pc. yes
> 4. Is it possible to install this dualboot without a disk drive? yes via USB
> 5. Can I, after making the partition, just remove the linux partition when I want to and just merge them back together (and also the other way around). not quite sure what you want to tell us with this...but deleting ubuntu is easy, you will need however a windows 7 installation disc or repair disc for afterwards to repair your MBR.
> 6. When I was thinking about the whole partition thing I was wondering if I could just use an external hdd to run linux on. Is this possible and does it work just as smooth? It runs a tad slower since in a USB there is nothing mechanical thats moving...otherwise 0 difference.
> 7. Following up on 3. : I have used a flash drive before for booting ubunt. Now is there a difference between booting from a flash drive and an external hdd? yes, the HDD has more space 8D
> 8. Are there any things I should be fully aware of? you should manually partition your drive before installing, i was rushing it and let the automatic installer take care of it without thinking it through...i ended up wiping windows..


p.s. everyone was noob at some point...keep asking questions as you will get answers and learn your way to ubuntu step by step. Don't rush it..

---

### Post by cortman on 2011-12-08
> **travolter said:**
> Hey,

Beware: noob talking. ^^

Now I've had the idea of dualbooting my 1gb ram pc with linxu (probs ubuntu) and w7 with the idea of having more ram when I use linux since it uses less ram leaving me with more ram then w7 would. Now I was wondering a couple things:

1. Does having both linux and w7 on my pc influence performance in any way? I mean is my reasoning correct of having more ram left?

2. How does it work with 2 screens?


3. Is it possible to install this dualboot when I have w7 preinstalled? In other words, can I just keep everything I already have on my pc.

4. Is it possible to install this dualboot without a disk drive?

5. Can I, after making the partition, just remove the linux partition when I want to and just merge them back together (and also the other way around).

6. When I was thinking about the whole partition thing I was wondering if I could just use an external hdd to run linux on. Is this possible and does it work just as smooth? 

7. Following up on 3. : I have used a flash drive before for booting ubunt. Now is there a difference between booting from a flash drive and an external hdd?

8. Are there any things I should be fully aware of?


I hope this isn't too much (or too stupid).

grtzz


Welcome to the forum, and to Ubuntu/Linux in general!

1. Only the OS currently running uses RAM. RAM erases when you shut down, so you would have the full 1 GB or however much you have no matter what OS you run.
Dual booting won't affect performance at all. I've been dual booting Win7 and Ubuntu for about half a year.

2. It works great. I've used two monitors off and on with my laptop and always worked fine, plug and play.

3. Yes, quite possible. You may have to shrink your Windows partition down a bit to make room for Ubuntu, assuming you have a good bit of empty space on it.

4. ??

5. You can very easily remove Linux and extend the Windows partition if you so desire. Use a Win7 boot CD or Ubuntu Live CD to remove the partition, and then you should be able to extend it in Windows itself.

6. Should be quite possible.

7. I don't believe so.

8. Sounds like you're doing the research well before you dive into it! Wise move. I'd suggest trying Ubuntu out on the live CD if you want to get a taste before doing any partitioning, but what you're describing doing sounds quite safe and workable. Enjoy Ubuntu and feel free to post ANY questions you have here!

---

### Post by travolter on 2011-12-08
Thanks for the answers. 

I think I am going to try running it from external hdd first. Does this look like what I need to follow? 

[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/]("http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/")

And how can I use that guide (if it's the one I need) without having a cd/dvd?

---

### Post by BC59 on 2011-12-08
> **travolter said:**
> Thanks for the answers. 

I think I am going to try running it from external hdd first. Does this look like what I need to follow? 

[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/]("http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/")

And how can I use that guide (if it's the one I need) without having a cd/dvd?

I think the better way to start, is installing Ubuntu on Windows like all the other programs. The advantage is that you don't have to partition your disk and after some time, when you feel ok with Ubuntu you can uninstall Ubuntu from Windows add-remove programs and try the Dual Boot. This type of installation is possible through a Windows program called Wubi.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by d2redneck on 2011-12-08
I am relativly new to linux as well but, I have learned alot from installing linux.  I think that putting ubuntu on you windows box via WUBI is about the best way to start because if you screw it up you just delete the file from windows and reinstall it with nothing happening to your windows box.  another way to do it is to start up a VM (Virtual Machine) again for the same reason if you screw it up you delete it and reinstal and another advantage with the vm route is that you can create a backup of that vm so if you must reinstall the vm all you have to do is to copy and paste the backup to the vm and you go from where you didn't have anything screwed up and it is all ready to go within a couple of minutes.  all of you that have been doing this please correct me if I am wrong by the way.  One thing that might be an issue when using the WUBI route is that because it is a file in your windows system (a.k.a. program file) you are suseptable to viruses through linux on your windows box.  I am trying to find a way to move the wubi installation over to a partition on this laptop at the moment so I can save what data I have done with Ubuntu to it's own drive.  So take it as you will and I would listen to what these other people have said before you listen to me but, if they agree with me there ya go two ways to do it without risking your system as much.  please correct me if I am wrong.  that is the best way to learn something.

---

### Post by x C0MMAND0 x on 2011-12-08
+1 Wubi.That is how I got started.  It works great, and allows you to really check things out without actually installing/repartitioning because everything is done from within Windows.

---

### Post by BC59 on 2011-12-08
@d2redneck

> One thing that might be an issue when using the WUBI route is that because it is a file in your windows system (a.k.a. program file) you are suseptable to viruses through linux on your windows box.

No there is no problem, because Ubuntu is not converted to a Windows program, but the whole installation is working totally out of Windows, like on a virtual machine. 

>  I am trying to find a way to move the wubi installation over to a partition on this laptop at the moment so I can save what data I have done with Ubuntu to it's own drive.

The way is called Remastersys. Is a Linux application creating a bootable DVD with the custom system you created.

---

### Post by H3110 on 2011-12-08
> 1. Does having both linux and w7 on my pc influence performance in any way? I mean is my reasoning correct of having more ram left?

Yes, Windows tend's to be the **** part of that performance, but seriously no.

> 2. How does it work with 2 screens?

I have Ubuntu 11.10 installed on my laptop and i could duel-screen split the desktop by plugging a monitor into it. So this is fine.

> 3. Is it possible to install this dualboot when I have w7 preinstalled? In other words, can I just keep everything I already have on my pc.

I would suggest to try it using wubi as suggested by everyone else. But this is how I see it.

a) Are you going to play any games? (if Yes) then Stick with windows since Wine is the only way of supporting games.

b) If however your answer is NO, then i'd go straight up and install Ubuntu Desktop overriding windows, obviously taking necessary back-ups of your work, place into zip folders and place on flash drives or an external hdd.

You will find, like all Operating Systems they have their "own little ways" but other than your navigation being on the left, no need for any anti-virus software. the only thing you may want to do is run a command to enable your firewall (ufw) unless you want to play with iptables (which is more advanced but better).

> 6. When I was thinking about the whole partition thing I was wondering if I could just use an external hdd to run linux on. Is this possible and does it work just as smooth? 

Why would you want to do this? I don't think you will dislike Ubuntu, considering it's faster than w7, nicer than w7, and funilly enough, simpler than w7. I would just install it after you've tried it on wubi.

> 8. Are there any things I should be fully aware of?

1. I have installed Ubuntu fully on my laptop the other day, (although I am a Linux person MySQL), and never have i regreted it. Using windows at work (compulsory) I know how poor, irritating and stupid it is.

2. I'd suggest you enable your firewall (terminal, sudo ufw enable) to restrict any attempt of attackers accessing your system.

3. Don't expect it to be like windows, because it's not. It's simply, better. But it's not like a completely new thing. You can also download and install Google Chrome.


Finally, no question is too stupid, we all learn from asking questions and others experiences.

---

### Post by travolter on 2011-12-08
I am familiar with ubuntu. I've run it before from a flash drive.
The reason I want it now is because I need some extra ram and this seemed the easiest way. Using a virtual way to run ubuntu doens't really fill in that need of extra ram. 

But I don't think I want to make a partition either. I am now trying to get it running on an external hdd without having a cd/dvd drive :).

Edit:

I've been looking around and I can't really seem to find it. The things I do find require me to use a cd and unplug my internal hdd (which I do not know to do nor do I want to risk damaging something by doing that). Anyone who can help?

---

### Post by Basher101 on 2011-12-08
> **travolter said:**
> I am familiar with ubuntu. I've run it before from a flash drive.
The reason I want it now is because I need some extra ram and this seemed the easiest way. Using a virtual way to run ubuntu doens't really fill in that need of extra ram. 

But I don't think I want to make a partition either. I am now trying to get it running on an external hdd without having a cd/dvd drive :).

Edit:

I've been looking around and I can't really seem to find it. The things I do find require me to use a cd and unplug my internal hdd (which I do not know to do nor do I want to risk damaging something by doing that). Anyone who can help?

thats the noob way so you do not end up installing ubuntu on your internal HDD. Considering you have

a) two USB ports 

and

b) can tell the difference between /dev/sd**[COLOR="Red"]a[/COLOR]** and /dev/sd**[COLOR="red"]b[/COLOR]** 

you can install it on your external HDD while your internal HDD is still inside your computer. You will need two ports so you can plug your external HDD  into one, and into the other goes your Live USB which is the replacement for the Live CD. If you are familiar with Ubuntu you should be able to follow the installer and install on /dev/sdb (or /dev/sd**[COLOR="red"]c[/COLOR]**, depending if the USB stick you boot from is coming before your external HDD). Just look at the total sizes of the storage devices and you can hardly mess up...good luck

---

### Post by travolter on 2011-12-08
Thanks for the info. 

One last question:

I have tried running from an usb again (in fact I am atm) and it works. Now I was wondering if there's a big difference in performance running from usb (I used the universal installer) compared to installing on an external hdd?

---

### Post by cortman on 2011-12-08
If the external drive is USB as well, there shouldn't be.

---


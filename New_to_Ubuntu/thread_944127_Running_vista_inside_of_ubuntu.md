---
title: "Running vista inside of ubuntu"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by LeftNut on 2008-10-11
Hi guys I have just recently started using Ubuntu 8.04 hardy. my comp specs are intel duo 1.9mhz processor 3gb of ram and 2x250gb hd. I have vista installed on one harddrive and ubuntu on the other. what i'm trying to accomplish is load ubuntu and have one of my desktops be windows either vista or xp. as of right now I only have 1 pc 1 partion has vista other drive as ubuntu partion and about 125gb of shared ntfs space for bit torrent dl's,music, and files that i can access on either boot. as of right now i dont have a vista install disk or xp but i will be buying a xp disc soon. so if i could run my current vista partion that would be idle because i could dedicate 2gb of ram for windows and 1gb of ram for ubuntu. any expert linux help would be greatly appreciated like a link to a guide and software needed or any help to accomplish my goals :KS my main goal is to run ubuntu for everything and be able to swap over and play my online games in a windows screen without having to reboot and wait which is what i'm doing now and it sux.

Thank you,
Gary

---

### Post by eternalnewbee on 2008-10-11
I'm not sure if that's possible, although you could try to play your games using "wine" or "cedega"

---

### Post by keplerspeed on 2008-10-11
Gary,

You can use virtualbox, which comes in 2 versions. the OSE edition (open source) doesnt support usb. However if you get virtualbox from [www.virtualbox.org](www.virtualbox.org) it will have usb support. Then using a win ISO you can install win on a 'virtual' harddisk. If you need more help with this, and you can find a tutorial, ask here, ive installed and used virtualbox numberous times.

Cheers.

---

### Post by LeftNut on 2008-10-11
> **eternalnewbee said:**
> I'm not sure if that's possible, although you could try to play your games using "wine" or "cedega"

i have wine but you cant play cod4 online with it because of punkbuster.

@2 poster 

I have virtual box 1.5.6 at the moment from the repository i think. i forget were i got it. if you could link me to a guide and possibly some were i could get an iso of xp so i dont have to order one online. dont really feel like dropping 80-100 bucks just for a virtual box. 

Thanks alot for the feed back.
Gary

---

### Post by keplerspeed on 2008-10-11
hmmm a win ISO for free...... well thats why we use linux right, its fast, free and fun! [http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/) good tut.

I luckily enough had an xp cd, but to remain legal you will have to buy a win cd or live with linux!

---

### Post by LeftNut on 2008-10-11
> **keplerspeed said:**
> hmmm a win ISO for free...... well thats why we use linux right, its fast, free and fun! [http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/) good tut.

I luckily enough had an xp cd, but to remain legal you will have to buy a win cd or live with linux!

lol i just wish my comp came with a windows cd instead of just a backup cd. i'll probably just break down and grab a xp cd off of ebay. also on your virtual setup does it lag? i'm willing to dedicate a lot of ram and cpu usage to it so i dont lag while i play online.

Thank you,
Gary

---

### Post by keplerspeed on 2008-10-11
I have only a gig of ram and an AMD 64 running 64 bit ubuntu ibex. My CPU is pretty busy when virtualbox is running bit its still great, only a slight performance drop.

---

### Post by Keen101 on 2008-10-11
***This was discussed once on the Colorado LoCo team mailing list awhile back. Here is basically the question and answer:***

[CoLoCo] VM full screen on a separate desktop
				
	
	
This question would usually be directed toward me or David, but hope springs eternal that someone has done this.

Is it possible to reserve one desktop for a virtual machine, then run
that virtual machine full screen.  Then, by simply going to that desktop
(desktop 4 for example) I can keep a Windows instance running?

I know I have worked on Sun machines this way, but can not ever recall
Linux configured like this.

To be clear as to what I am asking about...

desktop 1-3 = Linux
desktop 4 = Windows

by changing desktops (i.e. ctrl-alt-arrow) I move from desktop to
desktop.  But desktop 4 is full screen windows full time.

Thx
--
Kevin Fries
Senior Linux Engineer
Computer and Communications Technology, Inc
A Division of Japan Communications Inc.

--
Ubuntu-us-co mailing list
[email]Ubuntu-us-co@lists.ubuntu.com[/email]
Modify settings or unsubscribe at: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-us-co](https://lists.ubuntu.com/mailman/listinfo/ubuntu-us-co)
 

Reply

	
Brandan E. Lloyd
 to Ubuntu
	
show details Jul 22
	
	
Reply
	
	
Kevin,

I have done this with VirtualBox.  I go full screen then press the Host Key (Right Ctrl by default) then Ctrl+Alt+Arrow and I'm off to other desktops.

Brandan

---

### Post by mlentink on 2008-10-11
I like to add a word of caution here, just so as to avoid dissappointment. No VM-software that I know of (VirtualBox or VMWare) support 3D-acceleration. You will therefore be severely limited in the number and type of games you would be able to play within a virtual machine. 
The virtual machine gives you a very plain, run-of-the-mill type of graphics adapter without fancy doodahs.

So yes, you can run XP or even Vista in a virtual machine in e.g. workspace 4 (which is what I have at the moment), but sorry, no graphics intensive games....

---

### Post by scooop08 on 2008-10-11
Instead of install a new windows xp can you run the one your dual booting with in virtual box

---

### Post by LeftNut on 2008-10-11
> **scooop08 said:**
> Instead of install a new windows xp can you run the one your dual booting with in virtual box

How would this be done??

---

### Post by inxygnuu on 2008-10-11
I am not sure why you would want to install X-treme Problem (XP):lolflag: but you could just create a new partition for XP, but the switching without restarting thing sounds awesome, but I am afraid even I have never seen something like that:(.

---

### Post by inxygnuu on 2008-10-11
UPDATE::) I found something called EasyBCD 1.7.2 by Neosmart technologies that has something in which you can quickly reboot into another OS. It is called iReboot. Hope it helps, but I have never used it because my only other OS is Intrepid, which is wildly corrupted.:(

---

### Post by LeftNut on 2008-10-11
> **inxygnuu said:**
> UPDATE::) I found something called EasyBCD 1.7.2 by Neosmart technologies that has something in which you can quickly reboot into another OS. It is called iReboot. Hope it helps, but I have never used it because my only other OS is Intrepid, which is wildly corrupted.:(

didnt really work for me

thanks anyway,
gary

---

### Post by smooth3006 on 2008-10-11
> **keplerspeed said:**
> Gary,

You can use virtualbox, which comes in 2 versions. the OSE edition (open source) doesnt support usb. However if you get virtualbox from [www.virtualbox.org](www.virtualbox.org) it will have usb support. Then using a win ISO you can install win on a 'virtual' harddisk. If you need more help with this, and you can find a tutorial, ask here, ive installed and used virtualbox numberous times.

Cheers.

i don't mean to hijack this thread but if i could install xp or vista in a virtualbox running inside ubuntu. then i could install microsoft activesync on virtual xp / vista and still be able to sync my phone ? this may be a brilliant solution for me if possible ?

---

### Post by inxygnuu on 2008-10-12
> **smooth3006 said:**
> i don't mean to hijack this thread but if i could install xp or vista in a virtualbox running inside ubuntu. then i could install microsoft activesync on virtual xp / vista and still be able to sync my phone ? this may be a brilliant solution for me if possible ?

yes, probably, if you had the hardware connected. it should work.:)

---


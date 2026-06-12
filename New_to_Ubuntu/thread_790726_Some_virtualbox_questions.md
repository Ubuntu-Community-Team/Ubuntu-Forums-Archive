---
title: "Some virtualbox questions"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by seuzy13 on 2008-05-11
I am looking into virtualbox, because I've been having some issues with wine. However, the newest Windows CD I have is 98. I have two computers now though that are running Windows XP and have a restore partition.

I would really prefer to get Windows XP running in virtualbox if at all possible, but I don't think it is without an install CD. In my dual-boot laptop's Windows restore partition, I found the file "BootDisc.iso" This looks promising, but I have read that restore CDs do not work in virtualbox.

Any input or thoughts? Thank you!

---

### Post by SuperSon!c on 2008-05-11
worst it'll do is not fully boot in a VM scenario.  try it out.

---

### Post by HotShotDJ on 2008-05-11
> **seuzy13 said:**
> I found the file "BootDisc.iso" This looks promising, but I have read that restore CDs do not work in virtualbox.

Keep in mind, unless you've purchased a retail box, your Windows XP licenses are only for the computers that they came on.  If you've deleted the original Windows, installed Linux, and now wish to install the copy of Windows XP that came with that very same computer in VirtualBox, then you may do it (I don't know if you CAN do it without the original CD/DVD ... but that is another issue altogether).  Otherwise, you are violating the terms of Microsoft's End-User License Agreement.

I used the "Restore CD" that came with my laptop to install Vista Home Premium in VirtualBox after wiping the harddrive clean and installing Ubuntu.  It worked quite well (although Vista is a horrendous piece of... forum rules prevent me from completing this sentence).

---

### Post by inportb on 2008-05-11
> **HotShotDJ said:**
> Keep in mind, unless you've purchased a retail box, your Windows XP licenses are only for the computers that they came on.  If you've deleted the original Windows, installed Linux, and now wish to install the copy of Windows XP that came with that very same computer in VirtualBox, then you may do it (I don't know if you CAN do it without the original CD/DVD ... but that is another issue altogether).  Otherwise, you are violating the terms of Microsoft's End-User License Agreement.

I used the "Restore CD" that came with my laptop to install Vista Home Premium in VirtualBox after wiping the harddrive clean and installing Ubuntu.  It worked quite well (although Vista is a horrendous piece of... forum rules prevent me from completing this sentence).

I believe it's just a single-user license. I believe you can have Windows XP installed on more than one machine, but use only one setup at a time with the same license. It sounds like it'd work with the VM+dualboot setup.

Windows Vista has a different licensing model. I am not too familiar with it, but it's more restrictive.

You can generate an installer from the i386 folder on your harddrive.

---

### Post by HotShotDJ on 2008-05-11
> **inportb said:**
> It sounds like it'd work with the VM+dualboot setup.
Hmmm... if this is the case, the OP might want to simply [migrate the existing Windows installation to VirtualBox]("http://www.virtualbox.org/wiki/Migrate_Windows")

---

### Post by seuzy13 on 2008-05-11
I should not be violating any agreements, because I am installing on the same Windows/Ubuntu laptop. I've been keeping the Windows side around, because of the few programs you can't run in Linux or that have some difficulties, etc. Anyway, I will burn the BootDisc.iso to a CD and see how it works. I'll post when I see how it turns out.

---

### Post by kamitsukai on 2008-05-11
Basically if it's and oem edition of xp it is illegal to run it in virtualbox or any other virtual machine it has to run as it was intended to be...windows 98 should be ok for most things, what are you intending to run in the virtual os?

---

### Post by HotShotDJ on 2008-05-11
> **kamitsukai said:**
> Basically if it's and oem edition of xp it is illegal to run it in virtualbox or any other virtual machine it has to run as it was intended to be...Actually, that is not true.  Microsoft DID attempt to place that limitation into some versions of Vista... but there was quite an uproar over it, and [they backed off that limitation]("http://arstechnica.com/news.ars/post/20080121-microsoft-relents-vista-virtualization-ban-lifted.html").  As far as OEM editions are concerned, the only limit is that you can only run ONE copy of it and only on the machine it was originally installed on.  As long as those restrictions are adhered to, there should be no problems with virtualization.

---

### Post by seuzy13 on 2008-05-11
Well, I still have it installed on another partition, so if I installed it in virtualbox, I would technically be running two, yes?

The main thing I want to use is Photoshop Elements, because I can't get it working in wine. I know for a fact also, that it only works on XP and Vista. In any case, I've never liked GIMP nearly as much as Photoshop, and I'm tired of restarting and booting into Windows. It's a real time-consuming process. There are a few other things I might want to run that would probably work in 98...but Photoshop is pretty much eighty percent of it.

Anyway, I did burn the BootDisc.iso. When I started it in virtualbox, it prompted me to insert the first recovery disc...which I don't have. I assume if I booted into the recovery partition, I could create it, but I'm afraid of accidentally going to far through the restore process and wiping my hard drive or something like that. There are no other .iso files in the partition, so...hm...

> You can generate an installer from the i386 folder on your harddrive.

How so?

---

### Post by HotShotDJ on 2008-05-11
> **seuzy13 said:**
> Anyway, I did burn the BootDisc.iso. When I started it in virtualbox, it prompted me to insert the first recovery disc...which I don't have. I assume if I booted into the recovery partition, I could create it, but I'm afraid of accidentally going to far through the restore process and wiping my hard drive or something like that. There are no other .iso files in the partition, so...hm..Since you've got a working Windows installation already, why not give this a try: [http://forums.virtualbox.org/viewtopic.php?t=1404](http://forums.virtualbox.org/viewtopic.php?t=1404)

---

### Post by inportb on 2008-05-11
> **seuzy13 said:**
> Well, I still have it installed on another partition, so if I installed it in virtualbox, I would technically be running two, yes?

Are you running your virtual machine and physical machine on Windows at the same time? If not, only one license is being used at any moment, at most. And unless you've done some serious hacking, I don't think you would "technically" be running two.

---

### Post by seuzy13 on 2008-05-11
> **inportb said:**
> Are you running your virtual machine and physical machine on Windows at the same time? If not, only one license is being used at any moment, at most. And unless you've done some serious hacking, I don't think you would "technically" be running two.

kay. The legality of it should not be an issue then.

> Since you've got a working Windows installation already, why not give this a try: [http://forums.virtualbox.org/viewtopic.php?t=1404](http://forums.virtualbox.org/viewtopic.php?t=1404)

I gave the thread a quick read through, and it appeared to be a real hairy and advanced process to go through. As afore mentioned, I do not want to risk wiping any data from my hard drive.

From the link you posted:
> OK, I've done it for Windows XP like this:

1. have a running WinXP virtual machine  ...etc...etc

This sends a few question marks into my head. :confused: If the goal is to get a WinXP virtual machine from a physical partition, how do you start out with one? Am I reading this wrong?

---


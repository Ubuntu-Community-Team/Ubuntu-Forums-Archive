---
title: "Need help with partitioning"
date: 2016-08-31
forum: New to Ubuntu
---

### Post by emcuevas on 2016-08-31
Hi,

I would like to ask for your help with partitioning my ubuntu. I have ubuntu as my permanent OS. But it seems that it keeps crashing often. I do not know if it is because the partitioning is wrong. I actually ran boot repair and got this message 

"The boot files of [The OS now in use - Ubuntu 15.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)"

BUT, i cant partition my hard drive with gparted. I dont know why. can someone please help me? 

file:///home/migz/Pictures/Screenshot%20from%202016-08-31%2010-45-51.png


i really will appreciate all the help

---

### Post by Bucky Ball on 2016-08-31
Welcome. A few things. 15.10 is no longer supported. Advise you upgrade to a supported release.

You need to resize the / partition from a live session. In other words, boot from the install media and 'Try Ubuntu', launch Gparted and away you go. The partitions need to be unmounted to resize them and you can't unmount / if you are using it to run the OS.

Lastly, run boot repair but not a repair. Just get it to run the bootinfo script (you will see an option to do that when you launch Boot Repair). When it's done it will provide you with a link to the resulting output. Post that link here. Thanks.

---

### Post by emcuevas on 2016-08-31
so basically i cant resize it because i cannot unmount because im using it to run the OS. :(.. so it means i need to reinstall ubuntu all over again?

---

### Post by Bucky Ball on 2016-08-31
You did not read my post carefully. Boot from the install media you installed Ubuntu from, choose 'Try Ubuntu', when you are at a desktop, launch Gparted and resize your / partition. Done. You can also download Gparted as an ISO and make a bootable disk/USB and boot from that and resize. Gparted is also available on the SystemRescueCD and others. 

Bottom line: There is *_absolutely no reason or need to reinstall Ubuntu_*. 

Booting from a live session means / will be unmounted.

---

### Post by emcuevas on 2016-08-31
Can you suggest what should I do with my partitioning? Should I have /home also? Im new to ubuntu , so sorry if i ask too many questions.

where should i create  the ext4(200mb for /boot)

---

### Post by Bucky Ball on 2016-08-31
> **Bucky Ball said:**
> ... run boot repair but not a repair. Just get it to run the bootinfo script (you will see an option to do that when you launch Boot Repair). When it's done it will provide you with a link to the resulting output. Post that link here. Thanks.

Let's see what you've already got, please.

---

### Post by emcuevas on 2016-08-31
how can i upload a photo here?

---

### Post by howefield on 2016-08-31
> **emcuevas said:**
> how can i upload a photo here?

Use the paperclip icon to attach an image to you post. 

If you are using the Quick Reply box, click on Go Advanced to get the icon, it isn't available with quick reply.

---

### Post by emcuevas on 2016-09-01
[ATTACH=CONFIG]270953[/ATTACH]

---

### Post by yancek on 2016-09-01
The GParted output doesn't show anything unusual.  You have the standard efi partition at the beginning of the drive which is expected.  Your filesystem root partition takes up pretty much the rest of the drive with a small swap partition at the end so those partitions are not likely to be the cause of your problem.  

You were asked to run the boot repair again, select the Create BootInfo Summary option and do not try to do a repair.  Post the link to the output here and that might show a possible source of the problem.

---


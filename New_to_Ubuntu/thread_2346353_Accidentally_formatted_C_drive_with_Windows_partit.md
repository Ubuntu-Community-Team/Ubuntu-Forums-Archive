---
title: "Accidentally formatted C:/ drive with Windows partition."
date: 2016-12-13
forum: New to Ubuntu
---

### Post by outpact on 2016-12-13
Exactly what the title says. Am I able to dualboot back to Windows and if so how?

---

### Post by QIII on 2016-12-13
Hello!

If you are using that machine right now, stop.  Turn it off and get to another machine.  The more it is used, the more loss you risk.

Then, would you please describe your setup prior to formatting the partition?

---

### Post by outpact on 2016-12-14
Everything is normally functioning. I just cant pick Windows 7 as a startup OS anymore, just Ubuntu. My C:/ drive was formatted linux compatible, so nothing out of linux was formatted

---

### Post by QIII on 2016-12-14
I am sorry.  I do not have a crystal ball.  

Without information, we can't help.

Would you please describe how your system was set up?  You can give us some very useful detail if you will follow the instructions [here]("https://help.ubuntu.com/community/Boot-Info").

Use you machine only long enough to gather that data.

---

### Post by outpact on 2016-12-14
> **QIII said:**
> I am sorry.  I do not have a crystal ball.  

Without information, we can't help.

Would you please describe how your system was set up?  You can give us some very useful detail if you will follow the instructions [here]("https://help.ubuntu.com/community/Boot-Info").

Use you machine only long enough to gather that data.

I am a little lost on using this machine for just a little. I use this actively almost 5-6 hours a day without any major issues.
EDIT: Should add that this was an issue at least a month ago or more.

Also, heres what you've asked.
[http://paste2.org/8ymExjMV](http://paste2.org/8ymExjMV)

---

### Post by oldfred on 2016-12-14
What is sda1, now ext4 formatted?
I assume that was your Windows partition.
It also looks like it is not default mounted or your install.

If you had just reformatted it and not used it, you might be able to convert back to NTFS type 07 (not reformat). But if you have used it at all to write data, then you may be able to recover some data, not not a bootable system. Any one Windows file overwritten would prevent you from having a working system.

If you have no data in sda1, best then just to restore your last Windows backup. If you did not make a backup then you need to use your Windows repair/recovery tools or install disk to reinstall Windows to sda1. You will have to make sure it is NTFS formatted and has boot flag or Windows will not install into it.

---

### Post by nothingspecial on 2016-12-14
If your ntfs partition is just a data partition, as it looks like, and you have been using your ubuntu install for 5-6 hours a day for over a month, then in all likelyhood any data you stored on your windows install partition is gone. You will need to reinstall windows.

---

### Post by outpact on 2016-12-14
> **nothingspecial said:**
> If your ntfs partition is just a data partition, as it looks like, and you have been using your ubuntu install for 5-6 hours a day for over a month, then in all likelyhood any data you stored on your windows install partition is gone. You will need to reinstall windows.

So how can I do that via Ubuntu, what softwares and hardwares do I need? Will I have to purchase a cd?

---

### Post by mastablasta on 2016-12-16
you do not install Windows form Ubuntu. you use a Windows CD/DVD, boot form it and install windows. 

if your PC has recovery partition i think you can download a recovery CD and use that partition to recover (reinstall) Windows.

one of the reasons we advise new users to backup before messing with partitions is because things can easilly go wrong (accidentally deleting Windows partition, partition errors, disk errors...) this goes for any disk changes (even if you create new partitions in Windows etc.)

good free backup tools for imaging partitions are redo backup (with GUI) and clonezilla (text based GUI).

---


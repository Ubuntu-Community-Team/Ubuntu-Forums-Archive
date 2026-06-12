---
title: "Ubuntu and access to windows files security"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by simigdkon on 2013-12-19
Hi all, 
I installed ubuntu 12.04 and noticed that I can access all my windows (XP) files from ubuntu. 
That's great but on the other hand wtf?
What's the point having an administration account in windows xp if all you need is just an ubuntu live cd and "voila"! All files are accessed.
Is there a way to make ubuntu ask for password before accessing my files even if someone uses a live cd?? 
I know it seems like a question for a windows forum but I wanna use ubuntu along with windows and protect my windows files from access by anyone.
Thanks

---

### Post by monkeybrain20122 on 2013-12-19
You can change permission to the Windows partition
[http://askubuntu.com/questions/100698/restrict-access-from-another-user-to-the-ntfs-partition](http://askubuntu.com/questions/100698/restrict-access-from-another-user-to-the-ntfs-partition)

XP would be a wide open door when supports end soon. Ubuntu having access to your XP partition is the last thing you should worry about. :) I wouldn't  do anything important/sensitive on a 10+ year OS with a horrible reputation for securiry which will reach end of life soon.

---

### Post by grahammechanical on 2013-12-19
There is nothing strange at all about this. For compatibility reasons Linux developers sought to make Linux capable of accessing Micorsoft file systems. Microsoft, for reasons of customer lock in, ignores Linux and so we Linux users can access our Windows partitions but when we are a windows user we cannot access our Linux partitions. Or so I am told. I do not use a Microsoft OS. A networking share is another way of doing this. Or so I am told.

You should take the CD/DVD drive out of the boot order and do the same for the USB ports. That way the machine will always boot from a hard disk. And then password protect the BIOS. If that is possible on your machine. Do not let anyone have physical access to the machine. Encrypt the hard disk.

One day you may need to get data off of the Windows partition. Then, you will be glad that Linux can do that for you and it can be done from a Ubuntu live session. Security and convenience are incompatible.

Regards.

Checkout this thread. Sometimes we are glad that Linux can read Windows file systems.

[http://ubuntuforums.org/showthread.php?t=2194503](http://ubuntuforums.org/showthread.php?t=2194503)

---

### Post by 3rdalbum on 2013-12-19
> **simigdkon said:**
> Hi all, 
I installed ubuntu 12.04 and noticed that I can access all my windows (XP) files from ubuntu. 
That's great but on the other hand wtf?
What's the point having an administration account in windows xp if all you need is just an ubuntu live cd and "voila"! All files are accessed.
Is there a way to make ubuntu ask for password before accessing my files even if someone uses a live cd?? 
I know it seems like a question for a windows forum but I wanna use ubuntu along with windows and protect my windows files from access by anyone.
Thanks

What if somebody uses a live CD that doesn't respect the request to ask for a password?

There's not really any way to do it well. The previous poster suggested restricting the ability of somebody to boot a live CD and setting a BIOS password, but it only takes a minute to remove the hard disk from your computer and slam it into one of those USB docks and start copying the data off it.

Windows Vista and above (maybe 7 and above) support encrypting the Windows partition with a password, but then I believe you would lose access to it in Linux. Of course, Linux also supports encrypting its partition, and Windows can't read Linux partitions anyway. Encrypting a partition or a whole hard drive does incur a speed penalty. Encrypting the Windows partition and your Linux /home is about the best option I can think of, with one smallish partition in-the-clear for transferring data between the operating systems.

A slightly alternate idea would be to run Ubuntu as a single boot with an encrypted and password protected /home, but have a Windows virtual machine you can run when necessary. The virtual hard disk would be sitting in your /home and as a result would also be encrypted. Your Windows would run a bit slower because of virtualisation overhead, plus the need to decrypt the virtual hard disk while running; but it wouldn't be horrible. You could easily transfer files between Windows and Ubuntu using the normal Shared Folder functionality of your virtual machine. You can also run Windows programs without having to reboot.

So, there's no great way of doing what you want, but there's some ideas for you. Pick the one with the least-bad tradeoffs.

---

### Post by simigdkon on 2013-12-19
First thank you all for the discussion. 
I'm amazed that windows xp is like that. I still can't believe it! It's like sharing everything with everyone. 
Just to clarify,  I'm not AT ALL accusing linux for being able to access windows data. I'm glad I can access windows from live cd or so. Saved my ass and my friends asses lots of times. But I truly cant believe that if you have a virtual cd/usb with Ubuntu, windows xp is an open book hahahah.And we PAY for that!Damn i'm so pissed off right now!
 I think it's time to make Ubuntu my primary system.

---


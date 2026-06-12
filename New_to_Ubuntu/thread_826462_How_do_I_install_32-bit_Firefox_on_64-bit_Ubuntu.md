---
title: "How do I install 32-bit Firefox on 64-bit Ubuntu?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by SCURVER on 2008-06-11
[B][I] Well, I DID it! Moved over to UBUNTU and in the process must have dozed off as I lost everything I had in XP! Just as well, but still scary...But it seems that I almost have a good, complete rendition of UBUNTU, with a few problems...My FIREFOX won't work. Something tells me that with the implementation of version 8.04 UBUNTU, I am running a 64 bit rendition of FIREFOX  and need to install a 32 bit version of that browser. How do I do that? There are other issues, but I will get to them piece by piece. I need that browser, though. I seem able to download programs, but for the life of me cannot get them running. How do I do that?

     I am running UBUNTU 8.04 on an old Dell desktop with 3 GB of RAM, so it's running okay. I have plenty of room on several hard drives. I hate that I lost so much of my XP stuff, photos and all mostly, but they may be replaced. Digging out all of those addresses and such will be a bit painful. I'm going to check in with the LINUX guys over in Mobile this weekend and see if they can help me get this thing going properly. Is there a way to recover all of that which was lost in the re-pattitioning of the hard drives when I moved to LINUX? Oh if so that would be SO nice! But anyway..............It's good to be in LINUX at last!

                                 Scurver:)[/I][/B]

---

### Post by anjilslaire on 2008-06-11
If its an "old Dell Desktop" you may be better off running the 32bit version of Ubuntu, even if you have a 64bit CPU...

It's not likely that you'll be able to restore your data if everything has been formatted. Forensically possible, yes. But expensive and time consuming. In most cases, not worth it.

---

### Post by stalkier on 2008-06-11
> **SCURVER said:**
> [B][I] Well, I DID it! Moved over to UBUNTU and in the process must have dozed off as I lost everything I had in XP! Just as well, but still scary...But it seems that I almost have a good, complete rendition of UBUNTU, with a few problems...My FIREFOX won't work. Something tells me that with the implementation of version 8.04 UBUNTU, I am running a 64 bit rendition of FIREFOX  and need to install a 32 bit version of that browser. How do I do that? There are other issues, but I will get to them piece by piece. I need that browser, though. I seem able to download programs, but for the life of me cannot get them running. How do I do that?

     I am running UBUNTU 8.04 on an old Dell desktop with 3 GB of RAM, so it's running okay. I have plenty of room on several hard drives. I hate that I lost so much of my XP stuff, photos and all mostly, but they may be replaced. Digging out all of those addresses and such will be a bit painful. I'm going to check in with the LINUX guys over in Mobile this weekend and see if they can help me get this thing going properly. Is there a way to recover all of that which was lost in the re-pattitioning of the hard drives when I moved to LINUX? Oh if so that would be SO nice! But anyway..............It's good to be in LINUX at last!

                                 Scurver:)[/I][/B]

Cool to see someone that is happy with Ubuntu. Sorry I cannot help with the FF issue but I am sure someone will be on here quickly. I run a 32bit system so....

---

### Post by Harii on 2008-06-11
I Doze off while i did a install and the cat laid on the keys.
Just say the cat install didn't go well.

 Can't you apt-get remove and apt-get install an new firefox?
Or will it still be the 64 bit?

---

### Post by cariboo on 2008-06-12
IF you are going to be adding and removing programs get familiar with synaptic. You can access it in System-->Adminstration-->Synaptic Package Manager. There are more programs available in the repositories than you'll find a need for.

Jim

---

### Post by bumanie on 2008-06-12
To recover your xp partitions, is possible, but there are no guarantees. You could use test disk which is a partition/data retrieval program. Ubuntu itself also has a project/program called ntfsprogs that has a ntfs undelete function on it. I suggest you try not to use the partitions the xp data was on and read up on how to use these programs, if you use and write over you former ntfs partitions, the chances of recovering anything useful will be greatly reduced. Get test disk here[http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download"). To install ntfsprogs, > sudo apt-get install ntfsprogs You will have to search for a tutorial on how to use it. If you go down this path, you will have to reinstall ubuntu again.

---

### Post by Paqman on 2008-06-12
What makes you say that you need 32-bit Firefox? It used to be necessary to get Flash working, but not any more.

Flash is included in the package ubuntu-restricted-extras, which is a good thing to install anyway. As well as Flash it installs Java, multimedia codecs, fonts, etc.

---


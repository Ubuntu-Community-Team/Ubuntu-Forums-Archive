---
title: "Moving to Ubuntu - Need some advice"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by seomexfan on 2008-06-19
Hello Everyone,

I´m planning on moving to Ubuntu. I´m thinking Ubuntu 8.04 64 bits Version.

I have an AMD Athlon 64X2 4000+ Processor of 2.11 Ghz, 4GB of Ram Memory (Dual Channel), and 80GB Hard-Drive.

My daily tasks require me to use: Web Browser (Firefox 3), Text Editor (Word), SpreadSheet Editor (Excel), Websites Editor (Dreamweaver), FTP Client (FileZilla), and Corel Draw.

I´m currently using Windows XP. However, since I´ve always had troubles with Windows, I´m seriuosly thinking about moving to Ubuntu.


However, I have a few questions:

Due to my Computer Specs, Can I use Ubuntu 64 bits so I can have a faster Computer and really use my whole Ram Capacity?

If I install Ubuntu 8.04 64 bits, will I still be able to use OpenOffice with Text Editor, and SpreadSheet Editor?

On my Web search to move to Ubuntu 8.04 64 bits. I found that a software named Komposer could replace Dreamweaver. Is this Komposer available to run with Ubuntu 8.04 64 bits?

Does FileZilla works with Ubuntu 8.04 64 bits?

Is there a program to replace Corel Draw with Ubuntu 64 bits?

Will Firefox 3 run with Ubuntu 8.04 64 bits?


Or, would you recommend me to use Ubuntu 8.04 32 bits?


As you could see on my Daily Tasks above. I don´t use that much of software daily. But, I want to be sure that if I switch to Ubuntu 8.04 I will have programs to perform the same tasks I do with Windows.


Thank you all for kind comments.

---

### Post by mivo on 2008-06-19
With what you do, it's unlikely that you'd notice a speed difference between 32- and 64-bit. I certainly don't, and my profile is similar to yours. It's possible to use more than 4 GB with 32-bit too, but not out of the box. I doubt you'd notice a difference between 3.2'ish GB and 4 GB, by the way.

But anyway, if you go with 64-bit, note that there is no 64-bit Java browser-plugin from Sun (this isn't really Linux's fault) currently. There are some free alternatives, but I have found them to not work with some Java sites that I need/want to use. Flash is (usually) fine. You can still use 32-bit software on a 64-bit Ubuntu installation, so you could, if all else failed, installed a 32-bit Firefox with 32-bit Java browser plugin. There is a guide in the 64-bit section of the forum. This worked well for me in 7.10, but in 8.04 I had some trouble, so I dropped back to 32-bit for Hardy. I notice no difference in speed, but I only have 3 GB RAM (of which I never see more than 1 GB used even with lots of stuff running).

All the programs you listed have 64-bit equivalents. The issue is only with the Java browser plugins and very few drivers.

---

### Post by Delever on 2008-06-19
Yes, Ubuntu will take advantage of all your RAM. I have 4 GB ram which still was never full (~3 months usage of virtual machines, graphically intensive applications in them, visual studio in them).

All programs in repository are ready for both 32 bit and 64 bit versions. I don't see komposer 64 binary available for download, but you can run 32 bit programs without any performance penalty. For example, that's the only way with skype.

FileZilla exists in repositories (read: Applications -> Add/Remove -> Install)

I was Corel Photo Paint user a while ago, and some features in gimp reminds me of it, especially the way masks are handled (however, that is better in gimp). I have just finished my avatar with gimp, just to learn it more. It CAN replace photoshop, if you don't use specific plugins. For vector graphics, you may want to check Inkscape.

You may want to use 32 bit ubuntu if komposer does not work on 64 bit version and you find it invaluable.

---

### Post by jimmy the saint on 2008-06-19
check out [http://ubuntuguide.org/wiki/Alternatives#Vectorgraphics_editor]("http://ubuntuguide.org/wiki/Alternatives#Vectorgraphics_editor")  it is a list of software equivalents in linux.

---

### Post by mivo on 2008-06-19
Very few tasks require so much RAM. Linux does, however, use whatever additional RAM is there for file caching. It's readily available to applications if needed. But there is a difference between the RAM used by apps or used for file caching just so that it does something at all. Here's a good article on [how Linux manages memory]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management").

---

### Post by kansasnoob on 2008-06-19
Start with a dual boot!

There are many dual boot guides but I started with this and it just worked:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

This way you will have your Win XP to fall back on until you've worked out any potential problems!

---

### Post by Duck2006 on 2008-06-19
Dual booting will be the way go at first as "kansasnoob" posted.

---

### Post by seomexfan on 2008-06-19
> **kansasnoob said:**
> Start with a dual boot!

There are many dual boot guides but I started with this and it just worked:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

This way you will have your Win XP to fall back on until you've worked out any potential problems!


Thank you for pointing out the option of running a Dual-Boot first. Instead of moving to Ubuntu at once.

I saw another way or guide to do this (Dual-Boot), which is through Wubi. Is this any good? It seems that´s officially supported by Ubuntu Team.

Any thoughts?


Thanks everyone for helping me. This is my first post in the Ubuntu Forums, and I´m really impressed on how supporting this community is.


Best regards from Cozumel Island, Mexico.

---

### Post by Duck2006 on 2008-06-19
> **seomexfan said:**
> Thank you for pointing out the option of running a Dual-Boot first. Instead of moving to Ubuntu at once.

I saw another way or guide to do this (Dual-Boot), which is through Wubi. Is this any good? It seems that´s officially supported by Ubuntu Team.

Any thoughts?


Thanks everyone for helping me. This is my first post in the Ubuntu Forums, and I´m really impressed on how supporting this community is.


Best regards from Cozumel Island, Mexico.

You find that dual booting will be better and faster, as Wubi is just a file that runs an OS on top of an OS.

---

### Post by seomexfan on 2008-06-19
> **Duck2006 said:**
> You find that dual booting will be better and faster, as Wubi is just a file that runs an OS on top of an OS.

Thanks for your reply.

However, I´m Ubuntu or PC well versed. Please, could you explain me the difference of doing the Dual-Boot using Wubi and the other option?

Is Wubi or the Manual Option better?


Thanks.

---

### Post by Delever on 2008-06-19
> **Duck2006 said:**
> You find that dual booting will be better and faster, as Wubi is just a file that runs an OS on top of an OS.

Just to clarify, not "on top of OS" - it is not emulated. "On top" means that it requires windows loader (which is part of windows, loads windows), and specific file which is used as ubuntu disk. In wubi installation Ubuntu is loaded from that file and has filesystem in it. So file operations will be a little slower and that's it. Dual booting has advantage that ubuntu system is independent, on it's own space, and windows can be removed later if needed.

---

### Post by Duck2006 on 2008-06-19
> **seomexfan said:**
> Thanks for your reply.

However, I´m Ubuntu or PC well versed. Please, could you explain me the difference of doing the Dual-Boot using Wubi and the other option?

Is Wubi or the Manual Option better?


Thanks.

Doing an dual boot as dual boot, the system is partitioned for the other OS system and you get to chose witch OS you want. As Wubi is just a file that runs from with in windozes. you could run virtualbox and see if thats any better for your needs. It will be just running an OS inside an Os.

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Delever on 2008-06-19
Virtualbox, yet ANOTHER toy. I use it to run windows inside Ubuntu.

---


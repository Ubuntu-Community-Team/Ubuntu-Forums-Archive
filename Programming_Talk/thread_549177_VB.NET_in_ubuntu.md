---
title: "VB.NET in ubuntu?"
date: 2007-09-12
forum: Programming Talk
---

### Post by Posterus on 2007-09-12
Hi, i like to think i know my way around linux but im a student in college and i have feisty 7.04 on my alienware area-51 m5500 but i am taking a visual basic class.  in class i like to do my programming on my own laptop rather than the gateway's provided for us but if i go into windows my computer is over worked and the fans go crazy (idk if thats my problem or the computers lol) but i was wondering if there was any way to do VB.NET programming in ubuntu with out using vmware or going into windows in any way.


all help is much appreciated:)

---

### Post by gautada on 2007-09-12
C#.NET yes...  The mono team is working on a compiler for  [VB]("http://www.linuxdevices.com/news/NS9725385854.html").  For development you might be out of luck, try [Gambas]("http://gambas.sourceforge.net/").

---

### Post by Vadi on 2007-09-12
> **Posterus said:**
> Hi, i like to think i know my way around linux but im a student in college and i have feisty 7.04 on my alienware area-51 m5500 but i am taking a visual basic class.  in class i like to do my programming on my own laptop rather than the gateway's provided for us but if i go into windows my computer is over worked and the fans go crazy (idk if thats my problem or the computers lol) but i was wondering if there was any way to do VB.NET programming in ubuntu with out using vmware or going into windows in any way.


all help is much appreciated:)

I dropped a course as soon as I found we'll be doing stuff in VB.

But if that's not your option, look into getting a virtual windows running - VirtualBox is a program that was relatively easy for me to set up.

---

### Post by Posterus on 2007-09-12
> **Vadi said:**
> I dropped a course as soon as I found we'll be doing stuff in VB.

But if that's not your option, look into getting a virtual windows running - VirtualBox is a program that was relatively easy for me to set up.

yeah that is a good alternative but like i said i want a way to do it with out running vmware (virtual machine) which is was VirtualBox is.  I already have windows on my laptop so i dont want to take up more space on the disk so i was just wondering if there is a linux version of VB or a vb like copy cat

---

### Post by pmasiar on 2007-09-12
double-boot: VB course on Win, everything else on ubuntu.

If you want to share data, set up FAT partition, NTFS is readable but writing *might* go wrong.

---

### Post by Posterus on 2007-09-12
> **pmasiar said:**
> double-boot: VB course on Win, everything else on ubuntu.

If you want to share data, set up FAT partition, NTFS is readable but writing *might* go wrong.

if you actually read my post i stated i do have it Dual-booted with windows its just that i dont want to have to go into windows to do it.

---

### Post by Vadi on 2007-09-12
Short answer is no, VB is microsoft's language for programming windows apps :/

---

### Post by Posterus on 2007-09-12
> **Vadi said:**
> Short answer is no, VB is microsoft's language for programming windows apps :/

yes but you would think that since VB is a commonly used language that it's libraries would be converted to the linux platform thus being able to build windows apps that also work in linux (multi-platform apps) but still follow the same rules and guidlines as microsoft.

but i suppose it's just microsoft being greedy and nobody careing about it??

---

### Post by Vadi on 2007-09-12
I really doubt that microsoft published those libraries somewhere so that they can be converted to linux ;)

---

### Post by Posterus on 2007-09-12
[http://www.mono-project.com/Downloads]("http://www.mono-project.com/Downloads")

:-D sorry for saying no one cares....it's just that no one cares to look around, i found a compiler for VB that works on linux...downloading it now, i will post my results later

---

### Post by Vadi on 2007-09-12
Hey, who should the one be looking around here be? :P

---

### Post by Posterus on 2007-09-12
> **Vadi said:**
> Hey, who should the one be looking around here be? :P

well the reason i posted on here is because i needed help......which should mean that i was having trouble finding one.....it's easier if i have more than one person looking for it WITH me, i wasn't here to tell people to look for me......and it just seems like nobody looked at all considering the posts you left me were just basic information.

---

### Post by Vadi on 2007-09-12
Well, yeah, because that's all I knew. I assumed you'd google the topic first :P

---

### Post by Coyote21 on 2007-09-12
> **Posterus said:**
> [http://www.mono-project.com/Downloads]("http://www.mono-project.com/Downloads")

:-D sorry for saying no one cares....it's just that no one cares to look around, i found a compiler for VB that works on linux...downloading it now, i will post my results later

You can also read this [http://www.mono-project.com/Language_BASIC](http://www.mono-project.com/Language_BASIC), if you want to know more about the VB.NET implementation of MONO (In particular, it can only compile VB.NET 2.0 code, 1.0 code is not compilable)

---

### Post by Hairy_Palms on 2007-10-12
or you can try REALBasic, the linux standard version is free and the syntax is pretty much identical.

---

### Post by ryno519 on 2007-10-12
> **Posterus said:**
> [http://www.mono-project.com/Downloads]("http://www.mono-project.com/Downloads")

:-D sorry for saying no one cares....it's just that no one cares to look around, i found a compiler for VB that works on linux...downloading it now, i will post my results later

Warning: If you're going to go the mono route and get a VB compiler working with it keep your windows partition. You never know if you will only be able to do something on Windows (make a call to the win32 api for instance) that you can't do on GNU/Linux. I'd also make sure it's completely, 100% source compatible with whatever compiler you're using on Windows. Wouldn't want to send your professor some source code that doesn't compile on his platform. Other than that, good luck. :)

---


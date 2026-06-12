---
title: "Ubuntu uninstall rendered WinXP unusable and corrupted partition"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by krama09 on 2008-05-02
Hello I am completely new to linux.
I have downloaded Ububtu 8.04 LTS and installed in My Dell Inspiron 6000 laptop inside Windows XP Media Center Edn 2005.
It was working fine. Once accedentally power went off while working in Ubuntu and after restarting I could work in XP with out any problem.

However, when I restarted Ubuntu...it did not boot in normal way and only command prompt appeared (Debian....version)...I tried some commands mentioned in help...but of no avail.Later on I started XP and uninstalled ubuntu.

Subsequently, When I restared in XP...chkdsk started saying volume is dirty and later on automatically took several actions..one of them is "changing security id to default id of file___". Afterwards XP started. But none of the XP related applications (including word,ie)are not working throwing some exceptions. Even taskbar, start menu disappeared. Only non microsoft applications like acrobat, Firefox, are working.

I could not run XP properly neither could restore...

Several posts mentioned that installation inside Win XP will not modify hard disk partitions...But it appears it is not true...at least in my case it corrupted NTFS partition...

Can anyone help to restore XP?

---

### Post by Xiong Chiamiov on 2008-05-02
When you say that you installed Ubuntu "inside Windows XP", what exactly do you mean?  Did you use Wubi?

Before doing any messing with the partitions of a Windows drive, it's a very good idea to defrag it a few times.  My only suggestion would be to run chkdsk and repair your windows installation, which you will need a real XP disc to do.

---

### Post by jimv on 2008-05-02
Is your Windows drive showing up as C: or D: ?

---

### Post by krama09 on 2008-05-02
> **Xiong Chiamiov said:**
> When you say that you installed Ubuntu "inside Windows XP", what exactly do you mean?  Did you use Wubi?

Before doing any messing with the partitions of a Windows drive, it's a very good idea to defrag it a few times.  My only suggestion would be to run chkdsk and repair your windows installation, which you will need a real XP disc to do.
Yes I used Wubi...

I did defrag two times before installing Ubuntu

I did not have XP installation media..as laptop came with dell restore partition..Now that partition is not seen either in disk management...

---

### Post by krama09 on 2008-05-02
> **jimv said:**
> Is your Windows drive showing up as C: or D: ?
both C: & D: are being displayed...I have acess...bot cannot edit

---

### Post by jimv on 2008-05-02
which drive, c or d, has the Windows folder in it?

What I'm thinking is that when you got rid of Ubuntu, the partition that it was on may have been detected by Windows, and inadvertently changed the drive letter from C to D, which would screw everything up.

---

### Post by krama09 on 2008-05-02
> **jimv said:**
> which drive, c or d, has the Windows folder in it?

What I'm thinking is that when you got rid of Ubuntu, the partition that it was on may have been detected by Windows, and inadvertently changed the drive letter from C to D, which would screw everything up.

Windows is in C:. Win XP is booting normally. But after logging no welcome music..no permissions to change user accounts(strangely pasword only can be changed). No microsoft application works..other applications or running..I really dont understand this strange behaviour..

---

### Post by jimv on 2008-05-02
Darn.  I borked my XP install once when I removed my Ubuntu partition.  Since that was the first partition on the drive, XP could suddenly see it, and it moved it's C drive to D...all kinds of chaos ensued.

EDIT:

I just found this post about a guy with a similar problem.
[http://klo-2k.spaces.live.com/blog/cns!2872308BEB65CA67!396.entry](http://klo-2k.spaces.live.com/blog/cns!2872308BEB65CA67!396.entry)

The file he's talking about is C:/Windows/System32/svchost.exe

---

### Post by krama09 on 2008-05-02
> **jimv said:**
> Darn.  I borked my XP install once when I removed my Ubuntu partition.  Since that was the first partition on the drive, XP could suddenly see it, and it moved it's C drive to D...all kinds of chaos ensued.

EDIT:

I just found this post about a guy with a similar problem.
[http://klo-2k.spaces.live.com/blog/cns!2872308BEB65CA67!396.entry](http://klo-2k.spaces.live.com/blog/cns!2872308BEB65CA67!396.entry)

The file he's talking about is C:/Windows/System32/svchost.exe

Link you have provided is extermely helpful. I will try some of the tips to restore my system..
Thanks a lot.

---


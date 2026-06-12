---
title: "Installing or using Windows alongside Ubuntu"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by gstoilov on 2012-03-07
Hallo,

I started using Ubuntu but it appeared that there are features where I need to use Windows. How can I install both systems or how can I use them together. Is there any chance to do this. I know there are tools such as wine or VMware but I do not know how to use the,

Need help how to resolve this issue and mainly to pla my favorite game Civilization IV

HEEEEELP !!!!

---

### Post by AlexDudko on 2012-03-07
Install first Windows then Ubuntu. There are tons of information on Google and on this forum as well.

---

### Post by mastablasta on 2012-03-07
Civ 4 has gold rating with Wine, so you could try that. 
 
otherwise simply boto form live CD, run gparted and create some disk space for your windows.
 
then install windows.
 
then update grub: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Script Warlock on 2012-03-07
> **gstoilov said:**
> Hallo,

I started using Ubuntu but it appeared that there are features where I need to use Windows. How can I install both systems or how can I use them together. Is there any chance to do this. I know there are tools such as wine or VMware but I do not know how to use the,

Need help how to resolve this issue and mainly to pla my favorite game Civilization IV

HEEEEELP !!!! [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/VMware/Player](https://help.ubuntu.com/community/VMware/Player)

---

### Post by t0p on 2012-03-07
> **gstoilov said:**
>  I know there are tools such as wine or VMware but I do not know how to use the!

You may not know how to use wine or virtualisation, but you may just have to bite the bullet and learn.  It's not that difficult, honest.

I run Ubuntu on my pc, but I need Windows for one single job - to use my printer.  Dual-booting would have been an option, but I (like you) wanted to use Windows *alongside* Ubuntu - no pesky logging in and out and what-have-you.

The answer was [VirtualBox]("http://www.virtualbox.org").  It's free (as in beer anyway - I'm not sure if USB support has made it into the Free (as in speech) version yet) and it runs alongside (wel, actually *in*) Ubuntu so it ticks all my boxes.

YMMV but I like VBox, long may it reign (or something).

---

### Post by Mark Phelps on 2012-03-07
Just understand that, with Wine (and its derivatives), you're not really running MS Windows -- so you don't need an MS license for that.

But with Virtualization, you have to install MS Windows -- and you DO need a license for that.  You can't legally install from the same CD/DVD that you have already used on a different PC.

That means that while VirtualBox is free, the MS Windows OS you install using it is not.

---


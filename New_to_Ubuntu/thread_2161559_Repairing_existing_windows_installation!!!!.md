---
title: "Repairing existing windows installation!!!!"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by ashwin91 on 2013-07-11
I am currently running Windows 7 and Ubuntu 13.04 in parallel.Though I use Ubuntu most of the time,I shift to Windows whenever I need to work on MS Excel.
But,recently i found that I'm unable to open the control panel and I get a msg that the windows explorer.exe had stopped working.
From the many forums that provided solutions to this problem,I've come to a conclusion that only repairing the windows using the boot disc can correct this issue.
How can I go about repairing my Windows installation without affecting my GRUB?
I'm aware of the fact that windows doesn't recognize Linux partitions and that it isn't recommended to install Windows after Ubuntu.
But,given the fact that I'm just gonna repair and existing installation,I would like to know If this would cause problems in Ubuntu?
Any help is this regard is appreciated and thanks a lot.

---

### Post by mastablasta on 2013-07-11
repair windows and reinstall grub if necessary from live disk.

---

### Post by newb85 on 2013-07-11
I would back up your important stuff first, though.

---

### Post by Mark Phelps on 2013-07-11
When you say "boot disk" -- what do you mean?  Is this a CD that came with the PC?  Is it a Win7 installation DVD? Is it a Win7 Repair CD you made yourself?

The primary purpose of a Win7 Repair CD is to repair the boot loader -- it is very limited in what it can do for Windows in general.

---

### Post by ITfromScratch on 2013-07-11
> **Mark Phelps said:**
> When you say "boot disk" -- what do you mean?

By "live disk" I think he's referring to the Ubuntu live disk -- that is, the CD or DVD that you install Ubuntu with. It has more options than just installation. Specifically for your case, that would include "rescuing a broken system."

---

### Post by newb85 on 2013-07-11
An Ubuntu live CD would be little help for repairing a broken Windows system.

---

### Post by ITfromScratch on 2013-07-11
> **newb85 said:**
> An Ubuntu live CD would be little help for repairing a broken Windows system.

You're right. But from what I can tell, no one was telling ashwin91 to repair the Windows installation with the Ubuntu live CD. The way the original question was asked, it seemed that he already had a method of repairing Windows, but was unsure if it would screw up his Ubuntu installation. 

MastaBlasta said: "[COLOR=#000000]repair windows and reinstall grub if necessary from live disk."

[/COLOR]He wasn't saying to repair Windows with the live CD. He was saying you can reinstall grub with the live CD.

---

### Post by leunam12 on 2013-07-11
My advice is that you backup your data; then repair windows, then reinstall grub if needed. Repairing windoze will not break your Ubuntu installation in most cases but it may leave you unable to boot it, hence the need of reinstalling GRUB or run boot-repair from Ubuntu live CD.

Please, be aware also that it is possible to run Excel in Ubuntu using Wine. I do it all the time.

---


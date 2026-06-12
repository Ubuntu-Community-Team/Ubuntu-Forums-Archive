---
title: "Suspend and hibernate"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-05-28
Maybe this sounds like a silly question, but if I chose hibernate or suspend, how can I turn on my computer again?Are there some keys I can configure?
And another question.I turn off my computer from the power button, not from the menu.When I turn it back on it checked the drives and reported some error which couldn't be fixed automatically (I had to run fsck manually).The system booted and when I turn it of (the proper way :) ) it showed an error concerning "Network bus manager couldn't be shut down" and after 15-20 seconds the system rebooted.Now it works fine.Should I be worry that I broken something?I have 3 items in my "lost and found" folder.What should I do with them?
By the way I have Ubuntu 8.04.

---

### Post by crf on 2008-05-29
Probably you should turn your computer off using the menu. You can use the *shutdown -h now* command too, from the terminal.

You can do it the way you're doing it now, but it could lead to problems with the filesystem or corrupt files. I thnk it will also cause linux to scan your filesystem for errors each time you start up, which takes some time. Probably that's where those lost+found files came from.  You could probably delete them, unless you had open, not previously saved files when you cut the power, in which case the files in lost+found may be copies of that lost work you may then recover.

I guess, from the rest of your question, that you'd rather have the computer suspended, rather than off, mostly? I don't know about your computer, but I have an old laptop. When I press a blue button on the laptop, or run *sudo apm --suspend*, it suspends to disk. The menu option to hibernate and lock screen from the log off menu seems to work differently though, and not too well. The "Power Management" system preferences also do not seem to function as well as they should in my case, but perhaps they would work better in yours.

There is an ubuntu help page on suspend --> [https://help.ubuntu.com/community/SuspendHowto](https://help.ubuntu.com/community/SuspendHowto)

---

### Post by iaculallad on 2008-05-29
> **Troll_the_Great said:**
> Maybe this sounds like a silly question, but if I chose hibernate or suspend, how can I turn on my computer again?Are there some keys I can configure?


Had you tried pressing the "Wake Up" keyboard button to unlock from suspend/hibernate state?

---

### Post by Troll_the_Great on 2008-05-29
Well, that was my problem actually.I pressed the hibernation mode and the computer powered off, but when I pressed the power button I didn't have any effect.This is why I had to press the shutdown button.I don't have a swap partition or a swap file.Could this be the problem?

---

### Post by philinux on 2008-05-29
I have bugged this at launchpad. Either suspend or hibernate fail to resume.

I have to REISUB to get it to boot. 

I did press Alt F1 the last time I tried either of these two options and there was an error stating

No Resume Image.

I have 2gig ram and a 2gig swap so should work.

---

### Post by crosswalker21 on 2008-05-29
I'm having the same problem with suspend/hibernate.  When either one is activted (either manually or through power management) my power light pulses, like it should, but the system won't come back.  It looks like the machine wakes up (power light stays solid), but the screen is definitely off and won't turn on at all.  The only solution I have is to force-power down (which isn't a solution at all).  Hopefully the launchpad bug gets some traction.

---

### Post by PmDematagoda on 2008-05-29
What are the specifications of your PC?

---

### Post by tom56 on 2008-05-29
> **Troll_the_Great said:**
> Well, that was my problem actually.I pressed the hibernation mode and the computer powered off, but when I pressed the power button I didn't have any effect.This is why I had to press the shutdown button.I don't have a swap partition or a swap file.Could this be the problem?

Yes - hibernate requires a swap partition at least as large as your RAM. The recommended amount is double your RAM. Hibernate works by dumping everything from the memory onto the swap partition. It needs to be larger than the RAM to account for the fact that some of it may already be in use when you try to hibernate.

---

### Post by PmDematagoda on 2008-05-29
Hibernation/suspend may not work due to reasons besides low swap disk space, some of the more irksome are:-
1) Kernel bugs related to suspend or hibernation(thought these have received good attention in kernel 2.6.25).

2) Drivers that are incapable of suspending or hibernating properly, one example is the Nvidia driver, any other poorly built drivers may also be a cause of these problems.

---

### Post by crosswalker21 on 2008-09-02
> **PmDematagoda said:**
> What are the specifications of your PC?
Gateway T-1623 laptop
AMD Turion 64 X2 processor at 2.0 GHz
ATI Radeon x1270 integrated graphics card (suspected cause of the problem)
3 Gigs of Ram
5 Gig swap partition
250GB drive
I'm running the latest ATI proprietary driver (8.8)

---

### Post by kerry_s on 2008-09-02
> **Troll_the_Great said:**
> Well, that was my problem actually.I pressed the hibernation mode and the computer powered off, but when I pressed the power button I didn't have any effect.This is why I had to press the shutdown button.I don't have a swap partition or a swap file.Could this be the problem?

yes

---


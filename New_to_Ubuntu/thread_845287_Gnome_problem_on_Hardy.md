---
title: "Gnome problem on Hardy"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2008-06-30
Hi, I am running Hardy i386 on my desktop and recently I had a couple episodes with Gnome not coming on when I start up Hardy.  I thought I fixed that problem with help from a forum post suggested I delete all files named, ".g" something from my Home folder and restarting Gnome.  That worked great.

Then, this week, I installed an ATI graphics card, and set up dual monitors.  It worked superbly, and aside from that, I really have not changed anything on a system level. After that, a couple days went by with no issues at all, and I successfully shutdown, restarted the next day, etc.  Then today in the middle of converting a video in Kino (which I have done recently with zero issue) Ubuntu stops being responsive, desktop icons, panel menus, etc.

I tried restarting X, but when I got back into Gnome, neither drop down menus in the panel nor icons on the desktop could be accessed.  I tried restarting X several times, each time waiting a minute or so to see what would happen, and sometimes got nothing but the desktop picture, sometimes a normal looking screen, but with non responsive icons and menus. I tried restarting the computer a couple times and waiting, but nothing came of it.

I was able to get into failsafe mode a couple times, but half the time the desktop would just be stuck in that non-responsive manner. (example, if I restarted x from normal mode, and tried to get into Gnome via failsafe mode, it would not work; but a couple times, restarting the PC and going to failsafe mode directly, did work.)

So, I said, screw this, I dunno what to do with a broken Gnome, and went ahead an deleted my Ubuntu partition and installed a fresh Hardy. After doing that, I could access everything as a normal day, but after downloading the updates and restarting the computer, AGAIN I got this utterly non-responsive Gnome.

(I am referring to the desktop environment as Gnome, I hope that is correct)

It is pretty early in the morning now, so I think I am about done with this for today, but I hope to find something promising in the way of comments tomorrow.  Otherwise, I think I will delete this partition again and just try a re-install of GUTSY.

Was there something insidious and evil in the updates lately that wacked out my Hardy?

Please help me out if you can.
Thanks

---

### Post by bumanie on 2008-06-30
You could try booting with one of the previous kernels - sometimes that works. Occassionally, a newer kernel does not agree with some of ones setup. You could also try > sudo aptitude install ubuntu-desktop

---

### Post by Motorhead Kaze on 2008-06-30
Good morning, thanks for the response. I "Got in" (was able to use Ubuntu) with a previous kernel on failsafe mode, but even using kernel 16 on normal mode brings me to a, "Frozen" screen.

Thanks for the apt-install code, I did not know that one.  After exiting the terminal I came back to normal Gnome, and get a Gnome Settings Daemon error. "Did not receive a reply. Possible cause include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expires or the network connection was broken."

Which I got sometime last week as well. That one, I deleted the .g files in my home directory. But this time, that doesn't do anything to help the problem. Really, I have no idea specifically WHICH one of those is causing this issue, or if it really is causing anything. The kernel idea is interesting, and I do wish using an older one worked for me.

I admit a lack of understanding of "Failsafe mode". Does it not use the same kernel as "Normal" mode?  

So, currently, the only way for me to use Ubuntu is to go in through failsafe mode. Which...sucks ennit. Also, if I try normal mode, then go to failsafe from just ctrl+alt+bksp, failsafe mode will not work (meaning Gnome is frozen). Failsafe works if I restart the computer.

Reminder, this is a "Fresh" install now, not an upgrade. (This problem affected me in both upgraded Hardy and a new one).

Hmmm. 
Any more ideas one what to do next?

---

### Post by jflarm on 2008-06-30
> **Motorhead Kaze said:**
> Good morning, thanks for the response. I "
I admit a lack of understanding of "Failsafe mode". Does it not use the same kernel as "Normal" mode?  


Yes, they use the same kernel. You can check it doing this command:
cat /boot/grub/menu.lst
The output is the configuration of the grub (your boot loader).
You could also do the comand: "uname -r" to see your current running kernel.

---

### Post by Motorhead Kaze on 2008-07-01
Well, not a GREAT way to do it, but I decided to reinstall a fresh Hardy today and skip all the Gnome related updates. (My issues with Gnome all began...ended?... with an update.)

Gnome is fine now.

---


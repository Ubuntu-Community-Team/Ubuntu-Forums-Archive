---
title: "Odd (maybe) with soft reboot"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by abonon on 2008-07-03
I am having a bit of a problem with rebooting my laptop everyone.  :(   It is a Toshiba with windows Vista one the first parition (50GB) and Ubunutu (Hardy) on the other set of partitions (appx 85GB).

Im not sure why I cant do a soft reboot, and I have certainly searched around for it.  In contrast, I can restart from the Vista partition (when I actually ever go there which is seldommmmmm) back to the grub manager and load ubuntu 8.04 with no problems.  But, when I make a change that needs a reboot in ubuntu, I must turn off the laptop rather then reboot the laptop as it hangs on me after the post.  Quite weird.

Any help would be great.  And btw, I fixed my wireless connection from this forum.  THANK YOU so much!  Not having to use ndoswrapper solved all my wireless woes...  :)  THANK YOU!

p.s. If any information is needed, dont hesitate to ask....  Personally, im hoping this is a simple fix on something i missed.  :(

Thanks again and have a great day to all.  :)  :guitar:

---

### Post by jou770d on 2008-07-03
I'm having the same problem with my toshiba (satellite A30). Except that I had XP not vista (but now I only have hardy). And the same thing used to happen with gutsy.
I didn't make a post about it because I thought it's probably a hardware problem as my laptop is rather old and it had two users before me.

---

### Post by abonon on 2008-07-03
It is certainly odd.  And I am fairly certain it isnt a hardware issue as it soft reboots fine from windows to ubuntu, but not from ubuntu back to ubuntu or to windows.

I only have the windows partition because i havent finished moving everything off of it that i want to keep.

Hopefully someone here has the answer.  :)

---

### Post by jou770d on 2008-07-22
Since I'm not the only one with this problem I thought I'll give a thread a bump in case someone can help or explain why this is happening.
Oh and by the way I noticed that using reboot from a terminal works without a problem so I'm using that when I need to restart. Luckily I don't need to do that very often since this isn't windoze...

---

### Post by Joeb454 on 2008-07-22
Hmm...It could be a gnome fault then. It might be worth filing a bug report on [Launchpad]("http://launchpad.net")

For now you could create a small script and place it on your desktop, and just double click it to reboot. Say you wanted it graphically I guess you could have ```
#!/bin/bash
gksudo reboot
``` Simple as that :)

---

### Post by ace007 on 2008-07-22
From what I understand in my experience with my laptop, it is the fault of some module not wanting to unload.  My Dell 700m also fails to shutdown or suspend occasionally.  I suggest after a failed shutdown attempt, that you restart and open a terminal and enter the "dmesg" function.  Look for something hanging during the shutdown process in the printed log.

EDIT: you may wish to "sudo dmesg -c" to clear the current log file, then immediately reboot, so you can easily tell what has happened since you cleared the log.

---


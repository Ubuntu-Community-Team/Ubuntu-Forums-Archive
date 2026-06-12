---
title: "Lost printer"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by Greg Mueller on 2011-11-28
Everything was working fine until I did updates this morning, I saw that it did a bunch of kernel downloads and now my printer stopped working. Why must the Ubuntu programmers keep screwing with stuff like this?

I am running an HP network printer. Ubuntu can no longer see the printer on the network. The HP setup software says it can't see any printers. I go to my "Places" and it says it can't mount my network although the internet connection works.

I have now turned off my updates function and only want to get my printer back.

Help?

---

### Post by khelben1979 on 2011-11-28
Downgrading your Linux kernel to the previous one you had, should solve this problem. You say it happened recently, what version of Ubuntu are you using?

(Seems like you're using Linux kernel 2.6.38.2 or perhaps 2.6.38.3, can you check?)

---

### Post by Phillk on 2011-12-04
[FONT="Comic Sans MS"][SIZE="3"]Funny, I lost my printer after the last upgrades as well. 
I'm on kernel 2.6.38-13 generic.
The program "printing" cannot find my network printer now. I went to update manager and reinstalled anything to do with "CUPS". But, I still cannot find the printer.:confused:
Any suggestions would be appreciated. 
Thanks Phill K.[/SIZE][/FONT]

---

### Post by mijdrawoh on 2011-12-04
I use a HP1020 printer (not in a network) and more than once have lost the ability to print after kernel or cups upgrades, not just in Ubuntu, but in the other distro I also use. I moved to Ubuntu as my prime because I was never able to regain the ability to print in the other. The Ubuntu solution that works for me: unplug the printer, wait a few seconds, turn it on and re-plug. A message appears that Ubuntu is re-configuring to add the printer and, when it completes, my printer again works.

---

### Post by Phillk on 2011-12-05
[SIZE=3][FONT=Comic Sans MS]Well after all the reinstalling of cups and my canon drivers, I broke down and reinstalled the whole OS (11.04). I still had no printer. 
However, I started the program synaptic package manager. I had it search for broken packages and fix the broken packages. 
I was able to go the the printing program and install my network printer. I'm now printing again.

Phill K:popcorn:
[/FONT][/SIZE]

---


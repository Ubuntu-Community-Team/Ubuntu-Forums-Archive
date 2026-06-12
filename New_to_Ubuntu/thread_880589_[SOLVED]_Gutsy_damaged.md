---
title: "[SOLVED] Gutsy damaged?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by dansan on 2008-08-05
Hello all,

I switched from Vista to Ubuntu Studio not quite a year ago and have been happy with the change, thanks to considerable help from this community. 

I use  a computer all day every day in my translation business. Until last week, Ubuntu has given me few reasons to worry. Then a client bumped my desk while the computer was running. This, so to speak, "cleared" the desktop, leaving only the Ubuntu Studio background. No response to mouse or keyboard input, so alt+sys+reisub didn't help, forcing me to use the shut-off button. Restarting that day returned things to normal.

Today's a different story. After start-up, Kontact twice displayed errors when saving a long email to draft ("Permission denied"). Clicking OK made Kontact close, all the TB icons turn to Xs and Nautilus freeze as above. I restarted with the Recover option, and everything so far is behaveing normally, allowing me to finish answering emails and write this. 

Does anyone know what's broken? Whether it's fixable? Does this sound like a reinstall call?

TIA
Daniel

---

### Post by PmDematagoda on 2008-08-05
Perhaps the bump did something to the hardware? More specifically the hard drive, did you get the system checked to see if everything was in working order?

---

### Post by prshah on 2008-08-05
> **dansan said:**
> 
Does anyone know what's broken? Whether it's fixable? Does this sound like a reinstall call?

Looks like your HDD has got some damaged (bad) blocks after the bump; it happens sometimes. Here is a little test: Boot using a live CD, unmount your linux partition(s) and run the command ```
sudo badblocks -v /dev/sda1
``` This will run a READ-ONLY test on your partitions to check for physical damage. If any errors show up, post back here for instructions for a possible fix (which will require you to take a just-in-case backup).

Replace /dev/sda1 with your "/" and/or "/home" partition device ids. Ensure that they are both unmounted.

Reinstalling with unmarked badblocks may leave you worse off than you are currently.

---

### Post by dansan on 2008-08-06
Thank you and PmDematagoda for helpful pointers.

> **prshah said:**
> ... is a little test: Boot using a live CD, unmount your linux partition(s) and run the command ```
sudo badblocks -v /dev/sda1
``` 

I ran this test on the two partitions involved, but no bad blocks were reported. Then, when I rebooted later that afternoon, there were no problems.

So, things looked worse than they actually were, but I was very glad to learn about the bad blocks code and how to use it.

---


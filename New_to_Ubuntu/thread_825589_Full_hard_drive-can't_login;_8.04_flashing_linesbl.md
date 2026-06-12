---
title: "Full hard drive-can't login; 8.04 flashing lines/blacking out"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Erinn on 2008-06-11
Hi

Ok.. my pc no longer lets me log into Ubuntu. This is what happened, I guess. My hard drive was full, absolutely 100% full. Not realising this, I restarted, and after logging in it tells me I can't cos the drive is full. Nice. So I downloaded and installed 8.04 (previously was on 7.04) onto a different hard drive, and it worked fine, except for..there's green, purple, blue flashing lines al over the screen, everywhere, and every few seconds the screen goes black for a few seconds..becomes worse when I move the mouse. Only does this once I get to the splash screen, and only when I use 8.04. Any ideas? I'd really like to be able to access that full hard drive..and I really can't use 8.04 if it's like this. 

The plan was, by the way, to delete files from the old hard drive while on 8.04 to free up space, so I could then login. 

I'm stuck now :(

Thanks.

---

### Post by sherin on 2008-06-11
here are the options : 
1) try logging in in recovery mode ... 
2) use ubuntu live CD to boot the machine.  mount your hard disk and do the clean up

hope this helps

---

### Post by Najand on 2008-06-11
Push Ctrl+Alt+F1 and log into TTY1 and delete unneccessary files using rm command. If you are lucky, it is the easiest way to rescue yourself.

---

### Post by drascus on 2008-06-11
well if you can login under recovery mode use the command
> sudo apt-get clean

this will clean out packages that are left over in synaptic. and might give you some room. after that you can probably login and do the additional cleaning up graphically by saving some data on a removable drive or blank disks.

---

### Post by Erinn on 2008-06-11
Hi, thanks..

I tried just the live disk first, but I could barely see what I was doing in 8.04 and I couldn't delete files anyway, I didn't have permission? Had that problem in 7.04 for every other hard drive except the one it booted from.

Also, have tried recovery mode and it made no difference..tried to boot after a whole heap of command line stuff and then it just stopped.

:S

---


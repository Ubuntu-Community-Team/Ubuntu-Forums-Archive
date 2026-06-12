---
title: "dpkg was interrupted message"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by sranning on 2008-08-31
Hello. I am novice Mac user - very programing illiterate.I have now on a PC I cannot download software update or install new programs due to the following message.

E: dpkg was interrupted, you must manually run 'dpkg--configure-a 'to correct the problem.
E:_cache-> open() failed.Please report

I have been reading other forums and cannot figure out at all the very 1st thing to do. Please be very specific, as I need exact instructions for each step. 

Thanks very much in advance.

---

### Post by drs305 on 2008-08-31
Run in Terminal:
```
sudo dpkg --configure -a
```

It will ask for your password. As you type you won't see it but that is normal. Just type it in and hit ENTER.

Here's a tip. To open the terminal, go to the Main Menu, Accessories. Click and hold on 'Terminal' and drag it to the top panel and release. Now you will have a one-click shortcut to open a terminal any time you need it.

Added/edited: Command changed to add a space between dpkg and --configure. Interestingly, the original error message appears to also be missing the space, which I cut and pasted...

---

### Post by jemate18 on 2008-08-31
> **drs305 said:**
> Run in Terminal:
```
sudo dpkg--configure -a
```

It will ask for your password. As you type you won't see it but that is normal. Just type it in and hit ENTER.

1. Application -> Accessories -> Terminal
2. Um you have to put a "space betweein dpkg and --configure
type
```
sudo dpkg --configure -a

```
3. Enter your password upon the prompt

Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by sranning on 2008-08-31
Thanks,

That did work and allow me preform most of the updates. However I received the following error message


E: sun-java6-bin: subprocess post-installation script returned error exit status 134

---


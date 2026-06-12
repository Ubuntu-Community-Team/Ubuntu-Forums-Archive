---
title: "X won't start"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Sasansasan on 2008-05-08
I upgraded from 7.04 to 7.10 a few minutes ago and now X won't start ("Display Server has been shutdown 6 times in 90 seconds" or something to that effect).

I run Linux in a virtual machine (innotek VirtualBox) as I didn't feel like messing around with multiple partitions and have an ATI Mobility Radeon X1400 as my video card though I'm not sure whether the virtual machine uses this or some generic set of drivers.

Could anyone help me get X started up again?  Much thanks in advance.

---

### Post by tjwoosta on 2008-05-08
you say x wont start (can you at least get to the login menu?)

if you can get to the login screen there should be a small menu at the bottom left corner that will allow you to start in "safe graphics mode"

---

### Post by neurostu on 2008-05-08
if you don't get a login screen do you get a terminal log in?  what happens when you type:
```

startx

```
after you login to the terminal?

---

### Post by Sasansasan on 2008-05-08
> **neurostu said:**
> if you don't get a login screen do you get a terminal log in?  what happens when you type:
```

startx

```
after you login to the terminal?

I can start Ubuntu up in Recovery Mode where I can simply mess around with the console.  X keeps trying to restart itself in the "normal" mode so I can't get into the login screen.

At recovery mode, when I type "startx", it does exactly the same thing.

---

### Post by tjwoosta on 2008-05-08
this happened to me when i had gutsy 7.10

just get to a command line and do this

```

sudo dpkg-reconfigure xserver-xorg

```

as i understand this no longer works in hardy but you said you have 7.10 so it should work for you.

---

### Post by neurostu on 2008-05-08
Honestly I would recommend backing up your /home directory and then just doing a clean install of 7.1.

---

### Post by Sasansasan on 2008-05-08
Yeah, probably will, no fun though...

The configuration gave me a bunch of options I can't be bothered to fiddle with; thank goodness this is only a virtual machine.

---


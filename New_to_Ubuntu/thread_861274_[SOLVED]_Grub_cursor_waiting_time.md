---
title: "[SOLVED] Grub cursor waiting time"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by StephUb on 2008-07-16
Hi there,

First I apologize if a similar threat is around. I checked as much as i could to find it without success. (I found a bunch of threats about a waiting time in grub for the stage 1.5 loading).

My problem is:
Before I had winXP/Ubuntu Gusty and everything was working great.
I switch to Heron and now i have a Grub problem.
After the bios I got a cursor for 30 sec before he tells me loading stage 1.5 and the loading is pretty quick.

The only changes that i see are gutsy to heron and also i think it could be the freaking new grub editor I am using.
I will post the grub manager I use for more information if i got hnts that it could be it.

Thank you for your help

---

### Post by o.besner on 2008-07-16
I'm not sure I understand what you mean, but if you want to reduce the "wait time" until either ubuntu or windows boots from GRUB, here's how you do it. I'll use nano in this example, but any editor will do.

```
sudo nano /boot/grub/menu.lst
```

Now scroll a few lines down. You will see this entry :
> 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         2


on the timeout line, but the number of seconds you want before grub automatically launches your OS of choice.


Is this what you meant ?

---

### Post by StephUb on 2008-07-16
The program I am using for Grub management is QGRUBEditor.
I will try to reset it to default and unistall it to see if it fix the loading

---

### Post by StephUb on 2008-07-16
No, what i meant is that grub is in waiting time before loading 1.5 on my pc (30 sec):
The bios startup
i got a crusor for 30 35 sec before having the line grub loading stage 1.5

I did remove the QGRUBEditor.
The computer kept all the change that i made in the grub (default system and also splash image).
And I lost this lag of 30 seconds before stage 1.5 load.

So I think i found the fix myself but i prefer to put it here for my Ubuntu fellows.
I still don't understand why removing QGRUBEditor fixed it... :(

---


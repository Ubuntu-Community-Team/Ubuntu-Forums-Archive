---
title: "Booting to Kubuntu shows a bunch of text, driver problem?"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by garycheng12 on 2014-09-10
If I remember correctly, when I installed Kubuntu, it booted without displaying any text which seems to be about the booting process. I don't remember what I did since then (I'm new to Linux, trying to learn Kubuntu by tweaking and typing stuff on the terminal). Now I see a bunch of text and I don't see a pretty load screen. I don't necessarily want to change this (it would be interesting to learn what the text means), but I want to know what caused it to be like this and what I should do to be able to change between this and the screen with just the Kubuntu logo.

Thanks!

P.S. The driver manager on Kubuntu only shows the drivers for the graphics card and it doesn't even provide the most up-to-date driver from NVIDIA (although the latest one is only close to a month old). Still, I should get in the habit of installing the latest drivers so I did some googling and found out how to do that. How can I check whether I properly installed the driver? Going back to the driver manager I don't see the latest driver I installed being shown. Also, since the default Kubuntu settings don't even have the option to display the latest drivers for the graphics card, how can I install drivers of other hardware that makes up this laptop?

---

### Post by yancek on 2014-09-10
You could try the suggestion at the site below, easy enough to change and change back if it doesn't work.

[http://askubuntu.com/questions/248/how-can-i-show-or-hide-boot-messages-when-ubuntu-starts](http://askubuntu.com/questions/248/how-can-i-show-or-hide-boot-messages-when-ubuntu-starts)

---

### Post by SeijiSensei on 2014-09-10
I'd just use the NVIDIA driver from the repositories myself and not worry about how up-to-date it is.  Unless you have a bleeding-edge video card, it's unlikely that the driver at the NVIDIA site will perform any better than the one in the repositories.

Most of the text at boot is the system reporting that it has started services and the like.  Try typing 

```
dmesg | more
```

to see the messages generated during boot.  If you want to save them in a file for later review, use

```
dmesg > bootmsgs
```

to "pipe" the output into a file called "bootmsgs" in the current directory.

---

### Post by Vladlenin5000 on 2014-09-10
> **SeijiSensei said:**
> I'd just use the NVIDIA driver from the repositories myself and not worry about how up-to-date it is.  Unless you have a bleeding-edge video card, it's unlikely that the driver at the NVIDIA site will perform any better than the one in the repositories.

^^^
This. And the text you're noticing is an unfortunate side effect of the proprietary driver. It has no impact on your user session.

---

### Post by mastablasta on 2014-09-11
i don't know the NVidia, but in AMD there was a bug where Plymouth wouldn't show up on certain chips (even with opensource driver). there was a workaround. but I wouldn't worry too much. even with the nice screen the scrolling text is actually just hidden in the background (accessed by pressing Esc key).

as long as the PC boots ok the logo is not really an issue. but if it really bothers you you can troubleshoot it by searching solutions for Plymouth screen not loading. you could change the thread topic to one that reflects you issue better and while you are at it post output from :

cat /proc/cmdline

also you do not need to load all other drivers/latest and all that. usually if they are stable they are included in kernel. if you really have some device that was just launched you will need to upgrade to latest Linux kernel and get all new drivers. but you may run into some issue as well.

Arch Linux for example is a kind of rolling distribution that always has latest stuff installed or upgraded to. but you need ot know how to resolve the issues that will pop up... I don't really have time to deal with those...

---

### Post by garycheng12 on 2014-09-11
Ok, I'll just leave it alone. Thanks!

---

### Post by mastablasta on 2014-09-11
ahaha... actually it's usually an easy fix. I tried to find how I solved mine but can't find my thread where i got the solution from a forum member. there is a word or two to be added to grub startup command line. basically you just open a certain file, add two words and then save it.  however before doing that we would need to see your setup. or just leave it... who need those fancy screens anyway...

---


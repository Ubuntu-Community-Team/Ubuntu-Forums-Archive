---
title: "Is there a way to prevent reseating your hard drive?"
date: 2016-01-29
forum: New to Ubuntu
---

### Post by yves7 on 2016-01-29
Hi there, 

I have two operating systems on my laptop (Ubuntu & Windows). It happens a lot that Ubuntu gets stuck and that I just shut it down by pushing the power button.
When I want to start my computer it doesn't recognize the hard drive anymore in the BIOS- system information and when I run the diagnostics I get two types of logs: 

- computer shut down
- battery critically low

When I reseat my hard drive, it's all fixed (I can just start my computer).

 But is there a way to prevent doing this in the future? Is there a way to prevent Ubuntu from 'freezing'?
Is there a common cause for this pâttern that someone notices?


Thanks!

Cheers, 

Yves

---

### Post by SuperFreak on 2016-01-29
You should avoid using the power button to shut down your computer it can damage file systems. Try this instead:

to get into terminal  use :CTL ALT T 
Then ```
sudo poweroff
```

---

### Post by grahammechanical on 2016-01-29
What do you mean reseat the hard drive? I do not understand the word "reseat" in this context.

In the past I have had to use the power off button to shut down the machine as the Ubuntu shut down option did not actually power off the computer. But I have always been able to re-start the machine and load Ubuntu. When you power off the computer can you then switch it back on and load Ubuntu successfully?

The problem is not "reseating" the hard drive but Ubuntu freezing. And for that problem we need some more information. What version of Ubuntu? What are the hardware specifications? Is the user interface freezing or is it an application that freezes and does not respond.

I get applications freezing but I can still use the user interface to shut down. So, I know that it is not Ubuntu that is frozen. In my case I know why the two applications that I am using are freezing. One application is a word processor and the other lets me run an Android app on Linux and there is very little memory left out of my 1GB of RAM. And if I instruct both applications to do something at the same they freeze.

So, we need to know if it is Ubuntu that is freezing or the applications that are freezing. And the hardware specification is useful information. Are we putting loads in the OS that it cannot carry?

There is something we can do in these situations. We can press Ctrl+Alt+F1. That may get us to a Linux command line. We can log in and then run one or the other of these two commands.

To shut down

```
sudo shutdown -h now
```

to restart

```
sudo shutdown -r now
```

That should politely power off the machine.

Regards.

---

### Post by leclerc65 on 2016-01-29
Hold Alt & Sys Req keys then type
```

 R E I S U O (to turn off)
or 
 R E I S U B (to restart)

```

---

### Post by Habitual on 2016-01-29
> **yves7 said:**
> When I want to start my computer it doesn't recognize the hard drive anymore in the BIOS-
System Board battery. (CMOS/BIOS)

---

### Post by leunam12 on 2016-01-29
The fact the Ubuntu is stopping and then you have to reseat the HDD could be an indication that there is a hardware problem that is affecting your hard drive or the connector. As suggested above, I would replace the little coin-shaped battery that is inside the computer, and see if that fixes the problem. It may very well be a BIOS issue. It may be really easy or really hard to replace that battery depending on the computer. Another thing that I would do is check the hard drive for problems. Use the "Disks" application to check the S.M.A.R.T. data on the drive and if there are errors and bad sectors replace the drive. Sectors pending reallocation could be another indication of hard drive problems.

---

### Post by yves7 on 2016-01-30
Hi everyone, 

thanks for the comments! 

Today was the third time my laptop shut down (by just working on a powerpoint presentation in Windows).  When I checked the BIOS the hard drive wasn't detectable so I removed the hard drive from the laptop & plugged it back in (reseat). After doing this my laptop worked again.

When I checked the SMART data, it gave an end-to-end-error. 

Does anyone has a solution for this error except buying a new hard drive?

Cheers, 

Yves

---

### Post by kevdog on 2016-01-31
I've had many a hard drive fail on me unfortunately.  When the SMART system trips -- backup and replace.  The drive will work for a while, but then one day --- it will fail.  I was dumb once.  The SMART tripped and I kept using the drive for about 6 months, then with one reboot -- all kinds of corruption problems.  I was able to salvage some of the information of the drive with various tools, but what a waste of time that was.

---

### Post by leunam12 on 2016-02-01
Back up your data and replace the drive. You don't want to end up with an unmountable drive and a lot of lost data. Get an SSD if possible

---


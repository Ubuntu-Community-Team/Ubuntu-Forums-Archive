---
title: "strange behavior"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by fkil on 2012-02-22
I am in the process of trying out ubuntu, which is on a usb drive. Today several problems have popped up.
First of all I can't start the terminal anymore with Ctrl + Alt + T, although it worked fine yesterday. I have restarted the system several times already, but the command won't give me anything anymore.
Secondly the system was stuck today in a way that it was not possible anymore to shut down. I had to pull the powercable to get the system down. After that I was able to start up again.
Then there is that icon on the desktop with the text "Install Ubuntu 11.10." When the system is active long enough all characters of that text are mixed up and the original text is no longer readable.
And the last thing is the bar on the left of the screen. Sometimes it is completely hidden and it reappears when I move the mouse over it, which I suppose should be the correct behavior. But sometimes the bar stays visible whatever I try or do.
At this moment I don't think the system is as stable as was told to me. When this doesn't change I think I will keep Windows.
I use a Dell desktop with 2 Gb internal memory and 20 Gb free space.

Anyone with an idea what could be wrong?

---

### Post by roelforg on 2012-02-22
> **fkil said:**
> I am in the process of trying out ubuntu, which is on a usb drive. Today several problems have popped up.
First of all I can't start the terminal anymore with Ctrl + Alt + T, although it worked fine yesterday. I have restarted the system several times already, but the command won't give me anything anymore.
Secondly the system was stuck today in a way that it was not possible anymore to shut down. I had to pull the powercable to get the system down. After that I was able to start up again.
Then there is that icon on the desktop with the text "Install Ubuntu 11.10." When the system is active long enough all characters of that text are mixed up and the original text is no longer readable.
And the last thing is the bar on the left of the screen. Sometimes it is completely hidden and it reappears when I move the mouse over it, which I suppose should be the correct behavior. But sometimes the bar stays visible whatever I try or do.
At this moment I don't think the system is as stable as was told to me. When this doesn't change I think I will keep Windows.
I use a Dell desktop with 2 Gb internal memory and 20 Gb free space.

Anyone with an idea what could be wrong?

If you haven't used it much  yet; a reinstall might solve your problems.
Also, when ubuntu freezes, try this:
Press and hold ALT-PRTSC while pressing the following keys in this order (hold each key about 1 sec):
reisub

---

### Post by forrestcupp on 2012-02-22
It's hard to judge Ubuntu fairly from the Live USB instead of from a true installation. If you're not comfortable with installing it, you probably should stick with Windows. But I can tell you that there are a lot of people who have installed it without instability problems. On the right hardware, it's a pretty stable system, unless you're running a pre-release development version.

But the key is that Linux is still not smoothly compatible with every hardware combination out there. Without knowing what hardware you have, it's hard to help you see if it's compatible. If you post your computer's specs, product number, or hardware, you'll have a better chance of someone being able to help you out.

---

### Post by fkil on 2012-02-22
Thanks for your reply!

I think I will first burn a new LiveCd, but this time on a lower speed, maybe that will help.

My specs:
Dell Dimension 8400
Memory 2.5 GiB
Processor IntelPentium(R) 4 CPU 2.80 GHz
OS type 32 bit
Free disk space 20 GiB

---

### Post by roelforg on 2012-02-22
> **fkil said:**
> Thanks for your reply!

I think I will first burn a new LiveCd, but this time on a lower speed, maybe that will help.

My specs:
Dell Dimension 8400
Memory 2.5 GiB
Processor IntelPentium(R) 4 CPU 2.80 GHz
OS type 32 bit
Free disk space 20 GiB
Try using wubi, you can remove ubuntu again fairly easy that way whilst still experiencing the power because cd's/usb's are to slow.

---

### Post by forrestcupp on 2012-02-22
Does it have the Intel graphics. Intel graphics are pretty well supported. Since you have a little older system, if you don't have luck with Ubuntu, you might want to try out Xubuntu or Lubuntu. They're a little lighter on resources.

I'm not seeing anything that I know would have problems.

---

### Post by fkil on 2012-02-22
Thank you all for your suggestions.
First I am going to give Wubi a try. If that doesn't help I will probably switch to one of the ligther Ubuntu installations.

I will keep you informed!

---

### Post by grahammechanical on 2012-02-22
You do not tell us what changes to settings you have made in your testing of Ubuntu.

The Launcher (the bar on the left as you call it) can be set to automatically move out of sight or to stay on screen all the time. You might be using a version of Ubuntu where it can be set to dodge an open window as the window is moved to the left of the screen.

I doubt that this is a lack of stability. It could be down to a slow response because the operating system is running through a USB port off of a memory stick and not off of a much faster hard disk.

I have tested Edubuntu on a memory stick and found it to be very stable. So, I cannot agree with your assessment.

Regards.

---

### Post by d4m1r on 2012-02-22
> **fkil said:**
> Thanks for your reply!

I think I will first burn a new LiveCd, but this time on a lower speed, maybe that will help.

My specs:
Dell Dimension 8400
Memory 2.5 GiB
Processor IntelPentium(R) 4 CPU 2.80 GHz
OS type 32 bit
Free disk space 20 GiB


Your specs are more than enough for Ubuntu. If you already have a version of Windows installed, burn a Ubuntu installer CD (.iso download) and select the "install along side Windows" option when booting from the disk.

It will let you choose to boot into Windows or Ubuntu each time.

---

### Post by wildmanne39 on 2012-02-23
Hi, with your computer resources you would have better performance with lubuntu.

---

### Post by fkil on 2012-02-24
> **grahammechanical said:**
> You do not tell us what changes to settings you have made in your testing of Ubuntu.

The Launcher (the bar on the left as you call it) can be set to automatically move out of sight or to stay on screen all the time. You might be using a version of Ubuntu where it can be set to dodge an open window as the window is moved to the left of the screen.

I doubt that this is a lack of stability. It could be down to a slow response because the operating system is running through a USB port off of a memory stick and not off of a much faster hard disk.

I have tested Edubuntu on a memory stick and found it to be very stable. So, I cannot agree with your assessment.

Regards.

Ok, I have to admit that the strange behavior was not all due to an unstable system. I found out :oops: that during looking around I had made some changes to the system, because simply clicking these settings was sufficient to change them while I thought that I had to press some 'SAVE' button. 
Now I have installed the system with wubi and now everything goes much better, also because it still is an exciting learning process after using windows for at least 20 years.
Thanks to all of you for your remarks!

---

### Post by wildmanne39 on 2012-02-24
Hi, your welcome! I am glad it is working better.

You probably changed some settings in compiz.
Thanks

---


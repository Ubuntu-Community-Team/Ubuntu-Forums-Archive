---
title: "upgrading the kernal"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by AoFhEkOl on 2012-08-16
Hi, I would like some help upgrading the kernal on Ubuntu 12.04. My bios has a bug that blackscreens and restarts the laptop. 
 
I've tried updating the bios but it doesn't slove the problem...
 
Here is my old thread for info
[http://ubuntuforums.org/showthread.php?t=2036593](http://ubuntuforums.org/showthread.php?t=2036593)

---

### Post by AoFhEkOl on 2012-08-17
I tried downgrading the bios, but it didn't work. A piece of hardware must be broken :(. So.... I'm upgrading the kerel or......????

---

### Post by mlentink on 2012-08-17
Quickest way to test whether a newer kernel would have any effect is to [download]("http://http://cdimage.ubuntu.com/releases/12.10/alpha-3/") the Quantal Alpha, put it on a USB and boot from it. This does nothing to your current installation, but will allow you to see whether a newer kernel solves your problem.

---

### Post by AoFhEkOl on 2012-08-17
That download link doesn't work...

---

### Post by NikTh on 2012-08-17
Hi  , 

here is the working link 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Thanks

---

### Post by AoFhEkOl on 2012-08-17
Thanks

---

### Post by AoFhEkOl on 2012-08-19
Right then, i used the .iso from the link (x86) but it still black screened. What should i do next?

---

### Post by mlentink on 2012-08-19
Well, at least now you know that a kernel upgrade won't help you either, and it has cost you nothing. 
How are you so sure about
> My bios has a bug that blackscreens and restarts the laptop?
Have you e.g. tested memory?

---

### Post by AoFhEkOl on 2012-08-19
i have a link in this forum from another thread i started (first post), wildman told me so.  yep, tested ram etc

---

### Post by AoFhEkOl on 2012-08-19
There must be someone that can help me?

---

### Post by AoFhEkOl on 2012-08-20
Oh come on! Someone suggest something!

---

### Post by dodo3773 on 2012-08-20
Can you boot a livecd? Grad a livecd that has a text boot and see if that is the problem. Just see if they will boot that's all. Try and see if this boots up --> [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by AoFhEkOl on 2012-08-21
I'll give it a try. Ubuntu boots up, the problem is after 10 mins to an hour it will black screen and get stuck or restart.  I've been told it's a buggy bios, and there must be a solution to this. On windows i changed the processor driver and it works.

---

### Post by AoFhEkOl on 2012-08-21
Yes this boots, the same as windows safe mode and acpi=off boots (in ubuntu).  So it's a driver that's being loaded and it's causing this? Like in windows the solution was the processor driver.  

I'm new to ubuntu, well new to linux, so i don't have any idea how to trouble shoot this.  I was told by wildman (moderator) that i needed to start and new thread because i needed to upgrade the kernel. 

So.... i'm a bit stuck...

Start a new thread?

---

### Post by thomsebastin on 2012-08-21
> **Bowater said:**
> Yes this boots, the same as windows safe mode and acpi=off boots (in ubuntu).  So it's a driver that's being loaded and it's causing this? Like in windows the solution was the processor driver.  

I'm new to ubuntu, well new to linux, so i don't have any idea how to trouble shoot this.  I was told by wildman (moderator) that i needed to start and new thread because i needed to upgrade the kernel. 

So.... i'm a bit stuck...

Start a new thread?

have u tried an old live cd??perhaps an old kernal may work for u....just give it a try....or else may b the problem is with the bios in which case i think i don't know much.

---

### Post by AoFhEkOl on 2012-08-21
Ok, like a said before, the crashs/blackscreens/restarts were caused by the intel processor driver in windows, i changed the driver to processor driver which was listed in device manager. Below is what i dug up from an old thread of mine on sevenforums.

"Processor" has no sleep states or power management, the "Intel Processor" uses the intelppm driver and allows full power state management. If switching to a processor driver that doesn't allow sleep states "fixes" things, it's likely there's a hardware issue in one (or more) of the CPU cores or L1 caches at that point.

How can i implement this in ubunutu?

The weird thing is, in windows i can hibernate and sleep my computer which contradicts what i was told above...

---

### Post by AoFhEkOl on 2012-08-21
I will try this

[http://ubuntuforums.org/showthread.php?t=788276](http://ubuntuforums.org/showthread.php?t=788276)

---

### Post by AoFhEkOl on 2012-08-21
Ok, I tired and failed. Anybody know how to disable powermangement for the processors?

---


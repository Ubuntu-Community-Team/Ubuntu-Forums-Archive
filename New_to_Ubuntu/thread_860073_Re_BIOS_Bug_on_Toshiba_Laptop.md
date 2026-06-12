---
title: "Re: BIOS Bug on Toshiba Laptop"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Asuraw on 2008-07-15
Guys i am a newbie with Ubuntu cause i have been working windows for a long time and i was wondering if you could help me solve a problem of mine.I have a Toshiba laptop Satellite A75-S226 and i have installed ubuntu since then the BIOS bug 8254 has occurred.It suddenly closes my pc i dunno if its from the bug or whatever but i would to fix it cause i think thats what causing trouble for me. thnx for reading and i hope you could help me.

---

### Post by Sef on 2008-07-15
moved to absolute beginners.

---

### Post by lisati on 2008-07-15
What's BIOS bug 8254? Is that the warning that pops up when Ubuntu is starting? I get a message on my Toshiba A100 along those lines, but so far it hasn't caused any problems that I'm aware of......

---

### Post by bobnutfield on 2008-07-15
This bug is that the BIOS ACPI is not connected to the timer.  It have the same message, but it does not affect the operation of the operating system once it is booted.  There are many Google articles on this bug.

Bob

---

### Post by Asuraw on 2008-07-15
I have the feeling that it is somewhat affecting the system because i have also read somewhere else that it may cause some problems but rarely at that. I cant find why else the laptop in the middle of an operation would shut down.

---

### Post by bobnutfield on 2008-07-15
I could be wrong, but I doubt that it is related to this bug.  Many, many laptop users live with this but and it has been an issue in the Linux kernel for quite some time.  It could affect some operations like suspend and, as in my case, scrolling web pages can become choppy.  I have never known it to cause the effects described.  Sudden shut downs are more likely hardware related.

---

### Post by Asuraw on 2008-07-15
what would you advice me to do? Should i format my laptop and use a different operating system?

---

### Post by bobnutfield on 2008-07-15
No, I don't think it OS related.  What are you usually doing when it suddenly shuts down?

---

### Post by Asuraw on 2008-07-15
Well i usually have to wait for a couple of minutes cause it may open all the way and close when i input my username and code or it may not open at all.

---

### Post by bobnutfield on 2008-07-15
Do you get any error messages, or does it just suddenly turn off?  Does it shut down cleanly or does it just switch completely off?

---

### Post by Asuraw on 2008-07-15
No no i have encountered any error messages and almost every time it shuts down cleanly like i pressed the shut down button.

---

### Post by bobnutfield on 2008-07-15
Well, I have to alter my comment about it not being OS related, because that sounds like the init scripts are corrupt.  If you do not have too much stored on your computer, I would opt for a reinstall.  You can back up what you want to save, then just reinstall.

---

### Post by Asuraw on 2008-07-15
If that solves my problem i will gladly format my laptop thank you very much for your help and your time.

---

### Post by bobnutfield on 2008-07-15
My pleasure.  Don't give up on Ubuntu because of this problem.  Those in this forum can get you through just about anything.

Bob

---

### Post by Austin_KW on 2008-07-15
I have an A65 with the 8254 timer not connected to IO-APIC 'bug'. 
No ill effects at all.

The only sudden shutdown I have ever seen, on any distribution were heat related. On a restart after this happens are the fans on full blast.

Clean out the air flow path. Blow air through the reverse direction.

---

### Post by lisati on 2008-07-15
> **Asuraw said:**
> what would you advice me to do? Should i format my laptop and use a different operating system?

> **bobnutfield said:**
> No, I don't think it OS related. 


Asuraw: Don't give up too soon. I don't think the error message about the BIOS bug/timer is directly related to your problems with shutdown either. I've been using Ubuntu on a Toshiba A100 laptop and a Compaq desktop for over a year now. Both my machines show a similar error message with no obvious connection between the warning message and problems that occur. 

Most of the problems I've experienced have had more to do with messing up a setting somewhere, carelessness on my part,  or my not fully understanding what I was doing.

---


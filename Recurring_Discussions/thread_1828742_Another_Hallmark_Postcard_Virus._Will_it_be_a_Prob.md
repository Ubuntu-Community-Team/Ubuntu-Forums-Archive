---
title: "Another Hallmark Postcard Virus. Will it be a Problem on Linux?"
date: 2011-08-19
forum: Recurring Discussions
---

### Post by dniMretsaM on 2011-08-19
Just curious. My mom told me that there was a new Hallmark postcard virus discovered yesterday and told me that if I get the email to not open it and immediately shut down my computer. Wondering if this matters on a Linux machine. Also, how could it infect your computer if you don't open it? Any really smart people have some information?

---

### Post by eriktheblu on 2011-08-19
This might have been a concern if it were 2007, you were using a Windows machine that you did not update your OS.

---

### Post by CharlesA on 2011-08-19
It's been seen before. It's more of a problem with the browser (if the user clicks on the email) then the OS itself.

---

### Post by dniMretsaM on 2011-08-19
Ok thanks. A computer guru at my dads work said that's what you should do. I didn't think it was the best advise though. I figure you just delete the email and go on your way (enabling NoScript in advance couldn't hurt either).

---

### Post by Thewhistlingwind on 2011-08-19
Any "modern" web browser that does not have some sort of usable noscript style functionality is not feature complete.

With windows apparently moving to java/html5 this is only going to become more obvious in the future.

---

### Post by 3rdalbum on 2011-08-20
> **dniMretsaM said:**
> Just curious. My mom told me that there was a new Hallmark postcard virus discovered yesterday and told me that if I get the email to not open it and immediately shut down my computer. Wondering if this matters on a Linux machine. Also, how could it infect your computer if you don't open it? Any really smart people have some information?

Answer: If you don't open it, then its code does not get run and it doesn't actually "infect" your computer.

However, non-techie people seem to think computer viruses work almost biologically, as though they're a living organism that can act without their code ever going through the CPU. I mean, recently we had a poster here asking if the flashing insertion point in between his BIOS screen and GRUB meant that he had a virus. People don't really know what a virus is or how it works.

Theoretically, you could have a maliciously-crafted file that causes a buffer overflow as it's being downloaded, causing code to be put into an area of RAM that's likely to be executed in the near future. But it's not as widespread as you'd think.

---

### Post by jwbrase on 2011-08-21
> **dniMretsaM said:**
> Just curious. My mom told me that there was a new Hallmark postcard virus discovered yesterday and told me that if I get the email to not open it and immediately shut down my computer. Wondering if this matters on a Linux machine. Also, how could it infect your computer if you don't open it? Any really smart people have some information?

It can't infect your computer if you don't open it, and shutting down your computer is useless: It's either started running or it hasn't, and if it has, it's most likely already done damage.

A Windows virus won't run on a Linux machine unless you have Wine, and even then might not work properly. Unless you're stupid enough to run Wine as root there's no way it'll do damage to your system outside of your own user account (and may not even do damage outside your .wine directory, depending on how you have things set up).

---

### Post by Dangertux on 2011-08-21
> **Thewhistlingwind said:**
> Any "modern" web browser that does not have some sort of usable noscript style functionality is not feature complete.

With windows apparently moving to java/html5 this is only going to become more obvious in the future.

+1

I totally can't wait for cross application scripting attacks :-P

The hallmark postcard virus is an has been a hoak for a very long time. Either your mother is messing with you or someone is messing with her. 

[http://www.symantec.com/connect/blogs/virus-coming-tell-all-your-friends](http://www.symantec.com/connect/blogs/virus-coming-tell-all-your-friends)

---

### Post by dniMretsaM on 2011-08-21
> **Dangertux said:**
> +1

I totally can't wait for cross application scripting attacks :-P

The hallmark postcard virus is an has been a hoak for a very long time. Either your mother is messing with you or someone is messing with her. 

[http://www.symantec.com/connect/blogs/virus-coming-tell-all-your-friends](http://www.symantec.com/connect/blogs/virus-coming-tell-all-your-friends)

Well an IT guy at my dad's work told him and he sent my mom an email.

---

### Post by haqking on 2011-08-21
> **dniMretsaM said:**
> Well an IT guy at my dad's work told him and he sent my mom an email.

Sadly the world is full of IT guys and IT departments, IT professional does not a IT Security Professional make ;-)

Most IT professionals i know, who are very capable in IT in general and their respective areas of expertise know nothing about Security, or more to the point they know a little and that is often dangerous !

---

### Post by dniMretsaM on 2011-08-23
> **haqking said:**
> Sadly the world is full of IT guys and IT departments, IT professional does not a IT Security Professional make ;-)

Most IT professionals i know, who are very capable in IT in general and their respective areas of expertise know nothing about Security, or more to the point they know a little and that is often dangerous !

Very true. Very true.

---


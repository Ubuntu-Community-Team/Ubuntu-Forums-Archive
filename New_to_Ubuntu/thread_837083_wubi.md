---
title: "wubi"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by irishy on 2008-06-22
I really do struggle with pc's I had tried to install ubuntu with (wubi a program I had found on the ubuntu site) along side of xp and it seemed to work but a fault developed and the program crashed and I was not left with any alternatives because on screen was the message to press alt ctrl del as there was a fault and that was all I could get out of the pc so my option then was to format and reinstall xp so is there a method that will leave ubuntu and xp on seperate partitions so that this will not happen again 
thanks in anticipation

---

### Post by ex-wirecutter on 2008-06-22
Try [http://blog.briandicroce.com/2008/04/24/installing-linux-ubuntu-as-a-windows-application-with-wubi/](http://blog.briandicroce.com/2008/04/24/installing-linux-ubuntu-as-a-windows-application-with-wubi/)
It worked for me.

---

### Post by Paqman on 2008-06-22
> **irishy said:**
> is there a method that will leave ubuntu and xp on seperate partitions so that this will not happen again 


Downloading and burning the normal Ubuntu LiveCD and using it to install will do just that.

However, it sounds a bit strange that installing using Wubi destroyed your Windows partition. Can you provide a bit more info about what happened? What OS were you using when it crashed? When you rebooted when did you get the error message?

---

### Post by Bradtek on 2008-06-22
> **irishy said:**
>  so is there a method that will leave ubuntu and xp on seperate partitions 

Yes .....
The normal installation method does this.
(Wubi is not the normal way to install)

Boot from the Live CD 
Select Install
Once loaded, follow instructions.

(I'm sure there is an installation guide / how to around here somewhere)
Edit: here's one [http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

---

### Post by rockerphil on 2008-06-22
> **Paqman said:**
> Downloading and burning the normal Ubuntu LiveCD and using it to install will do just that.

However, it sounds a bit strange that installing using Wubi destroyed your Windows partition. Can you provide a bit more info about what happened? What OS were you using when it crashed? When you rebooted when did you get the error message?

my sister learned the hard way that hard booting from within a Wubi install can do some damage. it fried her MBR, so that could be the case, just a thought though

---

### Post by Paqman on 2008-06-22
> **rockerphil said:**
> my sister learned the hard way that hard booting from within a Wubi install can do some damage. it fried her MBR, so that could be the case, just a thought though

That's a shame. MBR borkage is fairly easily fixable though. I'm concerned that the OP said he had to reinstall Windows, which implies a much more serious problem.

---


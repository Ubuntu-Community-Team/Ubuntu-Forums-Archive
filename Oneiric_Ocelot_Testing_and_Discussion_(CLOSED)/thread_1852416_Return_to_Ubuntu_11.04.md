---
title: "Return to Ubuntu 11.04"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by amirfoad on 2011-09-30
Hi.
I have HP Mini 110 and after upgrading to Ubuntu 11.10 I'm really unsatisfied and angry of it.
The main problems are very slowdown speed of system in booting and running apps and also the wireless card (RT3090) which couldn't be recognized by 11.10.
I want to return my Ubuntu to 11.04 without new installation, because I want to have my installed programs.
Is there any way to do that?
Thank you.

---

### Post by lucazade on 2011-09-30
no, you can't.
and if the upgrade was the cause of your issues, a downgrade could be only worse.

---

### Post by amirfoad on 2011-09-30
Oh, so bad...!
OK, thanks.

---

### Post by ibutho on 2011-09-30
No, there is no easy way to go back unless you do a reinstall. When tinkering with test releases like 11.10 its better to test on a separate partition or in a virtual machine so that you do not mess up your production installation.

---

### Post by cmccauley on 2011-09-30
"I have HP Mini 110 and after upgrading to Ubuntu 11.10 I'm really unsatisfied and angry of it."

I'd be angry too if my computer spontaneously upgraded itself to a beta version of an unreleased OS. They really shouldn't be allowed to do that ;-)

---

### Post by amirfoad on 2011-09-30
:))

---

### Post by ft_ on 2011-09-30
your wireless driver is probably blacklisted in

/etc/modprobe.d

search it and remove it from blacklist-wireless file.

---

### Post by Rasa1111 on 2011-09-30
Hmm, I find just the opposite with 11.10, next to 11.04.
Everything is better in 11.10 over here. :)

Good luck

---

### Post by pkg9991 on 2011-09-30
> **Rasa1111 said:**
> Hmm, I find just the opposite with 11.10, next to 11.04.
Everything is better in 11.10 over here. :)

Good luck

true.. moreover try installing the latest updates today.. maybe some of the problems you're facing are already fixed

---

### Post by Rasa1111 on 2011-09-30
yeah todays updates rocked! :D

---


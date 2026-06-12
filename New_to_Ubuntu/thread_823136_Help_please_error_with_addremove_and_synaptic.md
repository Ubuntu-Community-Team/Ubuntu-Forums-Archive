---
title: "Help please: error with add/remove and synaptic"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by igorthrus on 2008-06-08
Hi, i am a completely new to linux and i got this error message when trying to add new programs:

E: Type '--22:54:27--' is not known on line 1 in source list /etc/apt/sources.list.d/mediabuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


can someone help me please

Thank you!

---

### Post by SunnyRabbiera on 2008-06-08
Alright first try sudo apt-get update in a terminal and see if any errors pop up

---

### Post by igorthrus on 2008-06-08
> **SunnyRabbiera said:**
> Alright first try sudo apt-get update in a terminal and see if any errors pop up

when i type this in it asks me for a password, but doesnt let me type anything....

---

### Post by mac9416 on 2008-06-08
Yuck, try gksudo apt-get update.

---

### Post by SunnyRabbiera on 2008-06-08
dont worry about that bit, just type in your password.
The password is hidden in the terminal, just type it out.

> **mac9416 said:**
> try gksudo apt-get update.

this command will also work if you are still not getting anything

---

### Post by Bubba64 on 2008-06-08
Sorry to interrupt your password doesn't show when you type it just type it and hit enter

---

### Post by SunnyRabbiera on 2008-06-08
> **Bubba64 said:**
> Sorry to interrupt your password doesn't show when you type it just type it and hit enter

correct, the entry of the password is hidden.

---

### Post by cariboo on 2008-06-08
Not echoing the password keeps people from shoulder surfing to get your password.

Jim

---

### Post by igorthrus on 2008-06-08
> **SunnyRabbiera said:**
> dont worry about that bit, just type in your password.
The password is hidden in the terminal, just type it out.



this command will also work if you are still not getting anything

ok, i typed my password and this is what i got:

aaron@aaron-linux:~$ sudo apt-get update
[sudo] password for aaron: 
E: Type '--22:54:27--' is not known on line 1 in source list /etc/apt/sources.list.d/mediabuntu.list

---

### Post by SunnyRabbiera on 2008-06-08
alright, now when adding medibuntu did you follow its instructions to the letter?

---

### Post by mac9416 on 2008-06-09
Hang on, the error says: E: "Type '--22:54:27--' is not known on line 1 in source list /etc/apt/sources.list.d/**media**buntu.list"
Shouldn't it say "medibuntu"?

Oh, and knock me over the head for not thinking about the non-echo thing. Duh.

---

### Post by igorthrus on 2008-06-09
> **SunnyRabbiera said:**
> alright, now when adding medibuntu did you follow its instructions to the letter?

ummm... i must have done something wrong because it didnt work and it did this.... do u know how i fix it?

---

### Post by SunnyRabbiera on 2008-06-09
well you can try to fix your sources lists, in a terminal I would just delete the bad sources list file by typing in sudo nautilus and making my way to /etc/apt/sources.list.d/mediabuntu.list
and just right clicking and deleting the thing.
then follow the instructions on how to use medibuntu again:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

ALWAYS remember to follow instructions on adding repositories, as you probably goofed something up.

---

### Post by igorthrus on 2008-06-09
> **SunnyRabbiera said:**
> well you can try to fix your sources lists, in a terminal I would just delete the bad sources list file by typing in sudo nautilus and making my way to /etc/apt/sources.list.d/mediabuntu.list
and just right clicking and deleting the thing.
then follow the instructions on how to use medibuntu again:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

ALWAYS remember to follow instructions on adding repositories, as you probably goofed something up.

cool, that worked, thanks a lot

---

### Post by SunnyRabbiera on 2008-06-09
No problem.
That is why we are here.
If you have more questions dont be afraid to ask.

---


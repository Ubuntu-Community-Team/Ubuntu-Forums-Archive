---
title: "Says my X86 is a AMD64?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by tropnevad on 2008-11-18
I tried to install skype.. it said that i have wrong architecture.. so i decided to try to use the force install option that i read about.. it also did not work due to depencancy problems.. but when it was running it said that my system is AMD64.. when i have a laptop that is running a intel core 2 duo.. very confusing.. is there any-way i can change this?

THanks in advance :)

---

### Post by lisati on 2008-11-18
About the best I can offer at the moment is that many of the "dual core" processors are capable of running in 64-bit mode.

Anyone else?

---

### Post by philinux on 2008-11-18
> **tropnevad said:**
> I tried to install skype.. it said that i have wrong architecture.. so i decided to try to use the force install option that i read about.. it also did not work due to depencancy problems.. but when it was running it said that my system is AMD64.. when i have a laptop that is running a intel core 2 duo.. very confusing.. is there any-way i can change this?

THanks in advance :)

You can check your install with

```
uname -m

```

---

### Post by Nepherte on 2008-11-18
AMD64 is sometimes used as a general term to indicate a 64bit architecture. It doesn't mean you have a amd processor. A Intel Core 2 Duo is 64bit, hence AMD64. Another (perhaps more correct) term to indicate 64bit is x86_64.

---

### Post by Sef on 2008-11-18
> AMD64 is sometimes used as a general term to indicate a 64bit architecture. It doesn't mean you have a amd processor. A Intel Core 2 Duo is 64bit, hence AMD64. Another (perhaps more correct) term to indicate 64bit is x86_64.

Because AMD came out with it first, the name is AMD64-bit.

---

### Post by 3rdalbum on 2008-11-18
Add the Medibuntu repository (instructions at [www.medibuntu.org](www.medibuntu.org)) and you'll find Skype there in your package manager, ready to install. Easy as pie.

---

### Post by biji on 2008-11-18
my Pentium dual core has 64bit support.. (only latest dual core version)

---

### Post by tropnevad on 2008-11-22
Is is better to run 64bit support for my dual core processor? i am just finding it annoying that most applications i cant install cuz they are not for 64bit..

Is there a way to change it back without the need for a re-install?, and if so is it recommended?,

---

### Post by igknighted on 2008-11-22
> **tropnevad said:**
> Is is better to run 64bit support for my dual core processor? i am just finding it annoying that most applications i cant install cuz they are not for 64bit..

Is there a way to change it back without the need for a re-install?, and if so is it recommended?,

64bit (AMD64) will use your processor to its fullest potential, but there are a few apps that can at times be problematic.

Anything can be made to work with 32bit without a lot of extra work, and it is very few things that are problematic.  Weigh this against the fact that the only way to "downgrade" to 32bit (x86) is to download a different CD and reinstall, and I think you will be better off with your current version.  There is a 64bit forum here, post any 64bit specific questions (like how to install skype, if you are still having issues) there, as you will get the best answers there.

---


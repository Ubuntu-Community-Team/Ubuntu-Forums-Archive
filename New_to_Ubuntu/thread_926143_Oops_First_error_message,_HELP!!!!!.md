---
title: "Oops First error message, HELP!!!!!"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by bootneck on 2008-09-21
Well it has happened I have broke it!!
I am running a Nvida Ge Force GT6800GTS video card and thought I would be clever and have a look at systems I went into Aperarances Preferences, visual effects and as the card is quite good I thought would download the Extra with the 3D, but all started well, then an error message came up and is as follows:-

E: dqkg was interrupted you must manualey run 'dqkg--config-a' to correct the problem.

E:_ cache-(V on its side)( ) failed, please report.

Boo Hoo now what do I do:confused:[-o< Now you can how techi I realy am:(

---

### Post by Vivaldi Gloria on 2008-09-21
Do what it says. Open a terminal and try

```
sudo dpkg --configure -a
```

---

### Post by ThrobbingBrain66 on 2008-09-21
Please run the following command in a terminal and post back if it does/doesn't fix your problem.
```
sudo dpkg --configure -a
```

---

### Post by bootneck on 2008-09-21
What is a terminal:confused: oh and by the way I found the error console in tools and I have hundreds of the little blighters:(

---

### Post by ThrobbingBrain66 on 2008-09-21
Sorry.

Go to Applications > Accessories > Terminal and type that code in.

---

### Post by bootneck on 2008-09-21
It tells me aplication not found

---

### Post by ThrobbingBrain66 on 2008-09-21
Could you please copy and paste the actual ouput (instead of just paraphrasing)?

---

### Post by bootneck on 2008-09-21
I am off to bed now as have to be up early for work and the wife is concerned that I have divorced her and married the PC:)

---

### Post by lisati on 2008-09-21
> **bootneck said:**
> I am off to bed now as have to be up early for work and the wife is concerned that I have divorced her and married the PC:)
Aaah, the wife thinks the computer is your second wife? I know that accusation well!

Sometimes "typos" can confuse things. 
Go to Applications->Accessories->Terminal, and type

```
sudo dpkg --configure -a
```
You can copy and paste this line, like you would with a word processor. Don't worry if it asks for your password and nothing appears when you type: this is a normal security precaution, just type in your password as usual.
If you then get an error message, use the "copy and paste" option to tell us about it. 

If you want to get really flash, put [noparse]> [/noparse] at the start of any error message in your reply, and [noparse][/noparse] at the end

---


---
title: "Where are the Programs?"
date: 2008-05-15
forum: Philippine Team
---

### Post by SHENGTON on 2008-05-15
Hi Ubuntu Experts!

Just wanna ask about the programs that are already installed in Ubuntu. In Windows all programs that are already installed are put in one folder "Program Files". Now my question is where are the programs placed?

Thanks and God bless!

---

### Post by Achetar on 2008-05-15
Most are in /usr/bin
Games are in /usr/share/games
Root-only ones are in /sbin and /usr/sbin

**DO NOT REMOVE PROGRAMS BY DIRECTLY DELETING THEM!!!!**

You need to use Synaptic (or apt-get) to remove them.

Synaptic is in the administration menu.

apt-get can be run using the following command.
```

sudo apt-get remove <package-name>

```

You can delete all configuration files for them as well by running:
```

sudo apt-get remove --purge <package-name>

```

You need to find the package name of a program in order to delete it. You can do that by search packages.ubuntu.com

One last word of advice, don't go overboard on the package downloads like I did when I started.

---

### Post by SHENGTON on 2008-05-15
Anong ibig mong sabihin dito Sir?

> Root-only ones are in /sbin and /usr/sbin

---

### Post by pendletone on 2008-05-15
> **SHENGTON said:**
> Anong ibig mong sabihin dito Sir?

Seeing that he's from Kentucky, I doubt he'll understand you. :)

Ang ibig nyang sabihin ng "root-only ones" ay yung mga programs na nagre-require ng administrative privileges (such as a root user) in order for it to run or make changes to your computer.

Hope that clarifies! :)

---

### Post by dodimar on 2008-05-15
Root-only ones are in /sbin and /usr/sbin

This are programs that can only be run by the "root" user.

*** Note:
   Bro, please check where the responder came from, Achetar is from USA, he might not be able to understand tagalog.

:guitar:


>>>>
hehehe, bagal mag click ng submit naunahan ako...

---

### Post by Achetar on 2008-05-15
OMGosh!!! This is in the Philippine Section??? How did that happen?

---

### Post by loell on 2008-05-15
> **Achetar said:**
> OMGosh!!! This is in the Philippine Section??? How did that happen?

in this side of the forum we are mostly bilingual  or multilingual , we speak english ,filipino and other local dialects in the mix :)

yeah a bit confusing for those who's wanting to help, but no worries someone will translate it for you , if you want. :D

---

### Post by SHENGTON on 2008-05-15
Sorry and thanks for the info experts!

---

### Post by ysNoi on 2008-06-16
So it is where the Programs are placed...! 
Nice information....! +1 info for Me..!
Thanks..!:guitar:

---


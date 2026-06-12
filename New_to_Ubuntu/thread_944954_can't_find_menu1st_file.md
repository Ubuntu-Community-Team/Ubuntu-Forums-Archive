---
title: "can't find menu1st file"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by terrylcozart on 2008-10-11
Hi guys,
A little background first. I am a Windows kinda guy. I understand most of it, but wanted to try a Linux OS and landed at Ubuntu. Loaded it onto 10 gigs of a partitioned 75 gig harddrive with XP the main OS. Loaded up and so far so good. I wanted to change the default OS to Windows (this is a family computer and Windows is all my wife knows and change is NOT a good thing). I print out the instructions from the A.B.T. forum, follow it to a T. "menu1st file not found" ???? What am I doing wrong? I will gladly admit my ignorance on Linux, but when I follow the instructions to the letter and it still doesn't work, I'm stumped. Oh yes one more thing. Type slow and simple. No answer is too stupid for me. Thanks a bunch!!!:)

---

### Post by jerome1232 on 2008-10-11
Just note it's a small letter L they can look similar on the forums font.

It is located at:
```
/boot/grub/menu.lst
```

---

### Post by jemate18 on 2008-10-11
where you able to find menu.lst?

if you want to view it in a console then

cat /boot/grub/menu.lst

if you want it in a text editor/GUI

gedit /boot/grub/menu.lst


to edit it, just append sudo

---

### Post by kansasnoob on 2008-10-12
> **terrylcozart said:**
> Hi guys,
A little background first. I am a Windows kinda guy. I understand most of it, but wanted to try a Linux OS and landed at Ubuntu. Loaded it onto 10 gigs of a partitioned 75 gig harddrive with XP the main OS. Loaded up and so far so good. I wanted to change the default OS to Windows (this is a family computer and Windows is all my wife knows and change is NOT a good thing). I print out the instructions from the A.B.T. forum, follow it to a T. "menu1st file not found" ???? What am I doing wrong? I will gladly admit my ignorance on Linux, but when I follow the instructions to the letter and it still doesn't work, I'm stumped. Oh yes one more thing. Type slow and simple. No answer is too stupid for me. Thanks a bunch!!!:)

A very simple way to do this with little fuss is just install startupmanager. It's in synaptic or go to terminal and:

```
sudo apt-get install startupmanager
```

You'll then see it in System > Administration > Startup Manager:

[ATTACH]88058[/ATTACH]

---

### Post by Keen101 on 2008-10-12
I do not recommend startupmanager for editing grub. Maybe for other things. But, not really for editing grub.

Your easiest way would be to copy and paste this into a terminal:

```
**sudo gedit /boot/grub/menu.lst**
```

oh, and note that **it is a lower case LETTER L**.

---

### Post by terrylcozart on 2008-10-12
> **Keen101 said:**
> 
oh, and note that **it is a lower case LETTER L**.

I think THIS is my problem. Thanks guys.:)

---

### Post by oldos2er on 2008-10-12
> **Keen101 said:**
> I do not recommend startupmanager for editing grub. Maybe for other things. But, not really for editing grub.

Your easiest way would be to copy and paste this into a terminal:

```
**sudo gedit /boot/grub/menu.lst**
```oh, and note that **it is a lower case LETTER L**.

 Use gksudo or gksu in place of sudo when calling up a graphical program.

---


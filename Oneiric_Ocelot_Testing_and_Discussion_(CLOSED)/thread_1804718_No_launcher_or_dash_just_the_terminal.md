---
title: "No launcher or dash just the terminal"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wildmanne39 on 2011-07-15
Hi, does anyone know how to fix having access to only the terminal after July 14th updates? Thanks for any help.

---

### Post by CaptainMark on 2011-07-15
ive not got this problem, do you have broken dependencies?, and have you tried an aptitude/apt-get update from the terminal

---

### Post by iClouseau88 on 2011-07-15
@wildmanne39:

I got the (same?) problem with July 15 alternate build: blinking cursor on a dark desktop.  Switching to July 15 daily-live build boots Ubuntu but no password window to login!

---

### Post by wildmanne39 on 2011-07-15
> **CaptainMark said:**
> ive not got this problem, do you have broken dependencies?, and have you tried an aptitude/apt-get update from the terminalHi, thank you for your reply yes I tried that but it is still the same, but I will figure it out.

---

### Post by mc4man on 2011-07-15
> **iClouseau88 said:**
> @wildmanne39:

I got the (same?) problem with July 15 alternate build: blinking cursor on a dark desktop.  Switching to July 15 daily-live build boots Ubuntu but no password window to login!

You could install and then switch to gdm or  - 
at login screen choose 'other'
type in your user name, click enter and you'll get a password box

Edit: I'd probably keep lightdm and do as above - gdm may have issues doing a logout/in after initial login, could hang at a blank screen, lightdm seems to be working ok after initial setup

---

### Post by wildmanne39 on 2011-07-18
Hi, I reinstalled and fixed this problem, now I can not boot at all but that is a different issue.

---


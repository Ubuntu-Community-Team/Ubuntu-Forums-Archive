---
title: "Screen resolution"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by VivNelson on 2012-12-31
Hi,

I have installed ubuntu 12.04 lts. I seem to have an issue with the screen resolution, in that it is too big, resulting in me not being able to see the login. I have googled this and seen solutions however as I am not technically minding I don't quite understand what to do. The instructions have been in computer commands. Just to add though I could not see all the login I was able to see enough to know I had to input my login details, however this morning as soon as I press the login it logs in to guest. ( Hope that makes sense)

Anyhow I have a RADEON X600/X550 series. It is setup to dual boot (windows XP professional - failed WGA).

I did have used Linux mint last year but that was on a different computer. 

Anyway, can you please advise in as simplified terms as possible as really I am a beginner and not at all technically minded.

Thanks in advance for your advice.
Viv

---

### Post by Otto-C on 2012-12-31
Not the permanent solution your looking for but:

ctrl + + (plus sign) will increase font
ctrl + - (minus sign will decrease font

repeat above as desired.

also

ctrl and moving scroll wheel forward increase font
ctrl and moving scroll wheel backward decrease font

hth

---

### Post by Bashing-om on 2012-12-31
VivNelson; Hi !

Try this to get an appropriate driver;
From the desk top bring up a Command Line Interface (terminal): press control+alt+t key combination.
In this terminal activate Additional Drivers utility:
```
jockey-gtk
```install the recommended driver.
Reboot to see the result:
```
sudo shutdown -h now
```The use of "sudo" requires your password, will get no response to the screen (security reasons).
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---


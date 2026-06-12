---
title: "[SOLVED] a battery status monitor"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by gagansinghjarry on 2008-09-28
i recently installed linux an my laptop and was not able to find a way to check your battery charge status and was also unable to find a way to change my display brightness or switch of my display when it was not needed i hope someone here could help me out with it:confused:

---

### Post by kjohansen on 2008-09-28
you can add a battery monitor by right clicking on a panel and selecting the battery monitor.

---

### Post by fooman on 2008-09-28
for battery status...right click on your panel > add to panel

highlight battery charge monitor and click "add"

---

### Post by Biggy on 2008-09-28
[Here]("http://ali.slackware.googlepages.com/") is a Battery Applet

---

### Post by gagansinghjarry on 2008-09-28
> **fooman said:**
> for battery status...right click on your panel > add to panel

highlight battery charge monitor and click "add"
yea i did as you said but it showed running on battery power 0 minutes and 0% left this was while i was plugged in and when i removed the cord it should have been at around 50 but no chang

---

### Post by gagansinghjarry on 2008-09-28
guys i really need your help

---

### Post by fooman on 2008-09-28
not sure,  but open synaptic (system > administration > synaptic package manager) and see if "laptop-detect" is installed.  it should be,  but if not...then try installing it.

---

### Post by gagansinghjarry on 2008-09-28
> **fooman said:**
> not sure,  but open synaptic (system > administration > synaptic package manager) and see if "laptop-detect" is installed.  it should be,  but if not...then try installing it.
yup it's installed anymore suggetions coz knowing laptop's battery status is very important to every laptop user

---

### Post by fooman on 2008-09-28
open a terminal and type the following into it,  then click enter:

```
acpi
```

what do you get?

---

### Post by gagansinghjarry on 2008-09-28
> **fooman said:**
> open a terminal and type the following into it,  then click enter:

```
acpi
```

what do you get?
sony@sony-laptop:~$ acpi
No ACPI support in kernel, or incorrect acpi_path ("/proc/acpi").

---

### Post by gagansinghjarry on 2008-09-28
thats what i got

---

### Post by fooman on 2008-09-28
hmmm,  what kernel are you running?  ...again in terminal,  type:

```
uname -r
```

whats the output of that command?

---

### Post by gagansinghjarry on 2008-09-28
> **fooman said:**
> hmmm,  what kernel are you running?  ...again in terminal,  type:

```
uname -r
```

whats the output of that command?
sony@sony-laptop:~$ uname -r
2.6.24-19-generic

---

### Post by fooman on 2008-09-28
back to synaptic...are acpi and acpi-support installed?

---

### Post by gagansinghjarry on 2008-09-28
> **fooman said:**
> back to synaptic...are acpi and acpi-support installed?
yup it's there 
and i am sorry for all the inconvineince i must be causing you guys

---

### Post by fooman on 2008-09-28
lol,  its no inconvenience....thats what the forums are here for! :) 

sorry i haven't been able to help...one more thing is the package "acpid"

i suppose thats already installed as well (if not then try it)?

i gotta run out for awhile...i am sure someone here will get you fixed up.

---

### Post by gagansinghjarry on 2008-09-28
> **fooman said:**
> lol,  its no inconvenience....thats what the forums are here for! :) 

sorry i haven't been able to help...one more thing is the package "acpid"

i suppose thats already installed as well (if not then try it)?

i gotta run out for awhile...i am sure someone here will get you fixed up.
yup acpid is also installed anyways thanks you've been great help and fast too

---

### Post by gagansinghjarry on 2008-09-28
> **gagansinghjarry said:**
> yup acpid is also installed anyways thanks you've been great help and fast too
back to ground zero

---

### Post by gagansinghjarry on 2008-09-28
maybe computer's do hate me

---

### Post by gagansinghjarry on 2008-09-28
isn't there like a fool's guide to linux i think i need one

---

### Post by gagansinghjarry on 2008-09-28
fuget it i am outta here to much for my brain to handel

---

### Post by fooman on 2008-09-28
not a fix but,  try

```
apm -v
```

in a terminal and whats the output?

---

### Post by gagansinghjarry on 2008-09-28
> **fooman said:**
> not a fix but,  try

```
apm -v
```

in a terminal and whats the output?
and just when all hope seemed lost along came a messenger from god i mean ubuntu 
ohh sorry forgot i am not supposed to be doing that here
anyways
here's what i got
sony@sony-laptop:~$ apm -v
The program 'apm' is currently not installed.  You can install it by typing:
sudo apt-get install apmd
bash: apm: command not found

---

### Post by gagansinghjarry on 2008-09-28
people say linux is not user friendly dat's not true linux is user friendly it's just not idot friendly artificial intelligence is no match for natural stupidity

---

### Post by gagansinghjarry on 2008-09-28
or maybe it's just a lil choosy about it's friend's anyways anyone here going to answer me except that poor guy whom i have been bothering for over and hour

---

### Post by gagansinghjarry on 2008-09-28
or maybe it's just a lil choosy about it's friend's anyways anyone here going to answer me except that poor guy whom i have been bothering for over and hour

---

### Post by gagansinghjarry on 2008-09-28
alright fella's i think i'd better get going now got a big day tommorow good night every one

---


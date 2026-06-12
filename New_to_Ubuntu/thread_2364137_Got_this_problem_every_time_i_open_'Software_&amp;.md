---
title: "Got this problem every time i open 'Software &amp; Updates'"
date: 2017-06-19
forum: New to Ubuntu
---

### Post by mac187 on 2017-06-19
Every time i open 'Software & Updates' i got this message everytime i click on 'Addictional drivers' tab section

Anubody know how to solve it ?

Thank a lot for help

---

### Post by mac187 on 2017-06-19
Did anyone see the picture ? Or do i need to upload it again?

---

### Post by kc1di on 2017-06-19
can't open the thumbnail here.

---

### Post by deadflowr on 2017-06-19
Unfortunately attachments are temporarily broken (hopefully it's only temporary)
See: [https://ubuntuforums.org/showthread.php?t=2363943]("https://ubuntuforums.org/showthread.php?t=2363943")

With that the preferred option to try and use an image hosting site, or if the image is small enough using the forum insert image tool.
 
But from a very far glance, as I see the attachment is there but cannot actually view it, I see it looks like a crash report, maybe.
Is it?

---

### Post by mac187 on 2017-06-19
i can post the picture again

---

### Post by mac187 on 2017-06-19
man im new to this, but everytime i open 'Software & Updates' and i go to 'Addictional drivers' tab section i got crash report like this :

ExecutablePath
   /usr/bin/software-properties-gtk
PorblemType
   Crash
TraceBack
   Traceback (most revent call last):
   File "/usr/lib/phyton3/dist-pacakge/apt/cache.py", line 194, in __getitem_


bla bla..

---

### Post by deadflowr on 2017-06-19
Try updating through the terminal to see if doing so helps fix it.
run
```
sudo apt update
```
and then run
```
sudo apt full-upgrade
```
post the output if it seems odd to you.

---

### Post by mac187 on 2017-06-19
ahh it help ! thank you ! 

i use to do

sudo apt-get upgrade

is better to take this -> sudo apt-get full-upgrade ?


and btw, wich option should i dont mark on Bleachbit, cus everytime i run it, i got the message again, and when i do what u said it dosent happen, so its something i have marked on bleachbit that cause that problem

---

### Post by deadflowr on 2017-06-19
> **mac187 said:**
> ahh it help ! thank you ! 

i use to do

sudo apt-get upgrade

is better to take this -> sudo apt-get full-upgrade ?


and btw, wich option should i dont mark on Bleachbit, cus everytime i run it, i got the message again, and when i do what u said it dosent happen, so its something i have marked on bleachbit that cause that problem

apt-get and apt are two different utilities.
apt-get is more commonly referred to, as apt is a newer utility.
see man apt and man apt-get for basics.
per those
man apt-get (upgrade):

 ```
upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

```

man apt (upgrade/full-upgrade)
 ```
upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. New package will be installed, but existing
           package will never removed.

       full-upgrade
           full-upgrade performs the function of upgrade but may also remove
           installed packages if that is required in order to resolve a
           package conflict.

```

Sorry, I don't use bleachbit, so cannot help with whatever you do with it.

---

### Post by monkeybrain20122 on 2017-06-19
I run bleachbit, never have any error message. In "run bleachbit as administrator" I unmarked:

APT > package lists (since sudo apt update will regenerate it anyway)

Deep scan

System >  custom

System >  Free disk space

System > memory

---

### Post by mac187 on 2017-06-19
Thanx ! This helped me a lot :D

---

### Post by kc1di on 2017-06-19
bleach bit is a good tool. I like ubuntu-cleaner also and it seems a little safer than bleachbit to me. 
you may want to give it a try.  you can install it via their ppa [here.]("http://www.omgubuntu.co.uk/2016/12/free-space-ubuntu-cleaner-janitor-app")

---

### Post by mac187 on 2017-06-19
Thanx for the gelp guys ! My first time using linux, i am a Programming student, just finish my first year :)

---


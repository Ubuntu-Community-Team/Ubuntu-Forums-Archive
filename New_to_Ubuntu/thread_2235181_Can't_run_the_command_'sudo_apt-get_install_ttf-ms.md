---
title: "Can't run the command 'sudo apt-get install ttf-mscorefonts-installer' in terminal."
date: 2014-07-19
forum: New to Ubuntu
---

### Post by Landen on 2014-07-19
So, I wanted to install Microsoft TrueType Core Fonts. However, the software center installation failed, so I resorted to using the terminal. The first time it worked fine, but I got stuck when I had to accept the terms and conditions (I didn't know I had to use the tab key to accept). When I tried again, it threw me this error: 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

So... Help? Or is there any other way I can get windows fonts?

---

### Post by steeldriver on 2014-07-19
Hello and welcome to the forums 

It *may* be sufficient to open a terminal (Ctrl-Alt-t) and then reconfigure the specific package

```

sudo dpkg-reconfigure ttf-mscorefonts-installer

```

which should pop up the EULA again - if that doesn't work, then take the installer's advice and run

```

sudo dpkg --configure -a

```

---

### Post by grahammechanical on 2014-07-19
Have you run?

```
sudo dpkg --configure -a
```

Did it suggest a single hyphen or a double hyphen? You show a single hyphen. Using the single hyphen will give this

> dpkg: error: unknown option -o

Regards.

---

### Post by Landen on 2014-07-20
Hello,

Running "sudo dpkg --configure -a" gave me this error: Error: dkpg status database is locked by another process.
Running "sudo dpkg-reconfigure ttf-mscorefonts-installer" gave me this: /usr/sbin/dpkg-reconfigure: ttf-mscorefonts-installer is broken or not fully installed

So... Now what?

---

### Post by steeldriver on 2014-07-20
Do/did you have another package manager open (Software Center, or Synaptic) when you tried the first command? if so, make sure they are closed first

---

### Post by Landen on 2014-07-22
I made sure I didn't have software center or anything else open. This time, running "sudo dkpg --configure -a" gave me nothing in return.

---

### Post by steeldriver on 2014-07-22
What does

```

dpkg -l ttf-mscorefonts-installer

```

say now? Are you now able to run 

```

sudo dpkg-reconfigure ttf-mscorefonts-installer

```

---

### Post by Landen on 2014-07-22
Alright, I fixed the problem!
Turns out this command worked: sudo dpkg -i --force-overwrite /var/cache/apt/archives/ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb
Thanks for your help, guys.

---


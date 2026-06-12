---
title: "skype on 64 bit"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by jsabina1 on 2013-03-08
Hi everybody
new on this forum.
I've installed yesterda Lubuntu on a quite old laptop (2gb of ram) with 64bit amd processor.
I cannot install skype.
If I download it from the website if fails saying that the architecture is wrong (even if on the website they wrote multiarch, when I download it it's called 32..)
If I try with apt-get it gives me error regarding skype-bin that doesn't exists..

---

### Post by Bucky Ball on 2013-03-08
Which release of Ubuntu are you using? Have you tried from Synaptic Package Manager or Software Centre?

Also, run these two commands in a terminal then give it another shot:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by gifford on 2013-03-08
Yes, try installing from Synaptic or Software center.

---

### Post by gordintoronto on 2013-03-09
"even if on the website they wrote multiarch, when I download it it's called 32." What????

Run Synaptic, install multiarch, install Skype. Works perfectly.

---

### Post by fantab on 2013-03-09
You have enable "**Cannonical Partners**" and "**Independent**" repositories to be able to install Skype and a lot other applications from Ubuntu Software Center or **Synaptic Package Manager**. These repositories are not enabled by default. I would recommend that you install and use Synaptic; you can install it from Software Center or the Terminal.

To install Synaptic from Terminal:

```
$ sudo apt-get update
$ sudo apt-get install synaptic
```

After installing and opening Synaptic navigate to **Settings -> Repositories** and select "**Canonical Partners**" and **"Independent**". After that you have to "**Reload**" from Synaptic. Then search for Skype and Install it.

Skype is not available as 64bit for Linux, so we have to install 32bit with the required libraries and dependencies to run it in a 64bit Linux. Synaptic Package Manager will take care of all that for you.

---

### Post by jsabina1 on 2013-03-09
Thanks for all the answers.
Synaptic was installed and yes it gave me the error for the architecture and skype-bin not installed.
Anyway I've solved in this way:

```

sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get -f upgrade
sudo apt-get install skype






```

I suppose that in this way ubuntu can use also the 32bit version of the applications?
Anyway it works.. thanks a lot..
now moving to the next problem... microphone not working :P I will open a thread if I am not able to fix it :P

---

### Post by Bucky Ball on 2013-03-10
> **jsabina1 said:**
> 
now moving to the next problem... microphone not working :P I will open a thread if I am not able to fix it :P

Good plan. I have marked this thread as solved for you as the regular method of marking as solved is currently not available due to the forum upgrade.

Good luck.

---

### Post by nassah on 2013-04-07
[QUOTE=jsabina1;12549123]
Anyway I've solved in this way:

```

sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get -f upgrade
sudo apt-get install skype






```

This solved it for me too, Ubuntu 12.10 64-bit. Thanks

---


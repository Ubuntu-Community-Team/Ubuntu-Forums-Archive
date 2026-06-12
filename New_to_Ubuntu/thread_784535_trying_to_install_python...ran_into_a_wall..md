---
title: "trying to install python...ran into a wall."
date: 2008-05-06
forum: New to Ubuntu
---

### Post by fignig on 2008-05-06
trying to do the install. i already did the ./config and make and i was trying to do the make install command and this came up:

pete@pete:~/Desktop/Python-2.5.2$ make install
/usr/bin/install -c python /usr/local/bin/python2.5
/usr/bin/install: cannot create regular file `/usr/local/bin/python2.5': Permission denied
make: *** [altbininstall] Error 1


can someone help me on what i did wrong?

---

### Post by Krumar on 2008-05-06
You shouldn't need to install python. python 2.5 comes with the ubuntu distro. just type python at command line and it will put you in the python interpreter.

---

### Post by Tatty on 2008-05-06
python 2.5 is installed by default in ubuntu hardy - have a look in synaptic if you arent sure.  If you dont have it installed for some reason do:

```
sudo apt-get install python2.5
```



And for future reference the problem you were having with compiling it was due to you not having superuser powers  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by luisromangz on 2008-05-06
You need to use sudo to be able to install a program in a system wide fashion.

Use:

sudo make install

First, run make without su privileges, and the the install.

By the way, why are you compiling python? There are packages in the repositories...

---

### Post by Steveway on 2008-05-06
1. Python comes preinstalled on most Linux-systems, you allready have it! Just type python into a terminal and voila the interactive python-shell opens.
2. On most Linux-system you don't install by downloading applications from webpages and then somehow installing them. We have so called package-managers. Look into your menu and select Synaptic then it will ask for your password and then you can search for specific programs or just browse through the avaiable ones.
3. If you want to learn a programming-language then you should have some basic knowledge about your system or at least you should be able to figure such essential things out for yourself.
Good luck with your Python-adventure, it is worth it if you stick to it.

---

### Post by fignig on 2008-05-06
> **Steveway said:**
> 1. Python comes preinstalled on most Linux-systems, you allready have it! Just type python into a terminal and voila the interactive python-shell opens.
2. On most Linux-system you don't install by downloading applications from webpages and then somehow installing them. We have so called package-managers. Look into your menu and select Synaptic then it will ask for your password and then you can search for specific programs or just browse through the avaiable ones.
3. If you want to learn a programming-language then you should have some basic knowledge about your system or at least you should be able to figure such essential things out for yourself.
Good luck with your Python-adventure, it is worth it if you stick to it.

yeah i know. i need to learn more about the linux, but i know windows in and out. so i didn't think switching would be that big of a problem. and python i hear is the easiest to learn, so i'm gonna try it.

---

### Post by Krumar on 2008-05-06
I've played around with python some myself it is really easy to use and you'll pick it up fast. Don't worry about not knowing python came preinstalled, I didn't know untill i went to the python site and read that it came on most linux oses. Just don't give up on linux, after you get over a few problems with the switch you'll really end up liking it a lot.

---

### Post by fignig on 2008-05-07
> **Krumar said:**
> I've played around with python some myself it is really easy to use and you'll pick it up fast. Don't worry about not knowing python came preinstalled, I didn't know untill i went to the python site and read that it came on most linux oses. Just don't give up on linux, after you get over a few problems with the switch you'll really end up liking it a lot.

i've had ubuntu for about 4-5 days now, and i'm never turning back to microsoft.

---


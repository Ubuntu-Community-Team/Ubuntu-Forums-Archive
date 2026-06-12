---
title: "Terminal wont open"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by ivan128 on 2016-05-26
my update wont work, and terminal wont open... i took some screenshots... anyone have solution???

---

### Post by cariboo on 2016-05-26
Can you get to a console by pressing Ctrl-Alt-F1?

---

### Post by ivan128 on 2016-05-26
yes i can...

---

### Post by bearlake on 2016-05-27
Now you made it to a console and logged in ( I hope ), try these commands.

> sudo apt-get update && sudo apt-get upgrade

Report any errors and if no errors, try a fresh boot after the updates.

---

### Post by QDR06VV9 on 2016-05-27
From a TTY or terminal with Ctrl-Alt-F1
Try this To reset the configuration run this:

```
dconf reset -f /org/compiz/
```

Then, to reset unity run:

```
setsid unity
```
Let us know.
Kind Regards

---

### Post by ivan128 on 2016-05-27
> **bearlake said:**
> Now you made it to a console and logged in ( I hope ), try these commands.



Report any errors and if no errors, try a fresh boot after the updates.


Didnt install any update... it say everything is up to date... so... it is the same... :(

---

### Post by ivan128 on 2016-05-27
> **runrickus said:**
> From a TTY or terminal with Ctrl-Alt-F1
Try this To reset the configuration run this:

```
dconf reset -f /org/compiz/
```

Than, to reset unity run:

```
setsid unity
```
Let us know.
Kind Regards

i have error doing this... -bash /usr/lib/comand-not-found: /usr/bin/python3: bad intrepeter: No such file in directory

---

### Post by QDR06VV9 on 2016-05-27
Yuck! That's not good. 
Sounds like something maybe you were trying to install may have mucked up the system. try this command.
```
gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window true
```

---

### Post by ivan128 on 2016-05-27
> **runrickus said:**
> Yuck! That's not good. 
Sounds like something maybe you were trying to install may have mucked up the system. try this command.
```
gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window true
```


i installed python 3.5.0 ... and... that i gues was a bad choise

when i tipe this i get error: failed to commit changes to dconf :( 

I gues reinstall Ubuntu is on the way... :(

---

### Post by QDR06VV9 on 2016-05-27
I am very sorry to hear that also.but is there a reason you need to have python 3.5... won't python 3.4 work for you.

---

### Post by Impavidus on 2016-05-28
Isn't python 3.5 supposed to be installed by default on Ubuntu 16.04? Alongside python 2.7 that is. And have you got Ubuntu 16.04?```
$ python3 --version
Python 3.5.1+

$ python --version
Python 2.7.11+

$ which python3
/usr/bin/python3

$ ls -l /usr/bin/python3
lrwxrwxrwx 1 root root 9 mrt 23 11:00 /usr/bin/python3 -> python3.5

$ dpkg --search /usr/bin/python3
python3-minimal: /usr/bin/python3

```
Maybe you need to reinstall python3-minimal.

---

### Post by ivan128 on 2016-05-28
> **runrickus said:**
> I am very sorry to hear that also.but is there a reason you need to have python 3.5... won't python 3.4 work for you.

well there was no spec reason... just wanted to see whats new in python 3.5 

Ty anyway :)

> **Impavidus said:**
> Isn't python 3.5 supposed to be installed by default on Ubuntu 16.04? Alongside python 2.7 that is. And have you got Ubuntu 16.04?```
$ python3 --version
Python 3.5.1+

$ python --version
Python 2.7.11+

$ which python3
/usr/bin/python3

$ ls -l /usr/bin/python3
lrwxrwxrwx 1 root root 9 mrt 23 11:00 /usr/bin/python3 -> python3.5

$ dpkg --search /usr/bin/python3
python3-minimal: /usr/bin/python3

```
Maybe you need to reinstall python3-minimal.

which python3
 no such file in directory ...

---

### Post by ivan128 on 2016-05-28
i reinstalled system, thank you all for the help :)

---


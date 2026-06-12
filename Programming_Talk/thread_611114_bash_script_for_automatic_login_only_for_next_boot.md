---
title: "bash script for automatic login only for next boot...."
date: 2007-11-12
forum: Programming Talk
---

### Post by pierissimo on 2007-11-12
HI!!!
I would create a script to login a user automatically only at  next boot...
Unfortunately i don't know bash, but however I have some ideas.
I would also that this script take a parameter, that is the name of the user to autologin.
In the file /etc/gdm/gdm.conf-custom there is the entry regards automatic login:

```
[daemon]

RemoteGreeter=/usr/lib/gdm/gdmgreeter

AutomaticLoginEnable=true

AutomaticLogin=piero
```


I thought something like this:
```

if ${0}== "tizio" then 

mv /etc/gdm/gdm.conf-custom /etc/gdm/gdm.conf-custom.bak
mv /etc/gdm/gdm.conf-custom.piero /etc/gdm.conf-custom      //the gdm.conf-custom will be configurated to allow automatic login to the user "piero"

//there will be the code for insert in /etc/init.d/rc.local the instructions to restore original gdm.conf-custom file.

```
It' symple but could work....
help for bash programming?
thanx

---

### Post by pierissimo on 2007-11-14
up

---

### Post by pierissimo on 2007-11-21
up!

---

### Post by soluphobe on 2007-11-21
I don't know bash either (much), but have you considered this?  Put a file on your desktop, then put a value in it (say, 1).  In your script, check the contents of the file, and if they equal a certain value log the user Piero in.

---

### Post by pierissimo on 2009-02-15
I exhumed this old post!
I created this script long time ago:
here's the script:
[http://pierissimo.ilbello.com/blog/?p=30](http://pierissimo.ilbello.com/blog/?p=30)

---


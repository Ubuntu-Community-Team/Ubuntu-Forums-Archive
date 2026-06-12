---
title: "Autlogin without GDM"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by skymera on 2008-08-27
Hi i use autologin to save time and have removed GDM.

How do i get Ubuntu to autologin to Gnome without the use of GDM?

i did read putting this

```
 
if [ -z "$DISPLAY" ] && [ $(tty) = /dev/tty1 ]; then
while true
do
startx --
sleep 5
done
fi

```

into my ~/.profile file auto logs in to Gnome. It does but it means i have to login to TTY1 for it to do so which totally ruined the reason of an autologin xD

So how do i autologin to Gnome without GDM?

---

### Post by pyromanic123boom on 2008-08-28
First set up an autologin in an easier way.

> click on System -> Administration -> Login Window 
Change to the Security tab.
Enable the checkbox for Enable Automatic Login
Select your user account from the drop-down list of users. 


And then I'd think you'd just uninstall gdm..

```

sudo apt-get remove gdm

```

---

### Post by aysiu on 2008-08-28
> **pyromanic123boom said:**
> First set up an autologin in an easier way.



And then I'd think you'd just uninstall gdm..

```

sudo apt-get remove gdm

```
That doesn't work. System > Administration > Login Window is otherwise known as ```
gksu gdmsetup
``` It's the graphical configuration for GDM. If you remove GDM, none of those settings will apply.

---

### Post by fbnaia on 2008-08-28
I use rungetty to do a autologin... you have to change a few lines in /etc/event.d/tty1

mine looks like this:

fbnaia@famini:/etc/event.d$ cat tty1
```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/rungetty --autologin fbnaia tty1
```

that will autologin user fbnaia, change username as appropiate

and on .bashrc in my home dir i have:

pgrep X &>/dev/null; [ $? = 1 ] && startx

to start the x server.

---

### Post by Vivaldi Gloria on 2008-08-28
> **fbnaia said:**
> I use rungetty to do a autologin

Hmm. I didn't know about rungetty. Good find there. I'll try it next time.

You can also use getty to autologin:

**1)** Create a file 

```
/usr/sbin/autologin 
```

which is as follows:

```
#! /bin/bash
exec login <your_username>
```

Replace <your_username> with the name of the user you want to login automatically. Then make that file executable via

```
sudo chmod a+x /usr/sbin/autologin
```


**2)** Edit the file 

```
/etc/event.d/tty1 
```

and change the line

```
exec /sbin/getty 38400 tty1
```

to

```
exec /sbin/getty -l /usr/sbin/autologin -n 38400 tty1
```

---

### Post by skymera on 2008-08-28
Thanks for the replies :)

I'll try later, on my laptop on the moment.

---

### Post by Lockheed on 2009-09-04
> **Vivaldi Gloria said:**
> Hmm. I didn't know about rungetty. Good find there. I'll try it next time.

You can also use getty to autologin:

**1)** Create a file 

```
/usr/sbin/autologin 
```

which is as follows:

```
#! /bin/bash
exec login <your_username>
```

Replace <your_username> with the name of the user you want to login automatically. Then make that file executable via

```
sudo chmod a+x /usr/sbin/autologin
```


**2)** Edit the file 

```
/etc/event.d/tty1 
```

and change the line

```
exec /sbin/getty 38400 tty1
```

to

```
exec /sbin/getty -l /usr/sbin/autologin -n 38400 tty1
```

That didn't work for me.
I followed this method and then removed GDM. Now, the system bootsup to command line and asks me for password. Once I enter it, I then need to type startx.

How is this autologin if I need to type two commands before getting to the desktop?

---

### Post by kerry_s on 2009-09-04
that's from 2008, things have changed, with policykit you really need to use a login manager or policykit will deny you access to just about everything.

---

### Post by Lockheed on 2009-09-04
Well. Are there any lightweight login managers with autologin option?

---

### Post by kerry_s on 2009-09-04
i would say slim, but i don't think it has auto login.
gdm is not that heavy, you can use it & cut corners elsewhere.

---

### Post by k33bz on 2009-09-04
Remove gdm as mentioned above then in /etc/rc.local write:
```
su - username -c startx
```

---

### Post by k33bz on 2009-09-05
> **kerry_s said:**
> i would say slim, but i don't think it has auto login.
gdm is not that heavy, you can use it & cut corners elsewhere.

Slim does have a auto-login feature, you just have to edit slim.conf.


Configure /etc/slim.conf (uncomment the corresponding lines)
-> default_user username
-> auto_login yes

you will need to add the auto_login feature right after default_user name

---

### Post by kerry_s on 2009-09-05
> **k33bz said:**
> Slim does have a auto-login feature, you just have to edit slim.conf.


Configure /etc/slim.conf (uncomment the corresponding lines)
-> default_user username
-> auto_login yes

you will need to add the auto_login feature right after default_user name

thats great, i knew it was talked about, just didn't know when it was going to be done. i'll have to try slim on my next custom install. :D

---

### Post by cimh on 2009-11-24
>>
default_user username
auto_login yes
<<

Can someone confirm that this works - I have seen it mentioned in one or two places but it doesnt work for me and there is no mention of it in the slim manual.

If anyone has found it works - is it faster than gdm. Without autologin I have a feeling that slim is taking quite a bit longer in karmic than gdm

cimh
eee 901 karmic+lxde

---


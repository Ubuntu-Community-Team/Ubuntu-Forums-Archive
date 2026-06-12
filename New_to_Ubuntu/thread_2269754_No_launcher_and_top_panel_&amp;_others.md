---
title: "No launcher and top panel &amp; others"
date: 2015-03-17
forum: New to Ubuntu
---

### Post by apk2 on 2015-03-17
I am using ubuntu 14.04 LTS amd64
I am unable to get launcher, menu and top panel, terminal, etc.
Want to reset unity but got dconf & X11 error.

Also due to missing top panel unable to connect to internet. (I am using ethernet)
I googled and tried to connect internet using tty1 but nothing happened .

So unable to do any apt-get install <packeges> to repair unity.

Please help me out !

Will installing gdm , kdm etc will solve the problem ?

---

### Post by CantankRus on 2015-03-18
Resetting unity using dconf won't work from a tty console because dconf needs a D-Bus session bus connection. D-Bus needs an X11 $DISPLAY.
Follow [**_[COLOR="#B22222"]this post[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2269378&p=13246478#post13246478") to place a terminal shortcut on your desktop from tty1.
You should then be able to run the reset command from your desktop.
```
dconf reset -f /org/compiz/ && setsid unity
```
Give the command 30 secs or so to run and if panel and launcher don't appear,
log out to the greeter with the command...
```
kill -9 -1
```
Log back in.

---

### Post by apk2 on 2015-03-18
I panicked I re-installed Ubuntu! I did not try this but  Thanks a lot!  I find this method to be unique & best for missing panel and launcher  ! :tongue:

---


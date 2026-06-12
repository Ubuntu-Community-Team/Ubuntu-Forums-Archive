---
title: "only terminal accessible after login"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-08-14
I'm running Ubuntu 10.04 on my system. Today when I  started it up, it came up with the normal login screen and I logged in,  but then all I could access was the terminal, which was docked in the  upper left corner of the screen. How do I get out of the terminal,  and/or what did I mess up or need to do to fix this? I don't recall  doing anything last time I used it other than installing updates.

---

### Post by NikTh on 2012-08-14
Hi , 
can you give the results of these commands ? 
```
nano .xsession-errors 
cat /var/log/Xorg.0.log | grep -e EE -e WW
``` 

If you cannot  , then run in terminal this command 
```
unity --reset
``` 
and see if something fixed. 
Do not stop the command with Ctrl+C or by closing terminal , if you find this command infinity , then logout and login again. 
Thanks

---

### Post by pmohankumar on 2012-08-14
[B]nano .xsession-errors 
[/B]
/etc/gdm/xsession: Beginning session setup...
stdin: is not a tty
setting IM through im-switch for locale=en_IN.
start IM through /et/x11/xinit/xinput.d/all_ALL linked to /etc/x11/xinit/xinpu$

**cat /var/log/Xorg.0.log | grep -e EE -e WW**

(II) Loading extension MIT-SCREEN-SAVER

**unity --reset**

No command unity found

---

### Post by NikTh on 2012-08-14
Hi , 
please post the output of 
```
cat /etc/lsb-release && uname -r 
echo $DESKTOP_SESSION
```
Thanks

---

### Post by pmohankumar on 2012-08-14
cat /etc/lsb-release && uname -r 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
2.6.32-33-generic

echo $DESKTOP_SESSION

xterm

---

### Post by roger_1960 on 2012-08-14
Hi

Have you tried the command

> startx

in terminal?

---

### Post by pmohankumar on 2012-08-14
i tried
but no effect

---

### Post by steeldriver on 2012-08-14
do you have a ~/.xinitrc or ~/.xsession file in your home dir? if so what do they contain?

it looks like something is setting your xsession to start up with just an xterm - or it's falling back to that as a minimal session because your regular session can't start

---

### Post by roger_1960 on 2012-08-14
Hi again

In post #3 is the line

> start IM through /et/x11/xinit/xinput.d/all_ALL linked to /etc/x11/xinit/xinpu$

correct or did you type it ie /et/x11 should surely be /**etc**/x11 ??

---

### Post by NikTh on 2012-08-14
> **pmohankumar said:**
> cat /etc/lsb-release && uname -r 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
2.6.32-33-generic

echo $DESKTOP_SESSION

xterm

Hi , you corrected your Original First post.. I thought you are running(you said) Ubuntu 11.10 
Ubuntu 10.04 has no unity environment. 

And you also running an outdated version of Ubuntu 10.04 . The newest version is 10.04.4
So try to apply these commands in terminal 
```
sudo apt-get update 
sudo apt-get dist-upgrade
``` let it do all updates and restart your system.
Thanks

---

### Post by pmohankumar on 2012-08-29
Hi friends,

I tried many command but at last My Problem solved by re-installing the gnome.
Command : apt-get install ubuntu-desktop

Thanks for your support.

---


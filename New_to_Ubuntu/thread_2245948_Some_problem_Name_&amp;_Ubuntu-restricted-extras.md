---
title: "Some problem: Name &amp; Ubuntu-restricted-extras"
date: 2014-09-27
forum: New to Ubuntu
---

### Post by czgirb on 2014-09-27
Today, I reinstall my Ubuntu 14.04 and face the following problem:
```
czgirb@czgirb-Compaq-Presario-CQ40-Notebook-PC:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for czgirb: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
czgirb@czgirb-Compaq-Presario-CQ40-Notebook-PC:~$ sudo apt-get install vlc
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
czgirb@czgirb-Compaq-Presario-CQ40-Notebook-PC:~$ sudo apt-get install vlc
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
czgirb@czgirb-Compaq-Presario-CQ40-Notebook-PC:~$
```
This problem was cause when **EULA** is out, but when I press **Esc** or **Enter** there's nothing happen. So I close the terminal.
Please help how to solve it
**Thank you**

Regarding Name, how can I change **czgirb@czgirb-Compaq-Presario-CQ40-Notebook-PC:~$** to **czgirb@czgirb:~$** ?
**Thank you**

---

### Post by Frogs Hair on 2014-09-27
See the link , I had a similar problem on one computer and just used the software center. 

[http://askubuntu.com/questions/16225/how-can-i-accept-the-microsoft-eula-agreement-for-ttf-mscorefonts-installer](http://askubuntu.com/questions/16225/how-can-i-accept-the-microsoft-eula-agreement-for-ttf-mscorefonts-installer)

---

### Post by czgirb on 2014-09-27
Use it already ... it takes a time.
Wait 15minutes already ... and still in progress

---

### Post by Rob Sayer on 2014-09-27
I've done this in terminal, no problem.  You have to hit the down arrows as I remember to get to the EULA check, then hit enter.

---

### Post by czgirb on 2014-09-27
> **Rob Sayer said:**
> I've done this in terminal, no problem.  You have to hit the down arrows as I remember to get to the EULA check, then hit enter.

as I remember ... YES
but this time it can not.
So I press Esc, but nothing's happen

@Frogs Hair
SORRY, it's not 15minutes, but it was 20minute ... and now, 35 minutes and still in progress
Huh !!!

---

### Post by Vladlenin5000 on 2014-09-27
It's the TAB key you need to hit first, not the down arrow...

You can try
```
sudo apt-get remove ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer
```
and this time remember to hit TAB then use the arrows to navigate the options.

---

### Post by Impavidus on 2014-09-27
Indeed use tab to select a button and use enter to push it.

However, as you already killed it, your apt-get failed to remove its lock. A new instance of apt-get or any other package manager will think you already have a package manager running and will refuse to work. If you're positive you've no other package managers running, you can release the lock manually:```
sudo rm /var/lib/dpkg/lock
```

---

### Post by Frogs Hair on 2014-09-27
> **czgirb said:**
> as I remember ... YES
but this time it can not.
So I press Esc, but nothing's happen

@Frogs Hair
SORRY, it's not 15minutes, but it was 20minute ... and now, 35 minutes and still in progress
Huh !!!

Beware of the EULA window opening under the software center window if haven't resolved this already.

---


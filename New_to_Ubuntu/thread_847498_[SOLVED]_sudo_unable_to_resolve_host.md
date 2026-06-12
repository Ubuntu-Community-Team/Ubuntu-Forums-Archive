---
title: "[SOLVED] sudo: unable to resolve host"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Madman6510 on 2008-07-02
Whenever I try to use sudo, I get an error message.

```
nicholas@Kidsroompc4:~$ sudo apt-get install rdate
sudo: unable to resolve host Kidsroompc4
nicholas@Kidsroompc4:~$ 

```

Tried looking for other solutions for the problem, but what worked for everyone else simply failed for me. (Namely, changing the hosts file, but you have to be root to do that... and I can't use sudo!) :confused:](*,) [IMG]http://www.customerssuck.com/board/images/smilies/bangheaddesk.gif[/IMG]

---

### Post by hyper_ch on 2008-07-02
boot into recovery mode and fix your hostname... there are plent of threads like that here... try the forum search.

---

### Post by nowshining on 2008-07-02
for edting the hosts file:

sudo gedit /etc/hosts

or sudo nano /etc/hosts

or whatever editor you'd like to use today.

then save the hosts file - ctrl+s and re-try ur request again.

---

### Post by hyper_ch on 2008-07-02
nowshining:

generally good advice but in this case useless.... sudo depends for some reason on a correct hostname and if he changed the hostname properly, namely by just altering the hosts file, he can't use sudo so he can't fix it... hence booting into recovery/single user mode.

---

### Post by Madman6510 on 2008-07-02
Ah, fixed it. Combonation of changing the hosts file in /etc/hosts and fixing my first "fix".

---

### Post by nowshining on 2008-07-02
lol :P yeah thanks for correcting me hyper. ;)

as for Madman - i'm happy u got it fixed. ;)

---


---
title: "LXDE desktop"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by woody13 on 2013-05-12
Problem:  I can login to cli but it wont let me log into the LXDE login menu!  How can I fix this ...tia

---

### Post by MG&amp;TL on 2013-05-12
> **woody13 said:**
> Problem:  I can login to cli but it wont let me log into the LXDE login menu!  How can I fix this ...tia

What distribution, what version, how did you install that distribution, what graphics hardware do you have, is the 'login menu' (this could be several pieces of software) you want actually installed?

Cheers. :)

---

### Post by woody13 on 2013-05-12
> **MG&TL said:**
> What distribution, what version, how did you install that distribution, what graphics hardware do you have, is the 'login menu' (this could be several pieces of software) you want actually installed?

Cheers. :)

The latest lubuntu 12.04.2 which didn't come with lxde installed so i added it and this is installed on a really small pc flash drive system. At first i was able to login and restarted the system then it wouldn't let me login via the desktop.

I am setting up a little micro system is all there is only 2G flash drive on the micro system.

---

### Post by MG&amp;TL on 2013-05-12
> **woody13 said:**
> The latest lubuntu 12.04.2 which didn't come with lxde installed so i added it and this is installed on a really small pc flash drive system. At first i was able to login and restarted the system then it wouldn't let me login via the desktop.

I am setting up a little micro system is all there is only 2G flash drive on the micro system.

Eh...Lubuntu 12.04 comes with LXDE installed. I suspect you installed the 'mini.iso' version, which doesn't really come with anything. 

What happens if you type:

```
sudo service lightdm restart
```

---

### Post by woody13 on 2013-05-12
hold ill try it

---

### Post by woody13 on 2013-05-12
lightdm unrecocnized service

---

### Post by woody13 on 2013-05-12
i was just reading this ...but forgot how to del file on command line?   arrgh been a while. [http://forum.lxde.org/viewtopic.php?f=1&t=1701](http://forum.lxde.org/viewtopic.php?f=1&t=1701)

---

### Post by MG&amp;TL on 2013-05-12
> **woody13 said:**
> lightdm unrecocnized service

Okay, try:

```
sudo service lxdm restart
```

As for removing that file:

```
sudo rm -f /etc/pam.d/lxde
```

---

### Post by woody13 on 2013-05-12
ok i tried the sudo lxdm restart and nothing aslo did the del of the file and rebooted the sys and no luck arrrgh

---

### Post by MG&amp;TL on 2013-05-12
> **woody13 said:**
> ok i tried the sudo lxdm restart and nothing aslo did the del of the file and rebooted the sys and no luck arrrgh

Erm...don't really know what to suggest. What did the 'lxdm restart' do, precisely? Have you tried Ctrl-Alt-F7?

---

### Post by woody13 on 2013-05-12
yes i performed the rm command and the file is gone as expected.  Ctrl_Alt-F7 brings back up the lxde login screen and doesnt allow me to login

---

### Post by MG&amp;TL on 2013-05-12
> **woody13 said:**
> yes i performed the rm command and the file is gone as expected.  Ctrl_Alt-F7 brings back up the lxde login screen and doesnt allow me to login

Oh, I see! I've been misunderstanding you. I thought you meant the login screen wouldn't appear, apologies.

I think this is probably helpful: [http://askubuntu.com/questions/223501/ubuntu-12-10-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-12-10-gets-stuck-in-a-login-loop) ?

---

### Post by woody13 on 2013-05-12
hmmm ok so continuing on i tried sudo server lxdm restart and it brought me back to the login menu
but still won't let me login into desktop

---

### Post by woody13 on 2013-05-12
**solved:  i removed banshee and it all worked just fine!**

---

### Post by MG&amp;TL on 2013-05-13
> **woody13 said:**
> **solved:  i removed banshee and it all worked just fine!**

Weird. Great you managed it though. :)

---


---
title: "MoBlock Installation help =]"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Own3d on 2008-04-25
Following this guide on how to installing Moblock on Ubuntu 7.10 32 bit ...

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

And I've got up to adding this: 

deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main

to /etc/apt/sources.list

But when I click save it says.. 

Could not save the file /etc/apt/sources.list.
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.

Help much appreciated =] Thanks

---

### Post by kamitsukai on 2008-04-25
you need to do this as root

---

### Post by Own3d on 2008-04-25
Gosh this must sound stupid but how do I do it as root?  :)

---

### Post by Own3d on 2008-04-25
Oh and also can someone explain this bit for me, I'm a newbie, Sorry:

MoBlock checks traffic that is sent to the iptables QUEUE (deprecated) or NFQUEUE (new) target. So there are two packages, moblock-ipq and moblock-nfq. Depending on your package of choice you need either the ip_queue or xt_NFQUEUE kernel module loaded. Unless you have a Linux kernel older than 2.6.14, you should use the moblock-nfq package with the new target.

Add the repositories using the above instructions.

---

### Post by kamitsukai on 2008-04-25
***im idiot so just ignore what i typed here***

---

### Post by kamitsukai on 2008-04-25
> **Own3d said:**
> Oh and also can someone explain this bit for me, I'm a newbie, Sorry:

MoBlock checks traffic that is sent to the iptables QUEUE (deprecated) or NFQUEUE (new) target. So there are two packages, moblock-ipq and moblock-nfq. Depending on your package of choice you need either the ip_queue or xt_NFQUEUE kernel module loaded. Unless you have a Linux kernel older than 2.6.14, you should use the moblock-nfq package with the new target.

Add the repositories using the above instructions.

But this is way out of my understanding:lolflag: 
but there's hundreds more people that will. I'm glad you posted this i will need to install moblock when my new pc arrives and im not sure on some things in that howto either...

---

### Post by Own3d on 2008-04-25
root deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
root deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main

When I type them in terminal it says:

chris@chris-laptop:~$ root deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
bash: root: command not found

And in the guide I thought it meant to add the lines to the txt document in etc/apt/sources.list not type in terminal

---

### Post by kamitsukai on 2008-04-25
> **Own3d said:**
> root deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
root deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main

When I type them in terminal it says:

chris@chris-laptop:~$ root deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) gutsy main
bash: root: command not found

And in the guide I thought it meant to add the lines to the txt document in etc/apt/sources.list not type in terminal

sorry my fault now i just look like an idiot...

it wants you to type:

```
sudo gedit /etc/apt/sources.list
```
i cant remember if theres a space between "gedit" and the first forwad slash so try both (im not at a ubuntu machine at the mo...)

then it will open a file up and then you copy and paste these into the bottom of it
```
deb http://moblock-deb.sourceforge.net/debian gutsy main
deb-src http://moblock-deb.sourceforge.net/debian gutsy main
```

and then click save

---


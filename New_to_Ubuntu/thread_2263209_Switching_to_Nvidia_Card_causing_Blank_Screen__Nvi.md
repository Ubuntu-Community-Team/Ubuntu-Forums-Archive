---
title: "Switching to Nvidia Card causing Blank Screen : Nvidia Prime"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by Abhisek Maiti on 2015-01-30
I'm using Ubuntu 14.04 LTS on my Dell Inspiron 3520 laptop with Intel HD 4400 + Nvidia GeForce 820M Hybrid Graphics. I added nvidia-edge ppa and installed nvidia-340.65 driver. Everything along with switching between Intel & Nvidia card worked fine. But today I noticed that somehow my graphics settings automatically transfarred to Intel card. Now, whenever I try to switch it to Nvidia Card and logout/reboot, it causes a completely blanck screen. When I try to switch using terminal..

```
$ sudo prime-select nvidia
```

It gives following error

```
update-alternatives: using /usr/lib/nvidia-340-prime/ld.so.conf to  provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf  (x86_64-linux-gnu_gl_conf) in manual mode
update-alternatives: using  /usr/lib/nvidia-340-prime/alt_ld.so.conf to provide  /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in  manual mode
```

I tried completely uninstalling & reinstalling the nvidia driver along with it's dependencies but I'm still out of luck. Please Help..

My GPU Manager Log attached below.

[ATTACH]259605[/ATTACH]

---

### Post by Sylve on 2015-01-30
Hi, same problem there. Since I did some hours ago
```
apt-get update
apt-get upgrade
```

My computer goes to black screen after GRUB, except if I launch from recovery mode, then with X server there is no problem.

Nvidia-Config doesn't even recognize my new 340.76 driver. That's weird, because the driver tool from my Kubuntu does.

I saw some posts about it:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg4598232.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg4598232.html)
[URL="http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg366770.html"]http://www.mail-archive.com/desktop-packages@lists.launchpad.net/msg366770.html
[/URL]
Maybe gotta install this one: [http://www.geforce.com/drivers/results/81252](http://www.geforce.com/drivers/results/81252) Edit : Still not working. The problem may come from X.org server.

---

### Post by ripedar2 on 2015-05-28
Is there some developement in this? I still have problem. Nothing seems to help from google or forums. There was some updates of drivers already but nothing changed. :mad:

---

### Post by kirby33 on 2015-06-01
Hello everybody!

As many others users, I get a black screen when I try to switch on the nvidia card.
I am just a user, therefore I just give my feedback.

I use nvidia-prime and the nvidia drivers coming from the ppa xorg-edgers ppa.
I use also prime-indicator for quickly switch between the nvidia (GTX880M) and the intel card and my login manager is lightdm.

First comment, for my case, the black screen issue doesn't comes from  the driver but of nvidia-prime.

My first suggestion to solve the black screen. Using the the root  privilege edit the file /sbin/prime-offload and just replace the first  line #!/bin/sh by #!/bin/bash.

Now, you can use the command: prime-select nvidia (or intel) and reboot  your laptop. Normally, now you can switch between the two cards but the  quick switch of "prime-indicator" doesn't work.

For the next step, I don't have a real solution but just a workaround:
With the root privilege edit the files /usr/lib/primeindicator/igpuon  and /usr/lib/primeindicator/dgpuon and just before "sync" insert this  line:
service lightdm restart

So you get this for the file igpuon:
  prime-select intel  
  service lightdm restart
  sync

And you get this for the file igpuon:
  prime-select nvidia
  service lightdm restart
  sync


I hope that this feed-back will be helpful to other people.
++ Kirby

---


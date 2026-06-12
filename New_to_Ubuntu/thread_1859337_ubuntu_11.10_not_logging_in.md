---
title: "ubuntu 11.10 not logging in"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by duruttye on 2011-10-13
Hey!

After about 6 months I had to start the windows xp on my laptop.

The problem is, that I replaced Ubuntu 11.04 with ubuntu 11.10. I have a / partition, a /home and a /stuff partition. (and an /xp ).

The first try I failed because I forgot that I had to point the installation to the /home partition. So after the install I changed the fstab and pointed it to the right partition and folder. But after reboot I got stuck at the login screen, because after I selected the user and typed the password, it just bounced back at the login screen after 3-4 seconds.
I tried to log in to the guest account, but it logged in to a blank screen, with just a short menu on the top, I'm not sure if that's the normal thing to do, I never had a guest user.

So, I said, okay, I have another 15 minutes so I installed it again, but this time, I pointed the installation to the right /home partition. After the installation the problem remains.

I can however log in to that tty (ctrl - alt - F1) or whatever it's called and I deleted some folders from the /home/user folder, for example: .compiz, .gnome2, .gnome2-**something** and a few more, but it didn't help at all.

Any ideas?

Unfortunately I can't access the partition from the windows to tell you what other folders I have in the /home/domelaci partition.

thank you!

---

### Post by Krytarik on 2011-10-13
> **duruttye said:**
> I can however log in to that tty (ctrl - alt - F1) or whatever it's called and I deleted some folders from the /home/user folder...
From there, try removing the file "~/.Xauthority", as stated in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/871667)

Hope that works!

---

### Post by Arachan on 2011-10-16
Hello,

I don't know of you have solved this issue or not, but I had a similar problem. When I installed 11.10 I used my /home from 11.04 and when I tried to login it went black and then took me back to the login screen. I found that the permissions on my /home were wrong, so I used ctrl+alt+f1 to login to a terminal and changed the permissions from there. 

HTH,
arachan.

---

### Post by duruttye on 2011-10-18
Hey!

Thank you guys, I deleted that file and it worked as it is supposed to work!

There was nothing wrong with the permissions!

Thanks again!

---

### Post by lordnemo on 2011-10-22
I removed ~/.Xauthority but i still cannot login. did i miss something? also after logging out of tty and logging back in apparently ~/.Xauthority reappears.

---

### Post by LinuxFan999 on 2011-10-22
I once had a similar problem with Xubuntu 10.04, but I didn't know how to fix it so I had to reinstall Xubuntu.

---

### Post by lordnemo on 2011-10-22
i can't reinstall lubuntu because i don't have any way of backing up my files.

---


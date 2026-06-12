---
title: "Password on Ubuntu desktop"
date: 2017-05-31
forum: New to Ubuntu
---

### Post by basicboy on 2017-05-31
I have created a username and password when I installed Ubuntu.
I then installed the desktop and was advised to restart so that the desktop can show.
With the restart the desktop does show and below the Libvert Qemu page, it shows my username as guest session, but it does not want to accept my password.
Any help will be appreciated.
Thanks

---

### Post by again? on 2017-05-31
Ubuntu has an Ubuntu desktop session, so bit confused by > I then installed the desktop
Which desktop did you install?
What Ubuntu release did you install?
Guest sessions use blank passwords.

---

### Post by basicboy on 2017-05-31
I installed Ubuntu rev 16.04.2 and then after installation I types at the terminal:

sudo apt-get update
sudo apt-get install ubuntu-desktop

and it installed the desktop.
A blank password did not work, but the installation package also installed Apache and MySql I think. 
It may be that one of those packages has this login, that is why I quoted the page login name.
Thanks

---

### Post by basicboy on 2017-05-31
I got the solution here:

[https://askubuntu.com/questions/889995/libvirt-qemu-password](https://askubuntu.com/questions/889995/libvirt-qemu-password), 

but now I do not know how to get out of the login page and go to the terminal or root.

---

### Post by again? on 2017-05-31
> **basicboy said:**
> I got the solution here:

[https://askubuntu.com/questions/889995/libvirt-qemu-password](https://askubuntu.com/questions/889995/libvirt-qemu-password), 

but now I do not know how to get out of the login page and go to the terminal or root.
Try ctrl+alt +F1 or F3 at the greeter.

---

### Post by basicboy on 2017-05-31
Thanks Guber,

I have researched many posts for circumventing the password in libvirt - and there are about twenty - but I could nor get anyone to work.
The best I have so far is:

[COLOR=#996633]$ [/COLOR]usermod --append --groups libvirt `whoami`

Just not getting anywhere slow.

---

### Post by Geoffrey_Arndt on 2017-06-01
Deleted orig. reply . . pending additional info

---

### Post by mc4man on 2017-06-02
Maybe this
[https://askubuntu.com/questions/889995/libvirt-qemu-password](https://askubuntu.com/questions/889995/libvirt-qemu-password)

[https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1667113](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/1667113)

---


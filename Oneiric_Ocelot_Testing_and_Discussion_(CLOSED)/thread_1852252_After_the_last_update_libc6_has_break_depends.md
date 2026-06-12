---
title: "After the last update libc6 has break depends"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by chek2fire on 2011-09-29
My distro is from 11.04 upgrade. After two days  an update break the library libc6 and libc6-i368. 
I know that both of these lib are from 11.04. Normally the distro has to install the new library libc-bin and remove both of the other but that didnt happen. 
I try to fix it with -f install but it returns this

> 
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

and i have now 57 break package that depends on libc-i368. Any advice what i have to do?

---

### Post by fillmont on 2011-09-29
I've just had a similar error with my Kubuntu test machine. It is a brand new install off of Beta 2. Libc6 is broken in the same way.

---

### Post by chek2fire on 2011-09-30
what we can do we have to wait for an update to fix the things or i have to report it to launchpad as a bug?

---

### Post by dino99 on 2011-09-30
reboot in recovery mode & select "repair packages" first

---

### Post by chek2fire on 2011-09-30
i try this but there is no fix broken package option anymore in recovery mode. There is a new simple option recovery mode with the last kernel update

---

### Post by el_koraco on 2011-09-30
> **chek2fire said:**
> i try this but there is no fix broken package option anymore in recovery mode. There is a new simple option recovery mode with the last kernel update

sudo dpkg --configure -a
sudo apt-get install -f

Run it a few times. But for shizz, untill this gets solved higher up, you're probably flat out of luck. Pretty much everything on the system depends on libc6, and if there are conflicting versions, it's not easy to solve. You can try to reinstall libc6, but the best option is to give it a day or two.

---

### Post by 3vi1 on 2011-09-30
> **chek2fire said:**
> My distro is from 11.04 upgrade. After two days  an update break the library libc6 and libc6-i368. 
I know that both of these lib are from 11.04. Normally the distro has to install the new library libc-bin and remove both of the other but that didnt happen. 
I try to fix it with -f install but it returns this


dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

and i have now 57 break package that depends on libc-i368. Any advice what i have to do?

I've seen this problem with debian upgrades before.  Instead of using sudo to runk the command, do 'sudo su' to become root first - then run the command without sudo.

If the problem is the same as I've seen in the past, you find that it works due to your path being different.  After all the updates are applied, you can go back to the normal procedure.

---

### Post by cariboo on 2011-09-30
> **3vi1 said:**
> I've seen this problem with debian upgrades before.  Instead of using sudo to runk the command, do 'sudo su' to become root first - then run the command without sudo.

If the problem is the same as I've seen in the past, you find that it works due to your path being different.  After all the updates are applied, you can go back to the normal procedure.

```
sudo su
```

doesn't work as expected in Ubuntu. The best thing to do is start in recovery mode, and select drop to root prompt (the wording may be different, but it's the last selection in the menu). You will be dropped to a root prompt where you can run any of the update commands without using sudo.

If you just want to run as root in a console, use:

```
sudo -i
```

---

### Post by chek2fire on 2011-10-01
I have try this solution but nothing happens. When i give -f install returns the same message. I think i have to report the problem to launchpad.

---

### Post by Larkspur on 2011-10-01
I'm having a problem with libc6, but I think it's different; basically, it won't download, but because of that, it's reported as a broken dependency (because so much depends on it?).  It happened last night when I downloaded the latest updates.  All of the others were downloaded without problems, but when it came to libc6, the download never started, which I presume means it's not on the server yet.  

Would it be advisable for me to get the deb directly from the Launchpad page and install it through Software Centre?  Or would that cause new problems?

---

### Post by dino99 on 2011-10-01
are you using non ubuntu genuine packages ? (third party and/or manual install)

sudo dpkg-reconfigure -phigh -a

and watch yours logs (/var/log/): apt, dpkg, ...

---

### Post by Larkspur on 2011-10-01
> **dino99 said:**
> are you using non ubuntu genuine packages ? (third party and/or manual install)

I think so, if you mean stuff from Universe and Multiverse.  Also, I installed Opera and Flash manually.  When the Update Manager suggest I deactivate the third-party repositories, I did so, then - as it asked - I ran "sudo apt-get install -f" but all that happened is that a connection was made, then it hung on "0% [Waiting on headers]" for a while before reporting a failure:

```
Err http://archive.ubuntu.com/ubuntu/ oneiric/main libc6 i386 2.13-20ubuntu4
  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.13-20ubuntu4_i386.deb  Connection failed
```Maybe it's the spaces in that first URL that's causing the problem?


I've got the original error reported by Update Manager, if it helps:

```
The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.13-20ubuntu3) but 2.13-20ubuntu4 is installed
libc6-dev: Depends: libc6 (= 2.13-20ubuntu4) but 2.13-20ubuntu3 is installed
           Depends: libc-dev-bin (= 2.13-20ubuntu4) but 2.13-20ubuntu4 is installed
```I went to the archives, libc6 2.13-20ubuntu4 was there, so I downloaded it through Firefox with no problems, but I can't install the deb through Software Centre.

---

### Post by chek2fire on 2011-10-01
the last is the same message i have when i try to give upgrade or to -f install. I have open and a bug report here

[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/863987](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/863987)

i dont know if the description is correct but anyone who has the same problem he can post a comment there. Maybe someone dev notice the bug and solve it.

---

### Post by rockair on 2011-10-02
I solved this "bug" by unpacking ldconfig from its origin lib-bin package from ubuntu repository. Than i copied it to sbin directory and dpkg package system now works. In Ubuntu commands: 

```
aptitude download libc-bin
dpkg-deb -x libc-bin*.deb libc-bin-unpacked/
sudo cp  libc-bin-unpacked/sbin/ldconfig* /sbin/

```
And then you must install libc-bin from package system by: ```
apt-get install libc-bin
```.

---

### Post by chek2fire on 2011-10-02
rockair thanks :) i use this solution and finally my package system was working again . I have to give and apt-get -f install aftre the installation of libc-bin

---


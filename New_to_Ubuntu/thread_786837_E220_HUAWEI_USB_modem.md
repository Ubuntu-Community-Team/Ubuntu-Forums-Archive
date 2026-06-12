---
title: "E220 HUAWEI USB modem"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by rkusumo on 2008-05-08
Hello,

I am a trying to install E220 HUAWEI USB modem in Ubuntu 8.04 with lots of problems. I have followed the steps prescribed in various forums, including downloading Vodafone Mobile Connect Card driver for linux 2.0.beta2-ubuntu-installer.run. I think I have successfully install the driver, but when I try to run it I encounter the following error message

“Permission problems

Vodafone Mobile Connect Card driver for Linux needs the following files and dirs with some specific permissions in order to work properly: /etc/ppp/pap-secrets should have 0660 mode, found 0600 /etc/ppp/chap-secrets should have 0660 mode, found 0600 /etc/ppp/peers should be readable and writable by group dip”

I am not sure how to fix the problem. I am a new comer to Ubuntu and Linux, so any help is much appreciated.

Cheers.

---

### Post by Wim Sturkenboom on 2008-05-08
Start a terminal (menu applications/accesories/terminal) and type the bold commands
```

wim@desktop1:~$ **cd /etc/ppp**
wim@desktop1:/etc/ppp$ **ls -ld peers**
drwxr-s--- 2 root dip 4096 2007-11-22 10:03 peers
wim@desktop1:/etc/ppp$ **ls -l chap-secrets**
-rw------- 1 root root 151 2007-11-22 10:03 chap-secrets
wim@desktop1:/etc/ppp$ **ls -l pap-secrets**
-rw------- 1 root root 1699 2007-11-22 10:03 pap-secrets
wim@desktop1:/etc/ppp$

```
The above will show you the current permissions and owner/group. Each 'r' equals 4, each 'w' equals 2 and each 'x' equals 1; add them together and you get 600 for e.g chap-secrets.

You can use chmod (change mode) to change permissions for pap-secrets (shown) and chap-secrets (for you to figure out ;) ).
```

wim@desktop1:/etc/ppp$ **chmod g+w pap-secrets**

```
You can change the group for peers to 'dip' using chgrp (change group)
```

wim@desktop1:/etc/ppp$ **chown dip peers**

```
If the last command fails with a message 'invalid group', you can add the group 'dip' to the system with the below command:
```

wim@desktop1:/etc/ppp$ **addgroup dip**

```

You probably have to preceed the last three commands with sudo (e.g ***sudo** addgroup dip*) which will prompt you for your password before the command is executed.

---

### Post by rkusumo on 2008-05-09
Hi,

I have managed to connect E220 Huawei USB modem using Ubuntu 8.04. These are the steps that I took:

1) Download the following files:

libgda3-3_3.0.2-2ubuntu1_i386.deb
libgda3-common_3.0.2-2ubuntu1_all.deb
libgdl-1-0_0.7.11-1_i386.deb
libgdl-1-common_0.7.11-1_all.deb
libgdl-gnome-1-0_0.7.11-1_i386.deb

at [http://packages.ubuntu.com/hardy/libs/](http://packages.ubuntu.com/hardy/libs/)

python-crypto_2.0.1+dfsg1-2.1ubuntu1_i386.deb
python-gnome2-extras_2.19.1-0ubuntu7_i386.deb
python-serial_2.2-4_all.deb
python-twisted_2.5.0-2build2_all.deb
python-twisted-bin_2.5.0-2build2_i386.deb
python-twisted-conch_0.8.0-1build1_all.deb
python-twisted-core_2.5.0-2build2_all.deb
python-twisted-lore_0.3.0-1build1_all.deb
python-twisted-mail_0.4.0-1build1_all.deb
python-twisted-names_0.4.0-1build1_all.deb
python-twisted-news_0.3.0-1build1_all.deb
python-twisted-runner_0.2.0-4build1_i386.deb
python-twisted-web_0.7.0-1build1_all.deb
python-twisted-words_0.5.0-1.1build1_all.deb
python-tz_2007k-0ubuntu2_all.deb
python-zopeinterface_3.3.1-5ubuntu2_i386.deb

at [http://packages.ubuntu.com/hardy/python/](http://packages.ubuntu.com/hardy/python/)

2) Install all the downloaded files by double clicking them.
3) Download vodafone-mobile-connect-card-driver-for-linux-2.0.beta2-ubuntu-installer.run 

at [https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=33](https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=33)

4) Install the driver by double clicking it
5) Reboot the computer with the USB model plug-in 
6) Start Vodafone driver by going to Applications->Internet->Vodafone Mobile Connect Card driver for Linux
7) Type in the detail in the New Profile and click OK

Profile name: <my name>
Username: <user>
Password: <password>
Preferred connection: 3G preferred
Authentication mode: PAP
APN host : <APN from my ISP>

8) Click Connect.

Thank you to those who have help. Much appreciated.

Let the journey begin.

Cheers.

---


---
title: "how to update bleachbit"
date: 2023-11-13
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2023-11-13
[SIZE=5]I am using Ubuntu 23.10. I went to bleachbit.org for instructions to update but it lead me to the deb package which wasn't in the Ubuntu store. I use this command to update snap and flakpak apps. i checked and bleachbit is a flatpak app in my system. I use this command to update and upgrade my system.[/SIZE]
[SIZE=5][COLOR=#333333][FONT=&amp]sudo apt update && sudo apt upgrade -y && sudo snap refresh && sudo flatpak update. When i use it bleachbit isn't updated. Thx for any help. [/FONT][/COLOR][/SIZE]

---

### Post by Claus7 on 2023-11-15
Hello,

I do not know which version you have installed, yet under 23.10 the version of bleachbit I have is 4.4.2. The 4.6.0 is the latest release available. From time to time, if you open bleachbit and a new version is available, it will ask you if you want to upgrade to the latest one. If the version is not updated, then it might not be ready for an update.

You could check this link if it is helpful: 
[https://ubuntuhandbook.org/index.php/2023/11/bleachbit-stable-4-6-0/](https://ubuntuhandbook.org/index.php/2023/11/bleachbit-stable-4-6-0/)
it mentions how you could install the latest deb version.

Regards!

---

### Post by #&amp;thj^% on 2023-11-15
> **Claus7 said:**
> Hello,

I do not know which version you have installed, yet under 23.10 the version of bleachbit I have is 4.4.2. The 4.6.0 is the latest release available. From time to time, if you open bleachbit and a new version is available, it will ask you if you want to upgrade to the latest one. If the version is not updated, then it might not be ready for an update.

You could check this link if it is helpful: 
[https://ubuntuhandbook.org/index.php/2023/11/bleachbit-stable-4-6-0/](https://ubuntuhandbook.org/index.php/2023/11/bleachbit-stable-4-6-0/)
it mentions how you could install the latest deb version.

Regards!+1 That link will work:
```
apt policy bleachbit
bleachbit:
  Installed: 4.6.0-0
  Candidate: 4.6.0-0
  Version table:
 *** 4.6.0-0 100
        100 /var/lib/dpkg/status
     4.4.2-2 500
        500 http://us.archive.ubuntu.com/ubuntu mantic/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu mantic/universe i386 Packages

```
I just don't use snaps :P
That will be your only route for the latest version:
```
 bleachbit | 1.0-1   | trusty/universe | source, all
 bleachbit | 1.10-1  | xenial/universe | source, all
 bleachbit | 2.0-2   | bionic/universe | source, all
 bleachbit | 3.9.0-1 | focal/universe  | source, all
 bleachbit | 4.4.2-1 | jammy/universe  | source, all
 bleachbit | 4.4.2-1 | lunar/universe  | source, all
 bleachbit | 4.4.2-2 | mantic/universe | source, all
 bleachbit | 4.4.2-2 | noble/universe  | source, all

```

---

### Post by tuesdaybarrett on 2023-11-25
thx used gdeb installer & got latest version

---

### Post by ActionParsnip on 2023-11-26
What is in the newer version that you need so badly?

---


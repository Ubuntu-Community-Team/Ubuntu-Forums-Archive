---
title: "How to install Internet Explorer?"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by zeynel2 on 2013-11-04
Unfortunately, I need to use IE for some programs, but I am having problems installing it. I am trying to follow this page: [https://help.ubuntu.com/community/InstallingInternetExplorer](https://help.ubuntu.com/community/InstallingInternetExplorer) but when I try ```
sudo aptitude install wine cabextract
``` I get ```
sudo: aptitude: command not found
```. Do I need to install Aptitude? I am not clear from this page: [HTML]https://help.ubuntu.com/10.04/serverguide/aptitude.html[/HTML]

What is the best way to install IE?

I am running Ubuntu 12.04 LTS

---

### Post by deadflowr on 2013-11-04
Try apt-get instead of aptitude.
Aptitude isn't installed by default anymore.

---

### Post by newb85 on 2013-11-04
No, you don't.  I don't know why that page used aptitude, but the default package management software for Ubuntu is apt-get.  You should be able to install those packages via:
```
sudo apt-get install wine cabextract
```

I would expect the rest of the instructions to work, but I cannot be certain, as those instructions are 2 1/2 years old.

---

### Post by sha1sum on 2013-11-04
We should ask the developers of Internet Explorer to bring out a Ubuntu-compatible version of their product.

---

### Post by SuperFreak on 2013-11-04
> **sha1sum said:**
> We should ask the developers of Internet Explorer to bring out a Ubuntu-compatible version of their product.

About as likely as Microsoft giving away Windows 9 for free and as open source

---

### Post by QIII on 2013-11-04
Back on topic, please.

---

### Post by zeynel2 on 2013-11-04
> **newb85 said:**
>  would expect the rest of the instructions to work, but I cannot be certain, as those instructions are 2 1/2 years old.

Yeah, it failed here:

```
a@b:~$ cd ies4linux-*
a@b:~/ies4linux-2.99.0.1$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).


ies4linux-gtk.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.



```

What does this mean?

---

### Post by sandyd on 2013-11-04
have you tried playonlinux instead? (has support for IE).
There are a lot of posts around for this issue with ies4linux

---

### Post by Mark Phelps on 2013-11-05
The problem you're going to run into is that recent versions of IE (9 and higher) will NOT work in Wine, so you're relegated to older versions -- and these may not support the features that the websites need.  Sorry, but if you have to rely on using IE, MS Windows is the only way to go.

---

### Post by ben-blankley on 2013-11-05
In this Ask Ubuntu post, the top rated answer is someone suggesting using virtualization with VirtualBox, rather than Wine.

[http://askubuntu.com/questions/190425/how-to-install-internet-explorer-multiple-versions](http://askubuntu.com/questions/190425/how-to-install-internet-explorer-multiple-versions)

---

### Post by mastablasta on 2013-11-05
yup. virtualbox is a better way to go. and less messy. but one does need a copy of windows for that and that costs money.

---

### Post by deadflowr on 2013-11-05
> **mastablasta said:**
> yup. virtualbox is a better way to go. and less messy. but one does need a copy of windows for that and that costs money.

On top of a system that can handle running the vm.
Not too much of a problem if running XP, but winvista on up needs a little more resources.

---


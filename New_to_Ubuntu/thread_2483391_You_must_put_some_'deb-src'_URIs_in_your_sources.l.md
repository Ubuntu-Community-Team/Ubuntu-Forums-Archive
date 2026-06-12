---
title: "You must put some 'deb-src' URIs in your sources.list"
date: 2023-01-29
forum: New to Ubuntu
---

### Post by kittu20 on 2023-01-29
I am new here I need to get the Linux kernel source. following link [URL="https://askubuntu.com/questions/159833/how-do-i-get-the-kernel-source-code"]https://askubuntu.com/questions/159833/how-do-i-get-the-kernel-source-code
[/URL] 
i tried below command 

```
 ruday@Hruday:~/Desktop$ apt-get source linux-source
Reading package lists... Done
E: You must put some 'deb-src' URIs in your sources.list
hruday@Hruday:~/Desktop$ sudo apt-get source linux-source
[sudo] password for hruday: 
Reading package lists... Done
E: You must put some 'deb-src' URIs in your sources.list


```

what's error message and how to get kernel source code ?

---

### Post by grahammechanical on 2023-01-29
In Ubuntu we download and install software from repositories. The updates to software also come from those repositories which are also called archives. We can see the internet addresses of these repositories in a file called sources.list. We find it at /etc/apt/sources.list. To see what is in the sources.list file without being able to edit the file run this command.

```
cat /etc/apt/sources.list
```

This is an example from my sources.list file:

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal universe

My system will update and download software from the first internet address but not from the second internet address. The hash ( # ) symbol means that the address is commented out and is ignored by the apt utility. The words "deb-src" show that this repository is an archive for software source code.

You need to identify which repository contains the Linux source code and edit the sources.list file to remove the appropriate hash symbol. If you open Software and Updates>Ubuntu Software tab you will see a check box labelled Source code. Tick that box and see if it helps you.

The error message is saying the the repositories for source code are not enabled which is the default situation for Ubuntu.

Regards

---

### Post by monkeybrain20122 on 2023-01-29
To get deb-src, bring up Software & Updates and check the box "Source code", then reload (the same as sudo apt update), see screenshot

If you want to build kernel from  source, you should get it here

[https://www.kernel.org/](https://www.kernel.org/)

---

### Post by kittu20 on 2023-01-31
> **grahammechanical said:**
> In Ubuntu we download and install software from repositories. The updates to software also come from those repositories which are also called archives. We can see the internet addresses of these repositories in a file called sources.list. We find it at /etc/apt/sources.list. To see what is in the sources.list file without being able to edit the file run this command.

You need to identify which repository contains the Linux source code and edit the sources.list file to remove the appropriate hash symbol. If you open Software and Updates>Ubuntu Software tab you will see a check box labelled Source code. Tick that box and see if it helps you.

The error message is saying the the repositories for source code are not enabled which is the default situation for Ubuntu.

Regards

Thank you both of you for help

I am attaching screenshot 

How to view source code ? what is command for it ?

---

### Post by monkeybrain20122 on 2023-01-31
dpkg-dev is in the repo

```
sudo apt install dpkg-dev
```

To view the source code, your screenshot shows that it is in your $HOME, the "git clone ..." command basically download the git repo to where you execute the command (so if you cd dir first and execute the command, it will be cloned to dir, if you don't cd anywhere first, it just in your $HOME)

---

### Post by ActionParsnip on 2023-02-01
What is the output of
```

cat -n /etc/apt/sources.list

```
From your previous post, it looks like you have added git repos to the file. That isn't how they are used

---

### Post by kittu20 on 2023-02-03
> **ActionParsnip said:**
> What is the output of
```

cat -n /etc/apt/sources.list

```
From your previous post, it looks like you have added git repos to the file. That isn't how they are used

uploaded screenshot

---

### Post by kittu20 on 2023-02-08
my desktop are showing some file. can anyone tell me which are related to  kernel source code ?

---


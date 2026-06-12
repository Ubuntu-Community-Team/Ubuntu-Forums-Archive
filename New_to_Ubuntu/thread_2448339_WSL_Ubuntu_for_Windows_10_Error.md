---
title: "WSL Ubuntu for Windows 10 Error"
date: 2020-08-06
forum: New to Ubuntu
---

### Post by giant-paw on 2020-08-06
I installed "Ubuntu" from official Windows 10 store app which is the best way for me to run package _youtube-dl_.
But when trying to download, it shows this error[COLOR=#000000]: 
> ERROR: Unable to download webpage: <urlopen error [Errno 111] Connection refused> (caused by URLError(ConnectionRefusedError(111, 'Connection refused')))
Both http and https tried.
What it means and how to solve it? [/COLOR]

---

### Post by CelticWarrior on 2020-08-06
The usage of youtube-dl is against Youtube's ToS therefore discussions about it are against this forum's rules and quite frowned upon by the staff.

The error message suggests the URL is wrong.

---

### Post by SeijiSensei on 2020-08-06
A more global answer is to not use WSL at all. Install VirtualBox for Windows from [https://www.virtualbox.org/](https://www.virtualbox.org/). It will enable you to create "virtual machines" into which you can load most any operating system. Rather than being bound by the version of Ubuntu in the Microsoft Store, you can install any Ubuntu "flavor" ([Ubuntu]("http://cdimage.ubuntu.com/ubuntu/releases/20.04/release/"), [Kubuntu]("http://cdimage.ubuntu.com/kubuntu/focal/daily-live/current/"), [Xubuntu]("http://cdimage.ubuntu.com/xubuntu/focal/daily-live/current/"), [Lubuntu]("http://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/"), etc.) into a VB virtual machine and have a fully-working system. You can even install another copy of Win 10 on top of Win 10.

---

### Post by QIII on 2020-08-06
Closed.

---


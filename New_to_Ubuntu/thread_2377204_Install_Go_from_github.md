---
title: "Install Go from github"
date: 2017-11-10
forum: New to Ubuntu
---

### Post by tactical2 on 2017-11-10
New to ubuntu, how do I load Go using github.
I have a basic ubuntu remote instance, so need to download the binary. How? to where?

---

### Post by DuckHook on 2017-11-10
Welcome to the forums, tactical2.

More info please:

[LIST]
[*]What is the nature of your remote instance?
[*]Does it prevent you from accessing the Ubuntu repos?
[*]Why do you need Github? The usual way to install GO is simply to pull it from the repos:```
sudo apt install golang
```This will install it automagically into your Ubuntu system, no muss, no fuss.
[/LIST]
If you are new to Linux in general, it is important to point out to you that the Linux world is completely different from the proprietary world of Windows. The best and safest way to install apps in Linux is to stick to the repositories for your distribution. For general users, it is almost never necessary to go outside of the repos. That's one of the many factors at play in enhancing Linux security and usability. Unless your use-case absolutely requires the latest and greatest version of GO (unlikely), then stick with the one in the repos.

---

### Post by kostkon on 2017-11-10
If you are after the latest version then there is also the snap package you can install with:
```
sudo snap install go
```

---


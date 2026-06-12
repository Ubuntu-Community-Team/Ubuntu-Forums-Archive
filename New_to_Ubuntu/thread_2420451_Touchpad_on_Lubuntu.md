---
title: "Touchpad on Lubuntu"
date: 2019-06-05
forum: New to Ubuntu
---

### Post by berderder on 2019-06-05
Hi everyone,  Brand new Lubuntu user and new to Linux in general.  I have a HP Stream. The touchpad tracks but the touchpad doesn't respond to tapping to open applications. I have to hard press. Any advice?  Thank you

---

### Post by cruzer001 on 2019-06-06
What version of Lu are you running?  18.04 or 19.04?

Have you updated your system?
```
sudo apt update && sudo apt full-upgrade -y
```
and reboot

I think Lu uses xinput.  Find the model of your touchpad here:
```
xinput --list
```
Please post that info

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---


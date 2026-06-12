---
title: "How to replace Kubuntu with Ubuntu?"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by rubytru on 2011-09-19
My brothers PC has Kubuntu installed and he wants Ubuntu instead.
any help on how to accomplish this will be greatly appreciated.   Thanks

---

### Post by Lisiano on 2011-09-19
First install Ubuntu
```
sudo apt-get install ubuntu-desktop
```
It will ask you what login manager you want, you want GDM.
Next log out and log back in but make sure it says Ubuntu Classic or Unity on the bottom then follow this
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by rubytru on 2011-09-19
Thanks! :)

---

### Post by Lisiano on 2011-09-19
Please mark the thread as Solved in the Thread tools at the top of the page.
Also, have fun with Ubuntu.

---

### Post by rubytru on 2011-09-19
Hi Lisiano, I did as you instructed and all went well except for this warning...
cryptsetup warning failed to detect canonical device of /dev/sda3

don't know what this means?

thank you again for the help.

---

### Post by Lisiano on 2011-09-20
Note: I don't know much about cryptsetup
A quick google showed that error followed by a error finding the fstab root, I think if it is not followed by that then it is safe but just in any case, could you post the output of this?
```
sudo fdisk -l
```
Also where or when do you get that warning?

---


---
title: "reinstall Catalyst drivers after each kernel update?"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by yesplease on 2013-05-25
I have the habit to purge AMD's catalyst drivers before a kernel update and install the drivers all over again after the kernel is updated. The kernel is updated frequently these days. My question is: is this really neccessary, perhaps the drivers do not have to be reinstalled every time? Is there a simpler solution?

(Currently I use Catalyst 13.4 on Ubuntu 13.04 64bit, for an ATI HD7950 video card (and Intel CPU), but my question is not hardware specific)

---

### Post by yeats on 2013-05-25
You might want to look into DKMS: [https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS).

---

### Post by yesplease on 2013-05-25
Thank you, it is good to know that this exists.

However, I might be able to follow these instructions, but I am not able to repair the installation if something goes wrong. That would mean reinstall (which is amazingly quick with 13.04) and customize, which takes rather longer. (I quote: With some luck, your module will be installed and reinstalled into future kernel updates.) 

If there is no other option, I consider using this: [http://askubuntu.com/questions/178324/how-to-skip-kernel-update?lq=1](http://askubuntu.com/questions/178324/how-to-skip-kernel-update?lq=1)

---


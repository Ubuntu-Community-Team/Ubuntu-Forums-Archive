---
title: "I cannot connect  my wireless network"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by empireruler on 2008-05-28
I have installed Ubuntu 8.04, and also set up ndiswrapper for my linksys wireless n connection. After doing this I was able to see my wireless network, but when I typed in the password, it wouldn't connect. I am using a 128 bit WEP security. Also my connection won't appear until I run 
```
sudo ndiswrapper -i ~/Desktop/wmp300n/bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```
which was what I did to set it ndiswrapper up. Any help would be appreciated. I am using Linksys wmp300n.
Thanks.

---

### Post by starcannon on 2008-05-28
Heres a how to guide in the forums:
[http://ubuntuforums.org/showthread.php?t=718244&highlight=wmp300n](http://ubuntuforums.org/showthread.php?t=718244&highlight=wmp300n)

A poster reported a happy ending with the 300n give that a go, and since its madwifi it should be much easier and stable than the ndiswrapper method anyway.

---


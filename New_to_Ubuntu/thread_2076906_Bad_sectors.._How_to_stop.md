---
title: "Bad sectors.. How to stop????"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by handofdave on 2012-10-27
does anyone out there know how to stop a bad sector from spreading?? The disk utility reports 1 bad sector

---

### Post by AlexDudko on 2012-10-27
Ubuntu Disk Utility? Have you tried your hardware vendor's one?  Does it show the same result? It could be a software issue.

---

### Post by NikTh on 2012-10-27
> **handofdave said:**
> does anyone out there know how to stop a bad sector from spreading?? The disk utility reports 1 bad sector

Hi , 

If your HDD started to fail , you cannot stop it. The bad sectors nowadays are reallocated and the HDD don't use them. It is not necessary to do it manually , the HDD has this ability (to reallocate the bad sectors). 

Some people say that you can modify the /etc/fstab to tweak the partition , but I am not sure if this will help you. See here for further knowledge in /etc/fstab : [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

You can check once per month and see if the bad sectors value increase with these commands 

This command run it once , is for install the tools 
```
sudo apt-get install smartmontools --no-install-recommends
```Then once per month you can run this command 
```
sudo smartctl -a /dev/sda
```I assume that /dev/sda is the disk with the problem. 
You can find detailed explanations of the results here : [http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).
You can find the letters of the dist with this command 
```
sudo fdisk -l
```Thank you.

---

### Post by handofdave on 2012-10-27
thank you i will try that out.

---


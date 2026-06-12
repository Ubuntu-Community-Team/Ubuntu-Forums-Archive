---
title: "installing both Kubuntu and Ubuntu on a machine , without downloading anything ."
date: 2008-09-05
forum: New to Ubuntu
---

### Post by medya on 2008-09-05
hey I have both Kubuntu and Ubuntu 8.04 CDs (64 bit) I wanna have both of them installed .

in some tutorials they say you install ubuntu first then using apt-get you install kubuntu (this requires downloading, and my internet is slow)
and also I dont like ubuntu and kubuntu affect each other's work .
I wanna have two pure Operation System and I wanna experieance both of them.

what should I do ?

---

### Post by tjajab on 2008-09-05
A simple way would be to install Ubuntu and then install kubuntu as a virtual system in Ubuntu (for example by using VMWare or KVM), or the other way around. Or both as virtual systems in Windows.

---

### Post by revanb on 2008-09-05
You can create two (or more as you require) partitions on your harddrive. Then you install each version seperately to a different partition. Then you configure grub so that that it will give you a menu at boot time as to which you want to use.

Basically its gonna be a dual boot system!

---

### Post by Elfy on 2008-09-05
If you already have the updates and a livecd I would make a dual boot as revanb has said.

Install ubuntu on the second partition, you can copy your packages onto the second installation so you won't need to download those again, you can use aptoncd if you like - it's in the repos ```
sudo apt-get install aptoncd
```

Once you have 2 up to date ubuntus you can decide which to use as kubuntu - you will have to download the kubuntu packages, but it's not as much as getting the whole livecd - approx 150Mb last time I did it.

Then you can remove ubuntu from the kubuntu installation.

One way ro the other you have to get the kubuntu packages doing it this will require less to be downloaded.

Psychocats has pages on getting kubuntu on your ubuntu and removing ubuntu.
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---


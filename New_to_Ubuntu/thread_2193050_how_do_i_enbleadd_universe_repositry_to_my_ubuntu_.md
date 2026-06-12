---
title: "how do i enble/add universe repositry to my ubuntu 13.10? please help me."
date: 2013-12-11
forum: New to Ubuntu
---

### Post by pambreesh on 2013-12-11
i have reinstalled  ubuntu 13.10 saucy. actually the problem is that when i try to download from ubuntu software centre , it says the software is availble from the universe source , and showing an option of 'use this source' but when i click it nothing happen in progress bar. it is not with all softtwares but most of them. actually when earlier i installed i was facuing the same problem i found something(command) on internet and ran it on terminal. and then it works. but now i dont have that command . i also  have enabed universe source in setting software and updates tab. bbut still faacing this. can anybody please provide me those commands to add repositry  for saucy. i can remeber that it was three step command. having 'sudo' in first command. update in second or third. please i dont understand all thease things please help me plz. because without it my ubuntu is looking useless all the useful softwares need that universe repositry. thanks in advance.

---

### Post by Bucky Ball on 2013-12-11
What happens when you:

```
sudo apt-get update
sudo apt-get upgrade
```

Please post the exact errors output.

---

### Post by pambreesh on 2013-12-11
when i run theaswe commands in terminal. thhis is result

Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
amrish@amrish-desktop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by Bucky Ball on 2013-12-11
You haven't got Synaptic or Software Centre open at the same time you are trying to do this by any chance?

Please post your sources file.

```
nano /etc/apt/sources.list
```

Paste the output of that command here.

---


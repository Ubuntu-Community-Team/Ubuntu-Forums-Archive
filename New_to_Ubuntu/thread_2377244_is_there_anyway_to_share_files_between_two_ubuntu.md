---
title: "is there anyway to share files between two ubuntu?"
date: 2017-11-10
forum: New to Ubuntu
---

### Post by wanggaoteng on 2017-11-10
hi, these days i install ubuntu(16.04) in my two homework computers, the computers use home wifi to explore the Internet. 
is there anyway to share files between the homework computers without install third-party softwares?
P.S. ubuntu is the only one OS installed in the computers, and, sorry for my poor English.
bestregards.

---

### Post by kc1di on 2017-11-10
Hello wanggaoteng  and welcome to ubuntu Forums,

It would depend on what you mean by share files. and what type of files you want to share.
It should be no problem to copy files from one computer to the other.   You should be able to set up sharing in your home network with not problem.
can the two computer see each other on the net work?  you could also sync file via dropbox (available in the repositories.) or using usb sticks. etc.
so give us a little more information on what your trying to do.

---

### Post by wanggaoteng on 2017-11-10
> **kc1di said:**
> Hello wanggaoteng  and welcome to ubuntu Forums,

It would depend on what you mean by share files. and what type of files you want to share.
It should be no problem to copy files from one computer to the other.   You should be able to set up sharing in your home network with not problem.
can the two computer see each other on the net work?  you could also sync file via dropbox (available in the repositories.) or using usb sticks. etc.
so give us a little more information on what your trying to do.
hi, kc 1 di, i want to make one folder in every homework computer as the share folder, so one computer can copy files in the share folder.
and, is there anyway to know whether the two computer see each other on the network?
P.S. dropbox has been forbidden in my country.
Bestregargs.

---

### Post by deadflowr on 2017-11-10
The file manager has a builtin file sharing utility you can setup by right clicking on the folder you want to share inside the Files program and selecting the Local Network Share.
It will need to download some extra software, but it's small in size and Ubuntu will automatically set it up for you.
Once it's setup other the machines on your local network should also see it.
(You can then try accessing it through the Files application's Browse Network option.)

Hope it helps

---

### Post by wanggaoteng on 2017-11-11
> **deadflowr said:**
> The file manager has a builtin file sharing utility you can setup by right clicking on the folder you want to share inside the Files program and selecting the Local Network Share.
It will need to download some extra software, but it's small in size and Ubuntu will automatically set it up for you.
Once it's setup other the machines on your local network should also see it.
(You can then try accessing it through the Files application's Browse Network option.)

Hope it helps

hi, deadflowr, thank you very much.
Following your direction, after checking "allow anonymous login" in the share folder priorities of computer A,  it works very well, in computer B, i can copy files from the share folder.
But when i checkout "allow anonymous login", namely, if i want to copy files, i should input password. after input the name and password, i still cannot open the share folder.

Thank you, bestregards.

---

### Post by Morbius1 on 2017-11-11
> **wanggaoteng said:**
> hi, deadflowr, thank you very much.
Following your direction, after checking "allow anonymous login" in the share folder priorities of computer A,  it works very well, in computer B, i can copy files from the share folder.
[COLOR=#0000cd]**But when i checkout "allow anonymous login", namely, if i want to copy files, i should input password.**[/COLOR] [COLOR=#0000cd]**after input the name and password, i still cannot open the share folder**[/COLOR].

Thank you, bestregards.
There are two passwords. One is the local user name and password - the one you use to log into your actual machine. The other is the password you use across the network.

Let's say your user name on Machine A is          wanggaoteng. You need to add that user name to the file sharing password database:
```
sudo smbpasswd -a wanggaoteng
```

---

### Post by wanggaoteng on 2017-11-11
> **Morbius1 said:**
> There are two passwords. One is the local user name and password - the one you use to log into your actual machine. The other is the password you use across the network.

Let's say your user name on Machine A is          wanggaoteng. You need to add that user name to the file sharing password database:
```
sudo smbpasswd -a wanggaoteng
```

Hi, Morbius1, your directions are very clear and helpful, now i can share files between the two computers using passward. 
Thank you very much.
Bestregards.

---


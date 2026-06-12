---
title: "Adding a new repository address"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by Befeltingu on 2012-05-09
Hey so this is a total newb question. 
            To add a new repository address I read that you can use the command line to just edit /etc/apt/sources.list and add the address to the list. But etc/apt/sources.list is not even in my system. When I type it into the command line it says it is not a list or a directory. Do I just create it and then add the repository to it? I got the Repository I wanted using synaptic but wanted to know how to do it using the command line.

---

### Post by Enigmapond on 2012-05-09
On the PPA's page, about halfway up on the left side, you will see in bold letters something like **ppa:whateverthename/ppa**. Open a terminal and add that line after:

```
sudo add-apt-repository
```
so it will look like this:

 
```
sudo add-apt-repository ppa:whateverthename/ppa
```

This will add it andd import the public key. Then just run an update and install whatever you need.

---

### Post by Befeltingu on 2012-05-10
> **Enigmapond said:**
> On the PPA's page, about halfway up on the left side, you will see in bold letters something like **ppa:whateverthename/ppa**. Open a terminal and add that line after:

```
sudo add-apt-repository
```so it will look like this:

 
```
sudo add-apt-repository ppa:whateverthename/ppa
```This will add it andd import the public key. Then just run an update and install whatever you need.

Thanks for the response. 
Im not sure why but i couldnt get it to work unless i used the gksudo  gedit /etc/apt/sources.list and then just manually insterted the address  into the file and saved it. 
when i tried sudo add-apt-repository it said it needed repository as an argument which im guessing is because maybe what i was getting was not actually a repository? Im not sure im a Linux newb

---

### Post by wilee-nilee on 2012-05-10
> **Befeltingu said:**
> Thanks for the response. 
Im not sure why but i couldnt get it to work unless i used the gksudo  gedit /etc/apt/sources.list and then just manually insterted the address  into the file and saved it. 
when i tried sudo add-apt-repository it said it needed repository as an argument which im guessing is because maybe what i was getting was not actually a repository? Im not sure im a Linux newb

The add ppa puts it in a file

/etc/apt/sources.list.d
command 
Give us the ppa and we can give you the right command.

---


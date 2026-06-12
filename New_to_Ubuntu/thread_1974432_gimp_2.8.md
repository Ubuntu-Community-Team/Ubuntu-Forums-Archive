---
title: "gimp 2.8"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by bre5 on 2012-05-06
Hi

I am running Xubuntu on a net book.
I have got gimp 2.6 installed and would like to upgrade to the latest stable version which is gimp  2.8.  Following the instructions on the gimp download page and running 'apt-get install gimp'  [FONT=Verdana]should give the latest version but I keep getting the message that the latest version is already installed.  Even if I remove gimp from my system and run this code it still downloads gimp 2.6.  So how do I upgrade to gimp 2.8 ?

thanks
Brian
[/FONT]

---

### Post by orange2k on 2012-05-06
You need to do the following in terminal:

```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp

```

---

### Post by Avaritia on 2012-05-06
Open a terminal and enter these two commands one at a time:
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp

```The first one will add the gimp PPA, like a mini repository and the second command will install it.

Edit: beat me to it :)

---

### Post by bre5 on 2012-05-06
Thanks
tried that and got 
W: Failed to fetch [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
brian@brian-laptop:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gimp is already the newest version.

So still got 2.6

Brian

---

### Post by zombifier25 on 2012-05-06
That PPA is not updated for Lucid (and probably never will) so you're out of luck.

---

### Post by orange2k on 2012-05-06
> **bre5 said:**
> Thanks
tried that and got 
W: Failed to fetch [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
brian@brian-laptop:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gimp is already the newest version.

So still got 2.6

Brian

What version of Xubuntu are you running?

---

### Post by bre5 on 2012-05-06
running

Xfce 4 Desktop Environment
version 4.6.1 (Xfce 4.6)

Not really bothered what distro I run as long as it runs on an oldish netbook. Only use it for internet and photo's hence the desire to update to gimp 2.8

---

### Post by orange2k on 2012-05-06
> **bre5 said:**
> running

Xfce 4 Desktop Environment
version 4.6.1 (Xfce 4.6)

Not really bothered what distro I run as long as it runs on an oldish netbook. Only use it for internet and photo's hence the desire to update to gimp 2.8

Yeah but what xubuntu?
Is it Lucid, Maverick, Natty, Oneiric, Precise or some other?

---

### Post by bre5 on 2012-05-06
Lucid

---

### Post by orange2k on 2012-05-06
> **bre5 said:**
> Lucid

Unfortunately, the repository we mentioned in our posts is not supported in Lucid. So you'll need to upgrade to something newer like Oneiric or Precise, or alternatevely compile Gimp 2.8 from source. 

Instructions for this are here:

[http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu](http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu)

---

### Post by studiogrynn on 2012-05-11
WARNING!  That PPA states that it will likely break Oneiric, so if your goal is to upgrade The Gimp to 2.8, you may wish to avoid that distro and go with Precise.

---

### Post by sadaruwan12 on 2012-05-11
It's better if you upgrade to 12.04 'cos lucid will loose the support and the software updates very soon.

---

### Post by I2k4 on 2012-05-12
I've used this compilation of the beta 2.7 (has the single window GUI) successfully in Mint 10 and Mint 11:

GIMP 2.7 for older Ubuntu versions (unofficial):

ppa:matthaeus123/mrw-gimp-svn

I'm not good with the terminal, I just added the PPA to the repositories in Synaptic PM, and update - the 2.7 replaces 2.6 and can be installed from there.  The GIMP data extras and UFRaw plug ins work fine with it.

---

### Post by shreepads on 2012-05-18
> **orange2k said:**
> Unfortunately, the repository we mentioned in our posts is not supported in Lucid. So you'll need to upgrade to something newer like Oneiric or Precise, or alternatevely compile Gimp 2.8 from source. 

Instructions for this are here:

[http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu](http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu)

Those instructions are for 12.04 not Lucid and are a little incomplete.

I've created the following post for noobs like me, is for Ubunutu Lucid 10.04.4, but should work for Xubuntu as well: 

[How to use GIMP 2.8 on Lucid 10.04.4 LTS]("http://ubuntuforums.org/showthread.php?t=1982183")

---


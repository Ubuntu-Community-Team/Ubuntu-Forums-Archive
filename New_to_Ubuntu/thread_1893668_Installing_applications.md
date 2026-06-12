---
title: "Installing applications"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by LuckiCharmzXP on 2011-12-10
I'm a new linux ubuntu user. I have installed Ubuntu 11.10 directly and I did the same upgrades and I can't seem to figure out how to install programs. I know some basic terminal commands.

I've tried doing the following commands when im in the folder that I extracted from the tar.gz:
./config
make
make install

and it doesn't even install. I've tried installing adobe flash and chrome with .deb extensions and whenever I install them through the software manager it doesn't install. Any help here for a new linux user?

---

### Post by mörgæs on 2011-12-10
Hi, welcome to the fora. 

I have moved your question to a new thread.

You should hardly ever install with **make**. Almost everything of value is in the repositories.

If you restart the computer and run
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
can you install after this? 

Please post the error messages, if any.

---

### Post by cybergalvez on 2011-12-10
> **LuckiCharmzXP said:**
> I'm a new linux ubuntu user. I have installed Ubuntu 11.10 directly and I did the same upgrades and I can't seem to figure out how to install programs. I know some basic terminal commands.

I've tried doing the following commands when im in the folder that I extracted from the tar.gz:
./config
make
make install

and it doesn't even install. I've tried installing adobe flash and chrome with .deb extensions and whenever I install them through the software manager it doesn't install. Any help here for a new linux user?

How do you know the programs are not installed? did you get any errors? what does the synaptic show for the packages you tried to install? 

In general installing programs on ubuntu is very simple assuming you stick to the default packages. Using the software center or synaptic is the simplest way install software. Although google does make you download a deb file which just installs a custom repository.

Jose

---

### Post by dFlyer on 2011-12-10
Install synaptic from the command line with the following:

sudo apt-get install synaptic
sudo apt-get update

Then launch synaptic and search for the programs you wish to install. Only if you can't find a program your looking for should you compile from source. Of course you can do the same thing with Ubuntu Software Center when it comes to searching for and installing programs. If your need to install from source, after you extract the file look for a text file named README or Install and read them as they will explain what needs to be done. But again installing from source should be your last choice.

---

### Post by LuckiCharmzXP on 2011-12-10
> **mörgæs said:**
> Hi, welcome to the fora. 

I have moved your question to a new thread.

You should hardly ever install with **make**. Almost everything of value is in the repositories.

If you restart the computer and run
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
can you install after this? 

Please post the error messages, if any.

After sudo apt-get upgrade and enter Y if i want to continue I get:

Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-libc-dev i386 3.0.0-14.23
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.0.0-14.23_i386.dev](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.0.0-14.23_i386.dev) Something wicked happened resolving 'ca.archive.ubuntu E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

---

### Post by mörgæs on 2011-12-11
So, did 
```
apt-get --fix-missing
```
help?

---

### Post by Spyderkid on 2011-12-11
install programs from the software center?
If for some reason you don't have it type
```
apt-get install software-center

```

---

### Post by 3rdalbum on 2011-12-11
> **LuckiCharmzXP said:**
> After sudo apt-get upgrade and enter Y if i want to continue I get:

Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-libc-dev i386 3.0.0-14.23
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.0.0-14.23_i386.dev](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.0.0-14.23_i386.dev) Something wicked happened resolving 'ca.archive.ubuntu E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

Try changing the mirror you're using. Go to Software Center, then in the Edit menu go to "Software Sources".

In this new program that opens, you can choose a different server to get your software from.

---


---
title: "Tar.gz"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Tharakanuwanpro on 2008-06-16
How can install Tar.gz things ? What are they ? I searched the net and found out some icon packs but how can i install them . This is the instructions they give me

wget [http://ubuntu-debs.googlecode.com/files/Elementary_1.7.tar.gz](http://ubuntu-debs.googlecode.com/files/Elementary_1.7.tar.gz) ; tar zxvf Elementary_1.7.tar.gz ; mv Elementary_1.7 ~/.icons

But i don't have internet on ubuntu .
I am running Ubuntu 8.04

---

### Post by the_doc on 2008-06-16
> **Tharakanuwanpro said:**
> What are they ?

It's a Tape ARchive file compressed with GZip.  Similar to a zip file in windows I guess.

---

### Post by Flimm on 2008-06-16
.tar.gz is a compressed archive, similar to .zip. They can contain practically anything.
You can install an icon pack by clicking on System, Preferences, Appearance, Install. You'll find the icon pack by clicking Customize.
The instructions you were given download the archive, uncompress it and move it to /home/username/.icons , which is what the way I suggested will do behind the scenes, minus the downloading part.

---

### Post by hyper_ch on 2008-06-16
wget just downloads the .tar.gz to your computer.... copy it by other means to your computer and run the commands then in the according directory where you copied the .tar.gz to.

---

### Post by Tharakanuwanpro on 2008-06-16
How can i install this CompiZ thingi

---

### Post by sharks on 2008-06-16
This link will be useful for u:
[www.lifehacker.com/software/ubuntu/how-to-install-anything-in-ubuntu-231105.php](www.lifehacker.com/software/ubuntu/how-to-install-anything-in-ubuntu-231105.php)
[www.monkeyblog.org/ubuntu/installing/](www.monkeyblog.org/ubuntu/installing/)

---

### Post by ChameleonDave on 2008-06-16
> **Tharakanuwanpro said:**
> How can install Tar.gz things ? What are they ? I searched the net and found out some icon packs but how can i install them . This is the instructions they give me

wget [http://ubuntu-debs.googlecode.com/files/Elementary_1.7.tar.gz](http://ubuntu-debs.googlecode.com/files/Elementary_1.7.tar.gz) ; tar zxvf Elementary_1.7.tar.gz ; mv Elementary_1.7 ~/.icons

But i don't have internet on ubuntu .
I am running Ubuntu 8.04

Do not try to compile and install raw software code in tar.gz archives.  It is **not** for newbies.

Please open up Synaptic and use it to install and remove all software that you are interested in.

Later, when you are an experienced Linux user, you can play with compiling.  If you need to ask here, then you are not ready to start!

Just use Synaptic.

---

### Post by Flimm on 2008-06-16
> **ChameleonDave said:**
> Do not try to compile and install raw software code in tar.gz archives.  It is **not** for newbies.

Please open up Synaptic and use it to install and remove all software that you are interested in.

Later, when you are an experienced Linux user, you can play with compiling.  If you need to ask here, then you are not ready to start!

Just use Synaptic.
Tharakanuwanpro's not talking about source tarballs. Tharakanuwanpro's talking about a icon set, which are practically always in .tar.gz. You can't install icon sets using Synaptic.

---

### Post by Tharakanuwanpro on 2008-06-16
How can i install Compiz

---

### Post by ChameleonDave on 2008-06-16
> **Tharakanuwanpro said:**
> How can i install Compiz
Use Synaptic.

Or, type the following into a terminal:

```
sudo apt-get install compiz
```

---

### Post by ChameleonDave on 2008-06-16
> **Tharakanuwanpro said:**
> How can install Tar.gz things ? What are they ? I searched the net and found out some icon packs but how can i install them . This is the instructions they give me

wget [http://ubuntu-debs.googlecode.com/files/Elementary_1.7.tar.gz](http://ubuntu-debs.googlecode.com/files/Elementary_1.7.tar.gz) ; tar zxvf Elementary_1.7.tar.gz ; mv Elementary_1.7 ~/.icons

But i don't have internet on ubuntu .
I am running Ubuntu 8.04
Sorry, I thought you were installing software there.

Here is what you need to do to install your icons.  I am basing these instructions on the instruction you quoted.

Somehow download the file that they mention.  Put it onto your Ubuntu desktop.

Type the following commands into a terminal, pressing Enter after each:

```

cd ~/Desktop
tar zxvf Elementary_1.7.tar.gz
mv Elementary_1.7 ~/.icons

```

---

### Post by oldos2er on 2008-06-16
> **Tharakanuwanpro said:**
> How can i install Compiz

 Compiz-fusion is installed by default in Ubuntu 8.04. Look under System, Preferences, Appearance, Visual Effects.

---


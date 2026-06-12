---
title: "Installing F-Spot"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by ejpyle on 2008-08-01
Well I just downloaded F-Spot  from [http://f-spot.org/Download](http://f-spot.org/Download) and I am trying to figure out how to install it. Could anyone outline the steps for me to accomplish this? F-Spot's website was not very helpful for us Linux noobies....

---

### Post by niyonk on 2008-08-01
I am assuming you downloaded [this]("http://ftp.gnome.org/Public/GNOME/sources/f-spot/0.4/f-spot-0.4.4.tar.bz2")

ok :)

-Open the file you downloaded (using any archive manager you have) 
EDIT:I just noticed inside that file there is another archive lol, silly. that's the one you should extract 
-extract it to your home folder
-open terminal
-type cd f-spot*
-type ./configure
-type make
-type sudo make install 

Actually, the steps are right on [their website]("http://f-spot.org/How_To_Build_from_Release") :lolflag:

Unless you wanted to install SVN version :)

Cheers!

---

### Post by nick_h on 2008-08-01
It is in the repositories so you can install it with:
```
sudo apt-get install f-spot
```
or you can use the Synaptic package manager.

If you really need to install software not in the repositories have a look at - [How to install ANYTHING in Ubuntu!](http://monkeyblog.org/ubuntu/installing/).

---

### Post by ejpyle on 2008-08-01
> **niyonk said:**
> I am assuming you downloaded [this]("http://ftp.gnome.org/Public/GNOME/sources/f-spot/0.4/f-spot-0.4.4.tar.bz2")

ok :)

-Open the file you downloaded (using any archive manager you have)
-extract it to your home folder
-open terminal
-type cd f-spot*
-type ./configure
-type make
-type sudo make install 

Actually, the steps are right on [their website]("http://f-spot.org/How_To_Build_from_Release") :lolflag:

Unless you wanted to install SVN version :)

Cheers!


Well I followed those steps...then I get this message....

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


Which is why the directions they have are not much help

---

### Post by niyonk on 2008-08-01
Why would you want to compile it if you said you are new to this anyway :-k.

Like nick said, install it from synaptics or Applications->Add or Remove Applications. :guitar: It is always the same as the latest on the website.

EDIT: run 'sudo apt-get install build-essential' in terminal, maybe you are missing some compiler features? I am not sure.

---

### Post by ejpyle on 2008-08-01
> **niyonk said:**
> Why would you want to compile it if you said you are new to this anyway :-k.

Like nick said, install it from synaptics or Applications->Add or Remove Applications. :guitar: It is always the same as the latest on the website.

EDIT: run 'sudo apt-get install build-essential' in terminal, maybe you are missing some compiler features? I am not sure.

I can not run it from Synaptic because Ubuntu only has 0.4.3 which has a bug when trying to export to SMugmug hosting.....

F-Spot corrected the bug in the 0.4.4 release which is why I have no choice but to compile it.  synaptic does not have the newer version

---

### Post by niyonk on 2008-08-01
Did you try building essentials then repeating the steps to see if the gcc error disappears?

---

### Post by ejpyle on 2008-08-02
How do I resolve this error


checking pkg-config is at least version 0.9.0... yes
checking for MONO_DEPENDENCY... yes
checking for al... /usr/bin/al
checking for mono... /usr/bin/mono
checking for mcs... no
configure: error: No C# compiler found
configure: error: ./configure failed for gio-sharp

---

### Post by nick_h on 2008-08-04
Install a C# compiler such as mono.

---

### Post by cariboo on 2008-08-04
As niyonk said above, make sure you have build-essential installed. Once you have install the meta package, delete config.log and run configure again.

Jim

---


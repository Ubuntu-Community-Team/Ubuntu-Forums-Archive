---
title: "Building from source...."
date: 2008-06-08
forum: New to Ubuntu
---

### Post by RadarBat on 2008-06-08
How do you build a linux game from source?  Ben

---

### Post by ChameleonDave on 2008-06-08
> **RadarBat said:**
> How do you build a linux game from source?  Ben

Typically, to compile a program from source in Linux, you do the following:
[LIST]
[*]Download a compressed archive containing the source code
[*]Uncompress it
[*]Use the "cd" command in the console to go to the newly created directory
[*]type "./configure"
[*]type "make"
[*]type "sudo install"
[/LIST]
The archive may contain a "readme" file with further information.

If this seems tricky, then you're probably not ready to start compiling.  Install programs from Synaptic instead.

---

### Post by Prospero2006 on 2008-06-08
It depends on which game. 
Generally speaking, source code is distributed in a zip format.
ie linux-game.tar.gz

The first step is to unzip the file:
tar -xzvf linux-game.tar.gz

Once the file is unzipped, there is either a makefile or a configure
file in the base directory. 

If there is a configure file you type:
```

./configure
make
make install

```

If there are errors, you'll have to apt-get install the missing libraries.

If there is a Makefile, but no configure you can just make and then make install.

Hope that helps

---

### Post by ad_267 on 2008-06-08
You will need the build-essential package to compile. This is a good read: [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by Oldsoldier2003 on 2008-06-08
if you have never compiled a program on your computer before you'll need to install the build-essential package as it is not installed by default.

```
sudo apt-get install build-essential
```

---


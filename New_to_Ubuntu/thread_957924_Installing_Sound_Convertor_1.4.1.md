---
title: "Installing Sound Convertor 1.4.1"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by poldie on 2008-10-24
I tried installing Sound Convertor using the add/remove tool, but it's installed an old version.  I like the look of the new version, so I've downloaded it from [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/) but clearly it's obviously to everyone but me how to install it.  It looks like it's only availble in a `here's the source code - compile it yourself` file, but I don't know how to do this.  I've unpacked it and tried to run the install-sh file but it's not having it.

Is there some standard way of installing files when the source is available?  Normally I'd experiment, but I don't want to harm my system.

These instructions are repeated in a few places on the net:

[http://www.detector-pro.com/2008/09/how-to-install-sound-converter-on.html](http://www.detector-pro.com/2008/09/how-to-install-sound-converter-on.html)

but that's probably going to get the old version again, isn't it? If I install from the source, is it going to get those other libraries etc? 

I've tried to install stuff myself and had problems with dependencies (using the command line dpkg, I think), so I used a front end tool instead (the Synaptic one) which worked.  It seems that Linux is more or less designed for command line use, so is there a way of using dpkg and having it handle dependencies for you?

Cheers in advance.

---

### Post by gborzi on 2008-10-25
> **poldie said:**
> I tried installing Sound Convertor using the add/remove tool, but it's installed an old version.  I like the look of the new version, so I've downloaded it from [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/) but clearly it's obviously to everyone but me how to install it.  It looks like it's only availble in a `here's the source code - compile it yourself` file, but I don't know how to do this.  I've unpacked it and tried to run the install-sh file but it's not having it.

Is there some standard way of installing files when the source is available?  Normally I'd experiment, but I don't want to harm my system.

These instructions are repeated in a few places on the net:

[http://www.detector-pro.com/2008/09/how-to-install-sound-converter-on.html](http://www.detector-pro.com/2008/09/how-to-install-sound-converter-on.html)

but that's probably going to get the old version again, isn't it? If I install from the source, is it going to get those other libraries etc? 

I've tried to install stuff myself and had problems with dependencies (using the command line dpkg, I think), so I used a front end tool instead (the Synaptic one) which worked.  It seems that Linux is more or less designed for command line use, so is there a way of using dpkg and having it handle dependencies for you?

Cheers in advance.

Hello Poldie,
generally when you install from source, you need to have the libraries already installed, along with the compiler. Luckily, soundconverter is in python, an interpreted language, so you don't need libraries and compilers, just python which is installed by default (if I remember correctly). To be sure, install and then uninstall the soundconverter package in the repos. The installation will install all the required packages, which will remain after you uninstall.
Let's start the installation: uncompress the tar.gz source file ```
tar -xzf soundconverter-1.4.1.tar.gz
```
enter the soundconverter-1.4.1 directory compile and install
```
./configure
make
sudo make install
```
the last command will ask for your password and install the program under /usr/local. It won't make a menu entry, you will have to do it yourself.
Let me know if this works for you.

---

### Post by Pro-reason on 2008-10-25
Is there any particular feature of the latest SoundConverter that you absolutely must have?  If not, then simply use the version in the repositories, which people have gone to time and effort to make available to you.  It is known to work, and will not mess up your system.

If you want to be cutting-edge, and risk instability in order to have the latest everything, then go ahead and learn to install this from source.

You can't really have it both ways.

Ubuntu 8.10 &#8220;Intrepid Ibex&#8221; is about to come out (at the end of the month).  It will have a lot of updated software.  According to [Packages.Ubuntu.com]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=soundconverter"), the latest version for Hardy is [1.0.1]("http://mirrors.kernel.org/ubuntu/pool/universe/s/soundconverter/soundconverter_1.0.1-0ubuntu2_all.deb") and the latest for Intrepid is [1.3.2]("http://mirrors.kernel.org/ubuntu/pool/universe/s/soundconverter/soundconverter_1.3.2-0ubuntu1_all.deb").

---

### Post by poldie on 2008-10-25
> **Pro-reason said:**
> Is there any particular feature of the latest SoundConverter that you absolutely must have?  If not, then simply use the version in the repositories, which people have gone to time and effort to make available to you.  It is known to work, and will not mess up your system.

If you want to be cutting-edge, and risk instability in order to have the latest everything, then go ahead and learn to install this from source.

You can't really have it both ways.

Ubuntu 8.10 “Intrepid Ibex” is about to come out (at the end of the month).  It will have a lot of updated software.  According to [Packages.Ubuntu.com]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=soundconverter"), the latest version for Hardy is [1.0.1]("http://mirrors.kernel.org/ubuntu/pool/universe/s/soundconverter/soundconverter_1.0.1-0ubuntu2_all.deb") and the latest for Intrepid is [1.3.2]("http://mirrors.kernel.org/ubuntu/pool/universe/s/soundconverter/soundconverter_1.3.2-0ubuntu1_all.deb").

It looks like 1.4.1 has APE support, which seems to be missing from mine, although I can't tell from the changelog in which version it was added.  I know I can't have it both ways - I was hoping that learning to install from the source would be a result of my post!

Yes, I can hardly wait for 8.10!

---

### Post by poldie on 2008-10-25
> **gborzi said:**
> Hello Poldie,
generally when you install from source, you need to have the libraries already installed, along with the compiler. Luckily, soundconverter is in python, an interpreted language, so you don't need libraries and compilers, just python which is installed by default (if I remember correctly). To be sure, install and then uninstall the soundconverter package in the repos. The installation will install all the required packages, which will remain after you uninstall.
Let's start the installation: uncompress the tar.gz source file ```
tar -xzf soundconverter-1.4.1.tar.gz
```
enter the soundconverter-1.4.1 directory compile and install
```
./configure
make
sudo make install
```
the last command will ask for your password and install the program under /usr/local. It won't make a menu entry, you will have to do it yourself.
Let me know if this works for you.

I tried what you suggested earlier, but it fails on ./configure with:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

and config.log seems to be a script of some sort.

---

### Post by Pro-reason on 2008-10-25
> **poldie said:**
> I tried what you suggested earlier, but it fails on ./configure with:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

and config.log seems to be a script of some sort.

Out of curiosity, I have just tried to compile the source code for versions 1.3.2, 1.4.0, 1.4.1 and 1.2.0.  I get that error for all of them.  I'm not a C programmer, but I feel that code must be badly written if it can't compile out-of-the-box on the most common Linux distro.

If the version in the Hardy repos is not recent enough for you, manually download the .deb for Intrepid and install that.  Wait for the latest version to be packaged by the experts.

In any case, SoundConverter is just a front-end.  The real work is done behind the scenes.  If you're savvy enough to compile stuff, you should be savvy enough to convert media files on the command line.

---

### Post by Pro-reason on 2008-10-26
Oops, silly me!

I've recently created a new partition, and I forgot to put “exec” in my /etc/fstab file so that files on it can execute.  I've now set that right.

I can compile the source code now.  You too should make sure that you can use executable files on the drive in question.

Also, install this software:

```

sudo apt-get install **python-gnome2 gawk build-essential**

```

---

### Post by Pro-reason on 2008-10-26
Here's a repo with the latest version.  Install it like this:

```

cd /etc/apt/
sudo cp sources.list sources.list.backup
echo "deb http://ppa.launchpad.net/chameleondave/ubuntu hardy main" | sudo tee -a sources.list
echo "deb-src http://ppa.launchpad.net/chameleondave/ubuntu hardy main" | sudo tee -a sources.list
sudo apt-get update
sudo apt-get install soundconverter faac lame gstreamer0.10-plugins-ugly

```

---

### Post by poldie on 2008-10-26
> **Pro-reason said:**
> Oops, silly me!

I've recently created a new partition, and I forgot to put “exec” in my /etc/fstab file so that files on it can execute.  I've now set that right.

I can compile the source code now.  You too should make sure that you can use executable files on the drive in question.

Also, install this software:

```

sudo apt-get install **python-gnome2 gawk build-essential**

```


My Ubuntu install is out of the box too, so I'll have default permissions on fstab and whatever.  

Are you saying I should install that python thing before I compile sound converter?

---

### Post by Pro-reason on 2008-10-26
> **poldie said:**
> My Ubuntu install is out of the box too, so I'll have default permissions on fstab and whatever.  
Hmm, yeah, but the similarity of the error makes me think that you must somehow have the same problem.

> **poldie said:**
> 
Are you saying I should install that python thing before I compile sound converter?

Yep.

Or just install SoundConverter from the extra repository that I mentioned above.

---

### Post by poldie on 2008-10-26
> **Pro-reason said:**
> Hmm, yeah, but the similarity of the error makes me think that you must somehow have the same problem.

Yep.

Or just install SoundConverter from the extra repository that I mentioned above.

My fstab file doesn't have execute.  Not too surprising, as it's a text file - i'm not sure what you mean by "...so that files on it can execute" as it's a text file.  How do you execute a text file?  But I'll do that now, and install the python software.

(Few mins later) - that's better, it's getting further, but now I'm getting the error:

configure: error: The intltool scripts were not found. Please install intltool.

I installed intltool via synaptic (it, in turn, needs a few megs of other stuff installed, so easier for me to use synaptic than to try and compile that from source)

Ah - I think that's fixed it.  It's installed into usr/local/bin.

How did you know to install that python stuff?  Is that something I should/could have been able to work out from an error message or something?

Thanks for all your help - it's really appreciated.

---

### Post by Pro-reason on 2008-10-26
This is getting a bit off-topic, but here is my /etc/fstab file (cleaned up a bit):

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>                                   
proc            /proc           proc    defaults        0       0                                        

# /dev/sda3
LABEL=Kubuntu   /               reiserfs notail,relatime 0       1

# /dev/sdb5
LABEL=Files     /media/Files       ext3    user,auto,exec  0       1

# /dev/sdb7
**LABEL=Extra     /media/Extra       jfs     user,auto,exec  0       1**

# dev/sda2: 
LABEL=Windows   /media/Windows    ntfs-3g    defaults,umask=007,gid=46,noauto,user 0       1

/dev/sda1       none            swap    sw              0       0
/dev/sdb1       none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


```

See the line in bold?  That's what makes my Extra partition mount at start-up.  I had to add “exec” to it to make it possible to run executable files from that partition.

There are two types of executable files: binary executables, and scripts.  The latter are just text files that contain code, and which have their executable bit set with “chmod” (you can also do it from the file manager).

---

### Post by Pro-reason on 2008-10-26
> **poldie said:**
> 

Ah - I think that's fixed it.  It's installed into usr/local/bin.

How did you know to install that python stuff?  Is that something I should/could have been able to work out from an error message or something?


You just have to do as you did with intltool.  You run the configure script and make.  When it complains that a certain bit of software is absent, you go and install it by any means available.  Rinse and repeat until it compiles correctly.  Then “sudo make install”.

The trouble with “sudo make install” though, is that it bypasses Ubuntu's standard packaging system, which is based on DPKG and APT.  You won't get any updates for soundconverter unless it is installed by a package.  It's also tricky to uninstall stuff which is put there by “sudo make install”.  In general, unless you're willing to deal with all the consequences, it's better to install a .deb (manually or via a repository).

---

### Post by poldie on 2008-10-26
> **Pro-reason said:**
> This is getting a bit off-topic, but here is my /etc/fstab file (cleaned up a bit):

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>                                   
proc            /proc           proc    defaults        0       0                                        

# /dev/sda3
LABEL=Kubuntu   /               reiserfs notail,relatime 0       1

# /dev/sdb5
LABEL=Files     /media/Files       ext3    user,auto,exec  0       1

# /dev/sdb7
**LABEL=Extra     /media/Extra       jfs     user,auto,exec  0       1**

# dev/sda2: 
LABEL=Windows   /media/Windows    ntfs-3g    defaults,umask=007,gid=46,noauto,user 0       1

/dev/sda1       none            swap    sw              0       0
/dev/sdb1       none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


```

See the line in bold?  That's what makes my Extra partition mount at start-up.  I had to add “exec” to it to make it possible to run executable files from that partition.

There are two types of executable files: binary executables, and scripts.  The latter are just text files that contain code, and which have their executable bit set with “chmod” (you can also do it from the file manager).

Amusingly, I seem to have utterly missed the point - what I did was to use chmod to make the fstab file executable!  I only have 1 partition with all my linux stuff on it (I have a few other ntfs ones with my Windows XP disk plus some mp3s and photos), so that's nothing to do with my earlier problem, so it was probably the install of that python package which did the trick.  I'll make my text file unexecutable again now!  :)

---

### Post by poldie on 2008-10-26
> **Pro-reason said:**
> You just have to do as you did with intltool.  You run the configure script and make.  When it complains that a certain bit of software is absent, you go and install it by any means available.  Rinse and repeat until it compiles correctly.  Then “sudo make install”.

The trouble with “sudo make install” though, is that it bypasses Ubuntu's standard packaging system, which is based on DPKG and APT.  You won't get any updates for soundconverter unless it is installed by a package.  It's also tricky to uninstall stuff which is put there by “sudo make install”.  In general, unless you're willing to deal with all the consequences, it's better to install a .deb (manually or via a repository).

I'm not sure what's going to happen when I upgrade to 8.10.  I've mostly installed stuff via either Synaptic or the add/remove tool.  I guess it'll be some combination of not ungrading certain apps, and breaking others. Hopefully not too much of the latter!

---


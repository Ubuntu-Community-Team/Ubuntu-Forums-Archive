---
title: "emelfm2, utility file manager, now with gtk2!"
date: 2005-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by landotter on 2005-10-22
My favorite file manager for heavy duty work is now available in sexy gtk2! :D

Great for renaming series of files and changing permissions on recursive directories.

:)

Get it from here: [http://master.grad.hr/~ivoks/ubuntu/emelfm2_0.1.0-1ubuntu1_i386.deb]("http://master.grad.hr/%7Eivoks/ubuntu/emelfm2_0.1.0-1ubuntu1_i386.deb")

[IMG]http://static.flickr.com/28/54772932_571dc17f4e_o.jpg[/IMG]

---

### Post by kleeman on 2005-10-22
Its not in my synaptic. Which apt repository is it in?

---

### Post by kleeman on 2005-10-22
btw I compiled it from source (version 0.1.2) easily enough and it looks very nice. Thanks for the tip...

---

### Post by landotter on 2005-10-22
[quote=kleeman]Its not in my synaptic. Which apt repository is it in?[/quote]

Ooopsies. It's only in Synaptic since I installed it. LOL, Wow, I feel stupid. :P

You can grab a Ubuntu deb here: [http://master.grad.hr/~ivoks/ubuntu/emelfm2_0.1.0-1ubuntu1_i386.deb]("http://master.grad.hr/%7Eivoks/ubuntu/emelfm2_0.1.0-1ubuntu1_i386.deb")

Please excuse me, I don't get out much. :D

---

### Post by dsyates on 2005-11-26
I have built a  deb of the latest version of emelfm2 for ubuntu 5.10. It can be found here:

[http://lottalinuxlinks.com/files/emelfm2_0.1.3-1_i386.deb](http://lottalinuxlinks.com/files/emelfm2_0.1.3-1_i386.deb)

---

### Post by landotter on 2005-11-28
[quote=dsyates]I have built a  deb of the latest version of emelfm2 for ubuntu 5.10. It can be found here:

[http://lottalinuxlinks.com/files/emelfm2_0.1.3-1_i386.deb]("http://lottalinuxlinks.com/files/emelfm2_0.1.3-1_i386.deb")[/quote]

:up: excellent! Thanks!

---

### Post by foxy123 on 2005-11-28
[QUOTE=dsyates]I have built a  deb of the latest version of emelfm2 for ubuntu 5.10. It can be found here:

[http://lottalinuxlinks.com/files/emelfm2_0.1.3-1_i386.deb](http://lottalinuxlinks.com/files/emelfm2_0.1.3-1_i386.deb)[/QUOTE]
how does start emelfm2?
```
:~$ emelfm2
bash: emelfm2: command not found

```

---

### Post by Evoreth on 2005-11-28
[QUOTE=foxy123]how does start emelfm2?[/QUOTE]

```
sudo mv /usr/X11R6/bin/emelfm2 /usr/local/bin/emelfm2
```

After that try it again.

---

### Post by foxy123 on 2005-11-28
[QUOTE=Evoreth]```
sudo mv /usr/X11R6/bin/emelfm2 /usr/local/bin/emelfm2
```

After that try it again.[/QUOTE]
thanks, it fixed it...

---

### Post by dsyates on 2005-12-29
The latest (emelfm2-0.1.4) packaged for ubuntu breezy is now availale at [http://lottalinuxlinks.com/emelfm2/]("http://lottalinuxlinks.com/emelfm2/")
 and more directly [http://lotalinuxlinks.com/files/emelfm2_0.1.4-1_i386.deb]("http://lotalinuxlinks.com/files/emelfm2_0.1.4-1_i386.deb")

---

### Post by aragorn2909 on 2005-12-30
Great, my favourite file manager now looks good too!

---

### Post by buildid on 2005-12-30
thanks , normally i use "mc" but this it seems iam gonna use this one for a while...

---

### Post by Gandalf on 2005-12-30
[QUOTE=Evoreth]```
sudo mv /usr/X11R6/bin/emelfm2 /usr/local/bin/emelfm2
```

After that try it again.[/QUOTE]
/usr/X11R6/bin/emelfm2 is installed via the deb file so it's not advised at all to move it, please use symlinks instead!!

```

sudo ln -s /usr/X11R6/bin/emelfm2 /usr/bin/emelfm2

```

---

### Post by ykpaiha on 2005-12-30
how is it possible this one could be forgotten by Ubuntu!!!

mc is in repos but not emlfm2 !!!!

sad it's far before any, the easiest tool around...

---

### Post by Haegin on 2007-11-04
Does anybody have a package for 64bit gutsy?

---

### Post by cronos6 on 2007-11-13
same here, where I could find a 64bit version for Gusty ?

Thanks ;)

---

### Post by kleeman on 2007-11-13
Get one from here:

[http://www.math.nyu.edu/faculty/kleeman/amd64/](http://www.math.nyu.edu/faculty/kleeman/amd64/)

---

### Post by kpictjl on 2007-11-27
Anybody have the 32bit version for emelfm2 for gutsy?

My version that I used in Feisty core dumps all the time since I've updated to gutsy.

---

### Post by kpictjl on 2007-11-27
I downloaded the latest source-code release is: emelfm2-0.3.5.tar.gz (1055 kb) - 2007-07-27, from [http://http://emelfm2.net/emelFM2]("http://http://emelfm2.net/emelFM2")

I untar'd the file then tried to compile.

```
$ make
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
```

This tells me I don't have and environment variable called PKG_CONFIG_PATH
[QUOTE]$ env | grep PKG
@pacman:~$[/CODE]

Synaptic tells me that gtk2-engines is installed...is that the right package?  I'm not sure what emelfm2 is looking for in order to compile.

---

### Post by kpictjl on 2007-11-29
> emelfm2 version 2-0.3.6 was released yesterday
[http://emelfm2.net/rel/emelfm2-0.3.6.tar.gz](http://emelfm2.net/rel/emelfm2-0.3.6.tar.gz)
fixes some annoying bugs with gnome.
 -- DY

I was able to compile after installing libgtk2.0-dev

```
sudo apt-get install libgtk2.0-dev
```

Then I did the make, sudo make install, and all was well.

emelfm2 works great in gutsy.

I tried to build a deb package by but for some reason my system can't find "configure."

```
bighead@pacman:~/mydownloads/emelfm2-0.3.6$ ./configure
bash: ./configure: No such file or directory

```

I installed checkinstall and tried to build the package as in the instructions below, but no-joy.

> Create an Ubuntu (Debian) package (.deb)

Install package tools:

gksudo apt-get install checkinstall

Rebuild package using "checkinstall":

cd /path/to/extracted/package
./configure
make
checkinstall

Keep the resulting ".deb" file for future use. It can be installed using:

gksudo dpkg -i package.deb

Note: These are basic instructions that may not always work. Some packages require additional dependencies and optional parameters to be specified in order to build them successfully. 

---

### Post by kpictjl on 2007-11-30
Dave Yates has the latest Gutsy compatible deb file posted...

[http://lottalinuxlinks.com/files/emelfm2_0.3.6-1_i386.deb](http://lottalinuxlinks.com/files/emelfm2_0.3.6-1_i386.deb)

---


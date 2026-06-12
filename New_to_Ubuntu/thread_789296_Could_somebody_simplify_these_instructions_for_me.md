---
title: "Could somebody simplify these instructions for me?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by gottabeandrew on 2008-05-10
Hi, could somebody make these instructions understandable for me please? I'm new.

[http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/)

I've downloaded the file to the desktop and thats as far as i've got.

---

### Post by TeoBigusGeekus on 2008-05-10
Open a terminal and type
```
cd /home/yourusername/Desktop
```
to navigate to your desktop.

Then type
```
tar xvf flashcam-X.Y.tgz
```
to unpack the compressed file.

There should be a folder on your Desktop now, called flashcam-X.Y
```
cd flashcam-X.Y
```
to navigate into the folder.

```
make
```
to compile the package

and 
```
sudo make install
```
to install it. You will be asked your password - type it and press enter.

I think you can take it from here...

---

### Post by gug@fnal.gov on 2008-05-10
locate where the file is, go to that directory and use the tar command to unpack it and write out as individual directories and files. Optionally first copy the file to some place you like working:

> mkdir build
> cd build
> tar  xvf ../flashcam-X.Y.tgz

Next you are going to change directories into the top level of the new directory tree created by unpacking the tar file. 
> cd flashcam-X.Y

Now you need to build the software, which means both compile, archive and link to form the libraries and executables.
> make

Now you need to install the libraries and executables in places the system will look when you try to run the application. Note you will need to use sudo this time.
> sudo make install

Just remember that in the instructions any command that has "[root]%" as the prompt before it should be executed with "sudo" in Ubuntu. Follow along each step as the instructions say, and see how far you get.

---

### Post by gottabeandrew on 2008-05-10
Thank you so much! I've had this problem for weeks and now it works. But 1 last thing. It says this in the instructions further down:

> During install a start up script has been set up so the module loading procedure will be automatic at boot time. This script is /etc/init.d/fcinit. On properly configured systems all /dev/videoN devices will have the correct permissions set when user takes console (see trouble shooting for details).

Now, using the wrapper is not that transparent, so a helper has also been setup at install time. Two predefined applications have been symbolically linked to the wrapper: firefox and flashplayer. No panic, original scripts or executables are intact. We have to make a given path take precedence on the common path for the wrapper to be automatically called when these applications are started.

In your ~/.bashrc file add the following line at the beginning:
PATH=/usr/local/flashcam/bin:$PATH


I don't want to mess up my system so i thought i'd ask you people before i did this. There is 1 .bashrc file at etc/init.d called bash.bashrc. I assume this is the file it's referring to. Could somebody please verify this. Thanks.

---

### Post by TeoBigusGeekus on 2008-05-10
The symbol ~ denotes /home/yourusername folder. So there should be a file
called .bashrc in there.

---

### Post by gottabeandrew on 2008-05-10
There isn't a file called that in there.

---

### Post by TeoBigusGeekus on 2008-05-10
Ok then.
```
gksudo gedit etc/init.d/bash.bashrc
```
and add the proposed line. Save, reboot and post us what happened.

---


---
title: "need help with installing from source"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by rehat on 2008-05-27
Hi I'm a noob with Linux and I'm trying to understand as much as I can about it.  Right now I'm working on installing new apps from a source tar.gz file and I know I can just do a apt-get, but I just want to learn how to do it from source.  I'm having troubles with ./configure when trying to install kmymoney2 or amarok. I get this same error message for both:

[B]configure: WARNING: libjpeg not found. disable JPEG support.
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.[/B]

They install fine when I use apt-get for these two programs.  Can anyone tell me what the problem is.  Also any tips or sites on how resolve ./configure errors.  Any help would be great.  Thanks

---

### Post by Maestro23 on 2008-05-27
First thing you need installed is "build-essential".

> sudo apt-get install build-essential

Compiling from source: [https://help.ubuntu.com/community/CompilingSoftware?highlight=(compiling](https://help.ubuntu.com/community/CompilingSoftware?highlight=(compiling))

*Each program should come with a README/Install doc or instructions on its website. Should also tell you any required dependencies that will be needed for the program.  You will have to install these before you can continue.

Good luck and have fun. :smile:

---

### Post by oldos2er on 2008-05-27
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by RequinB4 on 2008-05-27
Check out the first link in my signature.

For future reference, if a configure script says something like "**configure: WARNING: libjpeg not found. disable JPEG support.**" chances are "libjpeg" is just a package you need to install from synaptic/apt in order to have that feature enabled.

---

### Post by Paqman on 2008-05-27
Well, it's always good to learn how to do new things, so go for it.

However, compiling from source isn't really very sound practice on any distro that uses a package manager. Occasionally it might be your only choice, but 99.99% of the time you'll have a more stable system if you stick to the package manager.

---


---
title: "HOWTO: Install php-gtk 2.0 alpha"
date: 2007-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by eteran on 2007-01-07
This guide is meant to be an easy step to step guide
to simplify the installation of php-gtk 2.0 alpha.

**- Tested on**
Xubuntu 6.10 x64
should work on Ubuntu 6.04 x86/x64, Ubuntu 6.10 x86 too (please confirm)

**- Installing required packages**
php-gtk requires the php commandline and devel package in at least version 5.1.
Besides we need the build-essentials, the libgtk2.0 devel and the libglade2 devel package.
```

sudo apt-get install build-essential php5-cli php5-dev libgtk2.0-dev libglade2-dev

```

**- Installing php-gtk**
Grab php-gtk from the official homepage, extract and change dir.
```

wget http://gtk.php.net/do_download.php?download_file=php-gtk-2.0.0alpha.tar.gz
tar xzf php-gtk-2.0.0alpha.tar.gz
cd php-gtk-2.0.0alpha/

```

Build the source
```

./buildconf
./configure
make
sudo make install

```

**- Enable php-gtk in the php.ini**
Open the corresponding php.ini in your favorite editor.
i.e.:
```

sudo joe /etc/php5/cli/php.ini

```

Look for the "Dynamic Extensions" Section and add
```

extension=php_gtk2.so

```

And you're done!

*I'm willing to give Support, as good as I can. But still, use this guide at your own risk!*

_Related information and information used to create this guide:_
- [http://gtk.php.net](http://gtk.php.net)
- [http://gtk.php.net/manual/en/tutorials.installation.linux.php](http://gtk.php.net/manual/en/tutorials.installation.linux.php)
- [http://php.classes.free.fr/wiki/index.php5?title=Gtk2/InstallUnix#Installing_under_ubuntu](http://php.classes.free.fr/wiki/index.php5?title=Gtk2/InstallUnix#Installing_under_ubuntu)

---

### Post by JoseArmandoJeronymo on 2007-01-25
I've tested it on Ubuntu Dapper and it worked fine! :-)

---

### Post by D-- on 2007-02-10
For Feisty Fox users:

Add this line to /etc/apt/sources.list

```
deb http://people.debian.org/~dexter php5.1 dapper
```

Run the following:

```
sudo aptitude update
sudo aptitude install build-essential php5.1-cli php5.1-dev libgtk2.0-dev libglade2-dev
```

Then follow eteran's directions from the wget line onward.

You may also want to do the following if this is a clean PHP install:

```
sudo aptitude install php5.1-common php5.1-gmp php5.1-gd php5.1-bz2 php5.1-mbstring
```

Those are some kind of important modules to have.

---

### Post by unlotto on 2008-05-10
works fine in 8.04

---

### Post by another_sam on 2009-08-04
fails with 9.04 at the make step. it says:

make: *** No targets specified and no makefile found.  Stop.

"no makefile found" is the most humilliating message I've ever been told by a machine.

---

### Post by AndyCee on 2009-08-19
Strange, I had an error saying "LTOPTIONS_VERSION: command not found", with similar following.

I had to follow the instructions at [this site]("https://bugs.launchpad.net/ubuntu/+bug/262251") to fix the error. I may have done something wrong in installing the dependancies, but it's working now.

All to get the gui working for "Phoronix-test-suite" gui. Geez >-(

---

### Post by shofstetter on 2010-11-04
I have wrote a script to download compile and install the php-gtk2 extension In Ubuntu 10.10.

Just past the commands below in a terminal window and follow the instructions
it may take a while to complete.
It download and install all of the required packages 
Applies the necessary patches downloads builds/configures and complies the source and adds the extension to the php.ini 


```

wget http://carolinaboardrepair.com/php-gtk-install-ubuntu-10.10
chmod 777 php-gtk-install-ubuntu-10.10
./php-gtk-install-ubuntu-10.10

```Originally posted: [http://carolinaboardrepair.com/phpBB3/viewtopic.php?f=3&t=39](http://carolinaboardrepair.com/phpBB3/viewtopic.php?f=3&t=39)

---

### Post by jrz on 2010-11-16
> **shofstetter said:**
> I have wrote a script to download compile and install the php-gtk2 extension In Ubuntu 10.10.

Just past the commands below in a terminal window and follow the instructions
it may take a while to complete.
It download and install all of the required packages 
Applies the necessary patches downloads builds/configures and complies the source and adds the extension to the php.ini 


```

wget http://carolinaboardrepair.com/php-gtk-install-ubuntu-10.10
chmod 777 php-gtk-install-ubuntu-10.10
./php-gtk-install-ubuntu-10.10

```Originally posted: [http://carolinaboardrepair.com/phpBB3/viewtopic.php?f=3&t=39](http://carolinaboardrepair.com/phpBB3/viewtopic.php?f=3&t=39)

Thought the above might fix my problem, but still unable to use <?php in an html file, or from a terminal screen. Tried the example on the php wiki page also and it still does nothing. What am I missing?
Running ubuntu 10.10

---

### Post by Gulo gulo on 2010-11-20
Thank you for your effort to help , but you script doesn't work for me . How do you revert the changes the script made.

The Newbee

---


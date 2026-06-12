---
title: "HOWTO: Install Nitrogen from SVN on Feisty"
date: 2007-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by dbbolton on 2007-07-24
This guide will help you install Nitrogen from SVN on ubuntu feisty (7.04).

What is Nitrogen? It is a tool use to set your background image. Since GNOME, KDE, and Xfce already have tools to do this, Nitrogen is ideal for Openbox or Fluxbox users who want a graphical interface to change their wallpaper.

Project webpage: [http://l3ib.org/nitrogen/](http://l3ib.org/nitrogen/)

I wrote this guide because the .deb file that they link on their site doesn't work (for me), and SVN is always nice when you want to be able to use the latest version of developmental software. Plus, you don't have to wait for anyone to make a package for you :)

First, here is a list of software that I had to install before I installed Nitrogen on my computer. This list may vary from machine to machine. For instance, I may have had some of the required packages already installed before doing this. You are welcome to go ahead and install these, but if you want to escape redundancy or errors, you should just skip this part. When you're compiling it, it will tell you whether it lacks something.

```
sudo apt-get install build-essential subversion autoconf automake gettext libgtk2.0-dev libgtkmm-2.4-dev
```

In order to get the files, you have to "check them out" from the subversion repository:
```
cd ~
svn co http://svn.l3ib.org/nitrogen/trunk nitrogen
```

After that, there will be a folder called "nitrogen" in your home folder. It contains the source code. Now, change to that directory:
```
cd ~/nitrogen
```

The first thing you need to do is run
```
./bootstrap
```

If the output looks like this, then you're ready to go on to the next step:
```
+ libtoolize --copy --force --automake
/bin/sh: libtoolize: not found
+ aclocal
+ autoconf
+ autoheader
+ automake --include-deps --add-missing --copy
configure.ac:13: installing `./config.sub'
configure.ac:13: installing `./config.guess'
```
If not, then you probably have a dependency problem. If you can't get past the bootstrap, paste the output here and I'll try to help.

Next, run:
```
./configure
```
It should print
```
You are now ready to compile nitrogen
Type "make" to compile nitrogen
```

And that's exactly what you need to do:
```
make
```

Finally:
```
sudo make install
```

If at any time you want to get rid of Nitrogen, do this:
```
cd ~/nitrogen
sudo make uninstall
```

Here are usage instructions from the readme (~/nitrogen/README)
> Usage:  nitrogen [OPTIONS] DIRECTORY

Options:
        --no-recurse
                Do not recurse into subdirectories
        --restore
                Restore saved backgrounds
        --sort=[arg]
                How to sort the backgrounds. Valid options are:
                        * alpha, for alphanumeric sort
                        * ralpha, for reverse alphanumeric sort
                        * time, for last modified time sort (oldest first)
                        * rtime, for reverse last modified time sort (newest first)

DIRECTORY is the directory containing the backgrounds you wish to preview.  It
adds files recursively from here (so long as --no-recurse hasn't been supplied),
generating preview images asynchronously.

If you want to tell us about the many bugs that we have, drop by #gentoo.et on
irc.freenode.net, and talk to nightm4re or syscrash2k.

So, in my Openbox menu, I added an item that looks like this:
```
nitrogen --sort=alpha /home/daniel/images/wallpaper
```

I hope this helps :D

---

### Post by picpak on 2007-08-15
Thanks so much for this! The SVN didn't work, but version 1.0 did. I attached a .deb at the bottom of this post.

Also: to get Nitrogen to load on every login, edit ~/.xinitrc

```
nano .xinitrc
```

and put the following in:

```
#!/bin/sh

nitrogen --restore &
```

(#!/bin/sh is only needed if it's not at the top of the file.)

---


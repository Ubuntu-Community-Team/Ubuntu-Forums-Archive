---
title: "files to gedit"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-08
I have become enamored by these 'shell scripts' that are full of comments and bash commands and I want to explore them a bit more.  However, I don't really know what I have except for what I have been led to by others here in the forum. /boot/grub/menu.lst, and ~/.bashrc are the two that I specifically have looked at and tampered with.  SO...where do I begin?  Can I list 'geditable' files and them approach them in order?  How do ..I'm confused.

---

### Post by Iowan on 2008-10-08
I found [this]("http://ubuntuforums.org/archive/index.php/t-407989.html") one in the archives.  If it's CLI instructions you're looking for, check [here]("https://help.ubuntu.com/community/UsingTheTerminal").

---

### Post by bodhi.zazen on 2008-10-08
Or here :

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by ddarsow on 2008-10-08
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

excellent place to start

---

### Post by adamogardner on 2008-10-08
ok but how about some modifications you have made and where.  I learn best by example and this is really what I'm looking for.  these examples seem scarce online.

---

### Post by Iowan on 2008-10-08
Which kinds of files are you primarily interested in - shell scripts or command line instructions?  For some other shell-type examples, you can check the **/etc/rcX.d** directories, or the files in **/etc/init.d**.

---

### Post by nkri on 2008-10-08
I would try Conky.  It displays system (and just about any other) information right on your desktop, in a widget layer, in a separate window, or anything you want.  It is one of the most highly configurable and customizable programs I know of in Ubuntu.
```
sudo apt-get install conky
```
to install it, then create the file /home/*username*/.conkyrc.  There is a massive thread dedicated to this, with thousands of examples and ideas of how to configure it: [_http://ubuntuforums.org/showthread.php?t=281865_]("http://ubuntuforums.org/showthread.php?t=281865")

Also, you could try playing around with .bashrc (also with its own thread: [_http://ubuntuforums.org/showthread.php?t=679762_]("http://ubuntuforums.org/showthread.php?t=679762").  This one is also fun, but a bit more complicated.

You could try Nautilus scripts, which can make your workflow much faster when using a GUI: [_http://www.gnome-look.org/index.php?xcontentmode=188&PHPSESSID=9c904b3508124f7b3df764d8aeed099d_]("http://www.gnome-look.org/index.php?xcontentmode=188&PHPSESSID=9c904b3508124f7b3df764d8aeed099d")

Good luck!
-nkri

---

### Post by adamogardner on 2008-10-09
> **Iowan said:**
> Which kinds of files are you primarily interested in - shell scripts or command line instructions?  For some other shell-type examples, you can check the **/etc/rcX.d** directories, or the files in **/etc/init.d**.

ok, your asking the right question.  I'm interested in shell scripts not the CLI for this thread.  The examples I gave are the ones I know.  They are all I know that I have.  I want to view them all and get a better understanding of what's going on in my machine.  I will view those directories you mention here.  I think I am on the right track now.  ONE thing I really want to play with is making a sound effect for shutdown which although there is a gui there is a glich which makes shutdown not give a sound effect.  I would like to know the script for shutdown process so I can place a pause of 5 seconds and play a soundbite. as one example,

---

### Post by porchrat on 2008-10-09
shell scripts generally have the extension .sh e.g. filename.sh

If you want to locate ALL the .sh files in your system you can always run this command:

```
sudo find / -name "*.sh"
```

hope that helps.

---

### Post by adamogardner on 2008-10-09
> **porchrat said:**
> shell scripts generally have the extension .sh e.g. filename.sh

If you want to locate ALL the .sh files in your system you can always run this command:

```
sudo find / -name "*.sh"
```

hope that helps.

what about boot/grub/menu.lst , or ~/.bashrc ?  I see no .sh here.  Please explain.  Thankyou for the command this is exactly what I wanted I think.

---

### Post by aeiah on 2008-10-09
i think you've run into some confusion here. shell scripts, or scripts in general (bash scripts, python scripts, perl scripts etc) lie somewhere in between a 'list of instructions for the computer to perform' and a small program. 

things like menu.lst and .bashrc are configuration files. they're plain text files that contain strings in them that are human readable (and editable) and also machine readable. when a program or the operating system reads its configuration file, it uses the settings contained within it to behave in a certain way.

---

### Post by aeiah on 2008-10-09
for example, we'll look at mplayer. this is my configuration file for mplayer (there's another one thats more in depth, but there's no point posting that one)

```


monitoraspect=16:9
threads=2
subfont-text-scale=4
load_fullscreen = "yes"

```

its located in my home directory in .mplayer/config

mplayer will read this file and will use the settings ive stated in it. if i didnt want mplayer to always start playing a video in fullscreen mode, all id do, obviously, would be change the "yes" to a no "no" for the bottom string.

menu.lst, fstab, .bashrc, and all the others are the same kinda thing, albeit more complicated.

now, below is a script that uses mplayer as part of its list of instructions to perform:

```

#! /usr/bin/python

import sys, os

video = sys.argv[1]
os.system("unrar p -inul " + video + "|mplayer -fs -noidx -")

```

not the best example to be honest, but anyway. all this really does is enables you to play a video that's contained in a .rar archive through mplayer. its just a set of instructions for two particular progams: unrar and mplayer

---

### Post by adamogardner on 2008-10-09
> **aeiah said:**
> i think you've run into some confusion here. shell scripts, or scripts in general (bash scripts, python scripts, perl scripts etc) lie somewhere in between a 'list of instructions for the computer to perform' and a small program. 

things like menu.lst and .bashrc are configuration files. they're plain text files that contain strings in them that are human readable (and editable) and also machine readable. when a program or the operating system reads its configuration file, it uses the settings contained within it to behave in a certain way.

Ah okay, I see.  So I am interested in configuration files.  My mistake.  How do I find all these configuration files?  I like them.

---

### Post by Idefix82 on 2008-10-09
If you are looking at exploring the configurability of Ubuntu, try hitting Ctrl+h in the Nautilus and browsing through all the hidden files and folders in your home directory. A lot of it is self-explanatory and you will be surprised, what sorts of things you can modify via configuration files.

---

### Post by adamogardner on 2008-10-09
> **Idefix82 said:**
> If you are looking at exploring the configurability of Ubuntu, try hitting Ctrl+h in the Nautilus and browsing through all the hidden files and folders in your home directory. A lot of it is self-explanatory and you will be surprised, what sorts of things you can modify via configuration files.

there are a lot of directories with hidden material.  Is there a general tier or more specific directory I should be looking in?

---

### Post by adamogardner on 2008-10-09
so essentially any file that opens in gedit is a configuration file?

---

### Post by Idefix82 on 2008-10-09
For example ~/.gnome2 contains a lot of information on the configuration of your system. Eg if you a reusing evince to view pdf files then the ~/.gnome2/evince directory contains the default print settings for different printers that you have used which you can modify. Also, the ~/.gnome2/gedit directory will quickly become your friend if you install additional plugins for gedit or create templates for different files. In ./local/share you can define things like new mime types or syntax highlighting rules for gedit.

I guess what you can do with the hidden folders depends on what applications you use.

Not every editable file is a configuration file. There are shell scripts and other scripts, there are of course random documents like READMEs. The other way round it's also not so black and white. Gedit will not be the default application for .xml files for example, which are however very often configuration files.

---

### Post by porchrat on 2008-10-09
Generally speaking there are a lot of configuration files under the /etc directory.  Most programs create a directory in /etc which contains their configuration files, normally something along the lines of program_name.conf

Either that or they place their .conf file right into the /etc directory, with no subdirectory.

For example the x-server config file is located under /etc/X11/xorg.conf

And no any file that opens with gedit isn't necessarily a configuration file.  It just means that file contains text that has been encoded in a way that gedit can read (normally ISO-8859 or UTF-8 ).  Most shell and bash scripts for example, can be opened by gedit, as can normal word processor files like a .doc.  Think of gedit kind of like a Microsoft Notepad on steroids.

---

### Post by adamogardner on 2008-10-09
I found this in another's bashrc file. How does this work?:  I ask because the extract command isn't in my book and there is no manual entry.  Please break it down a bit. 

extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

---

### Post by Idefix82 on 2008-10-09
Looks to me like the list of commands that are executed when you choose to extract the given package format in the package manager. Eg opening the file /home/MyName/file.tar.bz in nautilus by double clicking it and then pressing "Extract" is equivalent to opening the terminal and typing in
```
tar xjf /home/MyName/file.tar.bz
```

The sign $1 stands for "current file". If you want to look up the syntax of the tar command, just type
```
man tar
```
in the terminal.
Suppose for example, that you want the default behaviour to be to preserve the owner of the extracted bz2 files rather than setting you to be the owner. Then you could change the line I quoted to read
```
tar -xj --same-owner -f $1
```

---

### Post by porchrat on 2008-10-09
If this thread goes on long enough it could double as an "ubuntu walkthrough" :)

---

### Post by adamogardner on 2008-10-09
> **porchrat said:**
> If this thread goes on long enough it could double as an "ubuntu walkthrough" :)

not

---


---
title: "the Ubuntu install shield"
date: 2007-08-21
forum: Programming Talk
---

### Post by hammer v2 on 2007-08-21
Installing programs in Ubuntu is easy and simple....as long as your ubuntu PC is connected to the internet. I'm trying to develop a simple way to make programs portable and installable with a simple double click. Most of the work has already been done in the form of apt on CD, but I want to take it a bit further. Now, here's the catch, I'm not a programmer, so I've been trying to do it all with bash scripts,

Here's where I'm up to...I need a LOT of help here (I've never scripted before)

#!/bin/bash
# Hamish's dodgy setup script

gksudo -k /bin/echo "login der"

sudo mv -f /etc/apt/sources.list /etc/apt/sources.list.bak

sudo mv -f /etc/apt/sources.list.d /etc/apt/sources.list.d.bak

sudo cp sources.list -t 

sudo apt-cdrom -d /media/cdrom

sudo apt-get update

sudo gdebi-gtk /packages/setup.deb

sudo mv -f /etc/apt/sources.list.bak /etc/apt/sources.list

sudo mv -f /etc/apt/sources.list.d.bak /etc/apt/sources.list.d

zenity --info \
          --text="Setup Completed. You can now run the program from the applications menu"

exit 1
fi

The aim of this script was to add it to a CD created with apt on CD.

You insert the CD then run the script by clicking on setup.sh and whammo! everything is installed.

[IMG]http://www.hamishrobertson.net/scribus/Screenshot-k3bcd%20-%20File%20Browser.png[/IMG]

This is how it works (feel free to chime in here if you think this could be improved) 

Apt on CD creates an apt repository on CD and a metapackage that installs everything on the CD. I rename the metapackage to setup.deb.

I add 2 files to the CD, the setup.sh script and a blank sources.list file.

When the script is run it renames the hosts sources.list and sources.list.d files to something else, imports the blank sources.list file, then adds the CDrom repository.

It then runs a really fast apt-get update then installs (graphically using gdebi-gtk.

Once that is finished it puts the original sources.list and sources.list.d in the correct spots and exits.

Er, follow? 
Anyway, I can't get it to work properly! Help!!!

Hamish

---

### Post by pmasiar on 2007-08-21
IIRC there is a project to create GUI frontend for apt from CD.

---

### Post by foxylad on 2007-08-21
I think I'm right that if you distribute your app as a *.deb you can just double-click on it to install. Apt-get adds the repository/download mechanics to this, but in essence just downloads the *.deb file and runs dpkg on it (which is what clicking on it from gnome does). 

Will this do what you want?

---

### Post by hammer v2 on 2007-08-22
The deb files work great, as long as you're on the internet. I'm trying to devise a way to install programs without internet dependance.

This script, creates a new sources.list file with only the CDrom as the repository then opens setup.deb which is just a metapackage that id dependant on everything else. 

I need help with the script? Come on you scripting junkies! :)

H.

---

### Post by Nekiruhs on 2007-08-22
> **hammer v2 said:**
> The deb files work great, as long as you're on the internet. I'm trying to devise a way to install programs without internet dependance.

This script, creates a new sources.list file with only the CDrom as the repository then opens setup.deb which is just a metapackage that id dependant on everything else. 

I need help with the script? Come on you scripting junkies! :)

H.
What exactly is the error you get? 

sudo gdebi-gtk /packages/setup.deb

Is telling gdebi-gtk to look for a folder /packages Inside the root partition of the users HD.

it should be 
gksudo gdebi-gtk packages/setup.deb

Please don't use sudo with Graphical apps, its just not intended to be used that way.

---

### Post by slavik on 2007-08-22
so, basically, you are creating a repo on the CD with packages and stuff and then you have setup.deb which is dependant on everything on the CD?

sounds neat (nice for distributing stuff on CD).

question/suggestion. Would it be possible to create a mini synaptic that only searches/looks on the CD it comes on (like synaptic but much lighter. something between synaptic and gdebi).

then you can install proper/selected .deb files via dpkg -i instead of apt and messing with user's repo stuff.

---

### Post by pmasiar on 2007-08-22
OK you cannot google so I have to do it.

Trivial Google search "debian repository cd" yielded [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by hammer v2 on 2007-08-23
Thanks nekirus, I will update the script for sure. I'm such a newbie to this. 

Now pmasiar, this is based off apt on CD. I'm gettin apt on cd to package everyhing up for me and create the magical metapackage. all I'm soing is creating a setup script so the whole thing becomes a windows-like install experience.

I got it working today sort of but I still need a little more help.

When I run apt-cdrom add /cdrom

I have to hit enter to mount the CD. Anyway of bypassing this or adding something into the script that will hit enter automatically?

This is a big deal as the main market for this setup script is for people who can't read english.

Any Ideas scripting gurus?

---

### Post by pmasiar on 2007-08-23
> **hammer v2 said:**
> This is a big deal as the main market for this setup script is for people who can't read english.

But they can read in their own language, right?

---

### Post by hammer v2 on 2007-08-24
> But they can read in their own language, right?

nup! Seriously! It's for a lao distro of ubuntu. Any reading or hitting enter is all just too hard, double clicking on setup is pushing it! I'm serious! 

SO getting back toi my original question...How can I make apt-CDrom NOT ask me to "insert a CD and hit ENTER"? I just want it to do it automatically. The cd will already be in the drive cause the script calling apt-cdrom is on the cd. :)

HELP!!!!

This is the last piece of the puzzle!!!!

---

### Post by pmasiar on 2007-08-24
I am not sure how to make programs for people who cannot read.

OLPC project is such a system, but they use wireless for communication, exactly to avoid this problem. You may take a look at the GUI the use, Sugar.

Sorry but when user cannot press ENTER, when asked, universe won, and I am out of game.

---

### Post by winch on 2007-08-24
Pipe the output of [yes]("http://en.wikipedia.org/wiki/Yes_(Unix)") into apt-cdrom

```

yes | apt-cdrom add /dev/cdrom

```

Why do these users need to install software themselves? Can't you just install all they will need in the first place? If pressing enter is too much they are not going to need a diverse range of programs.

---

### Post by hammer v2 on 2007-08-26
THANK YOU! IT WORKS!! ok, so now, how do i make my script file run from the cd? it currently just opens in gedit. is there any way that i can make it a program as opposed to a shell script? right clicking and making the file an executeable wont work. any ideas? H.

---


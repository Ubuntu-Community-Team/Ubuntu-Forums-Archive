---
title: "HOWTO: Setup conky with conkyexpress prebuilt conkyrc template"
date: 2006-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by lp7413 on 2006-08-04
Hello everyone, I am making this a mini HOWTO for conky.  Conky can definately be a rough thing to conquer for people who don't know scripting languages, however some people want to use conky without having to master these skills.  If your looking for that, then this is for you.  Conkyexpresss is simply just a modified .conkyrc file that will go in your home directory ~/  

Also included is a script called xmms.sh.

In order to get this to work you will need to have xmms installed, with xmms-infopipe plugin.  

Type:

sudo apt-get install xmms xmms-infopipe 

in your terminal.

With this plugin and script your conky will display your current playing song information from xmms. 

Untar the file conkyexpress-0.0.1.tar.gz to your ~/ directory, when you download try to save it to the ~/ (home directory) because that is how I am describing this install!

In your terminal do this:

$cd ~/
$tar -zxvf $conkyexpress-0.0.1.tar.gz

$mv conkyexpress ./.conkyrc

$chmod +x ./xmms.sh

$conky

Now when you run conky express you should see the new config display on your screen.  It defaults to transparent, with white text.

Now to make changes to the file

in gnome/ubuntu (standard)

$gedit ~/.conkyrc


in xubuntu/xfce

$mousepad ~/.conkyrc

Kde/kubuntu users, please use your favorite text editor to open the file .conkyrc from your home directory.

Now carefully read each commented section of this config file, as I have laid out details to each section on how to make the changes you might wish to tweak.

Please join #linuxsociety on freenode if you have any questions,  my irc name is ttyfscker.  You may also find me in #ubuntu #ubuntu+1 #xubuntu or #xfce

Thanks for trying out these small scripts/configs!!  Good Luck and Enjoy!!!

---


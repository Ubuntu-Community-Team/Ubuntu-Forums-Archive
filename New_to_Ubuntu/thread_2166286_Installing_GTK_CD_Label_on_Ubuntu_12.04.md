---
title: "Installing GTK CD Label on Ubuntu 12.04"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by amayan on 2013-08-08
Hello there, hoping someone may be able to help enlighten me on installing gtk cd label [http://gtkcdlabel.sourceforge.net/](http://gtkcdlabel.sourceforge.net/)  on ubuntu 12.04.

I've tried to find a program similar to the window's CoverPro for printing dvd covers and labels and this is the best ubuntu equivalent i could find, but am still open to ideas if there's something easier for me to handle. It's for someone who's never used ubuntu before so need it to be fairly straightforward.

Anyway, i've been looking on the website for a while now and feel a bit overwhelmed and aren't really any wiser to how to get it up and running. I've installed the cdlabelgen I found in the software centre and looked around for the other two but feel pretty out of my depth now. I know python's some kind of script thing but that's about all i can sum up.

Hopefully someone can give me a bit of a nudge here, and i apologise for still being a bit of a noob in this ubuntu world lol

---

### Post by amayan on 2013-08-08
Just a bit more info incase anyone can help, i've downloaded the tar.bz2 file for gtkcdlabel, checked i have GTK, python and pygtk and installed cdlabelgen from software centre. I've followed the intructions from [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) and get stuck at the 'Resolving Dependencies' section after running ./configure as it tells me there's no such file or directory. I've also followed other instructions on another forum and extracted the tar via the terminal but get stuck at the same place. I think the package mustn't have the parts i'm trying to work with. 

The README tells me > "INSTALLATION: tar -xjvf gtkcdlabel*tar.bz2 /". Within the decompressed folders there are files ending in .glade, .ui, .spec, .desktop, .xpm and .py. Am i trying to install the wrong type of files in the wrong way or something?

---

### Post by Richard_York on 2013-10-29
Hi, 
Did you sort your problem out? I'm also new to this, also trying to find a way of creating CD labels.
 There's one called circleprint in the software centre, but when I installed it, it (a) told me it was missing parts, and so would work the preview and (b) it was way beyond my comprehension! It has no reviews, so perhaps no-one else got it working either.

So if you've solved the problem I'd love to know, please! ... especially if it's in a way I can work. I confess that pythons still only mean large snakes to me...

---

### Post by amayan on 2013-10-30
Hiya fella, yeah I know what you mean haha. 

N no I never sorted the problem out for GTK, n after much mucking about I eventually found and ended up installing something called 'wxCovers', and it turned out to be really simple to install. It can be found at [http://sourceforge.net/projects/wxcover/](http://sourceforge.net/projects/wxcover/)

However, it doesn't have a preset for on-disk cd labels, but should be easy enough done with cd front and/or custom format setting it has. 

Hope it works out for you :)

---

### Post by vichman67 on 2014-01-08
Hi,

I'm almost new to Ubuntu 12.04, and absolute beginner on cdlabelgen, but I'm researching on this issue and I've found the way to run GTKcdlabel. Here are the detailed steps:

1. Be sure you have installed GTK (I have lots of GTK packages preinstalled on my Ubuntu, like libgtk2*, gtk2-engines*, etc., so I suppose it's a standard package), Python (package python and lots of other python-*) and pygtk (package called python-gtk2).

2. Install cdlabelgen from the software center.

3. Download gtkcdlabel-1.15.tar.bz2 and gtkcdlabel.py from the official URL ([http://sourceforge.net/projects/gtkcdlabel/files/gtkcdlabel/1.15/](http://sourceforge.net/projects/gtkcdlabel/files/gtkcdlabel/1.15/)) to your preferred directory for downloads, i.e. /home/victor/Downloads/.

From now on, open a shell terminal and type the following commands inside its interface.

4. Go to the downloads directory from the shell terminal: "cd /home/victor/Downloads".

5. Uncompress the bz2 file: "sudo tar -xjvf gtkcdlabel*tar.bz2 /". GTKcdlabel doesn't need neither compilation nor install, just uncompression.

6. You've got it. In order to run GTKcdlabel, you just have to execute the gtkcdlabel.py script. In my case, I open a shell terminal and type "python /home/victor/Downloads/gtkcdlabel.py", and the GTK GUI opens up. If you close the shell terminal, GTKcdlabel will close too.

7. Of course, you can delete the bz2 file ("rm /home/victor/Downloads/gtkcdlabel-1.15.tar.bz2"), and put gtkcdlabel.py anywhere you want. Remember where is that 'anywhere' so you can run "python /anywhere/gtkcdlabel.py" later.

As I told you early on, I've not used GTKcdlabel. I'll try it in the next weeks.

Hope it helps!

---


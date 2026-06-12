---
title: "How to install keepass?"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by Apertus on 2012-08-25
Hi all,

I've just downloaded Ubuntu, I really need to get keepass working before I can figure everything out. I'm wondering if it's possible for someone to give me step by step instructions on how to install it?

[http://sourceforge.net/projects/keepass/forums/forum/329220/topic/4503818](http://sourceforge.net/projects/keepass/forums/forum/329220/topic/4503818)

Thank you all, 

P.S. I know this post makes me sound very demanding and arrogant, but I promise to learn the OS once I get my passwords! ):P

---

### Post by newb85 on 2012-08-25
Hi, and welcome!

The page you linked has all you need, but I'm sure the important information seemed cryptic.

> to use it type into a terminal:
sudo apt-add-repository ppa:jtaylor/keepass
sudo apt-get update
sudo apt-get install keepass2Jtaylor108 created a ppa (a Personal Package Archive), which is an additional place for your package manager (apt-get) to find software.  (Both the Software Center and Synaptic run on apt-get, so this applies to them as well.)

To use it, open a terminal (ctrl+alt+t) copy and paste those three lines one-at-a-time into it, hitting Enter after each one.  (Note that to paste into the terminal, you will have to use ctrl+shift+v.)  After the first one, it will ask for your password, which is of course the password you set up when you installed Ubuntu.

Keep in mind that in setting up this ppa you are trusting Jtaylor108, since he or she is responsible for what is in the ppa.

---

### Post by Apertus on 2012-08-25
Thank you very much, I appreciate the fast reply!

I've never installed a program like that before.

---

### Post by newb85 on 2012-08-25
If everything installed properly, please mark this thread as solved.  At the top of the page, click Thread Tools>Mark as Solved.

---

### Post by Carborundum on 2012-08-25
For the record, keepass2 version 2.18 is already in the repositories. There is no need to add that ppa unless you need version 2.19 for some reason.

In the future, if you are looking for some application, start by searching for it in Software Center.

---

### Post by newb85 on 2012-08-25
@ Apertus - I recommend a little further reading to understand how software package management works in Ubuntu.  

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Warning--Some of the information on the page is a little outdated.  (And some of the images look like they came from Jaunty or Karmic.)

To be effective in Ubuntu, you should be comfortable installing from the command line (how you installed keepass).

If you don't know exactly what program you're looking for, the Software Center is a great place to start.  It shouldn't require any reading to figure out.

---

### Post by RolfBly on 2012-10-06
> **Carborundum said:**
> In the future, if you are looking for some application, start by searching for it in Software Center.

Thank you for this. Saved me a LOT of time.

---

### Post by TimEnid on 2013-03-24
I am trying to install Keepassx 2 from here
[http://www.keepassx.org/news/2012/10/367](http://www.keepassx.org/news/2012/10/367)
Its a tar file. And i cant figure out how to get it installed. This is the name of the Tar file "keepassx-2.0-alpha3.tar.gz"
I saved it to my Download folder, but when trying to follow the instructions on installing a tar file, i cant get it done. This app is not available in synaptic or the software center.

---

### Post by newb85 on 2013-03-25
> **TimEnid said:**
> I am trying to install Keepassx 2 from here
[http://www.keepassx.org/news/2012/10/367](http://www.keepassx.org/news/2012/10/367)
Its a tar file. And i cant figure out how to get it installed. This is the name of the Tar file "keepassx-2.0-alpha3.tar.gz"
I saved it to my Download folder, but when trying to follow the instructions on installing a tar file, i cant get it done. This app is not available in synaptic or the software center.

First, you should understand that a .tar file is basically just an alternative to a .zip file.  It's contents could be any number of things.  I'm not sure what "instructions on installing a tar file" you're following, but I don't think there could be any instructions that would cover all possibilities.  Often, the contents can be installed with Software Center or some other package management software.  In this case, I think you downloaded source code, so it will have to be compiled before it is installed.  There are plenty of tutorials out there on how to do this.  You might start with [this one]("https://help.ubuntu.com/community/CompilingEasyHowTo").

---

### Post by newb85 on 2013-03-25
> **newb85 said:**
> First, you should understand that a .tar file is basically just an alternative to a .zip file.

Sorry.  On reflection, that's a pretty poor description.  A .tar file is basically a container for other files.  In it's most basic form, it doesn't use compression, so the .tar file won't be any smaller than it's contents.  However, there are compression methods like bzip and gzip available for .tar files, making them .tbz or .tgz files.

Also, please note that keepassx *is* available in the Software Center if you have the Universe repository enabled.  Of course, it's the stable version, not the alpha.

---

### Post by mike555 on 2013-03-25
If you already have keepass files be aware keepass2 uses a different file system, so to keep the old files working use keepassx (not #2)

---


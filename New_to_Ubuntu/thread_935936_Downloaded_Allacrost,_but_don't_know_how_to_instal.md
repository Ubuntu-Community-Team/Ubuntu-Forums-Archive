---
title: "Downloaded Allacrost, but don't know how to install it!"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by MrPatton84 on 2008-10-02
Hey, 

I'm new to Ubuntu, and downloaded the game Allacrost from their SourceForge page, but  I don't know how to install it. 

Can anyone explain how to install games? 

Thanks very much in advance

Chris

---

### Post by Bölvaður on 2008-10-02
It seems to me that you downloaded the source code of this game and are able to build it.
There is also a package ready for you according to the website.


I quote :


> Linux (from source)

   1. Follow this link: Allacrost Sourceforge Download Page
   2. Click the "Download" link to the right. On the next page select the file that has the word "source" in the filename.
   3. Save the file to any location on your hard disk.
   4. After the download completes, open up a terminal and change the directory to where you downloaded the file.
   5. Unpack the tarball with the following command: untar -xvzf [file_name].tar.gz. The files will be placed in a new directory created in the current folder. Type cd [new_directory]>.
   6. Enter the following string of commands to compile, build, and install the game and editor: ./configure && make && make install
   7. You may now execute allacrost and allacrost-editor from the command line. 




Linux (from apt) - for Debian, Ubuntu, and other Debian-based distributions

The current release of Hero of Allacrost is available to install as a Debian apt package. It is available for i386 and amd64 architectures.

To download and install from the command line, type the following in your terminal.

   1. Add the following entry to your depository list: deb [http://debian.ettin.org/allacrost](http://debian.ettin.org/allacrost) unstable main., then refresh your package list via apt-get update
   2. To enable verification of this repository, run this command: wget [http://debian.ettin.org/key.gpg](http://debian.ettin.org/key.gpg) -O - | sudo apt-key add -
   3. To download and install the game, enter this in your terminal sudo apt-get update && apt-get install allacrost-demo
   4. After installation is complete, you can start the game by typing allacrost at the command line. You can launch the editor by typing allacrost-editor

---

### Post by Panzor on 2008-10-02
Well what you want to do is actually compile the source code. You may have to go digging for -dev files to do so, but the basic idea behind compiling is to do these things. Proceed to the next step only if prompted to or if there are no errors.

[quote=their website]# Unpack the tarball with the following command: untar -xvzf [file_name].tar.gz. The files will be placed in a new directory created in the current folder. Type cd [new_directory]>.
# Enter the following string of commands to compile, build, and install the game and editor: ./configure && make && make install
# You may now execute allacrost and allacrost-editor from the command line. [/quote]

1. Unpack tarball
2. cd to the directory you unpacked
3. type "./configure"
It should do a bunch of strange things and, most likely, will complain about not having a dev file it needs. I haven't compiled it myself on a clean machine, so I'm not sure what it wants, but it's not too hard to figure out. Read which dev it's complaining about and then search for the dev in either synaptic or tabbing through an apt-get line. 

4. After ./configure has run and is all fine and dandy, run "make"
You -could- have obvious errors, but sometimes source code is too out of date to work. If this is the case, then you're probably out of luck...Not always though! Just research the error or enter an IRC channel. This looks pretty updated though, so I wouldn't jump to grave conclusions.

5. "make install"
Wall of text, and you're done :) Hope this helps

---

### Post by MrPatton84 on 2008-10-05
Hey, 

When I run ./configure to install the game Allacrost I get a message saying 

configure: error: X11 GLX not found

I did search for this via Synaptic, but was confronted with several possible packages to download, but was wary to do so as I don't want to download the wrong one and mess with my system - not being confident enough to sort it out if it goes wrong. 

Any suggestions? Thanks very much in advance

Chris

---

### Post by MrPatton84 on 2008-10-05
Hey,

When I run ./configure to install the game Allacrost I get a message saying

configure: error: X11 GLX not found

I did search for this via Synaptic, but was confronted with several possible packages to download, but was wary to do so as I don't want to download the wrong one and mess with my system - not being confident enough to sort it out if it goes wrong.

Any suggestions? Thanks very much in advance

Chris

---

### Post by Perfect Storm on 2008-10-05
[http://gaming.gwos.org/doku.php/guides:64bit:hero_of_allacrost](http://gaming.gwos.org/doku.php/guides:64bit:hero_of_allacrost)

Edit thread merged. Please stick to one thread, thanks.

---

### Post by MrPatton84 on 2008-10-05
Sorry... :S

---


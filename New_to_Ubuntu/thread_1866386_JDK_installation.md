---
title: "JDK installation"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by 3v3rgr33n on 2011-10-21
hi
I'm trying to install JDK on ubuntu 11.04. I downloaded the file from the internet using windows because ubuntu doesn't want to connect to the internet. The connection is fine though (I'm using wireless) I saw that the connection is fine because linuxDC++ and its working just. I downloaded a file called "jdk-6u26-linux-x64.bin" when i tried opening it (with the hope of it executing like an ".exe" file) it just opened a folder. 

can someone please tell how to install that file without the internet. please don't give me the "sudo apt-get update" thing because it isn't working.I even tried the software center but....NOTHING!! it's just aisting my time.

thanx in advance.

---

### Post by raja.genupula on 2011-10-21
Hi

do this by opening terminal.
```
chmod 777 filename.bin
./filename.bin
```
make sure that while doing above operation you have that bin file in home dir.

---

### Post by 3v3rgr33n on 2011-10-23
[IMG]http://www.mediafire.com/i/?7b2l5mxl5583fav[/IMG]
I tried that but it isnt working...   it keeps saying there is not such directory/file

i took a screenshot, try [http://www.mediafire.com/i/?7b2l5mxl5583fav](http://www.mediafire.com/i/?7b2l5mxl5583fav)  to see what it said 
[IMG]http://www.mediafire.com/?7b2l5mxl5583fav[/IMG]

---

### Post by enkay009 on 2011-10-23
You need to go to the directory the installer is under. It looks like it's under ~/Downloads.

You can do this two ways, the terminal way is this...

```
cd ~/Downloads
ls -l
```

cd means change directory
ls means list the contnets of the directory

Now if the file is in this directory, type this in the terminal...

```
chmod +x filename.bin
./filename.bin
```

chmod is to change the permissions on the file. the +x option means add execute permissions for user, group and everyone
./filename.bin is to actually run the file

You don't have to change the execute permissions either. You could alternatively just type this in the terminal...

```
sh filename.bin
```

You can also do this from nautilus. Right-click the file, select properties, select the permissions tab, and check the "Allow executing file as program" checkbox.

This does the same thing as chmod +x.

---

### Post by 3v3rgr33n on 2011-10-24
;) thanx for your help guys. i installed jdk using the software center; the main reason it didnt install at first, it was because of my repository settings. 

I have major problems with vlc now, it seems to be delaying/ repeating the same sound in an interval of 5 sec.

---

### Post by HowardChau on 2011-10-26
I had tried installing Oracle's JDK 1.7.0_01 manually on my Ubuntu 11.10.

Here's my write-up on the steps I took.

[http://www.puppychau.com/archives/101](http://www.puppychau.com/archives/101)

---


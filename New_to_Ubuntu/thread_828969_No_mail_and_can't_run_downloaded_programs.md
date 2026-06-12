---
title: "No mail and can't run downloaded programs"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by SCURVER on 2008-06-14
[B][I]:)Good morning all......

     I'm still dealing with e-mail problems. Running my old Dell desktop with 3 GB RAM installed and three hard drives with tons of space. UBUNTU 8.04 is my O.S. and it runs well, but neither of my two e-mail clients, (Evolution and Thunderbird) will receive mail. They seem to send it okay. My problems appear to be with passwords. I just can't seem to remember them, even though I write them down. That doesn't make sense I know, but...Could you please tell me how to find my passwords?  I also cannot install any new programs. I acquire them easily enough, but installation is a problem. I click on them, try to run them using the terminal, but nothing seems to work.I've been at this with these two problems for days, now, but nothing works! I like UBUNTU very much and coming from XP PRO it is a wonder! But I do need some help with it!

                               Thanks,

                                    Scurver[/I][/B]

---

### Post by Gannon8 on 2008-06-14
Go to the web sites that you signed up for email and look for a "Forgotten Password?" link, and do what it says.

---

### Post by the_doc on 2008-06-14
> **SCURVER said:**
> ***:)....but neither of my two e-mail clients, (Evolution and Thunderbird) will receive mail. They seem to send it okay.***

Please don't post entirely in bold it is a tad irritating! 

Don't you need a password for sending mail?  In which case have you got the correct outgoing email server address?

---

### Post by mdpalow on 2008-06-14
Who is providing your e-mail service (example: Yahoo! / Gmail)? 

Doesn't sound like a password issue to me if you can get e-mail. Sounds more like a setting is wrong somewhere in your SENDING tab.

Why don't you post here what you've entered and let's take a look.

---

### Post by doorman on 2008-06-14
[EDIT] There was a syntax error in the untarring code, fixed now :)

I must confess I'm not sure what your problem with email is... You say you can send emails ( I'm guessing you're sure the other party gets the email ), but you forget your password?
If you saved it, but forgot it, you can easily retrieve your passwords in Thunderbird by going to Edit > Preferences > Privacy > Passwords, and then click on the "show passwords" button. The password for your account will then be revealed.

As far as the installing programs issue goes, my guess is you downloaded a program from the net and want to install it. If so there are 3 possibilities:

**1) You downloaded the source**
If you downloaded the source code, you probably downloaded a .tar.gz or a .tar.bz2 archive. Do the following:
a) open up a terminal, and navigate to the directory ( aka folder ) where you downloaded the archive:
```
$ cd /path/to/archive
```For example, if you downloaded it to the desktop, type
```
$ cd Desktop/
```b) untar the archive:[INDENT]b1) if it's a tar.gz archive, type:
```
$ tar -xzvf archive_name.tar.gz
```b2) if it's a tar.bz2 archive, type:
```
$ tar -yxf archive_name.tar.bz2
```[/INDENT]Now, a new directory should be created.
c) navigate to the newly created dir:
```
$ cd directory_name
```To discover what's the name of the directory ( which typically has the same name as the archive, but without the extension ), type:
```
$ ls -l
```You'll see now all the files & directories - directories have a "d" in the permissions column ( the first column in the listing )
d) compile & install the program:
```
$ ./configure
$ make
$ sudo make install
```That should be it... Watch the ./configure output - it could report some missing features needed to compile the source. If that happens, ask on the forums or try searching the net for that error.

**2) You downloaded the deb package**
You'll know it by looking at the extension of the file - if it's a .deb file, this is the case.
a) again, navigate to the dir you downloaded the file:
```
$ cd /path/to/deb/file
```b) install the file:
```
$ sudo dpkg -i file.deb
```**3) You downloaded the installer binary**
Most of graphic cards drivers comes as a binary installer, as well as flash plugins, etc...
a) navigate to the dir:
```
$ cd /path/to/binary
```b) run it:
```
$ ./bin_name
```If you cannot run it, it's probable that you have to make the file executable:
```
$ chmod +x bin_name
```That's it... If you have any problems with a specific software, ask in the forums...
Btw, There are already a lot of programs available to ubuntu users - try the "Add/Remove" application in the Applications menu, or the Synaptic Package Manager ( System > Administration )

---


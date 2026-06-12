---
title: "Compilation of MrBayes does not run ./cofig script"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by jonassullivan on 2013-03-04
Hello all!
I am sorry to have to post a new thread but I promisse I have done my homework on how to installing/compiling new applications in Ubuntu by the command line and despite my various frustations I am not yet able to accomplish this particular installation by myself. So I would like to acknowledge that I very much appreciate your help!

I am trying to install this application to my Ubuntu 12.04 64-bit system: [http://mrbayes.sourceforge.net/download.php](http://mrbayes.sourceforge.net/download.php)

So I download the package mrbayes-3.2.1.tar.gz and decompress it, creating a folder called mrbayes-3.2.1 in Downloads folder.
When I try to move on with the compilation instructions of the application wiki-site, which next step would be to ./configure installation, it does not work in my terminal:
[B]
<<SNAPSHOT OF THE APPLICATION WEBSITE INSTRUCTIONS ON TO HOW PROCEED IN COMPILING THE FILES>>[/B]
[IMG]http://sphotos-c.ak.fbcdn.net/hphotos-ak-ash3/549998_175250265957127_436734957_n.jpg[/IMG]

[B]
<<CERTIFYING I UNPACKED THE PACKAGE AND CREATED ITS FOLDER>>[/B]
[IMG]http://sphotos-b.ak.fbcdn.net/hphotos-ak-prn1/644347_175250079290479_2114321876_n.jpg[/IMG]

**<<TRYING TO MAKE IT RUN ./CONFIG COMMAND IN MRBAYES-3.2.1  FOLDER AND THEN ALSO IN MRBAYES-3.2.1/USR FOLDER WHICH SEEMS TO CONTAINS  MANY SCRIPTS>>**
[IMG]http://sphotos-d.ak.fbcdn.net/hphotos-ak-ash4/313815_175250085957145_1089614852_n.jpg[/IMG]

As you can see from the above pictures, I tried to do as the website instructions said (and all imaginable variations I could come up with) but still I do not know why these errors messages appear in terminal. Why doesn't ./config work?  I need install this software for my end-of-graduation theses so any help will be very much appreciated!

---

### Post by lechien73 on 2013-03-05
Hi & welcome to the forums,

First you need to run autoconf, which will create the configure script. You likely don't have it installed already, so:

```
sudo apt-get install autoconf
cd ~/Downloads/mrbayes_3.2.1/src
autoconf
./configure
```

Also, it might be an idea to make the install-sh script executable by typing the following in the src directory:

```
chmod +x install-sh
```

Hope this helps.

---

### Post by jonassullivan on 2013-03-05
Thank you @lechien73 ! Yoru suggestion of running autoconfig command did seem to work. I think that is what was missing before...
Even though I managed to proceed with the installation/compilation, the application did not install entirely because my ubuntu version (12.04) apparently is not compatible with mrbayes_3.2.1. I just saw that today. It only works on 12.10, which I intend to install this afternoon!

Thank you so much for your time!

---


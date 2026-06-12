---
title: "kb2kskype"
date: 2008-06-21
forum: Packaging and Compiling Programs
---

### Post by parann0yed on 2008-06-21
Copied from a post to the kb2kskype group.  I thought maybe this was more of an issue with Ubuntu since others seem to be able to compile the program.  Here is the situation...

Running Ubuntu 7.10 on amd 64, I've been able to *force* install skype as suggested in some doc I've seen recently (works great). I am also able to compile/install usbb2k-api-mod-2.8 successfully. When running *make* while installing kb2kskype-0.3.7 I get the error in the subject. As far as I know, I've satisfied the dependencies listed at [http://kb2kskype.sourceforge.net/install.html](http://kb2kskype.sourceforge.net/install.html) and [http://forum.skype.com/index.php?showtopic=67560&st=20](http://forum.skype.com/index.php?showtopic=67560&st=20). 
 
The last few lines from running *make* are: 
 
g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I. -DQT_THREAD_SUPPORT -D_REENTRANT -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -c -o kb2kmainwindow.o `test -f 'kb2kmainwindow.cpp' || echo './'`kb2kmainwindow.cpp 
/usr/share/qt3/bin/moc testapp_ui.h -o testapp_ui.moc 
make[2]: *** [testapp_ui.moc] Segmentation fault (core dumped) 
make[2]: Leaving directory `/home/bob/skype/kb2kskype-0.3.7/src' 
make[1]: *** [all-recursive] Error 1 
make[1]: Leaving directory `/home/bob/skype/kb2kskype-0.3.7' 
make: *** [all] Error 2 
 
Any ideas on how to resolve this would be much appreciated. Thank you.

---

### Post by parann0yed on 2008-06-21
Woops, forgot to specify the error.  If it's not obvious from the message, here it is:

make[2]: *** [testapp_ui.moc] Segmentation fault (core dumped)

---

### Post by parann0yed on 2008-06-22
Didn't think I'd get a reply on this one.  I was able to compile on a nearly identical machine so it would have to be that I'm missing a library or possibly the machine I was trying to compile on is using the third party nvidia driver.  I can't be sure, but I'll close this thread out with those thoughts.

---

### Post by altariel on 2008-06-23
unfortunately I have never compiled either stuff under 64 bit, but I'll forward your post to the developer :)

---

### Post by altariel on 2009-03-29
well, I did manage to built at least one 64-bit package - chose the 8.0.4.2 LTS version since that one was still easier to switch back to kde 3 instead of the newer kde 4 ... 

please report back any troubles if you try this package (both kb2kskype and usbb2k-api-mod) :) 

[https://sourceforge.net/project/showfiles.php?group_id=186708](https://sourceforge.net/project/showfiles.php?group_id=186708)

---

### Post by altariel on 2009-04-02
if someone would like to try the ppa lauchpad archive I set up (for hardy right now, will try to get at least intrepid as well) 

[https://launchpad.net/~alatariel/+archive/ppa](https://launchpad.net/~alatariel/+archive/ppa)

I think it should suffice to 
a) add the ppa to your apt sources list 
b) import the key (as per instructions on the page above)
and 
c) sudo apt-get install kb2kskype 
(this -should- pull in the usbb2k-api-mod as well)

---


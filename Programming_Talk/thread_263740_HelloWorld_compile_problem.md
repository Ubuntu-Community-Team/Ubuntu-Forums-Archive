---
title: "HelloWorld compile problem"
date: 2006-09-23
forum: Programming Talk
---

### Post by elpuerco on 2006-09-23
I am following the how to start a new project guide in KDevelop.

I have opened the new project called HelloWorld and then tried Build -> Execute Program and I get this error message

cd '/media/hda7/data/kdevelop/helloworld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/media/hda7/data/kdevelop/helloworld/debug' && cd '/media/hda7/data/kdevelop/helloworld/debug' && CXXFLAGS="-O0 -g3" "/media/hda7/data/kdevelop/helloworld/configure" --enable-debug=full && cd '/media/hda7/data/kdevelop/helloworld/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
/bin/sh: make: command not found
*** Exited with status: 127 ***

I have installed all the KDevelop3 entries in Adept.

---

### Post by breuerp on 2006-09-23
> **elpuerco said:**
> I am following the how to start a new project guide in KDevelop.

I have opened the new project called HelloWorld and then tried Build -> Execute Program and I get this error message

cd '/media/hda7/data/kdevelop/helloworld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/media/hda7/data/kdevelop/helloworld/debug' && cd '/media/hda7/data/kdevelop/helloworld/debug' && CXXFLAGS="-O0 -g3" "/media/hda7/data/kdevelop/helloworld/configure" --enable-debug=full && cd '/media/hda7/data/kdevelop/helloworld/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
/bin/sh: make: command not found
*** Exited with status: 127 ***

I have installed all the KDevelop3 entries in Adept.

You have to install the make utility to link your file
Code:  sudo apt-get install make

---

### Post by elpuerco on 2006-09-23
OK thanks I ran that, but now I have:

cd '/media/hda7/data/kdevelop/helloworld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/media/hda7/data/kdevelop/helloworld/debug' && cd '/media/hda7/data/kdevelop/helloworld/debug' && CXXFLAGS="-O0 -g3" "/media/hda7/data/kdevelop/helloworld/configure" --enable-debug=full && cd '/media/hda7/data/kdevelop/helloworld/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
This Makefile is only for the CVS repository
This will be deleted before making the distribution
<br />
*** YOU'RE USING automake (GNU automake) 1.4-p6.
*** KDE requires automake 1.6
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

---

### Post by Lord Illidan on 2006-09-23
Try

```
sudo apt-get install build-essential
```

---

### Post by elpuerco on 2006-09-23
:confused: 

Nope!

I still got the same message.  I then removed make using Adept and now I get the /bin/sh make not found message.

Am I supposed to have QT installed to do this?  Just thinking aloud here.  I tried downloading that but it errored trying to unpack.

The HelloWorld tutorial does not mention the need for this though?

---

### Post by Lord Illidan on 2006-09-23
Do not remove make... Re-install it please.

I think all you had to do was fire up synaptic, (easier than the command line) and search for those packages which KDevelop told you were missing. I know it can be confusing, but I don't have access to Ubuntu right now.

---

### Post by christhemonkey on 2006-09-23
I think you need to remove automake 1.4 and install automake 1.6 or later like it asks for.
```
sudo apt-get remove automake1.4 & sudo apt-get install install automake1.7 
```

---

### Post by elpuerco on 2006-09-23
OK folks, we are getting somewhere....I think.

Before coming back here I had a look in Adept for build-essential and found it was not installed, I guess when I removed make it did it?

So I intalled it again, but still the same problem!

I came back here and saw Lord Illidan's post about looking for missing parts.

I was already in Adept and purely by chance saw the entry for automake 1.4 and a load of later versions, 1.6 was not one of them.

So I installed 1.9 and removed 1.4 and tried again.

WOW the screen whizzed with activity!!! Loads and loads of scrolling text.

Excitment 'o' plenty until...

configure: error: Can't find X includes. Please check your installation and add the correct paths!
*** Exited with status: 1 ***

DOH!

---

### Post by elpuerco on 2006-09-23
Aha rejoice for I have a Hello World program :D 

I search this forum for the X problem and found how to install the required includes.

I then got an error about missing qt headers, so located the qt stuff in adept and got past that error.

I then got a kde headers error and fixed it using this thread:

[http://www.ubuntuforums.org/showthread.php?t=124483&page=2&highlight=kde+headers](http://www.ubuntuforums.org/showthread.php?t=124483&page=2&highlight=kde+headers)

And hey presto my program compiles and works

happy at last....

thanks folks

---

### Post by christhemonkey on 2006-09-23
Well done :)


Determination wins through eh!

---

### Post by elpuerco on 2006-09-23
yep, sure does ;) 

pleased I stuck at it :D

---


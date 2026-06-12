---
title: "[SOLVED] Installing Osmo......"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by jakewc2 on 2008-09-14
I want to install Osmo, and I'm trying to follow this 

[http://ubuntuforums.org/showthread.php?t=616116](http://ubuntuforums.org/showthread.php?t=616116)

but for a newby its a bit vague, is there anywhere else that gives a bit more detail on how to install it? 

Thanks for your help

John.

---

### Post by lyni on 2008-09-14
just go to [www.getdeb.net/category.php?id=6](www.getdeb.net/category.php?id=6) and download it from there and it will automatically install for you.

---

### Post by jemate18 on 2008-09-14
> **jakewc2 said:**
> I want to install Osmo, and I'm trying to follow this 

[http://ubuntuforums.org/showthread.php?t=616116](http://ubuntuforums.org/showthread.php?t=616116)

but for a newby its a bit vague, is there anywhere else that gives a bit more detail on how to install it? 

Thanks for your help

John.

Ok go to
> [http://www.getdeb.net/search.php?keywords=osmo](http://www.getdeb.net/search.php?keywords=osmo)

Click download osmo.. (the 0.2.2) version

Suppose you have downloaded into your DESKTOP
Follow these steps
1. Open terminal
> Applications -> Accessories -> Terminal
2. type> cd ./Desktop
3. type (supposing this is the file you have download)
> sudo dpkg --install osmo_0.2.2-0~getdeb1_i386.deb/QUOTE]

or
[QUOTE]sudo dpkg -i osmo_0.2.2-0~getdeb1_i386.deb
4. Type your password and hit ENTER

---

### Post by jakewc2 on 2008-09-15
Hi, thank you for your message, I followed your instructions, and got this error

> jakewc2@jakewc2-desktop:~/Desktop$ sudo dpkg --install osmo_0.2.2-0~getdeb1_i386.deb
[sudo] password for jakewc2: 
dpkg: error processing osmo_0.2.2-0~getdeb1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 osmo_0.2.2-0~getdeb1_i386.deb
jakewc2@jakewc2-desktop:~/Desktop$ ]

 what should I do now.

Thank you.

John

---

### Post by jemate18 on 2008-09-15
> **jakewc2 said:**
> Hi, thank you for your message, I followed your instructions, and got this error

]

 what should I do now.

Thank you.

John

What is the complete path and filename of the file you have downloaded?

---

### Post by jakewc2 on 2008-09-15
Hi thank you for you message.

I downloaded it to the desktop and the file is called osmo_0.2.2-0~getdeb1_i386.deb

---

### Post by jemate18 on 2008-09-15
> **jakewc2 said:**
> Hi thank you for you message.

I downloaded it to the desktop and the file is called osmo_0.2.2-0~getdeb1_i386.deb


did you try  the 
```
cd Desktop
```
before doing the ```
sudo dpkg -i osmo_0.2.2-0~getdeb1_i386.deb
```?

---

### Post by jemate18 on 2008-09-15
I got it... You have an architecture mismatch...... ARe you using Ubuntu 64 bit?

---

### Post by jakewc2 on 2008-09-15
this is how I just did it again ;_

> jakewc2@jakewc2-desktop:~$ cd Desktop
jakewc2@jakewc2-desktop:~/Desktop$ sudo dpkg -i osmo_0.2.2-0~getdeb1_i386.deb
[sudo] password for jakewc2: 
dpkg: error processing osmo_0.2.2-0~getdeb1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 osmo_0.2.2-0~getdeb1_i386.deb
jakewc2@jakewc2-desktop:~/Desktop$ 

jakewc2@jakewc2-desktop:~$ has a lowercase d in desktop and cd Desktop has upper D, does that make a difference?

thank you.

John

---

### Post by jemate18 on 2008-09-15
This is  strage I am als using amd64 and I have downloaded the same file as yours and this is the results I got

Selecting previously deselected package osmo.
(Reading database ... 123662 files and directories currently installed.)
Unpacking osmo (from osmo_0.2.2-0~getdeb1_i386.deb) ...
dpkg: dependency problems prevent configuration of osmo:
 osmo depends on libgringotts2; however:
  Package libgringotts2 is not installed.
 osmo depends on libical0; however:
  Package libical0 is not installed.
dpkg: error processing osmo (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 osmo

This means that the dependencies should be installed first before osmo could be installed.

---

### Post by jemate18 on 2008-09-15
> **jakewc2 said:**
> this is how I just did it again ;_



jakewc2@jakewc2-desktop:~$ has a lowercase d in desktop and cd Desktop has upper D, does that make a difference?

thank you.

John

Yes because Desktop is a place under your home so you shoud do this instead

```
cd ~/Desktop
```

then
```
sudo dpkg --install osmo_0.2.2-0~getdeb1_i386.deb
```

or
```
sudo dpkg -i osmo_0.2.2-0~getdeb1_i386.deb
```

---

### Post by jakewc2 on 2008-09-15
Ho do I find out? I was installing Sonata yesterday, and didnt have a problem, but I on my efforts try to install Osmo yesterday, and could have changed things. 

I used this thread, [http://ubuntuforums.org/showthread.php?t=616116](http://ubuntuforums.org/showthread.php?t=616116)


and used this command

> sudo aptitude install libxml2 libxml2-dev libgtk2.0-dev libgettext-ruby1.8

Have no clue if it changed my Ubuntu. Where do I look to see if it is Ubuntu 64bit

John.

---

### Post by jemate18 on 2008-09-15
> **jakewc2 said:**
> Ho do I find out? I was installing Sonata yesterday, and didnt have a problem, but I on my efforts try to install Osmo yesterday, and could have changed things. 

I used this thread, [http://ubuntuforums.org/showthread.php?t=616116](http://ubuntuforums.org/showthread.php?t=616116)


and used this command



Have no clue if it changed my Ubuntu. Where do I look to see if it is Ubuntu 64bit

John.

Oh I see.... Never mind the 64 bit thing.... Did you do the cd ~/Desktop and the sudo dpkg -i ?

---

### Post by jakewc2 on 2008-09-15
HI, ythank you for the message.

here's there result still have an error

> jakewc2@jakewc2-desktop:~$ cd ~/Desktop
jakewc2@jakewc2-desktop:~/Desktop$ sudo dpkg -i osmo_0.2.2-0~getdeb1_i386.deb
[sudo] password for jakewc2: 
dpkg: error processing osmo_0.2.2-0~getdeb1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 osmo_0.2.2-0~getdeb1_i386.deb
jakewc2@jakewc2-desktop:~/Desktop$ 

---

### Post by shirilover on 2008-09-15
If you are using 64-bit, can be found by entering uname -a in a terminal, change to 64-bit on the getdeb site by clicking the version link near the top of the page.

Then, when you download the deb file you will get the 64-bit version.

---

### Post by jemate18 on 2008-09-15
> **jakewc2 said:**
> HI, ythank you for the message.

here's there result still have an error

go to this
> [http://packages.ubuntu.com/intrepid/x11/osmo](http://packages.ubuntu.com/intrepid/x11/osmo)
and download the amd64 version at the buttom

---

### Post by jemate18 on 2008-09-15
if you are having hard time downloading using my post above..

try this
```
http://www.getdeb.net/search.php?keywords=osmo
```

and click the version in the

> Welcome Visitor, you can login  or register .

You are browsing software for Ubuntu Hardy (32 bits), you can select other [COLOR="Red"]version[/COLOR] .
Browsing software for Desktop , the following types are available. 

then select Ubuntu Hardy (64 - bit) then download it

---

### Post by jakewc2 on 2008-09-15
HI before I do that can you tell me how I find out what version I have,yesterday I didnt have this problem, and I'm wondering if I have inadvertantly installed something I shouldnt have. I just installed Ubuntu though Wubi, and dont remember in the installation it being 64.

Would all the other installation I have installed work if I now have 64 bits?

John

---

### Post by jemate18 on 2008-09-15
> **jakewc2 said:**
> HI before I do that can you tell me how I find out what version I have,yesterday I didnt have this problem, and I'm wondering if I have inadvertantly installed something I shouldnt have. I just installed Ubuntu though Wubi, and dont remember in the installation it being 64.

Would all the other installation I have installed work if I now have 64 bits?

John

To check if your hardy installed is 64bits go to Applications -> Accessories -> terminal and enter "uname -a"

in the results,

If you have x86_64 in the output you have a 64bit install, if it says i386 or i686 then you are running 32bit.

What is the result of uname -a

---

### Post by jakewc2 on 2008-09-15
I have another message now, I installed
> 
 sudo dpkg --install osmo_0.2.0-1_amd64.deb

and got this message, didnt go to the site to change my settings just stayed with the way I was, but it looks like I need something else to install before this works

> jakewc2@jakewc2-desktop:~$ cd ~/Desktop
jakewc2@jakewc2-desktop:~/Desktop$ sudo dpkg --install osmo_0.2.0-1_amd64.deb
Selecting previously deselected package osmo.
(Reading database ... 114100 files and directories currently installed.)
Unpacking osmo (from osmo_0.2.0-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of osmo:
 osmo depends on libgringotts2; however:
  Package libgringotts2 is not installed.
 osmo depends on libical0; however:
  Package libical0 is not installed.
dpkg: error processing osmo (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 osmo
jakewc2@jakewc2-desktop:~/Desktop$ 



so I think I'm getting there

John

---

### Post by jemate18 on 2008-09-15
> **jakewc2 said:**
> I have another message now, I installed


and got this message, didnt go to the site to change my settings just stayed with the way I was, but it looks like I need something else to install before this works



so I think I'm getting there

John


Yup in my previous post,, I have posted that you needed to install first the dependencies before you can install osmo..


```
sudo apt-get install yourdependency
```

where yourdependency is the one required in the error message.

Do it for all the dependencies.
After that,,, do the dpkg -i osmo......

---

### Post by jakewc2 on 2008-09-15
I have another message now, I installed
> 
 sudo dpkg --install osmo_0.2.0-1_amd64.deb

and got this message, didnt go to the site to change my settings just stayed with the way I was, but it looks like I need something else to install before this works

> jakewc2@jakewc2-desktop:~$ cd ~/Desktop
jakewc2@jakewc2-desktop:~/Desktop$ sudo dpkg --install osmo_0.2.0-1_amd64.deb
Selecting previously deselected package osmo.
(Reading database ... 114100 files and directories currently installed.)
Unpacking osmo (from osmo_0.2.0-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of osmo:
 osmo depends on libgringotts2; however:
  Package libgringotts2 is not installed.
 osmo depends on libical0; however:
  Package libical0 is not installed.
dpkg: error processing osmo (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 osmo
jakewc2@jakewc2-desktop:~/Desktop$ 



so I think I'm getting there

John

---

### Post by jakewc2 on 2008-09-15
Hi, sorry its taken me so long to get back to you, its been a bit confusing.

I tried to install the dependencies,and I think they were installed, but I still get the error on installing Osmo

> jakewc2@jakewc2-desktop:~$ sudo aptitude install libxml2 libxml2-dev libgtk2.0-dev libgettext-ruby1.8
[sudo] password for jakewc2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  osmo 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  osmo: Depends: libgringotts2 but it is not installable
        Depends: libical0 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
osmo

Score is 119

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  osmo 
The following packages will be REMOVED:
  osmo 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1102kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 114118 files and directories currently installed.)
Removing osmo ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
jakewc2@jakewc2-desktop:~$ sudo aptitude install libxml2 libxml2-dev libgtk2.0-dev libgettext-ruby1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
jakewc2@jakewc2-desktop:~$ 

Those are the dependencies

They seem to have been installed ok.

Still having problems with Osmo though, but going to try again.

John

---

### Post by jakewc2 on 2008-09-15
get this when trying to install osm,

> jakewc2@jakewc2-desktop:~/Desktop$ sudo dpkg --install osmo_0.2.0-1_amd64.deb 
Selecting previously deselected package osmo.
(Reading database ... 114100 files and directories currently installed.)
Unpacking osmo (from osmo_0.2.0-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of osmo:
 osmo depends on libgringotts2; however:
  Package libgringotts2 is not installed.
 osmo depends on libical0; however:
  Package libical0 is not installed.
dpkg: error processing osmo (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 osmo

seems like I'm going round in circles here.

John

---

### Post by jakewc2 on 2008-09-15
> jakewc2@jakewc2-desktop:~$ uname -a
Linux jakewc2-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
jakewc2@jakewc2-desktop:~$ 

It is 64 bits, if thats the case then arent the depedancies on that page I got, the wrong code, if so, where do I get those dependencies.

Thank you.

---

### Post by jakewc2 on 2008-09-15
Well afer all that, I had an update message suddenly appear, installed updated, booted my system, and Osmo suddenly apeared. 

Thankyou so much for your help, I really appreciate it. 

John.

---


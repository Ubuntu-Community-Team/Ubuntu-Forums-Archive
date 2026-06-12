---
title: "my hello.c file won't compile under gcc"
date: 2006-11-07
forum: Programming Talk
---

### Post by JasonFriday13 on 2006-11-07
Hi there. This is my first post, so please be nice. I have just downloaded and installed ubuntu 6.10 edgy, and its great. But the one thing I need is the compiler. I tried to compile some packages, but ./configure comes up with something like "Seeing if gcc works...   ( no  )". So, I made a 'hello world!' C file to compile. Command line: gcc hello.c
The file was as follows:

#include <stdio.h>

int main(void)
{
  printf("Hello World!\n");
  return 0;
}

When I tried to compile it, it comes up with some errors (not exact wording):
error: can't find stdio.h
error: funtion main implicit something something illegal
error: function printf not referenced or found

I already tried apt-get install gcc, and build-essential, but said that I was already using the newest version. Oh, and I don't have an internet connection at home (used the network at college to access the net - probably a proxy problem). I want gcc to function so I can build Audacity (don't know how to install the prebuilt binary I downloaded). Can someone help?

[edit]Fixed typo. And I relise this thread will probably be moved, but I thought I should post here because it is related to programming.[/edit]

---

### Post by deepwave on 2006-11-07
Ubuntu already has pre-built audacity package.

I guess you already have libc installed.  (On mine this would be libc6 and libc6-dev).  gcc and make and all that stuff should be installed with build-essential... wierd.

---

### Post by JasonFriday13 on 2006-11-07
Whoops, must have missed it while browsing the downloads section.

I haven't actually got 6.10 installed at the moment, I have 6.06 installed to see if it made any difference, which it didn't. gcc or any of the build tools were not present. 

I will reinstall 6.10 and see if gcc will work this time. I downloaded my iso from a mirror on the ubuntu website, along with 6.06 and Kubuntu 6.10 (just to try out). I will get back tomorrow.

[edit] Is there a gcc stable release available like the one here? [http://packages.ubuntu.com/edgy/devel/gcc-snapshot]("http://packages.ubuntu.com/edgy/devel/gcc-snapshot") I am a bit of a programmer and would like gcc to function properly. The gcc included with edgy is 4.1.1. I heard some where it was prerelease, so it maybe why its not working. [/edit]

---

### Post by djgrandmarquis on 2006-11-07
Glad you're giving Ubuntu a try!

Are you using Ubuntu's Synaptic package manager (Adept in Kubuntu)? Not sure where you were "browsing the downloads section" ... you can get all the programs you need in a graphical, precompiled fashion from the package management program. No need to compile, no need to use apt-get at the command line.

(Of course, you can use gcc and other command line tools as you learn more about Linux, but Synaptic is probably a good place to start.) 

FYI, if you install Ubuntu 6.10, you can install the kubuntu-desktop and xubuntu-desktop packages to try out KDE and xfce, respectively. You just pick which one you'd like at login time. (GNOME is the Ubuntu default.)

Hope that helps!

---

### Post by JasonFriday13 on 2006-11-07
The "browsing the downloads section" was at the ubuntu packages section, and I missed the i386 link to download, so I downloaded the .tar.gz file (which I found out was the source) :(. 

No, I am not using the package manager you mentioned. My install is as fresh as they come (os installed from the cd, no packages from the web).

From edit section of earlier post:

Is there a gcc stable release available like the one here? [http://packages.ubuntu.com/edgy/devel/gcc-snapshot](http://packages.ubuntu.com/edgy/devel/gcc-snapshot). I am a bit of a programmer and would like gcc to function properly.

---

### Post by JasonFriday13 on 2006-11-08
Sorry, was too busy last night, so it will be tomorrow that I will get back.

---

### Post by Choad on 2006-11-08
> **JasonFriday13 said:**
> Sorry, was too busy last night, so it will be tomorrow that I will get back.
as a general rule, you should try and install pre-compiled packages using apt-get or synaptic

that way everything has its dependancies met and its all cool. its what gives debian based distros their structure and its why they are so popular

the package you want is called build-essential. it contains gcc and g++ and all the standard header files you can shake a stick at. a default ubuntu install has no development files what so ever, which is why you werent having much luck compiling

sudo apt-get install build-essential

that will get u up and running

most programs available for linux will be in the edgy repositories. i certainly havent *needed* to compile anything in ubuntu

---

### Post by JasonFriday13 on 2006-11-09
I think I already mentioned I don't have the internet at home. The internet that I can access at college uses a proxy, and it requires a username and password, which apt-get dosen't show (a dialog to log in - which is why 'apt-get install build-essential' didn't work). 

So far, this is my only grump about linux, the other grump is ignored (building and running windows apps on linux). I want to start writing programs for linux, but will be very hard without a compiler. What are the basic packages needed to compile programs for linux?

[size=1][edit]Added extra in the bracketed sentence.[/edit][/size]

---

### Post by po0f on 2006-11-09
JasonFriday13,

build-essential should be included on the installation CD.  As for programming for Linux, packages you will need to install depend on what kind of programming you want to do.

---

### Post by Choad on 2006-11-10
> **JasonFriday13 said:**
> I think I already mentioned I don't have the internet at home. The internet that I can access at college uses a proxy, and it requires a username and password, which apt-get dosen't show (a dialog to log in - which is why 'apt-get install build-essential' didn't work). 

So far, this is my only grump about linux, the other grump is ignored (building and running windows apps on linux). I want to start writing programs for linux, but will be very hard without a compiler. What are the basic packages needed to compile programs for linux?

[size=1][edit]Added extra in the bracketed sentence.[/edit][/size]
edit /etc/apt/apt.conf and add the line

Acquire::http::Proxy "http://myname:mypassword@ourproxy.ourdomain:4480";

(not sure about the port number at the end.... that was taken from a google search)

or start up synaptic and settings>preferences>network and there u can set up proxy settings

---

### Post by arka on 2006-11-10
HI guys, i am new too to ubuntu and progamming languages.

When i opend gedit and i type this :  

 #include <stdio.h>

void main()

{

printf(" hi all ");

}


I save the file in test.cpp   and when i try to compile it with gcc test.cpp  i have this error : 


test.cpp:3: error: ‘::main’ must return ‘int’



What am i doing wrong? 

thx

---

### Post by Choad on 2006-11-10
> **arka said:**
> HI guys, i am new too to ubuntu and progamming languages.

When i opend gedit and i type this :  

 #include <stdio.h>

void main()

{

printf(" hi all ");

}


I save the file in test.cpp   and when i try to compile it with gcc test.cpp  i have this error : 


test.cpp:3: error: ‘::main’ must return ‘int’



What am i doing wrong? 

thx
int main() not void main()

as it says, main() must return an integer

---

### Post by arka on 2006-11-10
> **Choad said:**
> int main() not void main()

as it says, main() must return an integer
/tmp/ccmZ1BpI.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


AS you suggested i have used int but i got this error

---

### Post by Choad on 2006-11-10
thats..... wierd.....

just did it myself and it compiled fine. didnt actually print "hello" (is printf the right function? i dont use c...) but it compiled no errors

```

#include <stdio.h>

int main() {
        printf("hellooooo");
        }

```

---

### Post by Choad on 2006-11-10
do you have build-essential installed?

$ sudo apt-get install build-essential

---

### Post by arka on 2006-11-10
> **Choad said:**
> do you have build-essential installed?

$ sudo apt-get install build-essential
same error and i ran the command you said but the system is upgraded

---

### Post by shining on 2006-11-10
> **arka said:**
> 
I save the file in test.cpp   and when i try to compile it with gcc test.cpp  i have this error : 


Why cpp?

---

### Post by Choad on 2006-11-10
> **shining said:**
> Why cpp?
you sir, are an eagle-eyed genius!

call it .c not .cpp lol

---

### Post by arka on 2006-11-11
Thank's a lot :)  it works now

---

### Post by JasonFriday13 on 2006-11-12
Thanks for all the help. I might just wait until I can afford an internet connection at home. For now I think I am stuck on windows programming (C/C++).

---

### Post by pmendham on 2006-11-13
I'm having the exact same problem as JasonFriday13:  I have a fresh install of Edgy, I can run gcc but it doesn't seem to find the libraries i.e. it compiles but gives errors about not being able to find stdio functions etc.  The reason I need to compile is that I need to extract the firmware for my ADSL modem, so until I sort gcc I have no internet access under Ubuntu.  The machine is dual-boot though and I do have net access under Windows.  Any ideas?

---

### Post by hod139 on 2006-11-13
> **JasonFriday13 said:**
> Thanks for all the help. I might just wait until I can afford an internet connection at home. For now I think I am stuck on windows programming (C/C++).
  
What's wrong.  All the building tools are available on the CD, so you do not need an internet connection.  Just insert the cd into the cdrom drive and go to System->Administration->Software properties->Add Cdrom

Then you can install the package build-essential
```

sudo aptitude install build-essential

```

Also, make sure when compiling C code that you use gcc, and when compiling C++ code you use g++.

Or is there another problem you are having that I don't understand.

---

### Post by pmendham on 2006-11-14
No, you understand perfectly, it appears I was confused :-| ...

It did what you said and, of course, it now works just fine.  I had assumed that gcc and make were part of build-essential, so when I found I already had gcc and make on my system I thought "great, I don't need to do all this aptitude stuff".  But I did, just as you pointed out.  I clearly didn't understand what was in build-esential.  Whatever it was, turns out it was... well... essential.

Thanks :oops:

---

### Post by Choad on 2006-11-14
> **pmendham said:**
> No, you understand perfectly, it appears I was confused :-| ...

It did what you said and, of course, it now works just fine.  I had assumed that gcc and make were part of build-essential, so when I found I already had gcc and make on my system I thought "great, I don't need to do all this aptitude stuff".  But I did, just as you pointed out.  I clearly didn't understand what was in build-esential.  Whatever it was, turns out it was... well... essential.

Thanks :oops:
libraries n shizzle

mostly

---

### Post by JasonFriday13 on 2006-11-16
Just getting back to let you know.

I finally have Audacity running! Despite doing it the hard way (downloading the individual .deb's required), I now have the source packages, so now if I have to install Ubuntu again, the packages are all ready to go.

And 'sudo apt-get install build-essential' did the trick. Now I have gcc on my machine. Many thanks to all that helped.

---

### Post by anarky on 2006-11-17
i had the same problem but then i downloaded the g++ package (came with a ton of others due to dependency) and now all my libs are found :)

---

### Post by hod139 on 2006-11-17
The package build-essential depends on gcc and g++, so installing build-essential will also get you the compilers, but it also gets everything else needed for compiling/building.

---


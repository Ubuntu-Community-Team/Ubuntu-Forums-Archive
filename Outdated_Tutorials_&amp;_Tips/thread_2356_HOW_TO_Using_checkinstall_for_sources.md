---
title: "HOW TO: Using checkinstall for sources"
date: 2004-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by oddabe19 on 2004-10-27
So you want that app... yes... THAT app, so you goto the website... but... DAMN no .deb file only source files.
If you're anything like me, you hate ./configure, make, make install you just want an easy .deb package, for easy install and removing.
Well, checkinstall does that for you.  Checkinstall eliminates the 'make install' area and creates AND installs a .deb package for you, therefore you can remove it with a simple 'dpkg -r foo' or in synaptic.

The first thing you need to do is install check install.  So we have to uncomment universe, and apt-get check install like so:
```
$sudo gedit /etc/apt/sources.list
```

then uncomment universe so it looks like this
```
deb http://archive.ubuntu.com/ubuntu/ warty universe 
deb-src http://archive.ubuntu.com/ubuntu/ warty universe
```
save and exit.
Then, open synaptic and search for checkinstall (make sure you update first) or...
```
 $ sudo apt-get update && apt-get install checkinstall
Reading Package Lists... Done
Building Dependency Tree... Done
The following NEW packages will be installed:
  checkinstall
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.8kB of archives.
After unpacking 135kB of additional disk space will be used.
```
Enter Y to install.

Now, download that source file you need, unpack it using 'tar zxvf (or jxvf) foo' and  cd to that sources directory.

then do the usual.
```
  ~/Path/to/folder:$ ./configure

when that is done

   ~/path/to/folder:$ make

let that finish, then, instead of doing a 'make install' do this:

   ~/path/to/folder:$ sudo checkinstall
```

accept all the defaults, then an option will come up to set a description.  You can set one, then hit enter twice, or just hit enter. Select the next default. And that's it. You're done!!
Checkinstall installed the new .deb package for you, and put a copy of the package into that foler you were working in.  Now you can move that .deb package where ever you want it and delete that folder.
Now if you want to remove that package, just 'dpkg -r pkgname' or 'apt-get remove pkgname' or do it in synaptic.

Try it out... download beep-media-player based on the other howto ([http://www.ubuntuforums.org/showthread.php?t=1988](http://www.ubuntuforums.org/showthread.php?t=1988))  , then at the end instead of doing a 'make install' do a 'checkinstall'. Then you have a .deb package for future use.

Easy as that.

Comments appriciated!!!

---

### Post by tanari on 2004-10-31
thank you
Can I use that .deb package only on my machine? or all people can use it?

---

### Post by oddabe19 on 2004-10-31
[QUOTE=tanari]thank you
Can I use that .deb package only on my machine? or all people can use it?[/QUOTE]

Anyone, IIRC, cause i've built a few .debs using checkinstall and distributed them here.  As long as you have a standard .config file (universal config, whatever you wanna call it) you should be good to go.

---

### Post by tanari on 2004-10-31
hmmm it is very good, and very easy :) 
tomorrow i will create debs for all my favourite apps and post here

---

### Post by tanari on 2004-11-01
ok, a created debs for some packages, please test them.

[Mplayer-1.0pre5](http://tsarpovelitel.nextmail.ru/mplayer_1.0pre5-1_i386.deb)
[BMP-0.9.7rc2](http://tsarpovelitel.nextmail.ru/beep-media-player_0.9.7rc2-1_i386.deb)
[Tomboy-0.2.2](http://tsarpovelitel.nextmail.ru/tomboy-0.2.2_0.2.2-1_i386.deb)
[gwget-0.90](http://tsarpovelitel.nextmail.ru/gwget_0.90-1_i386.deb)

i noticed something strange
bmp folder size is 20 MB, but bmp.deb file is only 845 **K**B.

---

### Post by mr_ed on 2004-11-02
Yeah, checkinstall is a great program.  I was using it with Slackware last year.
>  As long as you have a standard .config file (universal config, whatever you wanna call it) you should be good to go.

The only other issue that can screw up is the options passed to ./configure.

---

### Post by jdong on 2004-11-02
using dh_make the proper way really isn't much harder...

---

### Post by kamstrup on 2004-11-19
dh_make... Well it wasn't /that/ hard but I have some serious troubles getting my manpage included in my package... I have packaged Drivel 1.2.2 and renamed debian/manpage.1.ex to debian/drivel.1 and made some small modifications to it. When I try a lintian it complains about no man page for drivel... Any ideas?

Where and how do I submit packages to uni-/multiverse?

Cheers

EDIT: I used the tutorial here : [http://www.debian.org/doc/maint-guide/ch-start.en.html](http://www.debian.org/doc/maint-guide/ch-start.en.html)

---

### Post by zenwhen on 2004-11-19
I loved this tool in Slackware, and even though the apt repos have most of what I need, it is still nice to have his wonderful tool.

---

### Post by FLeiXiuS on 2004-11-19
Sweet HOWTO, thanks.   I never knew of checkinstall, is it a recent release?

---

### Post by r_a_trip on 2004-11-26
No, Checkinstall is already a venerable project. I've played with it on and off for about two to three years, but until now I never really appreciated it's power.

I was using SUSE until recently and I installed Ubuntu just out of curiosity and that showed me two things.

One, RPM based package systems are utterly horrible and that is **THE** reason I didn't find much use in Checkinstall. What good is an easy source2package converter if the package system screws it up afterwards.

Two, KDE is overwhelming. The configurability of KDE is next to nothing, but it really IS cluttered and after using Gnome 2.8 for a month now, I realize that the Gnome developers went on the right path. But point two is reasonably off-topic ;)

---

### Post by xbaez on 2005-08-05
Thanks for the tip

Were can I understand how to create a proper control file?
that's the only thing that I'm really missing here

I will try checkinstall tonigh

---

### Post by xbaez on 2005-08-05
[QUOTE=xbaez]Thanks for the tip

Were can I understand how to create a proper control file?
that's the only thing that I'm really missing here

I will try checkinstall tonigh[/QUOTE]
 WOW
this is amazing, so what about this .deb file?
I've just installed Amarok and it works OK
I lunch synaptic, and check it's dependencies
check this:

No dependencies
How can I fix this with checkinstall?

I really, really, want an easy way to do this ;)

---

### Post by Kelsin on 2006-08-26
> **xbaez said:**
> WOW
this is amazing, so what about this .deb file?
I've just installed Amarok and it works OK
I lunch synaptic, and check it's dependencies
check this:

No dependencies
How can I fix this with checkinstall?

I really, really, want an easy way to do this ;)

I would assume that the "real" way of making a debian package listed here:
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

would step you through dependency checks and stuff... I'm not positive though. I think check install is more of a way to mark files that the make install command copied to your file system so that you can remove them. It's not the way to make a true deb package that should be distributed on a large scale.

Edit: I'm pretty sure even with that method you have to know the dependencies for the package you're building. That guide lists ways of making a clean chrooted debian environment to test dependencies, you can probably do the same thing with ubuntu relativly easily.

---

### Post by rahul_bhise on 2007-07-08
> **oddabe19 said:**
> 

then uncomment universe so it looks like this
```
deb http://archive.ubuntu.com/ubuntu/ warty universe 
deb-src http://archive.ubuntu.com/ubuntu/ warty universe
```
save and exit.


where to uncomment universe

---

### Post by smartygoldenfish on 2008-03-24
MAN I TRIED THIS ALL AND IT STARTED DDOWNLOADING SUMTHING
AND DONWLOADED 40 MB OF DATA 
I USE UBUNTU 7.10
AND AT LAST WHEN I TYPED
./configure
i got the same error msg as i got b4 d tutorial

u wasted my bandwidth nothing else

---

### Post by rogerdean on 2008-09-26
hi folks

am trying this, but when i try 

./configure

i get this

roger@roger-laptop:~/mozilla$ ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking build system type... i686-pc-linux-gnulibc1
checking for gawk... no
checking for mawk... mawk
checking for nsinstall... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
roger@roger-laptop:~/mozilla$ 

any ideas?

cheers
Roger

---

### Post by rogerdean on 2008-09-26
aha, i took a punt that i'd need build-essential installed. that helped, with loads of output which finished with this...

checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
roger@roger-laptop:~/mozilla$ 

what now??

---

### Post by kevdog on 2008-09-28
You haven't installed the libgtk package.  

When compiling from sources, you need to install the appropriate libraries (dependencies) or things will not compile.  When you get messages like this (when you compile you will get a lot of these), you need to learn how to search for your package.  In order to do this I usually do the following at the command line:

sudo apt-cache search <package name -- or guess at package name>

Please not that in your case the warning is telling you something about a gtk package.  So in your case I would do the following:

sudo apt-cache search gtk

When compiling from source you only need the library developmental packages to install.  Again to install a package found on the list it is:

sudo aptitude install <package_name>

In some cases aptitude which tends to pull in dependencies in most cases (which is good) works, but if you are getting screwy errors with aptitude:

sudo apt-get install <package_name>

You will have to use both of the aptitude/apt-get processes from time to time, so good to know both methods.

Finally I think the package you want (possibly) is

libgtk2.0-dev

So I think you should do (summary):
sudo aptitude install libgtk2.0-dev

Hopefully I answered your question and educated you on a general process to help you with future package errors you many encounter.

---

### Post by rogerdean on 2008-09-28
hi kevdog

thanks for that. yeah, i was missing plenty of packages...! i think i'm on track now, but merlwiz on the mint forums is likely to beat me to it...

cheers
roger

---

### Post by kevdog on 2008-09-28
Beat you to what?  Figuring out checkinstall??:confused:

---

### Post by rogerdean on 2008-09-29
he'll certainly make a deb quicker than i can figure out checkinstall...

---

### Post by kevdog on 2008-09-29
The only problem with checkinstall, that I am aware of, is that the deb package it makes doesn't include the needed dependencies, so for example if you are taking the deb to another machine -- or distributing it -- it might not work on other machines without the prerequisite libraries being installed.

Please correct me if I am wrong about this!!

---

### Post by andrew.46 on 2008-11-26
Hi kevdog:

> **kevdog said:**
> The only problem with checkinstall, that I am aware of, is that the deb package it makes doesn't include the needed dependencies, so for example if you are taking the deb to another machine -- or distributing it -- it might not work on other machines without the prerequisite libraries being installed.

Please correct me if I am wrong about this!!

Well I am not such a big fan of checkinstall but there is the ability to list dependencies by using the '--requires' option. But you are really getting towards needing to create a 'formal' debin package by then I think.

  Andrew

---

### Post by andy_blah on 2008-12-31
Can somebody show me a 'formal' method of creating a .deb package? Thank-you in advance

---

### Post by sleepyjon on 2009-02-26
Thank You! That is easier.

---

### Post by kevdog on 2009-02-26
I'm not trying to be Scrooge, hoewever I think you should discuss the problems associated with checkinstall such as the upgrade of packages/downgrade of packages, uninstallation, etc.  After using checkinstall for awhile, frankly I can't recommend it to anyone!

---


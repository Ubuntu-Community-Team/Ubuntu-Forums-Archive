---
title: "HOWTO: Maple"
date: 2006-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by PriceChild on 2006-10-24
Got a copy of maple10 the other day and had problems installing it because of an updated java version in edgy, although this has been seen in Dapper aswell.

If you see this error:
```

/media/cdrom0$ sudo sh installMapleLinuxSU
Password:
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.13374/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```when trying to install then this guide is for you.

make tmp dir in home for messing around in.
```
mkdir ~/tmpmaple
```cd to cdrom
```
cd /media/cdrom
```copy files
```
cp -R Linux ~/tmpmaple
cp installMapleLinuxSU ~/tmpmaple
```move to dodgy dir
```
cd ~/tmpmaple/Linux/Disk1/InstData/VM
```rename file
```
mv LinuxInstaller.bin LinuxInstaller.bin.pak
```edit file
```
cat LinuxInstaller.bin.pak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > LinuxInstaller.bin
```move back to start
```
cd ~/tmpmaple
```start the install
```
sudo sh installMapleLinuxSU
```

---

### Post by Hikaru79 on 2006-11-03
Thanks a million, it worked like a charm :)

May I ask how you figured out the change to the installer?

---

### Post by Ecthelion on 2006-11-03
Great HOWTO! :-D

---

### Post by redforce on 2006-11-03
Had this problem for Maple 9.5 on Ubuntu 6.10 as well. Your solution works, thank you very much! I already played around with LinuxInstaller.bin but I was not successful in finding the right knob to turn ;)

---

### Post by Kay on 2006-11-04
yehaaa thanks!

I have another Maple problem. I have US international keyboard activated (so I usually need to type a space after a ^ or ' or `  But in Maple that doesnt work, in other words, I cant get a ^, so cant take powers :(
OK, I can, by copying the ^ from another application, or use the maple sidebar icon for taking power, but its just not very nice.
Anyone has a solution?
(And another pretty offtopic question, but still related to this one, how can I set up in general that I dont have to press space after a ^ or ' or `, but can just continue typing, and if the next letter isn't one who supports accents, X just puts the accent and the letter on the screen. So I can type ^h  instead  of  ^ space h)

---

### Post by Ecthelion on 2006-11-04
Usually to take powers you can do **

example: x^3=x**3

:-)

---

### Post by dpm on 2006-11-05
> **Kay said:**
> yehaaa thanks!

I have another Maple problem. I have US international keyboard activated (so I usually need to type a space after a ^ or ' or `  But in Maple that doesnt work, in other words, I cant get a ^, so cant take powers :(
OK, I can, by copying the ^ from another application, or use the maple sidebar icon for taking power, but its just not very nice.
Anyone has a solution?
(And another pretty offtopic question, but still related to this one, how can I set up in general that I dont have to press space after a ^ or ' or `, but can just continue typing, and if the next letter isn't one who supports accents, X just puts the accent and the letter on the screen. So I can type ^h  instead  of  ^ space h)

I would try to see if there is an "Eliminate Dead Keys" variant of your keyboard layout under System>Preferences>Keyboard

---

### Post by franco44444 on 2006-11-07
thanks a lot, it worked very well on ubuntu 6.10 with Maple 9.5

---

### Post by rquint on 2006-11-09
You can also run the Maple 10 updates in Edgy by making the same changes to the installer .bin files.

---

### Post by BLTicklemonster on 2006-11-12
... what is maple?

---

### Post by Kay on 2006-11-12
> **BLTicklemonster said:**
> ... what is maple?
[http://www.maplesoft.com](http://www.maplesoft.com)

A computer algebra system, very handy on technical university :)

---

### Post by vloris on 2006-11-13
One warning: don't try to use vim to edit the LinuxInstaller.bin file :D 
It will give you a corrupted file and error-message like this:

```
floris@homeros:/media/data/Downloads/maple$ ./installMapleLinuxSU 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...

gzip: /tmp/install.dir.14603/Linux/resource/vm.tar.Z: not in gzip format

uncompress: /tmp/install.dir.14603/Linux/resource/vm.tar.Z: not in gzip format

gzip: /tmp/install.dir.14603/Linux/resource/vm.tar.Z: not in gzip format
The included VM could not be uncompressed (GZIP/UNCOMPRESS). Please try to
download the installer again and make sure that you download using 'binary'
mode.  Please do not attempt to install this currently downloaded copy.

```

Suddenly the .tar.Z archives are corrupted? Eventually I discovered I corrupted them myself by trying to be smart and using vim instead of sed ](*,) 

So, just do exactly as the first post states, then everything will be allright!

---

### Post by j_Doe on 2006-11-21
I am trying to see if others where I work can easily use Ubuntu on 
their computers, i.e. I do not need to hold their hands.  One of the 
programs they need is Maple 10.  I have tried to install and start 
Maple 10 on both ubuntu and kubuntu.  The instructions here for installing 
work quite well.  

Unfortunately, Maple 10 will not start after the installation. :( 
Has anyone had and/or solved this problem?

---

### Post by Hikaru79 on 2006-11-21
> **j_Doe said:**
> 
Unfortunately, Maple 10 will not start after the installation. :( 
Has anyone had and/or solved this problem?
Can you elaborate on how it is failing to start? Keep in mind that most likely the maple executable is not in your path; so for example, if you installed maple to /opt/maple10, the command to run is ```
/opt/maple10/bin/xmaple
``` not ```
maple
```

---

### Post by j_Doe on 2006-11-22
The command I use is

/usr/local/maple10/bin/xmaple 

for the installation directory /usr/local/maple10.

The processes that are running are:

xmaple
maple
Linux_shlibs
processor

Since there is no java running, I am wondering
if Maple is not finding its java installation.
On SUSE the processes are 

xmaple
maple
java
mserver
mfsd

An addendum:

It turns out that Maple 10 does not support the VIA C3 
processor under Linux and that is why it would not run.  Even after
removing the processor check, the Maple kernel does not start.
Maple is trying to fix this for Maple 11.

---

### Post by lucascr on 2006-11-24
I followed this howto, as well as others I found on this forum, but with no success.
I use kubuntu edgy and the installer returns the following output:

```

> sudo sh LinuxInstaller.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: cmd. line:6: warning: escape sequence `\.' treated as plain `.'

Launching installer...

An internal LaunchAnywhere application error has occured and this application cannot proceed. (LAX)

Stack Trace:
java.lang.IllegalArgumentException: Malformed \uxxxx encoding.
        at java.util.Properties.loadConvert(Unknown Source)
        at java.util.Properties.load(Unknown Source)
        at com.zerog.common.java.util.PropertiesUtil.loadProperties(DashoA8113)
        at com.zerog.lax.LAX.<init>(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)


```

It seems there are problem with Java. I have the following installed (only shown installed packages):
```

> dpkg -l *java*
||/ Name           Version        Description
+++-==============-==============-============================================
ii  java-common    0.25ubuntu1    Base of all Java packages
ii  java-package   0.27           utility for building Java(TM) 2 related Debi
ii  libcairo-java  1.0.5-0ubuntu2 CAIRO bindings for Java
ii  libglib-java   0.3.2-0ubuntu2 GLIB bindings for Java
ii  libgnucrypto-j 2.1.0-1        full-featured cryptographic library in Java
ii  libgtk-java    2.9.3-0ubuntu2 GTK+ bindings for Java
ii  libhsqldb-java 1.8.0.5-2ubunt Java SQL database engine
ii  libjaxp1.2-jav 1.2.01-1ubuntu Java XML parser and transformer APIs (DOM, S
ii  libjline-java  0.9.5-2ubuntu1 Java library for handling console input
ii  libservlet2.3- 4.0-8ubuntu2   Servlet 2.3 and JSP 1.2 Java classes and doc
ii  libxalan2-java 2.6.0-6ubuntu4 XSL Transformations (XSLT) processor in Java
ii  libxerces2-jav 2.6.2-4ubuntu5 Validating XML parser for Java with DOM leve
ii  libxt-java     0.20050823-2ub An implementation in Java of XSL Transformat
ii  openoffice.org 2.0.4-0ubuntu2 OpenOffice.org office suite Java support arc
ii  sun-java5-bin  1.5.0-08-0ubun Sun Java(TM) Runtime Environment (JRE) 5.0
ii  sun-java5-demo 1.5.0-08-0ubun Sun Java(TM) Development Kit (JDK) 5.0 demos
ii  sun-java5-font 1.5.0-08-0ubun Lucida TrueType fonts (from the Sun JRE)
ii  sun-java5-jdk  1.5.0-08-0ubun Sun Java(TM) Development Kit (JDK) 5.0
ii  sun-java5-jre  1.5.0-08-0ubun Sun Java(TM) Runtime Environment (JRE) 5.0
ii  sun-java5-sour 1.5.0-08-0ubun Sun Java(TM) Development Kit (JDK) 5.0 sourc

```

I'm missing some packages or should I set some variables/options?
Any hints?
Thanks in advance for your help.

Luca

---

### Post by djberndt on 2006-11-27
great howto!
thank you! :D

---

### Post by cdw on 2006-12-05
I am trying to install maple 9 on Ubuntu 6.10, I followed the instructions, modified slightly for the file names in maple 9 distro disk, including commenting out the export LD...  line, then when I went to install:

cdw@vacqueyras:~/tmpmaple$ sudo sh installMapleLinuxSU 
Error: failed /home/cdw/tmpmaple/Linux/Linux/resource/jre/lib/i386/client/libjvm.so, because libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

When I installed maple 9 on ubuntu 6.06, I found it necessary to create the
following link:
sudo ln -sf /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/lib/libstdc++-libc6.1-1.so.2

unfortunately the /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
file is not available in my 6.10 distro

---

### Post by cdw on 2006-12-06
The solution to the problem I described above is to load the tw missing packages and install them as described in:

[http://linuxcompatible.org/story35920.html](http://linuxcompatible.org/story35920.html)

then create the symbolic link, and the install runs smothly.

---

### Post by j_Doe on 2006-12-08
> **lucascr said:**
> I followed this howto, as well as others I found on this forum, but with no success.
I use kubuntu edgy and the installer returns the following output:

```

> sudo sh LinuxInstaller.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: cmd. line:6: warning: escape sequence `\.' treated as plain `.'

Launching installer...

An internal LaunchAnywhere application error has occured and this application cannot proceed. (LAX)

Stack Trace:
java.lang.IllegalArgumentException: Malformed \uxxxx encoding.
        at java.util.Properties.loadConvert(Unknown Source)
        at java.util.Properties.load(Unknown Source)
        at com.zerog.common.java.util.PropertiesUtil.loadProperties(DashoA8113)
        at com.zerog.lax.LAX.<init>(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)


```

It seems there are problem with Java. I have the following installed (only shown installed packages):
```

> dpkg -l *java*
||/ Name           Version        Description
+++-==============-==============-============================================
ii  java-common    0.25ubuntu1    Base of all Java packages
ii  java-package   0.27           utility for building Java(TM) 2 related Debi
ii  libcairo-java  1.0.5-0ubuntu2 CAIRO bindings for Java
ii  libglib-java   0.3.2-0ubuntu2 GLIB bindings for Java
ii  libgnucrypto-j 2.1.0-1        full-featured cryptographic library in Java
ii  libgtk-java    2.9.3-0ubuntu2 GTK+ bindings for Java
ii  libhsqldb-java 1.8.0.5-2ubunt Java SQL database engine
ii  libjaxp1.2-jav 1.2.01-1ubuntu Java XML parser and transformer APIs (DOM, S
ii  libjline-java  0.9.5-2ubuntu1 Java library for handling console input
ii  libservlet2.3- 4.0-8ubuntu2   Servlet 2.3 and JSP 1.2 Java classes and doc
ii  libxalan2-java 2.6.0-6ubuntu4 XSL Transformations (XSLT) processor in Java
ii  libxerces2-jav 2.6.2-4ubuntu5 Validating XML parser for Java with DOM leve
ii  libxt-java     0.20050823-2ub An implementation in Java of XSL Transformat
ii  openoffice.org 2.0.4-0ubuntu2 OpenOffice.org office suite Java support arc
ii  sun-java5-bin  1.5.0-08-0ubun Sun Java(TM) Runtime Environment (JRE) 5.0
ii  sun-java5-demo 1.5.0-08-0ubun Sun Java(TM) Development Kit (JDK) 5.0 demos
ii  sun-java5-font 1.5.0-08-0ubun Lucida TrueType fonts (from the Sun JRE)
ii  sun-java5-jdk  1.5.0-08-0ubun Sun Java(TM) Development Kit (JDK) 5.0
ii  sun-java5-jre  1.5.0-08-0ubun Sun Java(TM) Runtime Environment (JRE) 5.0
ii  sun-java5-sour 1.5.0-08-0ubun Sun Java(TM) Development Kit (JDK) 5.0 sourc

```

I'm missing some packages or should I set some variables/options?
Any hints?
Thanks in advance for your help.

Luca


When trying to install under KDE and SUSE 10.1 the

sudo ./LinuxInstaller.bin

command did not work for me.  The sequence

su
./LinuxInstaller.bin

worked.  Perhaps it will work for you.  

Another possible way to install Maple 10 is to use
the console option.  You can try

sudo ./LinuxInstaller.bin -i console

This is from MapleSoft.

Good luck.

---

### Post by reza81 on 2007-01-02
thanks a lot for all of this information, specialy the installing instructions! 

you helped me bigtime !!!

---

### Post by kapetanski on 2007-01-12
worled fine with maple 10 on my edgy (xubuntu) lappie, thanx ;)

---

### Post by ehamberg on 2007-01-30
I get the same error as lucascr mentioned above:

```
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

An internal LaunchAnywhere application error has occured and this application cannot proceed. (LAX)

Stack Trace:
java.lang.IllegalArgumentException: Malformed \uxxxx encoding.
        at java.util.Properties.loadConvert(Unknown Source)
        at java.util.Properties.load(Unknown Source)
        at com.zerog.common.java.util.PropertiesUtil.loadProperties(DashoA8113)
        at com.zerog.lax.LAX.<init>(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)

```

Any ideas?

Edit:

Found the solution here:
[http://ubuntuforums.org/showthread.php?p=2016839](http://ubuntuforums.org/showthread.php?p=2016839)

```
export PS1=">"
``` did the trick. Stupidest error ever.

---

### Post by googolminex on 2007-02-03
I purchased and downloaded the Maple 10 self-extracting installer from MapleSoft's website, Linux10Installer.bin. I received an error indicating that libc.so.6 couldn't be found. As has been suggested elsewhere, you must comment out the "export LD_ASSUME_KERNEL=2.2.5" lines. In fact, this was all I needed to do. As others have warned, this is tricky because the self-extracting file is easily corrupted by adding or deleting characters because it is a binary file. I used ghex, a hex editor to replace the "e" in export" with a pound sign to give "#xport". Keep a backup copy of your installer script just in case you make a mistake.

I hope this helps.

Damian Eads

---

### Post by lucascr on 2007-02-06
Dear ubuntu-users,

following the link reported by ehamberg ([http://ubuntuforums.org/showthread.php?p=2016839]("http://ubuntuforums.org/showthread.php?p=2016839")) I solved the problem. Many thanks.

Luca

---

### Post by JanusDC on 2007-04-20
Thank you very much!

---

### Post by Lyrandian on 2007-04-20
Thank you very much for your explanation.  We've been hitting the same exact problem trying to install the Millennium Innovation Catalogue software at the Drexel Library.  The guy who has been trying to get it installed on some of our linux boxes hasn't been able to get it to work on anything except Mepis and PCos.  I tried it on my debian server, and my ubuntu laptop with no luck, and threw it to the back of my mind, as I was just looking at it as a favor.  Your instructions, slightly modified, worked wonderfully.  Thank you very much.

---

### Post by cap_gemo on 2007-04-21
> **PriceChild said:**
> 
```
cat LinuxInstaller.bin.pak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > LinuxInstaller.bin
```


Say, thanks a lot! This guide saved my life! I have already wished, I'd better stay by Ubuntu dapper, although feisty is a lot cooler. Thanks again!

---

### Post by Yitram on 2007-04-22
I'm getting similar errors trying to install Maple 8.  Going to see if this works for me.
EDIT:

My file system has different directories and my souce for the Maple files is also a tar file "Maple8_CD.tar" or "Maple9_CD.tar" and so I don't know if this will work or not.

In another place on the network, I found a Maple10.rar, so I am going to try that to see if it has the same file structure as whats described here.

EDIT^2: 

The Maple 10 file has the same structure except the file in the /VM/ directory is UnixInstaller.bin  I think this is for a network Unix install.  I don't think they actually have an LInux version of maple available for students.

---

### Post by rayohauno on 2007-04-24
thanks a lot ... concise and precise ... :popcorn:

---

### Post by Madley on 2007-04-25
I've got the same problem with Maple 10 on Ubuntu Feisty Fawn, this HowTo resolve the problem!

Great HowTo!

---

### Post by gms on 2007-04-26
Hello.
This is not a question, but an answer. I have just installed Maple 11 under Ubuntu 7.04 Feisty Fawn and I thought I would share my experience.
1) Log in to an account with sudo rights.
2) Insert the Maple 11 cd for Linux. When asked about what to do with it, mount it.
3) Open a terminal and write
cd /cdrom
sudo sh ./installMapleLinux32
4) Enter your password.
5) For the location of the installation, I entered /usr/local/maple11 instead of the default.
6) After the installation (and the activation) is complete, I created two symbolic links as follows: on the terminal, write
cd /usr/local/bin
ln -s /usr/local/maple11/bin/xmaple
ln -s /usr/local/maple11/bin/maple
7) That is all!

---

### Post by cartan on 2007-04-26
I have installed maple9 in my system ubuntu feisty fawn (7.04).
there was no problem on installation. however when I try to run xmaple under ~/maple9/bin
it says that "Do you want to run "xmaple", or display its contents?", and when I press the "Run" 
button nothing happens. I could not resolve this problem. Could anyone please help me?

---

### Post by sasomao on 2007-04-27
Hi,

I've maple 11.

When I try to create a package with the command 


nameofpackage:=module()
.
.
.
end module;

savelib('nameofpackage'):



Maple print this error:

Error, cannot open archive, /home/salvatore/maple11/lib, for writing.

(the lib address is the good one...I can LOAD the packages)

So I think there is a problem of permission to write a new document in the dossier lib because maple dont have the autority

Someone can help me?

Tk you

S.

---

### Post by Seth Quarrier on 2007-05-06
Just so you all know this works for X86_64 version of Maple as well (on Feisty) just change the name of the installer files from Linux_Installer.bin to LinuxX86_64Installer.bin or LinuxX86_64NetworkInstaller.bin in the sed command and it should work.

-Seth

---

### Post by thk on 2007-05-10
A one-liner:

```

perl -p -i -e 's/export LD_ASSUME_KERNEL/#export LD_ASSUME_KERNEL/' <filename>

```

---

### Post by thk on 2007-05-10
Hmmm... now I get:

root@papua:/tmp# ./Maple1006LinuxUpgrade.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...

gzip: /tmp/install.dir.8714/Linux/resource/vm.tar.Z: not in gzip format

uncompress: /tmp/install.dir.8714/Linux/resource/vm.tar.Z: not in gzip format

gzip: /tmp/install.dir.8714/Linux/resource/vm.tar.Z: not in gzip format
The included VM could not be uncompressed (GZIP/UNCOMPRESS). Please try to
download the installer again and make sure that you download using 'binary'
mode.  Please do not attempt to install this currently downloaded copy.

---

### Post by thk on 2007-05-10
> **thk said:**
> Hmmm... now I get:

root@papua:/tmp# ./Maple1006LinuxUpgrade.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...

gzip: /tmp/install.dir.8714/Linux/resource/vm.tar.Z: not in gzip format

uncompress: /tmp/install.dir.8714/Linux/resource/vm.tar.Z: not in gzip format

gzip: /tmp/install.dir.8714/Linux/resource/vm.tar.Z: not in gzip format
The included VM could not be uncompressed (GZIP/UNCOMPRESS). Please try to
download the installer again and make sure that you download using 'binary'
mode.  Please do not attempt to install this currently downloaded copy.

Oh. Duh. I guess perl probably mangled the binary bits...

---

### Post by d4n on 2007-05-24
This How To fixes all my install problems for maple. However not when I try use maple I get an error saying Kernel Connection Not Available. When I google this everyone seems to say it's a firewall issue. Yet I don't think I have a firewall running (its a fresh install of Kubuntu 7.04) and just to make sure I loaded guard dog and selected disable firewall. However still don't seem to be able to run maple, I've never had any of these issues with maple before. Any ideas??

---

### Post by nmwhit06 on 2007-06-28
I am a new Ubuntu user so I'm very good at fixing my problems yet.  While installing Maple, everything in here worked for me in Feisty Fawn except the line 

> cat LinuxInstaller.bin.pak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > LinuxInstaller.bin

I found another post that worked for me.  I did not rename LinuxInstaller.bin, I just used this line:

```
sed -i "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" LinuxInstaller.bin

```

then 

```
sudo sh LinuxInstaller.bin
```

Hope this helps anyone in my situation.

---

### Post by ntlam on 2007-08-24
This HOWTO is great. I got maple 10 installed successfully.

Still have a question. How can I create an icon (on Desktop for example) so every time I want to open maple I dont have to go to the directory locating the xmaple file and run it.

---

### Post by rzrgenesys187 on 2007-08-27
Awesome Howto.  Worked for Maple 10 in feisty even though the installer didnt work in windows???

> **ntlam said:**
> This HOWTO is great. I got maple 10 installed successfully.

Still have a question. How can I create an icon (on Desktop for example) so every time I want to open maple I dont have to go to the directory locating the xmaple file and run it.

Right click on the desktop and select add launcher.  Type the name you want listed on the icon and next to command either paste the file location or use browse (in /root/maple10/bin i think).  That should work for you.

---

### Post by ntlam on 2007-08-27
> **rzrgenesys187 said:**
> Awesome Howto.  Worked for Maple 10 in feisty even though the installer didnt work in windows???



Right click on the desktop and select add launcher.  Type the name you want listed on the icon and next to command either paste the file location or use browse (in /root/maple10/bin i think).  That should work for you.

wow, how did you know that???
Thankssssssssss

---

### Post by rzrgenesys187 on 2007-08-28
Not a problem

---

### Post by Beoras on 2008-01-08
I still got Problems on Maple 8.
First what file exactly should be modified?
I got numerous versions, one in /Linux/ and one in /Linux/Linux/ bot named LinuxInstaller.bin
I allready tried changing them both the way you described above, with no result.
> /home/jujowi/tmpmaple/Linux/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
The libstdc++6 and libdc6 and both -dev are installed.
Creating the link
> sudo ln -sf /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/lib/libstdc++-libc6.1-1.so.2
didn't help a bit.
Allthough after everything together the many original complaints left for the one posted above.
Any suggestions?
Beoras

P.S.: The above may seem crap, I won't mind being told that ;)

---

### Post by Beoras on 2008-01-08
uhm, can you somehow erase double posts???

---

### Post by gertvdijk on 2008-01-09
Great How-to. Still one problem: Maple just won't start. When I execute xmaple in the terminal nothing shows, no window, no error.
I use Ubuntu Gutsy (7.10) 64-bit and Maple 10 .bin installer provided by my university. The activation failed in the installation process (too many registrations on purchase code). Could that be the problem? I just skipped the activation step and Maple assured me I can activate at a later time.
Edit: Now I have downloaded a license.dat file the maple commandline tool comes with the following:
> 
exec: 1: /usr/local/maple10/bin.X86_64_LINUX/cmaple: not found

So I found out that I miss the X86_64 dir! Well... I just symlinked that non-existing dir to the bin.IBM_INTEL_LINUX dir (Is that a good idea?). Now Maple is complaining about the license file.
> 
Maple initialization error, Invalid license file syntax
Feature:       Maple10
License path:  /usr/local/maple10/license/license.dat
FLEXlm error:  -2,413
For further information, refer to the FLEXlm End User Manual,
available at "www.globetrotter.com".

Edit2: I also needed to symlink the jre dir. Besides, somehow the license file I downloaded was empty.
**Solved that and now Maple is up and running @ Gutsy 64-bit!**
Edit3:

_**For in the how-to**_
If you're running **64-bit** version you need to symlink the non-existing dirs bin.X86_64_LINUX and jre_X86_64_LINUX to their 32-bit equivalents:
```

# First go to the install location e.g. /usr/local/maple10/
$ ln -s bin.IBM_INTEL_LINUX/ bin.X86_64_LINUX
$ ln -s jre.IBM_INTEL_LINUX/ jre.X86_64_LINUX
```
If you must use a network license and you don't get this option when installing Maple (Maple 11 & up seems to provide this):
download the license.dat file you must acquire from your institution or company and place it in the license/ dir.

---

### Post by VegaOmega on 2008-01-09
I've gone through all the install procedures and everything went great. However, when I go to start the program, it asks me to activate with my activation code, I do so, then it says that the product has been activated and prompts me to restart maple10, I do so, and upon restarting i need to activate again. This is what the error message reads:

Invalid or missing license file
System clock has been set back
Feature: Maple10
License Path:/home/'username'/maple10/license/license.dat
FLEXIm error: -88,309

And then i have to activate again. This is the point where i activate it once more the screen then pops up with a window stating the success of the activation and that i need to restart the program. The cycle then continues. Can anyone tell me how to get this program to work?

---

### Post by Peneus on 2008-03-01
Hello,

I installed maple 10 using sudo sh ./sudo ./installMapleLinuxSU -i console. And I have license code but  not a license file, though. So I can't use it. When I installed it using java before I just entered the code and that was it. Now that I couldn't install using java I don't know how to solve this lisence problem.  Any suggestions?

Thanks

---

### Post by Visitor.Q on 2008-04-15
Because I could not find icons, and I like those on my desktop instead of the default icon, I quickly made something using GIMP. They are attached to this message. Works best on a light background, but I included the GIMP file with layers so you can change it easily.

---

### Post by pete-the-meat on 2008-12-06
Hi - thanks for the instructions - the install worked fine after a wee bit of fiddling :) The only problem is that when I run xmaple (I use /root/maple9.5/bin/xmaple) it just won't start - the command line version works just fine but I need to use the gui for plotting and such... I tried capturing the output of the program using nohup but it exits without saying anything so I have absolutely no idea what the problem is.

(I am now using ArchLinux and KDE4.1 but this is the only guide I could find anywhere that applied to the problem)

---

### Post by tesfa on 2009-01-16
Hey all.  I'm really new to ubuntu and I'm trying to load maple 10 on Intrepid Ibex.  I followed the HOWTO and I still got the same error message.  Any help would be much appreciated.

---

### Post by freemath on 2009-06-19
> **gertvdijk said:**
> Great How-to. Still one problem: Maple just won't start. When I execute xmaple in the terminal nothing shows, no window, no error.
I use Ubuntu Gutsy (7.10) 64-bit and Maple 10 .bin installer provided by my university. The activation failed in the installation process (too many registrations on purchase code). Could that be the problem? I just skipped the activation step and Maple assured me I can activate at a later time.
Edit: Now I have downloaded a license.dat file the maple commandline tool comes with the following:

So I found out that I miss the X86_64 dir! Well... I just symlinked that non-existing dir to the bin.IBM_INTEL_LINUX dir (Is that a good idea?). Now Maple is complaining about the license file.

Edit2: I also needed to symlink the jre dir. Besides, somehow the license file I downloaded was empty.
**Solved that and now Maple is up and running @ Gutsy 64-bit!**
Edit3:

_**For in the how-to**_
If you're running **64-bit** version you need to symlink the non-existing dirs bin.X86_64_LINUX and jre_X86_64_LINUX to their 32-bit equivalents:
```

# First go to the install location e.g. /usr/local/maple10/
$ ln -s bin.IBM_INTEL_LINUX/ bin.X86_64_LINUX
$ ln -s jre.IBM_INTEL_LINUX/ jre.X86_64_LINUX
```
If you must use a network license and you don't get this option when installing Maple (Maple 11 & up seems to provide this):
download the license.dat file you must acquire from your institution or company and place it in the license/ dir.

Simply making a symbolic link didn't do it for me. I copied jre.IBM_INTEL_LINUX to a new directory jre.X86_64_LINUX. This works.

Thanks!

---

### Post by waterfish on 2011-07-21
I just successfully install maple 9.5 for single user on Ubuntu 11.04 after many trials.
The guide provided by [https://help.ubuntu.com/community/Maple/](https://help.ubuntu.com/community/Maple/)
is lack of some detail for this version of ubuntu.

Before you do this:
1. use the Ubuntu software center to install the <libghc6, font python font manager>

2. Info: Maple will be install in directory: opt/maple9.5
Copy the files from cdrom to home/user
 (note: if you cannot mount the cdrom: you will need isobuster under Windows to extract the needed files from the right track). 
3. use the commands as recommended by ubuntu community:
(i) use terminal (control + alt +T) to enter the following command lines after lines -- each ending with <enter>
(ii) sudo  mkdir  -p  /opt/maple9.5   (you shall install in this directory)
(iii) sudo  ./installMapleLinuxSU

Maple installer will appear:
>> enter serial number
>> directory -- you must locate opt/maple9.5 (do not use root directory)
>> message will indicate success and you now can close the installer.

(iv) Terminal screen may report some problems -- just ignore but record the message on paper for future use
(v) use the exact command given by ubuntu comm guide.
on the terminal, add these two lines:
     sudo mkdir -p /usr/local/bin   <enter>
     sudo ln -s   /opt/maple9.5/bin/{x, }  maple/user/local/bin

(vi) You are DONE with installing
   You will need to run maple.
   How? click <system file> <opt> <maple9.5><bin>
  select <xmaple> <copy to > <desktop>
(vii) from desktop click <xmaple> select <run>
(viii) you can see maple appears ... good luck.
   
   







5

---


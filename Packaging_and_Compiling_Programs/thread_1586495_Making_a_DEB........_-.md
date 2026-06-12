---
title: "Making a DEB........ :-/"
date: 2010-10-02
forum: Packaging and Compiling Programs
---

### Post by hakermania on 2010-10-02
Ok, I build all the directories and copy all the files in them, I am making the man pages, the changelogs and all all all the things needed, then I run dpkg and lintian.The only error the lintian outputs is aout the TCP bug!
I asked someone and told me that it isn't something serious and it would be better to ignore it. If you see here: [http://revu.ubuntuwire.com/p/adminutil](http://revu.ubuntuwire.com/p/adminutil) for example, you'll see some strange dsc files, some diffs etc... What are these? When I asked about them, I learned that you have to make a makefile in your source. This sounded very starnge to me. What is this make file? Is it unix script that places some files where needed? Please don't link me somewhere where I will have to read tones of text :(
Then, ok, I've made a nice prog in C++ and I would like it to post it to REVU to be reviewed! But I don't know how to create these dsc or diff files! I only know how to build the deb correctly, without lintian errors. Btw, where do I place the unistall script inside the DEB? Because lintian doesn't output any error like "Unistall script not found" but I haven't created one....!

Please I am very disappointed, and very confused!

*My question is the following:*
I have make a nice program in C++ which needs some files in $HOME/.config/ to run. My DEB package place them temporarily into the /usr/share folder and then, in the first-run of the program it copies these files into the .config dir. So, I have an executable and some files needed by it. How do I build all these diff dsc etc files? And why have they made this system so strange and confusing? Why only a DEB package isn't enough for a REVU upload? 

Thx in advance for any reply, i hope you'll get me out of this maze :'(

---

### Post by hakermania on 2010-10-02
I am soooo sad....*bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump* *bump

---

### Post by SoftwareExplorer on 2010-10-08
How do you compile your program? Do you use a specific command?

---

### Post by dv3500ea on 2010-10-08
I understand your frustration. It is very confusing at first.

You can't just upload a binary .deb file because that wouldn't work for the various different CPU architectures. To build the source package follow these steps:
[LIST]
[*]Copy your source code trunk to a new directory named package-version. Remove any version control directories (.bzr, .svn, .git etc.)
[*]Create an archive (.tar.gz) of this directory. This should not contain files specific to debian packaging.
[*]Navigate into the new directory and run ```
dh_make -c gpl -s -b -f ../package-version.tar.gz
```. Press enter when prompted. This creates a debian/ directory.
[*]Run this command to remove unnecessary files from the debian/ directory: ```
rm debian/*.EX debian/*.ex debian/R*
```
[*]You then need to edit [debian/control]("http://www.debian.org/doc/debian-policy/ch-controlfields.html"), [debian/copyright]("http://www.debian.org/doc/debian-policy/ch-docs.html#s-copyrightfile") and [debian/changelog]("http://www.debian.org/doc/debian-policy/ch-source.html#s-dpkgchangelog") with the relevant information. dh_make will have generated templates for you to use.
[*]Now edit the [debian/rules]("http://www.debian.org/doc/debian-policy/ch-source.html#s-debianrules") file. This is a [makefile]("http://www.student.cs.uwaterloo.ca/~isg/res/unix/make/index") that is used to generate binary .deb files. The best way to understand how these work is to look at the debian/rules file for the hello package. run: ```
cd /tmp && apt-get source hello && xdg-open hello*/debian/rules
```
[*]Once you have done all of this, navigate to the root of the source directory and run ```
debuild -S
``` to build the source package.
[/LIST]

---

### Post by hakermania on 2010-10-09
Ok, all went alright except 3 basic things I didn't get:
1) Should my whole source code be included into this (all the .cpp  and .h files???), because you told me to cd to the dir of my program's source code(!). Anyway I didn't have any problem there, just I want to know if I understood correctly.
2) What about the rules files? What is it's job? Why does it exist? To unistall the deb? To build the source? I didn't get it, and, in addition, the rules file seems to be written in a kind of unix scripting, but I cannot understand very well all the commands or what is trying to do (I am referring to the rules file of the hello package)
3) What about the folder that need to exist at /usr/share/ and then copied to $HOME/.config/ in first app run? Where do I include it?


Thank you so much for your help. I've stack here weeks now (ok, i'm not trying to do this weeks but I've tried at least 20 hours to get it work)

---

### Post by dv3500ea on 2010-10-09
> **hakermania said:**
> Ok, all went alright except 3 basic things I didn't get:
1) Should my whole source code be included into this (all the .cpp  and .h files???), because you told me to cd to the dir of my program's source code(!). Anyway I didn't have any problem there, just I want to know if I understood correctly.


To clarify, you copy your 'raw' source code directory, including all files except from unneeded version control folders, to a new directory to work in. You then do all of your steps with this directory. This should contain all of your .cpp, .h, etc. files - as should the .tar.gz archive.

> 
2) What about the rules files? What is it's job? Why does it exist? To unistall the deb? To build the source? I didn't get it, and, in addition, the rules file seems to be written in a kind of unix scripting, but I cannot understand very well all the commands or what is trying to do (I am referring to the rules file of the hello package)


The rules file is a make file that is used to compile the source code and create the binary .deb package. A make file is just a fancy shell script that has a set of commands for separate 'targets'. Here is a commented template for a debian/rules file:
```

#!/usr/bin/make -f

build:
	#put a list of shell commands here to compile/build your source code.

clean:
	#put a list of shell commands here to remove any temporary files created
	#during the build process (eg. .o files).

binary-indep: build
	#COMMANDS HERE SHOULD WORK THE SAME ON ALL CPU ARCHITECTURES
	#delete temporary data from any previous builds
	rm -rf debian/tmp
	#create a new directory tree for temporaty data
	#add commands to copy files into the debian/tmp directory
	#as if it were the '/' directory on the installing machine
	mkdir -p debian/tmp/DEBIAN
	#
	#Add commands here to:
	#  copy data files to /usr/share [debian/tmp/usr/share] (configuration files can be copied from
	#here to the user's home dir on first run.
	#  copy excecutable programs to /usr/bin [debian/tmp/usr/bin] and
	#make them excecutable by all users so that they become commands.
	#  copy shared libraries to the correct place for your programming language.
	#compiled '.so' files should be put in /usr/lib [debian/tmp/usr/lib].
	#  copy manpages to /usr/share/man/man1 [debian/tmp/usr/share/man/man1] (for excecutable programs).
	#  copy documentation files (README etc.) to /usr/share/doc/PACKAGE
	#[debian/tmp/usr/share/doc/PACKAGE]
	#  copy debian/changelog to the debian/tmp/usr/share/doc/PACKAGE/changelog.Debian and
	# compress it with `gzip -9`
	#  copy debian/copyright to debian/tmp/usr/share/doc/PACKAGE/copyright (DO NOT COMPRESS)
	#
	#compress man pages
	gzip -r9 debian/tmp/usr/share/man
	#
	#The following commands sets the correct permissions
	chown -R root:root debian/tmp
	chmod -R u+w,go=rX debian/tmp

binary-arch: build
	#COMMANDS HERE MAY WORK DIFFERENTLY ON DIFFERENT CPU ARCHITECTURES
	#sort out the control file, so that important metadata is visible
	#to package managers
	dpkg-gencontrol
	#Finally: this command builds the binary .deb file
	dpkg --build debian/tmp ..

binary: binary-indep binary-arch

.PHONY: binary binary-arch binary-indep clean

```

> 
3) What about the folder that need to exist at /usr/share/ and then copied to $HOME/.config/ in first app run? Where do I include it?

Put these files in a directory in your source code (data/config is a good idea). In your debian/rules file in the 'binary-indep' target, copy them all to debian/tmp/usr/share/PACKAGE_NAME/config. On the first run of your program, copy this to ~/.config.

> 
 I've stack here weeks now (ok, i'm not trying to do this weeks but I've tried at least 20 hours to get it work)

Just keep at it :). It will make sense *eventually* (It did for me) but there is a large learning curve and Debian packaging is very strict to ensure quality of packages. The difficult packaging process ultimately means that packages are easy for users to manage but, unfortunately, hard for developers to create.

---

### Post by Yellow Pasque on 2010-10-09
There should be a place where developers can upload their code for .deb packaging.

> Just keep at it . It will make sense eventually (It did for me) but there is a large learning curve and Debian packaging is very strict to ensure quality of packages. The difficult packaging process ultimately means that packages are easy for users to manage but, unfortunately, hard for developers to create.
Thanks for encouragement. The .deb package is the main reason I stick to Debian-based distros. RPM's and pacman (Arch Linux) are inferior solutions, IMHO.

---

### Post by hakermania on 2010-10-16
Thx for the support guys!
Question: In the information placed to the rules file it says that rules file is the right place to copy executables to /usr/bin/
So, do I copy there the executables generated after the build process, or do I place the executables to an another temporary directory (/debian/data for instance) and copy them to /usr/bin/ instantly? E.g. The output executable after the build is *omehin.01-1* then in the **binary-indep:** target should I do something like:
[B]        mv -f omehin.01-1 ome #Give the executable preferable name, not the name that build process gave it
        cp ome /usr/bin/[/B] #Copy it to the executables location
????

Another question: What about the **binary-arch:** target? 
It displays as info:[I]
    dpkg-gencontrol
    #Finally: this command builds the binary .deb file
    dpkg --build debian/tmp ..[/I]

I used to build the deb using 
*dpkg-deb --build helloworld_1.0-1* where *helloworld_1.0-1* was the folder in which all files were including (I am referring to the traditional way of building deb packages. Where should this command refer to? I mean to which folder? Into the folder I have the source at?

Thx very much again for the help :)

[COLOR=Navy]What is the correct way now?[/COLOR]

---

### Post by SoftwareExplorer on 2010-10-17
If I remember correctly, the recommended command to use is 'install'. I believe it also lets you set the file permissions at the same time.

---

### Post by dv3500ea on 2010-10-22
> **hakermania said:**
> 
Question: In the information placed to the rules file it says that rules file is the right place to copy executables to /usr/bin/
So, do I copy there the executables generated after the build process, or do I place the executables to an another temporary directory (/debian/data for instance) and copy them to /usr/bin/ instantly? E.g. The output executable after the build is *omehin.01-1* then in the **binary-indep:** target should I do something like:
[B]        mv -f omehin.01-1 ome #Give the executable preferable name, not the name that build process gave it
        cp ome /usr/bin/[/B] #Copy it to the executables location


In the rules script, copy your executables to debian/tmp/usr/bin. Use the debian/tmp directory as if it were the root directory of the machine it is installed on.

---

### Post by hakermania on 2010-10-23
I am a bit confused guys.... Can you explain me a bit better where do I place the files that are to be moved?

---

### Post by dv3500ea on 2010-10-23
> **hakermania said:**
> I am a bit confused guys.... Can you explain me a bit better where do I place the files that are to be moved?

These commands in debian/rules:

```

rm -rf debian/tmp
mkdir -p debian/tmp/DEBIAN

```

Create a temporary directory 'debian/tmp' and add  a DEBIAN folder to it. This folder is equivalent to the folder you use to create binary debs with ```
dpkg-deb --build
```. So in your rules file, you need to add commands to copy files from '.' (Your current directory which will be the root directory of your source code tree when it is built) to debian/tmp. Excecutables should be copied to debian/tmp/usr/bin. Data files should be copied to debian/tmp/usr/share/PACKAGE_NAME. Documentation should be copied to  debian/tmp/usr/share/doc/PACKAGE_NAME. The folders in debian/tmp are packaged into .deb files by the binary build process so that they are installed to the '/' directory of the users' machines. Like in the dpkg-deb method of packaging, the files in DEBIAN contain package metadata.

As a side note, I'm not sure if it matters whether you use ```
dpkg --build
``` or ```
dpkg-deb --build
``` in your rules file as they appear to do the same thing. However, I have only ever seen ```
dpkg --build
``` in examples so that is what I would use.

---

### Post by hakermania on 2010-10-27
Many thanks about the last answer! I didn't understand very well what you mean when you say root directory. Is the package-name/debian/  ,  package-name/debian/tmp/  or  package-name/debian/tmp/DEBIAN ??

And something else... Do I do exactly the same things with all of the files at the DEBIAN folder? I mean do I create /usr/bin for the executables and /usr/share/man/man1 for the manpages etc and place there the proper files ?
I am asking this because in the package-name/debian/ folder there are the files 'changelog' and 'copyright' that when done a DEB package these files must be placed at /usr/share/doc/package-name/ and the changelog must be compressed as well!

So, What do I do with these? Do I have to create package-name/debian/tmp/DEBIAN/usr/share/doc/package-name/ and place them there or do I copy them via the rules file?


Thx I think I am very close to understand and finally upload my program! :)))))))))

---

### Post by dv3500ea on 2010-10-27
You should treat the ```
package/debian/tmp
``` directory as if it were ```
/
``` on the users' machines. Ignore the DEBIAN folder. This is the only folder that won't be created on the users' machines on installation. It contains meta info about your package. This is generated by the ```
dpkg-gencontrol
``` command in your ```
debian/rules
``` file. Don't put anything else in this folder or you will get errors. 

Your files should actually not exists anywhere in ```
debian/
``` apart from control, rules, changelog etc. They should be somewhere within the the source code directory. For example, you could put your data files in ```
package-VERSION/data
``` and then in your ```
package-VERSION/debian/rules
``` file you would copy them to ```
./debian/tmp/usr/share/package-name
```.

Am I making sense?

---

### Post by hakermania on 2010-10-28
Ok, I'm very close :) Thanks for your patience :$
I've stack a bit to the 'debuild -S' command. After 5 secs of giving output and doing work it outputs:
[B]gpg: skipped "MY-Name <My-email@gmail.com>": secret key not available
gpg: /tmp/debsign.nS23IyH9/wallch_1.0.dsc: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1258:
running debsign failed - aborting...
[/B]I googled it but I didn't find any satisfying answer....

---

### Post by dv3500ea on 2010-10-28
You need to:
[LIST=1]
[*]Set up your name and email for Debian packaging:
[LIST]
[*]Edit your ~/.bashrc file ```
xdg-open ~/.bashrc
```
[*]Enter these lines at the bottom:
```
export DEBFULLNAME='Firstname Surname'
export DEBEMAIL='email@address.com'
```
Obviously you need to substitute your actual name and your actual email address.
[*]Restart your terminal ```
reset
```
[/LIST]
[*]Set up gpg keys (these are used to 'sign' your packages). Use [this guide]("https://help.launchpad.net/YourAccount/ImportingYourPGPKey?highlight=(gpg)"); skip to the section called 'Using GPG to manage OpenPGP keys'.
[/LIST]

---

### Post by hakermania on 2010-10-28
YEAAAAAAAAAAAAAHHHHH
:D:D:D:D
How will I check if this I've created works?
I mean when I built a DEB I double-clicked it to see if it will be installed correctly and then I run the program to see if it does work and I generally performed a lot of checks...
What do I do now to check if it does work?
There are these files created so far:
[B]wallch-1.0/               wallch_1.0.orig.tar.gz     wallch-1.0.tar.gz
wallch_1.0.debian.tar.gz  wallch_1.0_source.build
wallch_1.0.dsc            wallch_1.0_source.changes[/B]

---

### Post by dv3500ea on 2010-10-28
Excellent! :D

You can build a .deb for your architecture by running ```
debuild -b
``` in the same way you ran ```
debuild -S
```.

You can then test that .deb file.

---

### Post by hakermania on 2010-10-28
As *debuild -b* outputs, there seem to be a problem at the command _**dpkg-gencontrol**_  at the rules file...
There's the whole output:
**dpkg-gencontrol: error: must specify package since control info has many ()**

Then I tried _dpkg-gencontrol -c debian/control_ but it didn't work, it outputs unknown option debian/control

The first output talks about a package specification, what does it mean?

---

### Post by hakermania on 2010-10-28
That is my control file if needed:
[B]Source: some-1.0
Section: utils
Priority: optional
Maintainer: Jhon Smith <jhon.smith@gmail.com>
Build-Depends: qtcreator, g++ (>= 4.4)
Homepage: [http://www.isnaybodyhoomeee.com](http://www.isnaybodyhoomeee.com)
Package: some-1.0
Version: 1.0
Architecture: i386
Depends: mpg321, libc6
Description: bla bla bla
[/B]

---

### Post by dv3500ea on 2010-10-28
Try changing the control file to this: ```
Source: some-1.0
Maintainer: Jhon Smith <jhon.smith@gmail.com>
Section: utils
Priority: optional
Build-Depends: qtcreator, g++ (>= 4.4)

Package: some-1.0
Version: 1.0
Architecture: any
Depends: mpg321, libc6
Description: bla blabla??!
 blablabla!!!@
 blomblomblimblam!!!
 blipam!
Homepage: http://www.isnaybodyhoomeee.com

```

Note that the 2 'paragraphs' need an empty line between them. See [http://www.debian.org/doc/debian-policy/ch-controlfields.html]("http://www.debian.org/doc/debian-policy/ch-controlfields.html").

---

### Post by hakermania on 2010-10-28
You are too good to be true (wo)man. Excellent...
Thanks for your patience. I was really lost in this maze. I will definitely make a tutorial on how to do this somewhere on the net, I don't want other neither to go through reading the whole manual which is 123412349178246 pages nor to spend their time asking at foroums. Thank you again.

---

### Post by dv3500ea on 2010-10-28
> **hakermania said:**
> You are too good to be true man. Excellent...
Thanks for your patience. I was really lost in this maze. I will definitely make a tutorial on how to do this somewhere on the net, I don't want other neither to go through reading the whole manual which is 123412349178246 pages nor to spend their time asking at foroums. Thank you again.

No problem :)

I think it is a great idea that you are writing a tutorial. I had a lot of the same problems you had when I was first learning to package. Make sure you post a link on the forums so people can find your tutorial.

good luck.

---

### Post by hakermania on 2010-10-28
I will do so. I am very deep in the philosophy of ubuntu and I feel that if I don't share something I am performing a crime. I'll post a link somewhere around :)

---

### Post by hakermania on 2010-11-06
I found a much easier way to build my Qt App, so, when I finish my program and when I have some free time I'll post the tutorial somewhere around :)

---

### Post by hakermania on 2010-12-11
If someone follow this thread, I made this tutorial over here:
[http://ubuntuforums.org/showthread.php?t=1642956](http://ubuntuforums.org/showthread.php?t=1642956)

---


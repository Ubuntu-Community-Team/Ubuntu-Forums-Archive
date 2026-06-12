---
title: "Launchpad build problems...help?"
date: 2011-08-30
forum: Packaging and Compiling Programs
---

### Post by MG&amp;TL on 2011-08-30
OK, I have managed to upload a PPA to launcpad, and it accepts it.

However, the build (on launchpad) fails.

I have several 

```
cp thisfile thisrestrictedplace 
```

statements in my makefile, and if said makefile keeps them 'as is' then the buildlog says that it does not have permission and stops. BUT if I prefix 'sudo' to the commands, it does not recognize 'sudo' as a command.

What am I doing wrong? Do I need to have a separate 'install' target? Need to use 'su' ?  Mark the makefile as executable/only as root?

Help appreciated (lots!) as this is errrmmm...confusing. To say the least. What OS do the servers run? I know the makefile works, as it runs perfectly on my own machine if I run 

```
sudo make
``` in the directory.

---

### Post by Bachstelze on 2011-08-30
Of course sudo doesn't work on the build machines. Otherwise, what's to keep you from doing sudo rm -rf /* ? ;)

If you need to install some files your Makefile doesn't take care of, use dh_install.

---

### Post by MG&amp;TL on 2011-08-31
OK, so I worked out how to use dh_install, I think. But it don't work. There's no errors when I make, but it doesn't copy anything to anywhere. Here's my makefile:

```
all: Grubby
	cp -R Grubbythemes debian/tmp/
	cp -R lib debian/tmp/
	cp -R src debian/tmp/
	cp Grubby debian/tmp/
	dh_install --list-missing --sourcedir=debian/tmp/
	
Grubby: src/Grubbymain.cxx src/Installtheme.cxx src/Installtheme.h
	g++ -o Grubby src/Grubbymain.cxx src/Installtheme.cxx src/Installtheme.h
```

And here's my Grubby.install file:

```
Grubby /usr/bin/
Grubbythemes /usr/
lib/08_gfxmenu_theme /usr/lib/
src/*.cxx /usr/src/
src/*.h /usr/src/
```

Grubby is the executable, it depends on a file called 08_gfxmenu_theme, there's three source files, and Grubbythemes is some pre-made themes for it, containing images, GRUB fonts, and markup language.

I've also added a dh_install line to my /debian/rules page.

---

### Post by Bachstelze on 2011-08-31
No, you're doing it wrong. You must install them either with the makefile or with dh_install, not both. Make up your mind.

---

### Post by MG&amp;TL on 2011-08-31
OK. Right, sorry, I know I'm asking a lot, but given what I'm doing, could you post an example makefile/dh_install setup and filesystem? If I use makefiles, I get the issue about needing to be root, but if I use dh_install, I get 'exists but was not installed to anywhere' even if I specifically referenced the files.

Thanks for the help so far :) . Why can't it be simple? They'd get a lot more takers...I know programming is not simple, but it would be helpful. :D

---

### Post by Bachstelze on 2011-08-31
Basically, debian/tmp represents the root of the filesystem where the package will be installed. For example, you put your executable into debian/tmp/usr/bin, and when the package will be installed on an actual system, it will be put into /usr/bin.

Also, installation of files should be done with the install rule of your makefile, and you should use install instead of cp, and dh_install should go in your debian/rules, not in your Makefile. Your Makefile should be distro-agnostic. Is this a program you wrote yourself, or did you get the source from somewhere?

---

### Post by MG&amp;TL on 2011-08-31
I wrote it myself. Does all this apply to a project on Launchpad itself, rather an PPA?

So if I don't need to install any extra files I can just have my tree like this?

```
<project>
  <debian>
    <tmp>
      <usr>
        <bin>
          <executable>
        <lib>
          <libraries>
        <src>
          <source code>

```

?

And all I need to put into my makefile is the compilation commands, and the 'copy executable to debian/tmp/usr/bin/' command?

Thanks a lot! This is simpler than the guides make out (although correct me if I'm wrong). Cheers!

---

### Post by Bachstelze on 2011-08-31
> **MG&TL said:**
> I wrote it myself. Does all this apply to a project on Launchpad itself, rather an PPA?

What do you mean by "all this"?

> And all I need to put into my makefile is the compilation commands, and the 'copy executable to debian/tmp/usr/bin/' command?

No. As I said, your Makefile should be OS-agnostic. Not everyone runs Debian! You must clearly separate the program from the Debian packaging. For the install rule, your Makefile should support a DESTDIR variable, like this:

```
install: $(OUTPUT)
        install -o root -m 0755 $< $(DESTDIR)$(BINDIR)

```

And when debhelper will call make install, it will call it with the DESTDIR varaible set to your debian/tmp dirctory (here BINDIR is /usr/bin so that the file will be installed in debian/tmp/usr/bin). Once again, your Makefile is part of your program, not of the DEbian packaging, and therefore should do *nothing* Debian-specific.

---

### Post by MG&amp;TL on 2011-08-31
Oh. thanks for the help. :D If only launchpad had better how-tos. By 'does this apply to launchpad projects too?' I meant will this method work for a bzr repository too (as in, 'add project' on launchpad) ? ;)

Lots of support from this forum, keep it up!

---

### Post by MG&amp;TL on 2011-08-31
That works great...thanks! I'm still waiting to see if it makes it through the launchpad build farm, but it builds on my machine...Great. :)

---

### Post by Bachstelze on 2011-08-31
> **MG&TL said:**
> Oh. thanks for the help. :D If only launchpad had better how-tos. By 'does this apply to launchpad projects too?' I meant will this method work for a bzr repository too (as in, 'add project' on launchpad) ? ;)

I don't know exactly what a bzr repository on Launchpad is for. What I said applies to all Debian packages.

---

### Post by MG&amp;TL on 2011-08-31
There IS a minor problem. Whenever I upload anything to launchpad, it deletes /debian/tmp. As in deletes, not recycles. Then the build fails because needed files aren't there. Is there a reason for it to do this? Luckily, I had a backup, but why did it do this? And how do I stop it?

---

### Post by MG&amp;TL on 2011-08-31
Correction: it removes the files when I run debuild.

---

### Post by Bachstelze on 2011-08-31
What do you mean by "upload to launchpad"? How do you run debuild?

---

### Post by MG&amp;TL on 2011-08-31
I've run dh_make at some point in the past to generate files. I then edited them as necessary.

Then, in the directory with debian and the makefile in it, I run:

```
debuild -S
```

then (up one directory)

```
dput ppa:<my id>/grubby grubbyXXXX~0ubuntu1_source.changes
```

But it removes debian/tmp when I run debuild. Currently I'm trying replacing tmp with a carbon copy as soon as debuild has finished, then running dput. I'll keep you posted.

---

### Post by Bachstelze on 2011-08-31
It's normal that it removes debian/tmp. As its name implies, it is temporary.

---

### Post by MG&amp;TL on 2011-08-31
...but launchpad still says it hasn't got debian/tmp. Here's the important bit of the buildlog:

```
dpkg-buildpackage: source package grubby
dpkg-buildpackage: source version 1.0.5~0ubuntu1
dpkg-buildpackage: host architecture i386
 /usr/bin/fakeroot debian/rules clean
dh  clean
   dh_testdir
   dh_auto_clean
   dh_clean
dh_install
 debian/rules build
dh  build
   dh_testdir
   dh_auto_configure
   dh_auto_build
make[1]: Entering directory `/build/buildd/grubby-1.0.5~0ubuntu1'
make[1]: *** No rule to make target `debian/tmp/src/Grubbymain.cxx', needed by `Grubby'.  Stop.
make[1]: Leaving directory `/build/buildd/grubby-1.0.5~0ubuntu1'
dh_auto_build: make -j1 returned exit code 2
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
******************************************************************************
```

...sorry, I'm clueless. And a noob.

Yes, okay, so where do I put stuff so it doesn't get deleted when it builds?

---

### Post by Bachstelze on 2011-08-31
Why do you need a rule named `debian/tmp/src/Grubbymain.cxx'? Post your makefile.

---

### Post by MG&amp;TL on 2011-08-31
```
install: Grubby
	install -o root -m 744 $< $(DESTDIR) /usr/bin
	
Grubby: debian/tmp/src/Grubbymain.cxx debian/tmp/src/Installtheme.cxx debian/tmp/src/Installtheme.h
	g++ -o Grubby debian/tmp/src/Grubbymain.cxx debian/tmp/src/Installtheme.cxx debian/tmp/src/Installtheme.h
	
	
```

? Should I put the code and stuff somewhere else then?

I currently have three source files required for basic operation. Grubbymain.cxx Installtheme.cxx Installtheme.h. There is more, but I though I'd get the package uploaded first. I've spent five times as long on the packaging as the code...:D

---

### Post by Bachstelze on 2011-08-31
What did I tell you? Your makefile should do nothing Debian specific. debian/tmp must not appear in it. Remove all of them.

And you have an unwanted space in your install rule, it should be

```
install: Grubby
	install -o root -m 744 $< $(DESTDIR)/usr/bin
```

Also why install it with mode 744? Then no one will be able to run it.

---

### Post by MG&amp;TL on 2011-08-31
Right. So how do I build the executable? From another folder, then copy the executable to tmp? And where do I place the copy commands?

Sorry I'm being so slow, this packaging thing doesn't seem to click with me.
I've read the Ubuntu packaging guide, the launchpad how-tos, endless Internet trawls. I just don't get it. I can package a .deb fine. Just not one that adheres to Ubuntu's packaging policy.

---

### Post by Bachstelze on 2011-08-31
> **MG&TL said:**
> Right. So how do I build the executable? From another folder, then copy the executable to tmp?

Yes, you do the build normally, like you would if you just unpacked the tarball and built it. Then you move the things you want your package to install into debian/tmp, you don't do the build there.

> And where do I place the copy commands?

In your install rule, or in a .install file.

---

### Post by MG&amp;TL on 2011-08-31
Okay, thanks, I've got my head around pbuilder now, so I souldn't have to wait so long between builds.

---

### Post by MG&amp;TL on 2011-08-31
Why chmod 744? Guy here:

[http://ubuntuforums.org/showthread.php?t=1826022]("http://ubuntuforums.org/showthread.php?t=1826022")

told me to. Third post down. And, tbh, never had a problem. I need my program only to be run as sudo, else the bash scripts on which it depends complain. :confused:

Anyway, running in a pbuilder environment, I get:

```
install -o root -m 744 Grubby  /usr/bin
install: cannot create regular file `/usr/bin/Grubby': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/tmp/buildd/grubby-1.0.5~0ubuntu1'
dh_auto_build: make -j1 returned exit code 2
make: *** [build] Error 2

```

Do I need to put 'sudo' or something in the install file, or mark is as root or something? Or am I being dumb again?

---

### Post by Bachstelze on 2011-08-31
It's trying to install it into /usr/bin. It should not... Have you changed something else in your makefile?

*EDIT:* FYI, [here](http://svn.fkraiem.org/filedetails.php?repname=kanamemo&path=%2FMakefile)'s a basic makefile that works for a Debian package.

---

### Post by MG&amp;TL on 2011-08-31
Nope. Other than what you told me to, anyway. Surely it should be installing to /usr/bin? I told it to, in the install file. I want it so that it can run from command-line directly, rather than running from a long list of cd/.../.../ ./Grubby.

Where should it install?

Thanks for the patience. I must be VERY annoying?

---

### Post by Bachstelze on 2011-08-31
No, it should be installing to $(DESTDIR)/usr/bin, which in Debian is debian/tmp/usr/bin. Remember what I said earlier about debian/tmp representing the root of the filesystem where the package will be ultimately installed. See the makefie above.

---

### Post by MG&amp;TL on 2011-08-31
So...in my case...?

install file:

```
install -o root -m 744/55 ../Grubby $(DESTDIR)/usr/bin/
install --directory ../Grubbythemes $(DESTDIR)/usr/
install ../lib/08_gfxmenu_theme /usr/lib/
```

Yes? (I sense I am almost there?) :D

---

### Post by Bachstelze on 2011-08-31
You forgot DESTDIR on your last line. ;) But that should be it, yes.

---

### Post by MG&amp;TL on 2011-08-31
Well, it built in pbuilder, so it should run on the Launchpad build farm. Really, thanks a lot for all the packaging noob help you've given me, and (should it build on launchpad) I will mark the thread very satisfactorily solved...this is why I choose Ubuntu. I guess subsequent packaging attempts will be somewhat more streamlined. :)

---

### Post by SevenMachines on 2011-08-31
Hi, is this you?
[https://launchpad.net/~michaelrawson76/+archive/grubby/+packages]("https://launchpad.net/%7Emichaelrawson76/+archive/grubby/+packages")

In which case you'll notice,
```
$ debuild -b -us -uc
$ dpkg --contents ../grubby_1.0.6~0ubuntu1_all.deb 
drwxr-xr-x root/root         0 2011-08-31 21:48 ./
drwxr-xr-x root/root         0 2011-08-31 21:48 ./usr/
drwxr-xr-x root/root         0 2011-08-31 21:48 ./usr/share/
drwxr-xr-x root/root         0 2011-08-31 21:48 ./usr/share/doc/
drwxr-xr-x root/root         0 2011-08-31 21:48 ./usr/share/doc/grubby/
-rw-r--r-- root/root       922 2011-08-22 17:22 ./usr/share/doc/grubby/copyright
-rw-r--r-- root/root       166 2011-08-31 20:54 ./usr/share/doc/grubby/changelog.gz
```
(1) debian/Grubby.install is never used by the debhelper install calls in debian/rules. .install files are matched to the entry in the control file, and are case sensitive, so you need this file to be grubby.install

(2) install files dont use install commands, they're source/destination orders to debhelper. This for example

debian/grubby.install
```
Grubby /usr/bin/
Grubbythemes /usr/
lib/08_gfxmenu_theme /usr/lib/

```With that instead you should get something like
```
$ debuild -b -us -uc
$ dpkg --contents ../grubby_1.0.6~0ubuntu1_all.deb 
drwxr-xr-x root/root         0 2011-08-31 21:42 ./
drwxr-xr-x root/root         0 2011-08-31 21:42 ./usr/
drwxr-xr-x root/root         0 2011-08-31 21:42 ./usr/bin/
-rwxr-xr-x root/root      6224 2011-08-31 21:42 ./usr/bin/Grubby
drwxr-xr-x root/root         0 2011-08-31 21:42 ./usr/lib/
-rwxr-xr-x root/root      1151 2011-08-31 12:16 ./usr/lib/08_gfxmenu_theme
drwxr-xr-x root/root         0 2011-08-31 21:42 ./usr/share/
drwxr-xr-x root/root         0 2011-08-31 21:42 ./usr/share/doc/
drwxr-xr-x root/root         0 2011-08-31 21:42 ./usr/share/doc/grubby/
-rw-r--r-- root/root       922 2011-08-22 17:22 ./usr/share/doc/grubby/copyright
-rw-r--r-- root/root       166 2011-08-31 20:54 ./usr/share/doc/grubby/changelog.gz
drwxr-xr-x root/root         0 2011-08-31 12:10 ./usr/Grubbythemes/
drwxr-xr-x root/root         0 2011-08-31 12:10 ./usr/Grubbythemes/Ubuntu/
-rw-r--r-- root/root      3206 2011-08-31 12:16 ./usr/Grubbythemes/Ubuntu/dejavu-sans-10.pf2
-rw-r--r-- root/root    100153 2011-08-31 12:16 ./usr/Grubbythemes/Ubuntu/7x13.pf2
-rw-r--r-- root/root   2560080 2011-08-31 12:16 ./usr/Grubbythemes/Ubuntu/unicode.pf2
-rw-r--r-- root/root   3151760 2011-08-31 12:16 ./usr/Grubbythemes/Ubuntu/Desktop.png
-rw-r--r-- root/root       524 2011-08-31 12:16 ./usr/Grubbythemes/Ubuntu/theme.txt
-rw-r--r-- root/root      3792 2011-08-31 12:16 ./usr/Grubbythemes/Ubuntu/dejavu-sans-bold-14.pf2
-rw-r--r-- root/root      3471 2011-08-31 12:16 ./usr/Grubbythemes/Ubuntu/dejavu-sans-12.pf2
-rw-r--r-- root/root      1285 2011-08-31 12:16 ./usr/Grubbythemes/Ubuntu/grub
-rwxr-xr-x root/root       753 2011-08-31 12:16 ./usr/Grubbythemes/Ubuntu/Ubuntu.sh
drwxr-xr-x root/root         0 2011-08-31 12:10 ./usr/Grubbythemes/Fonts/
-rw-r--r-- root/root      3206 2011-08-31 12:16 ./usr/Grubbythemes/Fonts/dejavu-sans-10.pf2
-rw-r--r-- root/root    100153 2011-08-31 12:16 ./usr/Grubbythemes/Fonts/7x13.pf2
-rw-r--r-- root/root   2560080 2011-08-31 12:16 ./usr/Grubbythemes/Fonts/unicode.pf2
-rw-r--r-- root/root      3792 2011-08-31 12:16 ./usr/Grubbythemes/Fonts/dejavu-sans-bold-14.pf2
-rw-r--r-- root/root      3471 2011-08-31 12:16 ./usr/Grubbythemes/Fonts/dejavu-sans-12.pf2
drwxr-xr-x root/root         0 2011-08-31 12:10 ./usr/Grubbythemes/Default/
-rw-r--r-- root/root      3206 2011-08-31 12:16 ./usr/Grubbythemes/Default/dejavu-sans-10.pf2
-rw-r--r-- root/root    100153 2011-08-31 12:16 ./usr/Grubbythemes/Default/7x13.pf2
-rw-r--r-- root/root   2560080 2011-08-31 12:16 ./usr/Grubbythemes/Default/unicode.pf2
-rw-r--r-- root/root       495 2011-08-31 12:16 ./usr/Grubbythemes/Default/theme.txt
-rw-r--r-- root/root      3792 2011-08-31 12:16 ./usr/Grubbythemes/Default/dejavu-sans-bold-14.pf2
-rw-r--r-- root/root      3471 2011-08-31 12:16 ./usr/Grubbythemes/Default/dejavu-sans-12.pf2
-rw-r--r-- root/root      1286 2011-08-31 12:16 ./usr/Grubbythemes/Default/grub
-rwxr-xr-x root/root       798 2011-08-31 12:16 ./usr/Grubbythemes/Default/Default.sh

```I need to point out that there are still a lot of problems here, the installation directories are not right, /usr/share/grubby i'd imagine for the themes and the 'lib', lower case the files/directories, and a bunch of other things that lintian will tell you about when you build. But, if you change the install file you will get a package with all your files in you can move on from there

---

### Post by SevenMachines on 2011-08-31
Just to add, if the Makefile of your source tree had an install: rule, then debian/grubby.install wouldn't be needed, debhelper would use that rule to populate the fake root debian/grubby directory. Just that I notice thats been mentioned over the thread, the .install will work, but since the debian packaging and the source code would properly be completely separate, it would be better if your build system was also capable of install, probably clean and uninstall too :)

---

### Post by MG&amp;TL on 2011-09-01
So remove the install file, (and dh_install from the rules file?) then this in the makefile (along with compilation)?

```
install: Grubbythemes, Grubby, lib/08_gfxmenu
       install -o root -m 744/55 ../Grubby $(DESTDIR)/usr/bin/
       install --directory ../Grubbythemes $(DESTDIR)/usr/
       install ../lib/08_gfxmenu_theme /usr/lib/
clean: all 
       rm -r../grubby1.0.6
remove: all
       rm -f /usr/bin/Grubby
       rm -f -r /usr/Grubbythemes
       rm -f /usr/lib/08_gfxmenu 
```

Thanks for the catch, 7machines. I can't pretend I was overjoyed to see this first thing in the morn, when I thought I'd I'd cracked it, but thank you all the same...:P

---

### Post by SevenMachines on 2011-09-01
Hi, I'd just change the grubby.install file and leave the Makefile as it was for the moment, it'll give you a working package, albeit one that you'd need to work on to tidy up with directories and so on as mentioned. 
Before tackling a more complete makefile, you might want to look through a few tutorials and examples of makefiles and other build systems and then have another look at fixing up your source, its a bit of a tricky topic at times. 

I'd also recommend when building a package,

(1)Test the build locally
$ debuild -b -us -uc 
See if the build is successful, look at the lintian warnings, check the contents of the package with dpkg --contents 

(2) Test the build with pbuilder, pbuilder-dist-simple is the easiest.

(3) Upload to launchpad, if pbuilder is successful then launchpad should be too

---

### Post by Paddy Landau on 2011-09-01
> **MG&TL said:**
> I need my program only to be run as sudo, else the bash scripts on which it depends complain.
May I suggest that instead of relying on chmod, you create the script so that it runs from a normal user? It would work as follows, which would also match Ubuntu's safety standards:
```
[COLOR=DimGray][I]        :        :
    lines of code that don't need sudo ...[/I]
*        :        :*

[COLOR=Navy]# Register the password with sudo:[/COLOR][/COLOR]
gksudo --message 'System changes required. Type your password, or press Cancel.' -- [ 1 ]
if [[ ${?} != 0 ]]
then
        exit 3[COLOR=Navy]   # User asked to cancel or user not an administrator.[/COLOR]
fi

gksudo *command that*[I] needs sudo
[/I][I]
[COLOR=DimGray]       :        :[/COLOR][/I][COLOR=DimGray]
[/COLOR] [COLOR=DimGray][I]    etc. ...
[/I]*       :        :*[/COLOR]
```

---

### Post by MG&amp;TL on 2011-09-01
Oh right. OK. That's going in the code now. :D

So...does it matter if I have wiped the install file, and put the stuff I posted in the makefile? I have read multiple tutorials, most of them used it as shortcuts to compile big projects. :confused:

I'm just fixing stuff at the moment like changelogs, and spaces, not [TAB] in the makefile...

---

### Post by Bachstelze on 2011-09-01
> **MG&TL said:**
> 
So...does it matter if I have wiped the install file, and put the stuff I posted in the makefile?:


Both are acceptable. In general, since you package programs someone else has written, you use the install file to install stuff the Makefile doesn't take care of, because modifying the Makefile is not alway possible, and almost always a bad idea even when it is possible. But here since you write both the program and the Debian packaging, you can adapt your Makefile.

---

### Post by MG&amp;TL on 2011-09-01
Can I be really cheeky, a cheat, coward and lots of other bad things, and email a lucky volunteer who's done it before to package it for me, and send it back? That way, I get the idea of what I am supposed to do, and also I get my package? Really sorry to ask, but I've beating my head for three weeks now. From then on, I can package my own stuff.

Cowardly, spineless teenager that I am.

?

Oh yeah, and if said volunteer wants any menial tasks doing....

---


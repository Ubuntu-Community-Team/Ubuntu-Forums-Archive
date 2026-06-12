---
title: "Help packing DEB - missing something"
date: 2009-12-04
forum: Packaging and Compiling Programs
---

### Post by beli0135 on 2009-12-04
Hi

I have made small program in qt4, made DEB package and it installs alright (used tutorial from Debian site), but after installation I didn't create menu item neither I can run it from atl+f2.
In Synaptic, I see program installed. 

I am missing something, but I do not know what. Debian tutorial doesn't mention it. 
Program works, its already in openSUSE and Fedora repositories. I am used to spec files for rpm, but totally new to DEB
(btw, I am using Mint KDE4 at work computer).

Thank you.
Emil Beli

---

### Post by Brandon Williams on 2009-12-04
What do you see if you run 'dpkg --contents <packagename>.deb'? Does it list all of the files you expect will be installed? Of the files being installed, do they all have the right ownership and permissions?

Based on your description of the problem, I'm guessing that either files are not being installed or they're being installed with the wrong ownership/permissions. You'll have to provide more information to get a better response.

[Here](http://ubuntuforums.org/showthread.php?t=910717) is a simple tutorial that shows how to build a simple deb. Maybe this one will work better for you than the one you tried first.

---

### Post by beli0135 on 2009-12-05
I cant tell you now, I am at home, (opensuse). When I go to work, I will check out.
However, debian's tutorial was far more complicated, but I will try simple way.
I just dont understand why should I copy files to /bin (as tutorial says).

No, there is no permission problem, program installs, it has execution permissions, there is no link to it anywhere.

---

### Post by alfplayer on 2009-12-05
To create a menu item a .desktop file must be installed.

---

### Post by andrewsomething on 2009-12-06
> **beli0135 said:**
> I cant tell you now, I am at home, (opensuse). When I go to work, I will check out.
However, debian's tutorial was far more complicated, but I will try simple way.
I just dont understand why should I copy files to /bin (as tutorial says)

I wouldn't recommend following that tutorial. It is basically showing you a hack to drop a file somewhere into the user's PATH using a deb. It might be helpful for distributing a random script, but it's not a proper package.

It's hard to help you with out some more details. Does the program have it's own build system? Is the program or packaging hosted anywhere accessible so we can see exactly what it going on? 

alfplayer is correct about the desktop file. In order of a program to show up ion the menus you must install one to /usr/share/applications See: [http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/) But that isn't anything Debian/Ubuntu specifc; it's a Freedesktop Spec.

As mentioned above, running 'dpkg --contents <packagename>.deb' (or just 'dpkg -L <packagename>' if the package is installed) will show what files are actually being installed. Just because the package is installed doesn't mean that all the files are, if the package was made incorrectly.

It's unclear to me if the package is working at all or just not showing up in the menu. Can you call it from the command line?

---

### Post by beli0135 on 2009-12-07
I really don't know what is happening. I managed to build it, before, I do have .desktop file, it installed but I couldn't run the application.

Now, it complains that control file is not in order. Wonder how did he managed to build it last time..

If anyone wishes to help me, source code is  here:
[http://www.beli.ws/storage/baires-1.0_1.tar.gz](http://www.beli.ws/storage/baires-1.0_1.tar.gz)

thank you

---

### Post by SevenMachines on 2009-12-07
a few things about the package source in your last post.
* DEBIAN/ should be named debian/
* in debian/control there should be an empty line before the Package: baires line
* the source shouldnt include any pre-built binaries, see ./baires and bin/local/bin/baires
* in debian/rules you are calling make install but your makefile (here it ends up calling Makefile.debug) doesnt actually do anything on install. you need to write something to actually install your binaries and whatever else to a location (probably using ${DESTDIR} as a base ). thats why no binary is installed into your package

---

### Post by beli0135 on 2009-12-08
> **SevenMachines said:**
> a few things about the package source in your last post.
* DEBIAN/ should be named debian/
* in debian/control there should be an empty line before the Package: baires line
* the source shouldnt include any pre-built binaries, see ./baires and bin/local/bin/baires
* in debian/rules you are calling make install but your makefile (here it ends up calling Makefile.debug) doesnt actually do anything on install. you need to write something to actually install your binaries and whatever else to a location (probably using ${DESTDIR} as a base ). thats why no binary is installed into your package

Well, how to write makefile? What do I need?
In baires.spec, which is for making RPM on openSUSE and Fedora, makefile is not necessary. Never-ever did a debian package...  :(

---

### Post by SevenMachines on 2009-12-08
sorry,i dont know much about qmake which is what the project uses. 
you could though build a package by running dh_install in the binary-arch rule in debian/rules. 
Then create a debian/baires.install file with files you want to install and places to install them to, i.e.
baires    usr/bin/
baires.desktop     usr/share/applications/

---

### Post by beli0135 on 2009-12-09
Well, this I did 1st time, and it did create DEB, but didnt install item in menu, neither could I run it.

:(

---

### Post by SevenMachines on 2009-12-09
i quickly did exactly as i described before i posted the suggestion and it ran fine and showed up in the menu. if you try it and it doesnt work you'll need to post the actual packaging you're using that is failing to find out whats going wrong

---

### Post by beli0135 on 2009-12-11
What exactly you did? I got lost (in "above");

---

### Post by SevenMachines on 2009-12-14
> **beli0135 said:**
> What exactly you did? I got lost (in "above");

from the tarball you sent in comment #6
1. rename DEBIAN directory as debian
2. edit debian/control and insert a newline before Package: baires
3. edit debian/rules and uncomment dh_install in the binary-arch: install rule
4. create a file debian/baires.install with the lines,
baires usr/bin
baires.desktop usr/share/applications

if you build that you'll see baires goes to /bin and the menu entry should automatically appear

---

### Post by beli0135 on 2009-12-28
It build OK, but still didn't put Baires in menu.

---


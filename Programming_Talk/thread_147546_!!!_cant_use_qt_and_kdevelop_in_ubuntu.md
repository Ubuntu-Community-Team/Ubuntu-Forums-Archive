---
title: "!!! cant use qt and kdevelop in ubuntu"
date: 2006-03-20
forum: Programming Talk
---

### Post by sharperguy on 2006-03-20
I found out i need kdelibs-dev but:

sharp@xxxxx:~$ sudo apt-get install kdelibs-dev
Reading package lists... Done
Building dependency tree... Done
Package kdelibs-dev is a virtual package provided by:
  kdelibs4-dev 4:3.4.3-0ubuntu2
You should explicitly select one to install.
E: Package kdelibs-dev has no installation candidate
sharp@ali2600:~$ sudo apt-get install kdelibs4-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdelibs4-dev: Depends: kdelibs4c2 (= 4:3.4.3-0ubuntu2) but 4:3.5.1-0ubuntu0bre ezy1 is to be installed
                Depends: kdelibs-bin (= 4:3.4.3-0ubuntu2) but 4:3.5.1-0ubuntu0br eezy1 is to be installed
                Depends: libarts1-dev (>= 1.4.0) but it is not going to be insta lled
E: Broken packages


not sure if i needed to cat all that but it might help.

I need this to live!!!! Ok not quite but it looks easyer than using ajunta+gtkmm+glademm

---

### Post by sharperguy on 2006-03-21
btw its getting boring having noone reply to any of my topics recently although loads of people are relplying to all the other topics withing minuates and mine end up scrolling off the page.

---

### Post by Adrian on 2006-03-21
[QUOTE=sharperguy]btw its getting boring having noone reply to any of my topics recently although loads of people are relplying to all the other topics withing minuates and mine end up scrolling off the page.[/QUOTE]

Well, I saw your post, but I couldn't figure out any good solution, so I thought that I'd better let someone else answer.

Obviously the KDE 3.5.1 repository and the KDE 3.4.3 repository don't go very well together in this case. My guess is that you'll probably need to uninstall certain components and then try again.

But what components? Well, I don't know and that's why I didn't answer :)

---

### Post by sharperguy on 2006-03-21
sorry about the last psot, i was a bit depressed

neway i got kdelibs4-dev installed. By reinstalling kubuntu-dekstop no less than 3 times! (Havnt got round to putting ubuntu-desktop back on even though it was there originaly)

Neway its strange because although the configure detects the headers, gcc wont so i get: /home/sharp/Projects/test/src/test.h:10:25: error: kmainwindow.h: No such file or directory


and a whole pile of other stuff resulting from this.

Strange, but more likely that someone can help (i hope).

---

### Post by njf on 2006-03-21
I think if u pass the flags output by "pkg-config --cflags qt-mt" when compiling, and "pkg-config --libs qt-mt" when linking, it will work fine.

---

### Post by sharperguy on 2006-03-22
how exactly do i tell kdevelop do do this then?

---

### Post by njf on 2006-03-22
Sorry my bad, "kmainwindow.h" is a KDE header. 
Go to  menu "Project" > "Project Options". Under "Configure Options" on the left, go to "C++" tab on the right. Add the flag "*-I/usr/include/kde*" in the "Compiler flags" field. I think that should work.
Anyway, if u create a KDE project it should work out of the box.

---

### Post by sharperguy on 2006-03-22
it seems to work now

cheers

---


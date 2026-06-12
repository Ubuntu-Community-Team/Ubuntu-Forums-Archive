---
title: "How to develop app in Linux?"
date: 2020-05-21
forum: New to Ubuntu
---

### Post by chrisnk on 2020-05-21
Hi!
I'm migrating to Linux-Ubuntu/Lubuntu and I develop apps under Visual .NET in Windows. vISUAL bASIC, c/c++...

Now I wish to try how it is in Linux.
Can you pls give me a turn sign what IDE is similar to Visual Studio to develop C++ apps in Linux?
What should I download lets say to open and develop forder an app from github which is programmed in C++ but for linux?

Thank you.

---

### Post by grahammechanical on 2020-05-21
Are you aware that there is Visual Studio for Linux? The Ubuntu 18.04 app store has two versions. Visual Studio Code & Visual Studio Insiders. I do not know what is different between them. Both are snap packages but unlike the usual snaps they are unconfined. They will have access to everywhere on the OS.

There is also a deb packaged version if you want that but you will have to download it from the Microsoft web site. The snap versions can be installed through the Ubuntu app store.

[https://code.visualstudio.com/docs/setup/linux](https://code.visualstudio.com/docs/setup/linux)

As for programing for Linux I cannot help there.

Regards

---

### Post by chrisnk on 2020-05-21
Hi!
Thank you for your replay and time spent  to help me.

I wish to have an app similar to ms visual studio to develop under linux. Programming is not a problem for me but to find a suitable linux development editor for me is a bit problematic for me.

Lets say I get a free source code from github of an app and I wish to make some mod and tweak which is written i cpp.
The app is lets say with a GUI.
How would I do that in ubuntu 18.04?

Thank you.

---

### Post by TheFu on 2020-05-21
Most long-time Unix developers use the OS as the IDE, not some program.  It is a different way of working for someone used to MSFT stuff.  [https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/](https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/) explains.
I've been developing that way since the early 1990s.  It is language agnostic. My workflow for C++ or Perl is basically the same. Just the compile step isn't needed.  I use gmake to build. This is pretty common, but so are other methods. Larger projects would probably use something like autoconf.  cmake is popular too and what the new kids use, I hear.

There are multiple choices for GUI toolkits.  You get to pick the one that meets your needs. Be certain to read the licenses and understand them. Some have hidden restrictions.  Qt and GTK+ are the most popular and allow code to run on OSX and Windows if written in a cross-platform way.  In the 1990s, I was a cross-platform developer - we supported 12 platforms from the same codebase. Back then, Qt and GTK didn't exist. Be paid huge prices for the tools. This was before Java and Java was ... cough ... is ...  really slow.

Of course, you can program without a toolkit too, using straight X11 calls.  I took a 2-week class in X/Windows programming. Still have all the books, but the manpages cover all the functions. manpages are the normal C references on Unix.  **man -s 3 printf** for example. Programming APIs are in man section 3.

Every project chooses the libraries they use, so you'll need those dependencies on your system as well. There isn't 1 answer. There are 100,000 answers, depending on the project.  Unix is very open, full of options.

KDE uses the Qt toolkit, so most KDE applications choose Qt too.
Gnome3 uses GTK+ toolkit.  Different programs will often pick one or the other of those. I tend to avoid any Qt programs to avoid having 500MB-1G of RAM used just for another toolkit in RAM. It really isn't that bad, since much will not be loaded until requested.  

I also avoid all mono based applications. That's more political.

.dlls and .so are similar, but different.  With DLLs, we can share data between different programs, if we like.  .so files don't do that. Each program has protected memory and a .DS for each .so.  Unix has shared memory instead and a few other IPC methods.  Multi-threaded programming is very similar, only with very slight differences. I don't recall all the diffs, but it wasn't hard to handle.  Windows uses threads much more often than Unix does, mainly because Windows processes are heavy, while Unix processes are light.  The different philosophies can really be seen when doing systems programming.

If VS is a snap package, be aware there are certain limitations for accessing files outside the HOME directory. That's an issue for all snaps.

Please don't confuse "free code" with "code you can do anything you want".  Most code has a license that must be followed.  Developers need to be aware of the licenses for each library they use to ensure a violation doesn't ruin the ability for that code to be used in the intended way.  This is especially important for any code used by a business or for profit.

---

### Post by chrisnk on 2020-05-22
Ok. Thank you for this valuable writing. I really appreciate it.

So, it went a bit over my head now here in Ubuntu/Linux world... :-)

Can somebody give me a list of what to install on Ubuntu to have the ability to write apps in c++ with gui?
No command line app.

In MS VS under windows when I install VS I have forms, buttons, text boxes etc... here I'm lost . . . :-)

I hope you got what I mean.
Thank you.

---

### Post by dino99 on 2020-05-22
install 'synaptic' + 'apt-xapian-index' to know about the descriptions/dependencies/analogs search ):P

---

### Post by TheFu on 2020-05-22
You want to use something like this? [https://www.qt.io/product](https://www.qt.io/product) 
There are liabilities in doing it that way.

if you want an ubuntu-specific way: [https://ubuntu.com/desktop/developers](https://ubuntu.com/desktop/developers)
[https://ubuntuforums.org/forumdisplay.php?f=310](https://ubuntuforums.org/forumdisplay.php?f=310)

As a dev, you must learn to use and love the shell.  That's how most Unix development is done.  it is just too powerful in comparison to point-n-click methods.

---

### Post by grahammechanical on 2020-05-22
You asked a simple question but as you can see with Linux a simple answer is a rare thing. Freedom in Linux is the freedom to do things differently. And there is plenty of that kind of freedom.

The software you write will have to be packaged. Converted (if that is the right expression) so that it will run on a specific Linux distribution. Redhat is a company that produces the Redhat Enterprise Linux distribution. There are other distributions that are based in some way upon Redhat. An application will need to be packaged in the Redhat rpm format to run on those distributions.

Another long standing Linux Distribution is Debian. It has its own package format called deb. Ubuntu is built upon Debian and so we cannot run an application packaged as an rpm but only as a deb. The same is true of the distributions built upon Ubuntu.

As far as I can tell there are three projects that have the basic aim of producing a package format that is distribution neutral. Can be run on any Linux distribution. They are Appstream, Flatpack & Snap

Snap

[https://snapcraft.io/](https://snapcraft.io/)

Flatpack

[https://flatpak.org/](https://flatpak.org/)

Appstream

[URL="https://www.freedesktop.org/wiki/Distributions/AppStream/"]https://www.freedesktop.org/wiki/Distributions/AppStream/
[/URL]
I know that Snap is being promoted by Ubuntu. In fact the software to run snap applications is installed by default on recent versions of Ubuntu. Users of distributions not based on Ubuntu will have to install some software in order to run a snap application.

As I understand it Flatpack is being developed by Redhat. Certainly the main developer is a Redhat employee. We can run Flatpack applications on Ubuntu provided we install some software.

[https://flatpak.org/setup/Ubuntu/](https://flatpak.org/setup/Ubuntu/)

I think that it is likely that these package formats will prove to be the future of Linux application distribution. Most likely co-existing. So, a developer would need to package his applications in more than one package format and put it in more than one app store. Everything changes and yet nothing changes.

Regards




[URL="https://www.freedesktop.org/wiki/Distributions/AppStream/"]


[/URL]

---


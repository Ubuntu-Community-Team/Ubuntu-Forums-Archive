---
title: "Python Program Packaging / LaunchPad"
date: 2011-07-15
forum: Packaging and Compiling Programs
---

### Post by arm-c on 2011-07-15
First, up front, I know this is going to sound quite stupid with the questions I am going to ask.  With that said, I also want to say that I have spent hours and hours googling and reading and really cannot make heads/tails of where to start and what to do.  I really would appreciate some assistance on that, so I have resorted to posting here in hopes that a kind, patient, and understanding mentor/assistant will help me through the process.

Background:  I have written a couple of programs in python.  They consist of python code, some scripts, and misc other files such as icons, etc...  I have also created .deb files for them using the following:
```
sudo dpkg -b /path/to/project/directory/ project_0.0_all.deb
```My development structure was to recreate the directory tree as I wrote the program, so all files are in a directory that corresponds to its location when installed.  EX:

```
~/project/
  +DEBIAN/
  |   + <debian files>
  +usr/
    +bin/
    |  +file.py
    +share/
       +applications/
       |   +launcher.desktop
       +myproject/
       |   +data/
       |   |   + <data files>
       |   + <supporting files such as glade, etc>
       +icons/
```Now, I do not know what I have to do to get this into launchpad.  It asks for sourcecode, but my sourcecode is my project tree and what is placed in the .deb

QUESTIONS:

a.  Do I need to do anything special to upload this to launchpad or do I just need to tar up the directory and treat that as source?

b.  Do I have to write a setup.py and misclaneous files to accompany this?  In most examples, it appears that all the files are lumped together and the setup.py / MANIFEST.in / etc... gives instructions on distributing the files across the system file tree... which means I have developed all wrong and will have to hack to pieces what I did without being sure that is what I need to do.

OBJECTIVE:
1.  Have a working launchpad PPA to distribute the programs through.
2.  Have my project build into .deb and install/run correctly.

My projects are and where you can get/look at the .debs I have made are located here:

AcerHK GUI:  [http://sourceforge.net/projects/acerhkgui/](http://sourceforge.net/projects/acerhkgui/)

DisPlex:  [http://sourceforge.net/p/displex/home/Home/](http://sourceforge.net/p/displex/home/Home/)

My priority is on DisPlex.  Once I do it once, doing it a second time should be on my own.

I sincerely hope there is someone who will help guide me along on this.

v/r
ARM-C

---

### Post by SevenMachines on 2011-07-16
Much as i hate to quote myself! Have a look at 
[http://ubuntuforums.org/showpost.php?p=11050093&postcount=37](http://ubuntuforums.org/showpost.php?p=11050093&postcount=37)

In short, what you have is a deb archive, to upload to a ppa this isnt useful, you need to properly package up your source. 
For examples you can look at the stickies in this forum
Theres a python walk through example that will explain most of your questions hopefully,
[https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python)

If you follow through that example then hopefully your code will look easy to package to you

---

### Post by arm-c on 2011-07-16
Seven Machines,

Thanks for the pointing.  I believe that I have been able to determine based on a section at the bottom of the wiki post that I do not have to mess around with the setup.py if I don't want to.  Depending on time, I may give that a shot, but am leaning toward the <package>.install format for handling files.

I also appreciate the information about the difference between a .deb archive and a .deb debianized package.

Thanks for your reply.

v/r
ARM-C

---


---
title: "Archive Manager; what's the point?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-10
all I know is sometimes I download things amd everything falls into place.  Then other times it gets swallowed up by this Archive manager and I never get the package to "work."  It's just a bunch of folders and stuff.  I would like to become clear with this because I'm sure there is a guiding principle behind the AM for it to always be complicating things.

---

### Post by estyles on 2008-07-10
Based on your question, I'm going to assume you're a complete newbie (and I'm only a couple steps beyond that myself), and answer accordinly.  If that's a bad assumption and you think I'm talking "down" to you, then I apologize.

Does this happen when you download .tar .gz or .tar.gz files?  If so, that file is an archive, like a .zip file in Windows.  Archive Manager is like Winzip - without it (or some other tool) you'd be unable to view the files in that archive at all.  What you want to do is extract those files to a directory under your home directory, then follow any install instructions.

Most likely, you're downloading something that has to be compiled, and in most cases, I would advise against it.  Unless you know what you're doing and/or there's no other way to install the program you're downloading, you're going to have problems.  (If on the other hand, you're just downloading an archive of documents or pictures or something, go ahead - it shouldn't be a big deal.)

If you're downloading a program, check the repositories (using Synaptic) to see if the program (or something that can do a similar job) is available there.  The Synaptic package manager really simplifies installing and managing programs.

---

### Post by ajgreeny on 2008-07-10
I'm not quite sure what your point is, but I think you appear to be trying to install applications from archived compressed files that you have downloaded.

If you are not sure about linux and are a comparative newcomer, I suggest you forget about trying to install things that way and use Add/Remove or synaptic, where you will find hundreds (thousands?) of applications for install, which can do just about anything you want.  In linux there is no equivalent to the setup.exe file that you have perhaps been used to in windows.

All GPL applications are available as source code which usually comes as a tarred archive, and to do anything with those they must be un-archived, hence the need for an archive manager.  However, I suggest you forget that for now.  Get used to using ubuntu and linux in general and then if you want to do more with the system, learn about the intricacies of installing from downloaded tar-balls etc etc.

EDIT:  Too slow again!

---

### Post by DGortze380 on 2008-07-10
> **ajgreeny said:**
>  In linux there is no equivalent to the setup.exe file that you have perhaps been used to in windows.


This isn't entirely true. 
.deb files will install in the same manner as a .exe in windows.
Also, a number of programs which you compile from source will include installer scripts which behave in the same manner.

---

### Post by adamogardner on 2008-07-10
I am very new but am eager to learn this and don't want to shy away from difficulty. It does happen with .tar et al.   Ok I moved it to a file in my home directory, and I understand how it horks better.  I need now to compile it as you say.   anyone?...

---

### Post by DGortze380 on 2008-07-10
> **adamogardner said:**
> I am very new but am eager to learn this and don't want to shy away from difficulty. It does happen with .tar et al.   Ok I moved it to a file in my home directory, and I understand how it horks better.  I need now to compile it as you say.   anyone?...

There should be a readme file for specific instructions on install that particular program (if you post what you're trying to install that might help.).

Here are some general instructions for installing anything in ubuntu:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by estyles on 2008-07-10
You said that you "moved" it to your home directory.  Did you extract it there, or just move the .tar file?

Archive Manager should have a button for "extract to", and that's what you should use.  Also, you should always extract to a brand new clean directory.  I'm on Windows right now, so I can't check the exact wording, but when you click on "extract to", you should be automatically in your home directory (if not, browse to it), and there should be a button or something in the dialog box to create a new folder.  Extracting to a clean directory is helpful for various reasons, one is that it helps you to keep things organized, and another is that it's slightly more secure (for malicious tarballs that try to inject crap by guessing filenames).  I wouldn't worry too much about the security thing, since you're not running as root, but it doesn't hurt to always make a new directory.

Also, check that you extracted the entire tarball, not just one file (this might happen if you click on a file or a folder inside the Archive Manager before clicking "Extract To"... when in doubt, select all before clicking).

Then there should be instructions either on the page you downloaded from or in a README file inside the extracted directory.  They should tell you what to do from there.  Like I said before, compiling from source can be really annoying if you don't know what you're doing, so I advise against it if you can help it, and well... good luck if you try it out.  It will work easily for some programs and not so easily for others.

Also, you may need to install "build essential" in Synaptic.  If the compile doesn't work, that should be the first thing you try.

---

### Post by adamogardner on 2008-07-10
can I have some direction through these instructions.  right now it is in a file in my home directory. 

\par
To perform a system-wide installation, we recommend that you copy the entire
Framework directory into a globally accessible location (/usr/local/msf) and
then create symbolic links from the msf* applications to a directory in the
system path (/usr/local/bin). User-specific modules can be placed into
\texttt{HOME/.msf3/modules} directory.  The structure of this directory should
mirror that of the global modules directory found in the framework
distribution.

---

### Post by adamogardner on 2008-07-10
i extracted it.  it's not a box but a folder.  and it's in it's own folder in my home folder.

---

### Post by SunnyRabbiera on 2008-07-10
> **adamogardner said:**
> i extracted it.  it's not a box but a folder.  and it's in it's own folder in my home folder.

yes that is normal.
If this is a app you have to compile make sure you have what is needed to compile software.
Now what is the application you are trying to install and is it linux compatible?

---

### Post by adamogardner on 2008-07-10
here are some instructions  and It is linux compatable, and I read that I need a ruby interpretter for it   I'm not sure if it's included.  

\par
To perform a system-wide installation, we recommend that you copy the entire
Framework directory into a globally accessible location (/usr/local/msf) and
then create symbolic links from the msf* applications to a directory in the
system path (/usr/local/bin). User-specific modules can be placed into
\texttt{HOME/.msf3/modules} directory. The structure of this directory should
mirror that of the global modules directory found in the framework
distribution.

---

### Post by BGFG on 2008-07-10
I myself ususlly use apt-get add remove or synptic. But why has'nt anyone mentioned the below commands ? If properly explained, compiling seems pretty straightforward. it's just a matter of getting used to something new. 

Still, at my level there's rarely a program that i need to compile. The repositories and availability of .deb files are phenomenal.

Please, one of the advanced guy's explain the below commands....
(so that i too may benefit :) )
```
./configure

make

sudo checkinstall -D make install
```

---

### Post by bobnutfield on 2008-07-10
> **BGFG said:**
> I myself ususlly use apt-get add remove or synptic. But why has'nt anyone mentioned the below commands ? If properly explained, compiling seems pretty straightforward. it's just a matter of getting used to something new. 

Still, at my level there's rarely a program that i need to compile. The repositories and availability of .deb files are phenomenal.

Please, one of the advanced guy's explain the below commands....
(so that i too may benefit :) )
```
./configure

make

sudo checkinstall -D make install
```

in its most concise description:

./configure:  sets up the code for the make command, setting the arguments

make:  an examination of the system for the install requirements (compiler present, other prerequisites...etc.)

make install:  installs the software to the system according to the authors instructions

Someone else may want to expand on this, but this is basically what the process does.

Bob

---

### Post by adamogardner on 2008-07-10
ok let me see if i get this: I cd to the framework folder,...ok thats as far as I can get..

---

### Post by BGFG on 2008-07-10
There's also a package called build-essential. Recently, when i was following a guide on installing skype or forcing architecture for something ( i can't remember which) i downloaded this package. i thing it's an important tool when compiling.

```
sudo apt-get install build-essential
```

---

### Post by bobnutfield on 2008-07-10
Inside that folder there should be README file which will give you install instructions and flags you must set in the ./configure option.  Check also in there is an uninstall file in case you want to uninstall the software.  Where possible, you should always install via the Synaptics Package Manager because it makes it much easier to uninstall and start over should you need to.

Bob

---

### Post by BGFG on 2008-07-10
Hey, mind telling me the package ? I could try to check it out hands on...

---

### Post by adamogardner on 2008-07-10
no  I would prefer to maintain my privacy with regards to this particular software.  But hell choose anything you want and if you figure it out please post some notes.

---

### Post by ajgreeny on 2008-07-10
> Originally Posted by **ajgreeny** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5359056#post5359056") 				
 				* In linux there is no equivalent to the setup.exe file that you have perhaps been used to in windows.*
 			 		 	 	 This isn't entirely true. 
.deb files will install in the same manner as a .exe in windows.
Also, a number of programs which you compile from source will include installer scripts which behave in the same manner.
Yes I agree with your comments but it is still my feeling that there is no real equivalent to the setup.exe.  There are several versions if you want to think of them in the deb, rpm, and other linux packages depending on distro, but no overall similar .exe file type, that was my meaning.

---


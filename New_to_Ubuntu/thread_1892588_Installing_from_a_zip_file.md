---
title: "Installing from a zip file"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by owdcoder83 on 2011-12-08
Hi everyone - I have am at the moment trying out Ubuntu 11.10 running it as a Demo from a CD.  What I would like to know is 'How does one install a program/application for a zipped file' ?

---

### Post by Lars Noodén on 2011-12-08
One would first unzip it and then look for instructions.  Usually there is a file called README or INSTALL that contains the instructions.  However, it is far better to use the package manager instead.  The Ubuntu Software Center, Synaptic and [apt-get](http://manpages.ubuntu.com/manpages/precise/en/man8/apt-get.8.html) are all front ends for the package manager.

---

### Post by shashanksingh on 2011-12-08
Unzip it to a place you want it to be.

Then there are commands like "make" which you type by going in its directory.

Can you give a little more information?

---

### Post by flemur13013 on 2011-12-08
> **owdcoder83 said:**
> ... What I would like to know is 'How does one install a program/application for a zipped file' ?

FOR a zipped file or "fro" a zipped file?

---

### Post by owdcoder83 on 2011-12-08
> **flemur13013 said:**
> FOR a zipped file or "fro" a zipped file?

Sorry it should read 'from' a zipped file.

---

### Post by oldos2er on 2011-12-08
> **owdcoder83 said:**
> Hi everyone - I have am at the moment trying out Ubuntu 11.10 running it as a Demo from a CD.  What I would like to know is 'How does one install a program/application for a zipped file' ?

What program?

---

### Post by owdcoder83 on 2011-12-09
The program I want to install is "RawTherapee" but I need to know how to install _any_ program which I may require which is obtained as a '.zip' file.

---

### Post by Lars Noodén on 2011-12-09
> **owdcoder83 said:**
> The program I want to install is "RawTherapee" but I need to know how to install _any_ program which I may require which is obtained as a '.zip' file.

It varies from zip file to zip file and the instructions, if there are any, are nearly always contained inside the zip file itself.  See post #2 above.

If you are uncertain as to the contents of the file, you can make a new directory and unzip the file inside that directory.  That way it can't make a mess where you work.

---

### Post by owdcoder83 on 2011-12-09
Hi Lars - Thanks for second reply.   I have unzipped the zip file and there are no installation instructions contained within.  There is a license, an 'About' file containing the all the names of the developers and lots of supporting files that the program requires and finally the main program which is about about 7.5 MBs in size.  I am stuck for ideas on how to proceed.??

---

### Post by EngineersGarage on 2011-12-09
im no expert, but i would say open it, open it some more, then go inside, click on something, see what happens. do this with all the stuff inside there. when you did this to all the items. open terminal. put in sudo apt-get whatapoesiam install.

if that doent work, then still in terminal put in sudo install (filename). I think this should do it.

---

### Post by mcduck on 2011-12-09
> **owdcoder83 said:**
> Hi Lars - Thanks for second reply.   I have unzipped the zip file and there are no installation instructions contained within.  There is a license, an 'About' file containing the all the names of the developers and lots of supporting files that the program requires and finally the main program which is about about 7.5 MBs in size.  I am stuck for ideas on how to proceed.??

In that case it sounds like the program is distributed ready to run. Just copy it where you want and run the program, there's nothing to be installed.

Anyway, it's impossible for anybody to give any kind of general advice about how to handle *any* distributed as .zips, as .zip is just an compressed archive and can contain any files. So the only general rule is to check the archive itself, or the developer's web site, for instructions. (and of course to use the package mangement instead of .zips when ever possible ;))

---

### Post by Lars Noodén on 2011-12-09
Can you list ([ls -l](http://manpages.ubuntu.com/manpages/precise/en/man1/ls.1posix.html)) the directory contents here?  There might be a clue in some of the file names.

---

### Post by owdcoder83 on 2011-12-09
Hi Lars - is this what you mean ?:-

iccprofiles
images
languages
profiles
share
sounds
themes
AboutThisBuild.txt
AUTHORS.txt
LICENSE.txt
options
rawtherapee

---

### Post by Lars Noodén on 2011-12-09
I was thinking with the [font=Courier New]-l[/font] option on [font=Courier New]ls[/font] so that we can see which are executable.  

It looks like Mcduck's suggestion applies to the situation.  The program might be distributed all ready to run.  What happens when you enter the same directory as contains 'rawtherapee' and enter the following?

```

./rawtherapee

```

...assuming you trust the source of this file ...

---

### Post by owdcoder83 on 2011-12-09
Lars - It looks like I first need to find out how to open a terminal in Ubuntu as what you are suggesting seems to rquire typing in the commands in terminal mode.   Am I correct ? If so how do i open a terminal.?

---

### Post by Lars Noodén on 2011-12-09
If you are in regular Ubuntu then ctrl-alt-t should do it.  So will going into the Dash and entering 'terminal'

Since you are using the GUI, what happens when you double click on the file 'rawtherapee' ?

---

### Post by oldos2er on 2011-12-09
> **owdcoder83 said:**
> The program I want to install is "RawTherapee" but I need to know how to install _any_ program which I may require which is obtained as a '.zip' file.

Their forums are here: [http://rawtherapee.com/forum/](http://rawtherapee.com/forum/) but like the others said, it looks like a ready-to-run binary.

A zip file, or tar.gz or tar.bz2, is just an archive. What steps you need to take to get a running program depend on what the archive contains, which could be several different things. Hopefully you're checking the repositories first.

---

### Post by Lars Noodén on 2011-12-09
> **oldos2er said:**
> Hopefully you're checking the repositories first.

LOL.  We all missed that.

There it is.  [rawtherapee](http://packages.ubuntu.com/oneiric/rawtherapee).  You can [get it](apt://rawtherapee/) from the Software Center or with Synaptic or even [font=Courier New]apt-get[/font]

---

### Post by oldos2er on 2011-12-09
Yes, but it looks as though the version in Oneiric's repos is significantly older than the one from [http://rawtherapee.com/downloads](http://rawtherapee.com/downloads)

---

### Post by Lars Noodén on 2011-12-09
> **oldos2er said:**
> Yes, but it looks as though the version in Oneiric's repos is significantly older than the one from [http://rawtherapee.com/downloads](http://rawtherapee.com/downloads)

[s]I've put in a request for it to be packaged:
[https://bugs.launchpad.net/ubuntu/+source/rawtherapee/+bug/902203](https://bugs.launchpad.net/ubuntu/+source/rawtherapee/+bug/902203)

I hope it can be done for Oneiric.[/s]

Edit:  The version at the rawtherapee site is the development version not a stable version.  I overlooked that by mistake.

---

### Post by owdcoder83 on 2011-12-10
I have now found the version that you mentioned in Software Centre and installed it from there.   The trouble now is that I cannot find it to run it  - where do I look please.   Sorry to be such a dope but I am a newbie to Ubuntu and Linux and have a lot to learn. !!!

---

### Post by Lars Noodén on 2011-12-10
No worries.  If you are running Unity then go to the Dash -> Search and enter the name 'rawtherapee'.  Once it is up and running you can right click on it to leave the icon in the launcher.

If you are using a different desktop than Unity, say which one.

---

### Post by owdcoder83 on 2011-12-10
Once again Lars many thanks.    I am now able to run it successfully.   I shall be forever in you debt. !!!!

---


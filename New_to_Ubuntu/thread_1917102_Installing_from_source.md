---
title: "Installing from source"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by cheatos on 2012-01-29
Hi,

I have recently got a WolframMathematica .iso file and I tried to install it. (it is for Linux)
I already extrated the iso using the Archive Manager and got a bunch of stuff but first of all, all this had a .;1 at the end of the file name what confused me pretty much.
Still I just went on trying everything with make install, apt-get install and stuff but nothing really worked.
All I have is a shell script named MATHINST but when I try starting it with the terminal I get something like this:
```
user@MartinsPC:~/Downloads/Mathematica/UNIX/INSTALLE$ sh MATHINST
CRITICAL FAILURE: Fundamental Error
 Installer text not found.

```with a bunch of free space below.
Does anybody have an idea what I could do?

---

### Post by Lars Noodén on 2012-01-29
Mathematic is closed source, proprietary so you cannot install from source.  They won't give you the source.  What you have are the binaries.  Look around and see if you can find a file ending in .deb or .rpm.  If there is a file .deb, then you can install it directly with [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html).  If there is a file ending in .rpm, then you can use [alien](http://manpages.ubuntu.com/manpages/oneiric/en/man1/alien.1p.html)

---

### Post by cheatos on 2012-01-29
Hi, thanks for your response, I meant what you mentioned, so the binaries.

I have been looking around but couldn't find a .deb or .rpm file, only this MATHINST shell script and a whole bunch of CONTENT.GZ files in various subdirectories, all packed into the folder FILES.
THe MATHINST is in a folder called INSTALLE and there's also another folder eith a GREETING.ENG file and another folder inside, which contains ERROR, PROMPT, TEXT and VERBOSE which all are just text documents.

---

### Post by Cheesemill on 2012-01-29
When your in the INSTALLE folder try this:
```
chmod +x MATHINST
./MATHINST
```

If you get permissions errors when installing you may need to try
```
sudo ./MATHINST
```
instead.

---

### Post by cheatos on 2012-01-29
Nope, sadly the same thing:
```
user@MartinsPC:~/Downloads/Mathematica/UNIX/INSTALLE$ ls
MATHINST  TEXTRESO
user@MartinsPC:~/Downloads/Mathematica/UNIX/INSTALLE$ chmod +x MATHINST
user@MartinsPC:~/Downloads/Mathematica/UNIX/INSTALLE$ ./MATHINST
CRITICAL FAILURE: Fundamental Error
 Installer text not found.






```What does chmod +x actualy do? Would I need to be root to execute it normally because I'm running my system only as a user without sudo permisions most of the time...

EDIT:
Am I able to change the subject, though? Maybe it would be better if changed to Installing from binaries...

---

### Post by Cheesemill on 2012-01-29
> **cheatos said:**
> ]What does chmod +x actualy do? Would I need to be root to execute it normally because I'm running my system only as a user without sudo permisions most of the time...

chmod +x changes the permissions of the file to make it executable.
As the file is in your home directory then you shouldn't need to use sudo as it is probably owned by you.

---

### Post by Lars Noodén on 2012-01-29
[chmod](http://manpages.ubuntu.com/manpages/oneiric/en/man1/chmod.1posix.html) changes the file permissions.  +x means to make the file executable in addition to whatever it may already be.  What kind of instructions can you find?  In normal open source software, which this is not, there is usually a file called README or INSTALL which has step-by-step instructions.  There might be something corresponding.  

Are the instructions on their web site wrong?

[http://reference.wolfram.com/legacy/v5_2/GettingStarted/SystemAdministrationGuide/InstallingMathematicaAsAMathLMClient/InstallingMathematicaOnUnixAndLinux.html](http://reference.wolfram.com/legacy/v5_2/GettingStarted/SystemAdministrationGuide/InstallingMathematicaAsAMathLMClient/InstallingMathematicaOnUnixAndLinux.html)

---

### Post by cheatos on 2012-01-29
Oh, okI haven't seen these instructions, but I didn't have a CD, I just had the iso, I think the problem then is, that I extracted the iso file.
I'll try this, and come back then.

Thank you all for your help!

---

### Post by cheatos on 2012-02-22
So, it worked fine with the manual, but first I had to mount the iso.
I'll mark this as solved

---


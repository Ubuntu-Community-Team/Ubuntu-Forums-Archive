---
title: "Ubuntu (terminal) not recognizing files..?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by captainhydrollama on 2008-06-21
I'm assuming this is an absolute beginoob question.  I'm very new to Ubuntu.  I am trying to get online with a Linksys WUSB54Gv4 usb adapter. As a result I'm trying to install things. Things like, ndiswrapper, etc.  Since I don't have a linux machine with an internet conxn I'm sort of stuck dloading stuff on a windows machine and trying to figure out how to install those things on my soon to be oh so sweetly online Ubuntu machine.  The problem is when I extract the packages and then try to install terminal says no such files exist (or something to that effect).  I have the files extracted to my desktop (which may be the first mistake).

Any suggestions??

---

### Post by lisati on 2008-06-21
There is often a "read me" file included in packages. They often have instructions in them.

Can you see a file "install" on your desktop? If so, all is not lost!

---

### Post by Presto123 on 2008-06-21
Maybe try this:
```
gksudo (command)
```
Shoud show:
```
Enter Password:
```

Path to file you could probably work your way to by typing in:
```
cd Home\YOURNAMe\Desktop
```

It's been a while since I've done much searching around through the terminal, so I may be off here somewhere; but it's worth a shot.

---

### Post by Presto123 on 2008-06-21
> **lisati said:**
> There is often a "read me" file included in packages. They often have instructions in them.

Can you see a file "install" on your desktop? If so, all is not lost!

Yeah...I agree with you. If it's not there, then check the site of the product for installation instructions.

---

### Post by smo0th on 2008-06-21
your terminal initiates at your home folder(/home/user). Type ```
pwd
``` to see where you are located, then do ```
cd /path/to/your/installation/files
``` and use ```
sudo ./config
``` or whatever the installation script is. Post back results ;)

---

### Post by captainhydrollama on 2008-06-28
I was in /home/captainhydrollama but not /home/captainhydrollama/Desktop. Ok, so that minor issue is solved.

But here's the real problem: I had used the built in extractor and just dragged the directory onto my desktop, since I was having issues. I read the readme which told me to refer to the sourceforge wiki ([www.ndiswrapper.sourceforge.net/wiki](www.ndiswrapper.sourceforge.net/wiki)) for more complete instructions. That page doesn't seem to exist but I'd found another through the Ubuntu community docs but that one gave me vertigo. So I decided to look at the install file instead.  Of course it refers me to the same page but it has a "short form" install instruction set.

It says "I need a recent kernel, at least 2.6.16, with header files for the kernel. Make sure there is a link to the kernel source from the modules directory. The command
                      
          ls /lib/modules/`uname -r` /build

should have at least 'include' directory and '.config' file."

Ok, first off, this paragraph makes my head hurt and maybe vague sense to me but I went into file system to see if there was something resembling a "recent kernel". I found /usr/src/linux-headers-2.6.24-16/kernel.

This seemed like I was probably in the right area. Hmm...link to the the kernel from the modules directory...not really sure what this means but I do the command and I find there is not a .config file. Hmm...not looking especially encouraging.

I do try to install anyway (running 'sudo make' and 'sudo make install') and I get an intimidating string of errors as it attempts to load the ndis drivers (no such directories, all kinds of declaration warnings, blah).

So, I'm guessing the lack of a .config is getting in the way...at the very least.

I so need help here (on so many levels!)

---


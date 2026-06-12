---
title: "[SOLVED] Another &amp;quot;How do You un-install question&amp;quot;????"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-24
Ubunteros,


I found this link:

[http://ubuntuforums.org/showthread.php?t=966398&highlight=camera+webcam](http://ubuntuforums.org/showthread.php?t=966398&highlight=camera+webcam)

On Ubuntu Forum which gives help for getting your webcam up and running.

Unfortunately for me nothing met with success. The latest "sudo" code I ran was:

"sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget [http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2](http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2) &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)"

SO, my question is how do I remove all which was just installed as nothing helped me?

I can see in the code that install appears 2 times. Does this mean I simply replace install with remove 2 times or what?

Thanks for helping me.

---

### Post by lswest on 2008-11-24
first do this:
```
cd gspca-* && sudo make uninstall && cd .. && rm -r gspca-<hit the tab key here to autocomplete>
``` it should remove the compiled program and then delete the source folder.  The reason I autocomplete the name this time is so that you don't accidentally delete anything else you might need that happens to start in the same way.

Then run:
```
sudo apt-get remove subversion build-essential linux-headers-$(uname -r)
``` though I wouldn't recommend this, as these 3 packages can be very useful later on, especially if you want to program in c or c++ (build-essential).

Just going to ask, have you rebooted and/or unplugged and plugged the cam back in?

---

### Post by suomalainen on 2008-11-24
LSWEST,

So if I understand you correctly, your saying that these last installed "programs" will not have any adverse/bad/detrimental effect on my system/Ubuntu software, although they may not be being used? Simply said, it's ok that they are there not being used???

I have re-booted my PC. I have un-plugged and then plugged back in the USB connection for the webcam any everytime meet with failure.

What do you think???

Thanks again...

---

### Post by lswest on 2008-11-24
Sorry about the delayed reply, supper called.  The last 3 packages you installed won't have any effect whatsoever on your system, and the packge that's been compiled (first half of my previous post) shouldn't do anything either, though it may conflict with other drivers if you continue to try to get your webcam working.

I'm happy to help, and if you post the output of ```
lsusb
``` we can probably even figure out which webcam model you have, and find drivers for it that work.

---

### Post by suomalainen on 2008-11-24
LSWEST,

Here is the info you requested:

Bus 007 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 03f0:0205 Hewlett-Packard ScanJet 3300c
Bus 004 Device 004: ID 03f0:3402 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04c1:009d U.S. Robotics (3Com) HomeConnect WebCam [vicam]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Does this help?

---

### Post by lswest on 2008-11-24
well your webcam is definitely > Bus 002 Device 003: ID 04c1:009d U.S. Robotics (3Com) HomeConnect WebCam [vicam] Are you sure it doesn't work?  Try installing cheese ```
sudo apt-get install cheese
``` and seeing if it recognizes it.  Otherwise I'll continue looking for a suitable driver, will post back if I find one.

Might try looking at this: [http://homeconnectusb.sourceforge.net/](http://homeconnectusb.sourceforge.net/) not 100% sure if it has what you need though, best thing I found.

---

### Post by suomalainen on 2008-11-24
Hi LSWEST,

I installed cheese, even re-booted, and it too did not work.... :<

What are your thoughts on the stuff I downloaded? Should I uninstall?

Thanks!

---

### Post by lswest on 2008-11-24
I'd uninstall the gcpa stuff, and keep the official packages (the subversion, build-essentials, and the linux-headers), since they are important for certain other things you may very well end up doing.

I'm not sure about the webcam, I can't find any up to date driver for it, and the other drivers I did see you seem to have tried.  Sorry I can't be of more help.

---

### Post by suomalainen on 2008-11-24
Lswest,

What would be the codes I need to uninstall? When I look above the first one say's:

cd gspca-* && sudo make uninstall && cd .. && rm -r gspca-<hit the tab key here to autocomplete>


I'm unclear what "hit the tab key here to autocomplete" MEANS?

Also, what does "keep the official packages (the subversion, build-essentials, and the linux-headers)" mean??... Are you referring to a code that I should NOT run? If so, what is the code I should not run?

Sorry for the questions but I want to get this right first time and not make problems...

Thanks again!

---

### Post by lswest on 2008-11-24
okay, the code you copied and pasted is what you're meant to run, just for the last bit of the code, that's enclosed with <> means that you're meant to actually physically hit the tab key. It's the key with the arrows in opposite directions about each other like: ```
<--
-->
```

The "official" packages are ones you installed using apt-get, and they're official since they are in the actual repositories (servers of packages that have been compiled for easy installation on Ubuntu systems, which are used by aptitude, apt-get, synaptics, etc. and are updated over time).  So avoid the second command I wrote in the post you referred to.  The "sudo apt-get remove" one.

Basically, run the commands you referred to in the last post, and delete everything in <>, then, with the cursor at the point where the leading < was, hit the tab key, it should auto-complete the name of the directory, and then hit enter.

The reason for this is because "*" is a wildcard (stands for anything) so that if you had a folder called gcpa-pictures (for example) it would delete that too if it's in your home folder.  That's what I want to avoid (deleting other files that start with "gcpa-").

Hope that helped, and if not feel free to post back again and I'll try to do better.  Don't worry about the questions, I'd rather you ask questions now than blame me for any misunderstandings that may have occurred.  And thankfully, you're not one who asks the same question a million times :P
Lswest

---

### Post by suomalainen on 2008-11-24
Lswest,

I ran the command like you said and got this:

desktop:~$ gspca-* && sudo make uninstall && cd .. && rm -r gspca-8d178f462ba7/
bash: gspca-8d178f462ba7: command not found

What to do?

---

### Post by lswest on 2008-11-24
you missed the "cd" at the start of that.  You need to change to the directory, so you can execute the install script to remove the links it created when installing.

---

### Post by suomalainen on 2008-11-24
Lswest,

So what does that mean? Now I'm lost.... Also, do you mean delete CD? or do I replace CD with something else?

Sorry.

---

### Post by lswest on 2008-11-24
no, you seemed to have missed the "cd" bit of the code when you copied and pasted.

---

### Post by suomalainen on 2008-11-24
Lswest,

OK now I see thanks!

But now I got this error:

pa@pa-desktop:~$ cd gspca-* && sudo make uninstall && cd .. && rm -r gspca-8d178f462ba7/
[sudo] password for pa: 
make -C /home/pa/gspca-8d178f462ba7/v4l uninstall
make[1]: Entering directory `/home/pa/gspca-8d178f462ba7/v4l'
make[1]: *** No rule to make target `uninstall'.  Stop.
make[1]: Leaving directory `/home/pa/gspca-8d178f462ba7/v4l'
make: *** [uninstall] Error 2
pa@pa-desktop:~/gspca-8d178f462ba7$

What happened? I don't know how to translate this stuff....

---

### Post by lswest on 2008-11-24
It just means the install script doesn't support uninstalling, because (I assume) the links are all created within the folder, so deleting it will uninstall it.

It's from this error: > make[1]: *** No rule to make target `uninstall'. Stop.

---

### Post by suomalainen on 2008-11-24
Lswest,

So how would I determine that everything has been deleted?

Thanks!

---

### Post by lswest on 2008-11-24
if you delete the gspca-8d178f462ba7 folder, you're all set.  The only thing that might stay are symbolic links to files that don't exist, but it won't cause any errors, and they take up <1kb, so I wouldn't worry about those.

---


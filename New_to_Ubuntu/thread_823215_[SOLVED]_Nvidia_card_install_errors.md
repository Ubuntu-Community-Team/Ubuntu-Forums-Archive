---
title: "[SOLVED] Nvidia card install errors"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by ross_m on 2008-06-09
I am trying to install nvidia drivers and consistently get the following error message:

"Removing nvidia-glx ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)"

I am running Ubuntu 8.04 0n AMD64 but the script seems to be looking in /lib32/ and, obviously can't find it because libGL.so.1 is in /lib64/. Is that the prob, and if so, what can be done?

---

### Post by The Cosmic Hobo on 2008-06-09
I'm afraid I don't know how to solve your problem from the information given, but starcannon posted this [guide to installing Nvidia drivers](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6). You could do worse than seeing if doing it his way works.

Other than that... sorry, I got nothin' - hopefully someone more knowledgeable will come along in a minute.

---

### Post by kayfes on 2008-06-09
Went through a some tough times getting my Nvidia drivers to work so here is thread to what I posted and eventually found my solution in

[http://ubuntuforums.org/showthread.php?t=820160&highlight=Nvidia+drivers](http://ubuntuforums.org/showthread.php?t=820160&highlight=Nvidia+drivers)

Good Luck I am new to this linux stuff too, but I have found if you ask they will answer.

---

### Post by ross_m on 2008-06-09
> **The Cosmic Hobo said:**
> I'm afraid I don't know how to solve your problem from the information given, but starcannon posted this [guide to installing Nvidia drivers](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6). You could do worse than seeing if doing it his way works.


First, thanks for the help. This issue seems to be pretty intractable for many, including me. I've been to the suggested links and followed them to the letter. When I ran "build-essential" I noticed at the end of the process the same old error messages were coming up: "error checking `/usr/lib32/libGL.so.1': No such file or directory..." etc. However, I continued through to the end hoping it would all come right, but on running the nvidia installer it errored out with:

"ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package."

What this looks like to me is that the build-essential script (or any script involved in installing nvidia drivers) is looking for a file: libGL.so.1 in directory /usr/lib32. I've looked for /usr/lib32 and, indeed it is not there - but /usr/lib64 is. Lo and behold, in /usr/lib64 is, you guessed it, libGL.so.1. I'm assuming this is because I have AMD64. I've got 64bit version Ubuntu 8.04, and my driver package is for my graphics card (6100) - 64 bit. So why the hell is it looking for stuff in /lib32/ when I've got /lib64/. Is it possible to edit the script? Should I make a directory usr/lib32/ and copy libGL.so.1 into it so it has the satisfaction of deleting what isn't there in the first place? This just seems like a completely lame problem for such a fantastic OS. How hard can it be to get a driver working?

ross

---

### Post by uncannybuzzard on 2008-06-09
> **ross_m said:**
> I am trying to install nvidia drivers and consistently get the following error message:

"Removing nvidia-glx ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)"

I am running Ubuntu 8.04 0n AMD64 but the script seems to be looking in /lib32/ and, obviously can't find it because libGL.so.1 is in /lib64/. Is that the prob, and if so, what can be done?

i haven't much experience with 64 bit systems, but you can try this the rerun the install:

```
sudo ln -s /usr/lib64/libGL.so.1 /usr/lib32/libGL.so.1
```

if that doesn't work, try Envy. tseliot rocks my faces ***.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Dizzle7677 on 2008-06-09
Just do a search in package manager for 'libc headers' [in descript & name] ... make sure libc-dev and linux-libc-dev are installed to complete the nvidia install. libGL.so.1 is the main opengl library file. Don't edit the script whatever you do.:) It's a pain to install but it's cool once you get the kinks out. Oh and make sure you reinstall nvid drivers after a new kernel install.don't worry about the ftp kernel build thingy either,b/c you're building one.

Did you uninstall the linux-resticted-generic stuff or de-select the drivers in HW Drivers? Just don't uninstall 'linux-restricted-modules-common'. Usually it's the first stuff I get rid of then I install the nvidia stuff. 
 
cheers

---

### Post by ross_m on 2008-06-10
Thanks for the idea but get "no such file or directory" error. Tried Envy - same problem as original: "error checking `/usr/lib32/libGL.so.1': No such file or directory"

ross

---

### Post by ross_m on 2008-06-10
Thanks Dizzle7677, I think that's done it. For future reference starcannons advice was great. It worked until the driver install program failed to find the libc header files. Your advice seems to be the missing link - make sure libc-dev and linux-libc-dev are installed - then follow starcannons procedure. Unfortunately, I'd also fiddled with all sorts of things. Now it's done I'm not totally sure of what actually fixed it - a bit like programming a video recorder. Eventually you get it done but you've no idea how you did it.

Regards and thanks to all who offered advice,
Ross

---

### Post by kayfes on 2008-06-10
> **ross_m said:**
> Thanks Dizzle7677, I think that's done it. For future reference starcannons advice was great. It worked until the driver install program failed to find the libc header files. Your advice seems to be the missing link - make sure libc-dev and linux-libc-dev are installed - then follow starcannons procedure. Unfortunately, I'd also fiddled with all sorts of things. Now it's done I'm not totally sure of what actually fixed it - a bit like programming a video recorder. Eventually you get it done but you've no idea how you did it.

Regards and thanks to all who offered advice,
Ross

Lol damn vcrs glad you got it fixed!

---

### Post by jonkirian on 2008-10-16
i just came across this issue on 8.04.1 AMD64. the issue in this case was that there was a /usr/lib & /usr/lib64, but no /usr/lib32. apt was looking for libGL.so.1 in /usr/lib32, which did not exist.

solution:

sudo ln -s /usr/lib /usr/lib32

---


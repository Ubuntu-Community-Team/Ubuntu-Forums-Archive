---
title: "Ndiswrapper problems"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Xanaklusmos on 2008-06-09
I did a command line only install of debian with the laptop set of packages also.  I have ndiswrapper installed and the appropriate driver.  The wireless does not work, I have no internet, and the computer is very old.  I'm also new to Linux.  Where do i go from here?

---

### Post by patrickaupperle on 2008-06-16
> **Xanaklusmos said:**
> I did a command line only install of debian with the laptop set of packages also.  I have ndiswrapper installed and the appropriate driver.  The wireless does not work, I have no internet, and the computer is very old.  I'm also new to Linux.  Where do i go from here?

Sorry, but I can not help. At least this will get your post to the top of the stack where a linux pro will see it, though.:)

---

### Post by bobnutfield on 2008-06-16
You do not mention what wireless chipset you are using.  You also do not menton what errors you are getting.  You just say that wireless is not working.  Provide a little more information to get the best help.

---

### Post by prshah on 2008-06-16
> **Xanaklusmos said:**
> I did a command line only install of debian with the laptop set of packages also.  I have ndiswrapper installed and the appropriate driver.  The wireless does not work, I have no internet, and the computer is very old.  I'm also new to Linux.  Where do i go from here?

Why not try my (solved) step-by-step thread (with expected outputs)  [http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260) to set up your wireless network card? If you run into any problems, post back which step you are stuck at.

---

### Post by Xanaklusmos on 2008-06-19
> Quote:
Originally Posted by Xanaklusmos  
I did a command line only install of debian with the laptop set of packages also. I have ndiswrapper installed and the appropriate driver. The wireless does not work, I have no internet, and the computer is very old. I'm also new to Linux. Where do i go from here? 

Why not try my (solved) step-by-step thread (with expected outputs) [http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260) to set up your wireless network card? If you run into any problems, post back which step you are stuck at. 
> 3) Copy your NetGear .INF file (note; the location given here is the most likely; please check your exact location)
Code:
mkdir inf && cp /media/sda1/windows/inf/WG311v3/* inf/
what is the NetGear .INF file?

---

### Post by prshah on 2008-06-19
> **Xanaklusmos said:**
> what is the NetGear .INF file?

The INF(ormation) file contains information about which files are needed to make the device you have work. It also contains other information which tells windows what the device is (a network adapter), what interface it has (usb), what resources it requires, how it's started up, handled, and terminated, and where to put the files required to do these actions.

---

### Post by Xanaklusmos on 2008-06-19
one thing, will these instructions work with a WPC54G v.2?  Thats what mine is.

---

### Post by prshah on 2008-06-19
> **Xanaklusmos said:**
> one thing, will these instructions work with a WPC54G v.2?  Thats what mine is.

Yes these instructions should also work for PCMCIA adapters.

---

### Post by Xanaklusmos on 2008-06-28
for a bunch of things it says "bash: sudo: command not found"

---

### Post by Xanaklusmos on 2008-06-28
anything that starts with sudo

---

### Post by prshah on 2008-06-28
> **Xanaklusmos said:**
> for a bunch of things it says "bash: sudo: command not found"

> **Xanaklusmos said:**
> anything that starts with sudo

Well then, [there goes your sandwich..]("http://images.google.co.in/images?q="sudo make me a sandwich"") (stupid joke, forget it, too good to resist).

No idea why you are getting sudo errors. Are you running as root by any chance? I think you may have made some simple copy/paste/typo mistake. Please post a screenshot of this error in terminal.

---

### Post by patrickaupperle on 2008-06-28
> **prshah said:**
> Well then, there goes your sandwich.. (stupid joke, forget it, too good to resist).

No idea why you are getting sudo errors. Are you running as root by any chance? I think you may have made some simple copy/paste/typo mistake. Please post a screenshot of this error in terminal.

He probably does not have sudo installed. 
@xanaklusmos, Type su, prees enter, type your password, then run the commands that start with sudo, but without the sudo. 
Sudo runs a command as if you are root (have inputted su).

---

### Post by Xanaklusmos on 2008-07-21
hey patrick im not sure how much of prshah's instuctions i already did with you.  Can you take a look and tell me where I need to start?

---


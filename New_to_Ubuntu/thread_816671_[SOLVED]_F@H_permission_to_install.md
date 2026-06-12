---
title: "[SOLVED] F@H permission to install?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by The Crystalline Entity on 2008-06-02
Hey there folks!  I'm in the process of reading as much of the stickies as possible but have already run across a few stumbling blocks.  The first one I'd like to remedy is my inability to install F@H.  I downloaded FAH504-Linux.exe from the website and I see the file on my desktop however double clicking it gives me an error of > couldn't display..........  There is no application installed for this file type.

I said to myself OK this is when sucking it up and moving to the command line (I'm a total noob) is probably appropriate.  So I opened my terminal and type 
```
/home/username/Desktop/FAH504-Linux.exe
```
and it spits back
```
bash: /home/username/Desktop/FAH504-Linux.exe: Permission denied
```

OK permissions... I read something in the tutorial I'm reading about  "press Alt-F2 and type"
```
gksudo nautilus
```
so I do that and it just brings up a window with my desktop folder in it, but nothing in the folder:confused: So I try to graphically launch the F@H installer but I get the same error as before, then I drag it into that new root desktop folder and try it, same error.  Now I can't drag it back to my original desktop, so I just deleted it and downloaded another copy.

What am I doing wrong?  I knew there were going to be problems but I didn't know I couldn't install files.  I know I sound frustrated but it really is a good sort of frustration.  I really do want to learn Linux and command line.  I've been putting this off for **far** to long.  Thanx!

---

### Post by SunnyRabbiera on 2008-06-02
Huh?
it looks like to be a windows executable there, you cant use windows executables in linux by default.

---

### Post by chewearn on 2008-06-02
> **SunnyRabbiera said:**
> Huh?
it looks like to be a windows executable there, you cant use windows executables in linux by default.

it's not a Windows executable, though it might look like one.

.

To The Crystalline Entity,
Are you running 64-bit ubuntu?

.

---

### Post by The Crystalline Entity on 2008-06-02
That's the linux console version listed on F@H's website.  Clicked on the little peguin and everything.  The directions to install from the website tell me
> To launch: To use this program, make sure that you can execute it (chmod +x FAH5-Linux.exe) and then run it ./FAH5-Linux.exe

I tried putting that in the terminal and just got an error.

Here's a link to the page and the instructuions page
[F@H Downloads](http://folding.stanford.edu/English/Download)
[Linux instal instructions](http://folding.stanford.edu/English/LinConsoleInstall)

---

### Post by The Crystalline Entity on 2008-06-02
> **AstalaVista said:**
> it's not a Windows executable, though it might look like one.

.

To The Crystalline Entity,
Are you running 64-bit ubuntu?

.

No it's 32bit.
It's an old 733 Mhz pIII

---

### Post by SunnyRabbiera on 2008-06-02
> **The Crystalline Entity said:**
> No it's 32bit.
It's an old 733 Mhz pIII

ah, well its good we asked so we can assess your problem.

---

### Post by The Crystalline Entity on 2008-06-02
> **SunnyRabbiera said:**
> ah, well its good we asked so we can assess your problem.

Yup it's an old 32bit 733Mhz PIII with 384 Mb of RAM.  Running the 32bit Ubuntu Desktop and trying to install the Linux Console (x86) and BSD v5.04 of the F@H console

---

### Post by chewearn on 2008-06-02
You need to do everything in terminal, because there is no GUI version of F@H in linux.


First create a subdirectory in your home and move the file over.  When you get the file to run, it will start to create many other files, and you don't want them to clutter up your desktop.

```
mkdir ~/fah
mv ~/Desktop/FAH504-Linux.exe ~/fah
```Make the file executable:
```
cd ~/fah
chmod +x FAH504-Linux.exe
```Run the file:
```
./FAH504-Linux.exe
```You will have to keep the terminal window open while F@H is running.

This is important: if you encounter an error, post the exact error message.

---

### Post by The Crystalline Entity on 2008-06-02
^Thanx I'll give this a shot as soon as I'm done installing VLC.  I'll post results!

---

### Post by The Crystalline Entity on 2008-06-03
Huzzah!  Success! :biggrin:

Though the change directory command should read:
```
cd ~/fah
```
For anyone running into the same problem.

So like you said I'll have to keep the terminal open continue to run it.  That's fine I've been using the console versions for a while now, so I'm used to seeing it in my "start menu" (what should I be calling that bottom bar that lists all open windows?).  I assume that I can open another terminal with that one still running?

Thanx very much!  I'll mark this as solved as soon as I figure out how!\\:D/

---

### Post by chewearn on 2008-06-03
> **The Crystalline Entity said:**
> Huzzah!  Success! :biggrin:

Though the change directory command should read:
```
cd ~/fah
```For anyone running into the same problem.


Thanks, I fix it now.

> 
So like you said I'll have to keep the terminal open continue to run it.  That's fine I've been using the console versions for a while now, so I'm used to seeing it in my "start menu" (what should I be calling that bottom bar that lists all open windows?).  I assume that I can open another terminal with that one still running?

Thanx very much!  I'll mark this as solved as soon as I figure out how!\\:D/

Yes, you can open another terminal, without affecting that one.

Glad it's now working. :smile:

---


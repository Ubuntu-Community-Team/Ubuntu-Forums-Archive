---
title: "New User - First Post - Where did my application go?"
date: 2015-06-01
forum: New to Ubuntu
---

### Post by David_Linscott on 2015-06-01
Just installed Ubuntu yesterday and have been playing with dual boot to see if I can get away from Microsoft.  Wanted to see if I could get Lightscribe to work.  Downloaded the deb packages and ran the install from terminal and it looked like it worked, but could not find application.  Then I found I could use the installer to install the pkg but same result.  Noticed on the pawtec site where the software was they say applications will be in the opt folder.  Sure enough, if I do ls on the opt folder I see lightscribeApplications.  But if I search with Dash or installed software in the software center I don't find them.  How do I run the application?  I'm sure it's easy but this stuff is a bit confusing to me.

---

### Post by TheFu on 2015-06-01
Manual installation of file with .deb packages is to be avoided, especially for someone new to Linux/Debian/Ubuntu.  **Always** use the official repos and package managers.

This isn't Windows. Think different.
For a quick primer to Linux, [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - read the 1st 3 links in the list. Should take about an hr and it will open your eyes.

There are many how-to guides and instructions for step-by-step things around the internet for Ubuntu/Linux.  That doesn't mean any of those are smart for your situation. Just because something seemed to work, that doesn't mean it did what you actually wanted or expected.  At this stage, you don't know, what you don't know. We've all been there.  

In the beginning, stay with *ubuntu.com websites for help. This should limit the confusion.  Also, always clearly say which release and which GUI you are running to get the most help.

Where do your application go?  I'm not certain it will actually run at this point. Most non-trivial applications have multiple dependencies. If you install through the package manager download/installation tools, those are handled for you (almost always).

---

### Post by grahammechanical on 2015-06-01
What exactly did you download and install? Was it Lightscribe System Software? Or Lightscribe Simple labeler? Or both? According to the pawtec web site the two go together. I am guessing the Lightscribe System Software is the back-end and does not have an icon to click, and Lightscribe Simple Labeler is the front-end that will come with an icon that will be put in the Dash.

Regards.

---

### Post by David_Linscott on 2015-06-01
OK, thanks.  Will do some more reading and use more caution in the future!

---

### Post by David_Linscott on 2015-06-01
I first downloaded and installed the system software deb package.  dpkg -s lightscribe indicated it was successful.  Then did the labeler software which also indicated it was successful.  Then while looking around I saw the deb folders for both of these and discovered I could use the Software Center Installer for those so I tried that also.  When I used that, it did give a warning that the software might be unreliable, but I chose to ignore and proceed.  Those installations also appeared to work.  I am running release 14.04 which I just started playing with yesterday.

Looking at this some more, I'm guessing that those packages are for 32 bit systems.  Doesn't look like it was ever developed for 64.  There are some threads about forcing it for 64.  I think I will give up the Lightscribe pursuit.

---

### Post by mastablasta on 2015-06-02
> **David_Linscott said:**
> I first downloaded and installed the system software deb package.  dpkg -s lightscribe indicated it was successful.  Then did the labeler software which also indicated it was successful.  Then while looking around I saw the deb folders for both of these and discovered I could use the Software Center Installer for those so I tried that also.  When I used that, it did give a warning that the software might be unreliable, but I chose to ignore and proceed.  Those installations also appeared to work.  I am running release 14.04 which I just started playing with yesterday.

type the name of program in terminal

in kubutnu you hit Alt+f2 and can then run stuff. or just find it in the menu

programs in Linux often go all over the place as they share libraries. in windows they also often share libraries but often bring their own "duplicates" along.

> 
Looking at this some more, I'm guessing that those packages are for 32 bit systems.  Doesn't look like it was ever developed for 64.  There are some threads about forcing it for 64.  I think I will give up the Lightscribe pursuit.
you can easily run 32 bit packages in 64 bit, just not the other way around..

---

### Post by vasa1 on 2015-06-02
> **mastablasta said:**
> ... you can easily run 32 bit packages in 64 bit, just not the other way around..
I had a hard time trying to get 32-bit Seamonkey running on my 64-bit laptop. Like OP, I gave up.

---

### Post by buzzingrobot on 2015-06-02
A program correctly constructed and built to run on a modern Linux desktop will follow certain standards.  That includes creating and placing a specific file in the /usr/share/applications directory.   That file -- a '.desktop' -- associates an icon with the specific executable file used to launch the program.  In other words, it tells the system what icon to use to represent the program and it tells the system what to do when someone clicks on that icon. 

In Unity, it's those icons that populate the Dash. 

If the OP's program follows those standards, then -- no matter what it calls itself -- its icon will be displayed. The icon should also appear in response to a keyboard search for its name or some closely associated keyword.

If the program does not adhere to standards, then the OP probably needs to manually locate and launch it.  Best bet is to look in /usr/bin.  (Some Windows developers do a rough port of their product to Linux and do not adhere to these standards.)

---

### Post by David_Linscott on 2015-06-02
Mastablasta - thanks.  I figured that out last night - that one can execute the program by going to terminal and typing the name.  When I did that there was a library it couldn't find that appeared to have something to do with 32 bit.  Don't remember the exact name now.  The program is buried a couple levels in the /opt directory.

---

### Post by David_Linscott on 2015-06-02
Buzzingrobot - thanks.  The Lightscribe software has not been supported for a couple years and what is out there for Linux is evidently pieced together and not up to standards.  I might revisit this at a later time.

---


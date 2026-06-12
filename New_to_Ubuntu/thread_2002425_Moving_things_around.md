---
title: "Moving things around"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by Bob Saget on 2012-06-12
So I bought an ubuntu beginner's guide for my kindle, and have read up on it.  It's great for working with command line and showed me things I never would've considered existing on an OS.

I remember intimately the chapter on creating, moving, and deleting directories.  In Windows I know if a directory has program files in it, do not move it because then the registry can't find the files (a reason why you don't try to copy game files off a disc straight into the program files without an installer).  More than likely this is the case for ubuntu, but I really must ask what all can I move around in my filesystem while not screwing things up because I really find my directories to be an unorganized, cluttered mess with no sense of a logical path.  For example, I expect a program to be in the applications folder, but instead it's in a lib.  I try to figure out a pattern but I'm just so lost in my directories.

I would appreciate some insight into what I can touch and move around, and what I should keep my hands off of.  thanks!

---

### Post by snowpine on 2012-06-12
touch: your /home folder
don't touch: anything not in your /home folder

That's my advice.

ps In Ubuntu you don't execute programs by navigating to /usr or /lib; simply tap the Super/Windows key and type what you want to do. :)

---

### Post by bencouve on 2012-06-12
Agreed, only touch things in home if you are a beginner. Create your directories off home too. It would do you well to read up on /etc /bin /usr /var to name a few to get a general understanding.

I personally have left Unix/Linux for a while and am now back working with it as an os. Sorry I ever left it to be honest. Having to re-learn everything.

---

### Post by Bob Saget on 2012-06-12
Simple enough.  Thanks.  I've only read a quarter of this book on my kindle, so I might run up on etc, bin, usr, and var.  Maybe after one read-through it'll all make sense lol.

---

### Post by vasa1 on 2012-06-12
> **Bob Saget said:**
> Simple enough.  Thanks.  I've only read a quarter of this book on my kindle, so I might run up on **etc, bin, usr, and var**.  Maybe after one read-through it'll all make sense lol.
As the others have said, read whatever you like but stay at **home** :)

Leave **etc, bin, usr, and var** for later, much later!

---

### Post by deadflowr on 2012-06-12
I tend not to move folders and files I do not have permission or ownership of. I also tend to think of the hidden folders and files in the home directory as equally off-limits. As, even though they are user-owned, most of them are configuration files, and set as they are for a reason.

---

### Post by Cheesemill on 2012-06-12
A bit of light reading for you to help you understand the Linux filesystem:

[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)
[http://www.tuxradar.com/content/take-linux-filesystem-tour](http://www.tuxradar.com/content/take-linux-filesystem-tour)
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

As mentioned above unless you know exactly what you are doing then you should only make changes to files and folders in your home directory.

---

### Post by buzzingrobot on 2012-06-13
There's no Registry in Linux.

That said, Linux uses a variety of environmental variables (info read at system startup and stored in memory) to tell it how to find the programs and files you want to run. Change either those variables or the file systems without knowing what you  are doing and something will, sooner or later, go wrong.  Not that you have a reason to do that.

Your Home directory is yours to do with as  you please. The rest of it belongs to the system.

Programs often consist of more than one file, and typically are supported by code contained in library file in the "lib" directories.

---


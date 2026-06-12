---
title: "[SOLVED] computer language"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Camilia on 2008-08-29
Reading computer lanugage I get from those for suggestion as to solve problems is frustrating. Where do I learn computer language?  For example I was told to save the wallpaper in a directory. I don't know what a directory is.

---

### Post by RequinB4 on 2008-08-29
basic:

[http://www.webopedia.com/](http://www.webopedia.com/)
[http://www.saugus.net/Computer/Terms/](http://www.saugus.net/Computer/Terms/)

more specific:

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5026-glossary-common-linux-computer-terms.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5026-glossary-common-linux-computer-terms.html)

bunch more on google

---

### Post by nicedude on 2008-08-29
A computers file system works like a family tree as in you start out with the root and then there are directories under that in the tree and in each of those directories there can be more directories and so forth. Directories themselves are like file folders in a file cabinet as they can contain files & or other directories which can then also have files & or directories.

When you say commputer language I am thinking you mean commands that you can use in a terminal window. Which a terminal window is like the old DOS prompt where you can type commands for software that is contained in your PC. This is for when a given software does not have a shortcut in the applications menu.

In general for learning Ubuntu the thread at the top of the main page entitled "new to Ubuntu start here" is probably as good a place as any. If you run into a specific thing you need to know how to do or need advice about which programs you could install to do a given task then just post a new thread with your question and we will all help you to do whatever you need to do.



Hope this helps you get started learning :-)

---

### Post by Camilia on 2008-08-29
Now I even more confused as to why I was told to copy a wallpaper in a directory. For at [http://www.webopedia.com/](http://www.webopedia.com/) at the top of the tree is c/ which to me stand for c drive.

I accidentally got the problem solved concerning downloading wallpaper anyway.

I was thinking of learning more about ubuntu to get a certificate. I don't know if I can get through all of the computer language. I have an associates degree in electronics but didn't have to learn much computer language.

---

### Post by nicedude on 2008-08-29
wasn't trying to confuse you more and didn't relize how tough it is to try and describe what a directory is or how a drive is laid out, I guess it is so ingrained in my geeky brain that this is second nature to me to understand such things. In general if someone gives you a command to do something and you trust them then you only need to copy and paste it into a terminal ( Top menu bar click Applications -then-> Accessories -then-> Terminal to open a terminal session ) and press enter and the command will run. In general though you don't have to do that very often unless you are fixing a problem or trying to use a utility that is only command line based and has no flashy window type GUI ( graphic user interface ), but these are usually utilities that you will not need to learn in order to use Ubuntu as your personal home computer. 

Just be sure if you ever do run commands that anyone gives you that you trust them ( if they are in these forums you most likely can as people who give destructive commands as pranks etc get the big boot around here )  

Hope you can learn all about PC's and see how the file system tree works, its really simple just hard to describe.

Sorry again if I confused you but do some reading and you should figure this out rather quickly.


nicedude

---

### Post by Camilia on 2008-08-29
I get the zist of the tree. Just don't understand the instructions someone gave me about saving a wallpaper in a directory, since that is a drive. It is a drive?

---

### Post by nicedude on 2008-08-29
You would do what they said if you were going to organize your stuff. Like I have directories for wallpaper where I keep a couple thousand wallpapers in that directory there are more sub directories that are broken down by categories  ( like cars, girls & nature scenes )  all that is so that I can find something when I want to as easy as possible. For example I also on my data storage partition have a directory called Multimedia and when you open that directory you would see sub directories of music, movies & TV which each contain those types of files, this is all for my organizational benefit not because I have to do it etc. They were most likely telling you to make a wallpaper directory so that you could store wallpapers in it and be able to find them when you want to switch what wallpaper you are displaying on your desktop. So directories are just containers you can create on a drive to hold your files and organize them, I hope this is understandable to you.

Well it is almost 3am here so I must get some shuteye but I hope you will just read up on these topics a bit and see if things don't become clearer for you.

Goodluck with this and goodnight,
nicedude

---

### Post by nothingspecial on 2008-08-29
I found this a great help.

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by lisati on 2008-08-29
> **Camilia said:**
> I get the zist of the tree. Just don't understand the instructions someone gave me about saving a wallpaper in a directory, since that is a drive. It is a drive?

A directory is a convenient way of organizing information on a drive. You might want to think of a "directory" as a "folder".

When you're organizing the paperwork in your office, you wouldn't just pile up the letters and files in one enormous heap on the floor - you'd probably have some system of filing cabinets and folders within the filing cabinets. In the same way, a computer can organize its information into disk drives (a bit like the filing cabinets) and into directories on the disk drives (a bit like the folders)

When you click on the "places" menu on your Ubuntu desktop, you might notice an entry, "home folder". This is like a folder (directory) where you can store your personal data, and keep it separate from the information used by Ubuntu to run your computer. You can make new folders within this folders to organize things further. How you do that will depend on whether you're using the "Graphical user interface" (where you use the mouse to instruct the computer what to do) or the "terminal" (where you type in a command using the keyboard).

Hope this helps.

---

### Post by dmizer on 2008-08-29
Think of a Disk drive like a filing cabinet.

Each drawer is like a disk drive partition.

Each drawer (partition) is filled with file folders, and some file folders have folders inside of them. Each folder can be though of as a directory.

Inside the folders (directory), is where all your pictures and documents and other information is contained.

There's a good reason that the little icons you see on your desktop and in your Home are shaped like file folders.

---

### Post by lisati on 2008-08-29
> **dmizer said:**
> Think of a Disk drive like a filing cabinet.

.....

Nicely said.....

---

### Post by howlingmadhowie on 2008-08-29
> **Camilia said:**
> I get the zist of the tree. Just don't understand the instructions someone gave me about saving a wallpaper in a directory, since that is a drive. It is a drive?

the simple answer? no, it doesn't have to be.

the idea of a directory came about so files could be grouped. On my computer at the moment there are 271414 files. imagine the mess if there was only one place files could be. i'd spend ages searching for the file i wanted to look at. so the idea of a directory was born. it's basically a place you can put files. the base directory of my ubuntu installation for example contains 27 items, 21 of which are directories (which in their turn contain further directories and files), 2 of which are files, and 4 of which are (symbolic) links (don't worry about that for now). as to where this stuff physically is: because i'm reading it, the list i'm seeing is contained in the ram of the computer. in my case the list has (mostly) been loaded from the hard drive (don't worry about the 'mostly' atm). in my case the hard drive is a 2.5" S-ATA which i can get at by turning my laptop over and unscrewing the cover on the left. it is however possible to install ubuntu on large servers with huge numbers of disks churning away storing information according to complicated mathematical algorithms. in such cases it becomes very hard to say on which physical device data is stored (with some mathematical algorithms it doesn't really make sense to talk about a single physical device storing the data) and the best response to the question as to where the data is is just to wave your hand at the server and say "somewhere in there". 


you seem to have not had much exposure to computers up to now. i'd recommend finding the address of a local linux user group (try googling for lug and where you live) and asking there for help. i'm sure they'd be happy to explain the basics to you :)

---

### Post by Camilia on 2008-08-30
Well I have saved all of the links given and will read them later.
As if I don't have other things to do. I have become addicted to the computer since starting with ubuntu. Love to do things that stimulate my mind.

---


---
title: "Green as a dollar"
date: 2015-07-27
forum: New to Ubuntu
---

### Post by Mike Zahorik on 2015-07-27
I've loaded Ubuntu 12.04 on a computer of mine and have gotten used to using it. I'm an old OLD guy who has been using the A: for drives since the early 1970's. I started on a DEC PDP8E. Anyway, I'm tired of MicroSoft's constant changes and expense of upgrading so I though I'd try Ubuntu. BUT, for some reason I just can't get the hang of the filing system. I like to see a tree of directories and like to know where files are. Where can I find something to read to become more familiar with the filling system. Confused with /media or /dev etc. Mike

---

### Post by yancek on 2015-07-27
Try the link below which gives a fairly basic explanation of it.

[http://www.tecmint.com/linux-directory-structure-and-important-files-paths-explained/](http://www.tecmint.com/linux-directory-structure-and-important-files-paths-explained/)

---

### Post by Mike Zahorik on 2015-07-27
OK, looks like a lot of directories. All off the root? Which is, C: ? How do the different drives work into this. If I have a Floppy Drive how would this show up here? Again, I'm very ignorant of this. Thanks for the help, Mike

---

### Post by mystics on 2015-07-27
To my knowledge, all external drives should appear under */media/<username>/* once mounted.

And as far as I know, Linux file systems essentially treat  everything as a file: actual files, directories/folders, and even devices.  So unlike Windows where you're considering each device as its own file system, devices in Linux, once mounted, are just added on to the file system hierarchy and stem off from the */media* directory.

---

### Post by Bashing-om on 2015-07-27
Mike Zahorik; Hi ! My Welcome to the forum.

Allow me to fill in a bit of the gap.
In linux (ubuntu) :
A IDE hard drive would be identified as hd ( Hard Drive)
With the advent of SATA drives the hard drives are identified as Serial Device (sd);
such that:
sda == hard drive number 1
sdb == hard drive # 2
sdc == hard drive #3
then on the hard drives are the partitions;
Partitions are identified:
sda1 == 1st partition on the 1st hard drive
sda4 == 4th partition on that 1st hard drive
sdb3 == 3rd partition on the 2nd hard drive
sdc 5 == 5th partition on the 3rd hard drive.
--------------
fd == floppy disk
sr would be the CD/DVD drives
-------------

And yes, everything is under / ( termed 'root') in the linux file system.
A bit of a change, and takes a bit to understand it, but it is completely logical I assure you.

[INDENT][INDENT]the curve of learning,
[INDENT][INDENT][INDENT]it can get steep -> but worth the effort 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bab1 on 2015-07-27
> **Mike Zahorik said:**
> OK, looks like a lot of directories. All off the root? Which is, C: ? How do the different drives work into this. If I have a Floppy Drive how would this show up here? Again, I'm very ignorant of this. Thanks for the help, Mike
It might help if you some Linux to Microsoft terminology translation.

In Linux speak a drive is the physical device (i.e HDD)  The HDD has partitions on it (MS calls these drives).  The file system of both Linux and MS are hierarchical and the root of the file system is the same (/).  The system partition of Windows has the label named C:

---

### Post by Bucky Ball on 2015-07-28
If you want something more familiar and 'Windows-like', try another flavour. Lubuntu, Mate, and Xubuntu don't use the Unity desktop environment, are easily configurable and look a lot more like, say, XP. 

Most of the Ubuntu file managers have the option to see the left hand pane as a tree, which I think is what you're after. I use PCmanFM for my file manager and in there I click on 'Places' at the top of the left hand pane of the file manager and you can select Directory Tree or Places. In Ubuntu you would be using Nautilus. Unsure how you would get there using that as don't have it installed, but don't doubt it is possible.

---

### Post by Topsiho on 2015-07-28
If you know the Windows file system, you should be able to understand the far simpler Linux file system: everything hangs just under ***one*** root directory. In Windows every socalled drive uses it's own file system, so you have an A:\ system, C:\, D:\ and so on (backward slashes). In Linux it's just one system: / (forward slash, just as on the internet).
Often the user files, in /home, such as /home/John, /home/Jane, etc.), are on a separate partition of the hard disk, or on an other hard disk, and there are a number of dedicated directories for dedicated files, as used for the system files and other.

Do a ls, or ls -al, (read the contents of the directory) in the root directory, and try to find out what the directories in it, such as etc, are used for.

Contrary to what Bucky Ball says (sorry BB :) ) there are no Linux flavours (or any other "flavour") that use the idiosyncratic MS way of organizing hard drive partitions ...

Cheers,

Topsiho

---

### Post by Mike Zahorik on 2015-07-28
Thanks for the information. I really don't want to think like windows as I use Ubuntu. I'd rather become comfortable with the Linux terms and conditions. So, to me it looks like all the equipment, drives, CD, USB, terminals, anything connected to the computer is looked at as a file (?) and is a directory under the root. When looking around in the tree I see that some of the drives, for example sda1, will be listed in a few different places. Right now I don't know why. If I saved a document file where would the default save be, /home? If I saved it to fd1 or hda1, I should be able to find it there, correct? I might stop at the local library and see if they have a book on this. Then maybe I can experiment independently and when I get stuck I can ask here. 

One last question, for now, I was reading about Open Source Code being written in Linux. Ubuntu is an operating system, but is there an assembly language or a programming language in Linux or Ubuntu to writing OSS?

Thanks for all the help, Mike

---

### Post by Topsiho on 2015-07-28
To better understand Linux, it's best to google for a Linux tutorial, or Linux tutorial for beginners. There are lots and lots of tutorials out there, and most elementary things (and you need not know more than that, unless you want to) is explained sufficiently well.
The knowledge you gain there is knowledge that was valid 30+ years ago, and it still will be 30 years from now. Far better than knowing the GUI of a an application, which may be changed two days after tomorrow :)

Presently I am dabbling with a very popular programming language called Python. Itself seems to be written in C or C++, but Google and Canonical and many other firms are writing at least much of their code in Python, as it is very easy and versatile. I hope this answers your question.  And of course there are many other programming languages, such as Java, Ruby and others, and possibilities to write graphical applications for them, such as tkinter and others.
And if you want to write code in assembly, google for it, I think there is nothing to stop you doing so. Assembly is for one kind of processor only, the languages I mentioned are multi platform. Google also for GCC compiler, it blows my mind that a compiler like that is open source and free.

Topsiho

---

### Post by steeldriver on 2015-07-28
The above is all fine and dandy, but IMHO is "too much information"

As a regular user, you don't need to worry about /dev or any of the hda, sda, fd0 and so on - these are low level device files that the user (almost) never needs to interact with

In desktop versions of Ubuntu, there are some default directories under /home/username which is where you will spend 99% of your time:

```

/home
&#9500;&#9472;&#9472; steeldriver
&#9474;   &#9500;&#9472;&#9472; Desktop
&#9474;   &#9500;&#9472;&#9472; Documents
&#9474;   &#9500;&#9472;&#9472; Downloads
&#9474;   &#9500;&#9472;&#9472; Music
&#9474;   &#9500;&#9472;&#9472; Pictures
&#9474;   &#9500;&#9472;&#9472; Public
&#9474;   &#9500;&#9472;&#9472; Templates
&#9474;   &#9492;&#9472;&#9472; Videos

```

For example, /home/user/Downloads is where most browsers will default to saving downloaded content from the internet.

Things like floppies, USB sticks and other external drives will generally automount under /media/user

```

/media
&#9492;&#9472;&#9472; steeldriver
    &#9492;&#9472;&#9472; 387D-22B1

```

---

### Post by oldos2er on 2015-07-28
[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Mike Zahorik on 2015-07-29
Thanks for the replies. Actually, that 'too much information' is exactly what I'm looking for. Figuring out how Word or a spreadsheet works is rather boring. I'm more interesting in the mechanics of the operating system. I found a book at the library, yesterday, 'Beginning Ubuntu Linux'. Although it was written when Ubuntu 9.04 was the thing, it has some good stuff in it. The first 10 chapters are basic stuff I think I figured out already. But after that there is a chapter on the file system, which I will be experimenting with. Then there is a chapter about the BASH, which I find very interesting. I'm more interested in learning about the kernel and the shell rather than the GUI. They also talk about alternate Bash's. So, I have a bunch of new things to try and I'm sure that questions will follow. Thanks a lot, Mike

---

### Post by Bucky Ball on 2015-07-29
Don't forget to have a dig around the threads in [here]("http://ubuntuforums.org/forumdisplay.php?f=39"). You might pick up something interesting. ;)

---

### Post by Topsiho on 2015-07-30
Probably things get more clear when you realize that Linux derives from Unix, which was an OS used in big mainframes, that were operated by an operator, and served many clients (some times from all over the world) who had accounts. So Unix, and thus Linux, are multi user multi tasking OS's from the start, run by a root, with (one or) many accounts.
The users each had/have their own directory under /home, that they can use, without having access to the directories of the system itself, or of the other users, unless permissions are set to give access. So reading about permissions is one paramount item you have to do.

The operator (root) has all rights on the system to enable him to run it, to change the system files and configurations, to administer the accounts, and so on.

In Ubuntu the user who installed the system is a normal user, without admin rights (he is no root), but is usually the only user who can get these rights using sudo.
That's why he can change system files and configurations, if he precedes his command by sudo, and gives his password. He then is root for a period of 15 minutes. This for safety reasons, so no one uses his system as root full time.

This also answers your question that as a normal user you don't save or read files to or from another place then from your own directory under /home, except when you use another medium, such as an external disk or USB thumb, which usually is mounted under /media, as someone already mentioned here.

Success :)

Topsiho

---


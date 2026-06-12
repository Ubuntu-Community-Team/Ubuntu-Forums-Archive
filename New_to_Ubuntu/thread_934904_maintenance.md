---
title: "maintenance"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by 007casper on 2008-10-01
does ubuntu require maintenance issues such as disk defragmentation etc like windows?

thank you

---

### Post by rybaxs on 2008-10-01
my Ubuntu automatically scan at the start boot.. so far for more than a year, my ubuntu works well without any maintenance.. i d0nt have a real answer, sorry..

---

### Post by iaculallad on 2008-10-01
Like they always say: "Linux does not need filesystem defragmentation like windoze". 
Like, Ext3, It uses a journal instead of writing directly to the disk in sequence.

---

### Post by Ryadt on 2008-10-01
> **007casper said:**
> does ubuntu require maintenance issues such as disk defragmentation etc like windows?

thank you
Ubuntu does not really require defragmetating cause of the way file is saved on the HD. 
Have a look here:[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by kpkeerthi on 2008-10-01
[http://www.ubuntu-unleashed.com/2007/09/clean-up-ubuntu-junk-files.html](http://www.ubuntu-unleashed.com/2007/09/clean-up-ubuntu-junk-files.html)

---

### Post by 007casper on 2008-10-04
everyone thank you so much for your inputs

I have tried the link kpkeerthi suggested and tried  

sudo apt-get autoclean

I got this message
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
-
I will try to figure out what else is going on... 

in the mean time is there any other things I should look out for in regards to maintenance issues...

---

### Post by Crafty Kisses on 2008-10-04
You don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can
suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in Terminal:
```
sudo apt-get clean

```

---

### Post by Paqman on 2008-10-04
> **007casper said:**
> 
I will try to figure out what else is going on... 


You'll get an error like this if you're already running Synaptic, Add/Remove or the Update Manager, since they all use the apt system.

As for maintenance, besides allowing the system to do the regular security updates you shouldn't need to do anything. There are a few minor tidiness tasks you *could* do, such as removing orphaned packages. If you're not short on storage you don't need to bother with those though.

Of course the most important maintenance task is the same for every OS: back up regularly.

---

### Post by iansane on 2008-10-04
> **Ryadt said:**
> Ubuntu does not really require defragmetating cause of the way file is saved on the HD. 
Have a look here:[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Not arguing. I understand the concept and it does make sense but the person who did this explaination gave much bigger hard drive space to the linux example and it makes it appear that if they both had the same limited amount of space they would both have a problem. It's called controlled experiment when all factors are the same and only one changes. It makes no sense to me to change the size and the filing system to demonstrate that the filing system is better.

I wonder though what happens when there's plenty of space but every file is to big to move around to an empty space cause all the spaces are smaller than the files. It has to push two files together to make the empty space bigger. Does it start putting them together to make bigger spaces and end up the same as the FAT example then? Or does that just mean it's time to clean some junk off the drive or get a bigger drive?

---

### Post by iponeverything on 2008-10-04
> **iansane said:**
> Not arguing. I understand the concept and it does make sense but the person who did this explaination gave much bigger hard drive space to the linux example and it makes it appear that if they both had the same limited amount of space they would both have a problem. It's called controlled experiment when all factors are the same and only one changes. It makes no sense to me to change the size and the filing system to demonstrate that the filing system is better.

I wonder though what happens when there's plenty of space but every file is to big to move around to an empty space cause all the spaces are smaller than the files. It has to push two files together to make the empty space bigger. Does it start putting them together to make bigger spaces and end up the same as the FAT example then? Or does that just mean it's time to clean some junk off the drive or get a bigger drive?

Read this back back in the day very good paper:
See: [http://web.mit.edu/tytso/www/linux/ext2intro.html](http://web.mit.edu/tytso/www/linux/ext2intro.html)

Also look at ext2, ext3 and reiserfs on:
[http://en.wikipedia.org/](http://en.wikipedia.org/)

The short answer is that you don't need to defragment -- The design of ext2, ext3 and most of the other modern filesystems makes them very resistant fragmentation. Depending on what your primarily using the filesystem for, will decide how you format it to  optimize performance.

---

### Post by Kellemora on 2008-10-04
Hi Iansane

Someone explained it to me so simply using two common objects as examples.

First the DOZE system.  Are you familiar with vinyl Pop-Beads that kids play with.  They plug together to make long chain of beads.  Or you could think of a string of pearls, all the pearls on a long string.
In the Doze, they have two chains, one the TOC tells WHERE the strings of pop-beads are located.  The other chain is the file system.  Each letter or space represents a single bead and they are all linked together in one big long chain.  When you edit a file and it grows shorter, blank beads fill up the space until the start point of the next file.  BUT, if you make the file bigger, the rest of the file gets added to the very end of the chain of pop beads.  The first chain called the TOC keeps track of where all these bits and pieces of a single file are located.

OK, now lets look at LINUX.
Linux looks like the file sorting case at the post office.  One big empty box after another stretching for miles, hi hi...........
When you write a document, save a picture, whatever, that chain of pop beads is stuck into a pigeon hole (BLOCK).  The TOC remembers WHICH pigeon hole the chain was stuck into.  When you write a new document, it goes into another pigeon hole.  If you amend a document, it goes back into the pigeon hole it came from.

But your question was, what if the file is too big for any empty spots.
If you completely fill a pigeon hole, a second pigeon hole is dedicated to the rest of your file.  But at the same time, it does try to keep the pigeon holes next to each other, although it wouldn't matter that much, it only has to look for TWO pigeon holes.  NOT 180 or more different start stop places as a heavily edited file in the DOZE.

One of the other reasons you don't need to defrag in Linux is it may move where it stores a file to another area of the hard drive.  Oft used files are located like in the center where the read heads ride and rarely used files end up near the outer edges where they take longer to get to.
When and how this happens I don't know, never studied it that close.

I have a friend who works in Forensics and one of the things they do is recover data from confiscated hard drives.  Reading a Doze drive is like trying to read a newspaper, every few lines of the article are on a different page in the newspaper.  But reading a Linux drive is like reading a book, everything is together for the whole chapter.  You may have to look around for where Chapter 2 starts, but at least everything is all together.

This was a gross oversimplification of what's going on inside that Hard Drive, but parallels what the drive would look like if you stretched it out.

TTUL
Gary

---

### Post by bodhi.zazen on 2008-10-04
Every OS needs cleaning :

[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---


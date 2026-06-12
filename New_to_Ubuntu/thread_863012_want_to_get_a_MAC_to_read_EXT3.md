---
title: "want to get a MAC to read EXT3"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by nynoah on 2008-07-18
Sorry to ask a question that may have been answered.  But I could not find what I was looking for with the search.  

I have an ext3 HD on my system.  I am trying to transfer some files to my friends MAC but it won't read ext3.  Anyone know how I can get her MAC to read my external HD?

---

### Post by mcduck on 2008-07-18
There is Ext2/Ext3-driver for OS X, but it's a bit of a pain to use as it's graphical configuration tool and automatic monting seem to fail, at least on every Mac I've tried.. So you need to mount the drive by hand from command line..

I'm not absolutely sure if this is the one I'm using: [https://sourceforge.net/projects/ext2fsx/]("https://sourceforge.net/projects/ext2fsx/")

---

### Post by nynoah on 2008-07-18
Great.....I hate having to mount from command line. I had a REAL bad experience with that once.  Besides she is a total........non computer person.  Damn, any good graphical GUI ones out there?

---

### Post by nynoah on 2008-07-18
Can a MAC read NTFS easy?  I might just reformat to NTFS and do it that way.

---

### Post by mcduck on 2008-07-18
> **nynoah said:**
> Great.....I hate having to mount from command line. I had a REAL bad experience with that once.  Besides she is a total........non computer person.  Damn, any good graphical GUI ones out there?

Like I said, the driver is _supposed_ to incude a GUI tool and automountin, but they fail to work..

But it's true that it's a nasty thing to do by hand, even more so on a Mac as it doesn't even work exactly the same way as it does on Linux.. Most likely she wouldn't exactly enjoy doing it.. BUt if you only need to do it once to move the files it's still an option.

I don't know about NTFS suport on Macs, I suppose there must be at least some driver for it. Never tried, I don't have any NTFS drives around. 

If reformatting is possible, and your files are smaller than 4GB, FAT32 works fine on all operating systems.. Of course that's the only good thing there is to say about FAT.. :D

---

### Post by nynoah on 2008-07-18
So a MAC can read FAT32 fine.  What file system does MAC use?  Can Linux write natively to that format?

---

### Post by Canis familiaris on 2008-07-18
> **nynoah said:**
> So a MAC can read FAT32 fine.  What file system does MAC use?  Can Linux write natively to that format?

Mac uses HFS+
[http://en.wikipedia.org/wiki/HFS_Plus](http://en.wikipedia.org/wiki/HFS_Plus)

I think it is possible to use it in Linux but since I never used a Mac, I dont know.

---

### Post by coffeecat on 2008-07-18
> **nynoah said:**
> Can a MAC read NTFS easy?  I might just reformat to NTFS and do it that way.

Yes it does read NTFS fine, but not write to unless you install the ntfs-3g driver (which is more fiddly than in Linux). FAT32 is the easiest choice because both Macs and Linux support read/write out of the box, but it has the limitation that files cannot be greater than 4Gb. You can even format an external HD with FAT32 in the Disk Utility in Macs.

I have no experience of the ext2/3 driver for Mac OS, but I can anticipate one problem. MacOS, like Linux, supports Unix file permissions. If you are the first created user in Ubuntu, you will have a UID 0f 1000. Chances are the UID of the Mac user will be different, and you won't have access to the files. My UIDs in my Mac Mini and Ubuntu are different. I discovered this when I copied some files from my Mini to a hfs+ formatted drive (the MacOS filesystem) and then plugged it into my Linux box. Linux can read hfs+ but not write to it. It was then I discovered the UID problem. I was locked out of subfolders. I had to open a terminal and do 'sudo cp' and then 'sudo chown' to get at my files.

Using NTFS or FAT32 actually has the advantage of avoiding permissions issues. They are both Microsoft filesystems which do not support Unix permissions.

---

### Post by nynoah on 2008-07-18
Thanks coffeecat and arnuag-panda......thanks for taking the time to explain the long way too.  I learned a little more about things that way.  Yeah I just repartitioned my external and put a big FAT32 partition on there.  I think that will be the easiest route.  I wish all the different OS's would just get programs that are easier to use for file system reading.  Ubunutu is far superior but something tells me the big box corp guys in the other world are purposely not making it easy.  Lame.

---


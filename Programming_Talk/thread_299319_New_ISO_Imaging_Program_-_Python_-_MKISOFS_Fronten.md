---
title: "New ISO Imaging Program - Python - MKISOFS Frontend"
date: 2006-11-14
forum: Programming Talk
---

### Post by gerowen on 2006-11-14
I'm a new-ish programmer learning python, and I've written a python frontend for mkisofs.  Reason being that especially for people like me who take backups of data quite often, which may include making .iso images of discs, speed is always a good thing, and it just got tiring to keep typing:
```
mkisofs -r -J -o '/home/marcus/cdimage.iso' /media/cdrom0
```
every single time I wanted to make an image, and having to retype it if I forgot a quotation around a filename with spaces, etc.  So I wrote this program mainly in python, partly using bash scripts, to make it slightly faster(and more user friendly for those new to Linux) to create a .iso image of a CD.  It assumes the -r and -J options and will put the image wherever you want it to.  The only problems that I can think of it having right now is if the CD ROM drive being used is not /media/cdrom0 , which can be quickly solved by editing the program file to use the new device, but I don't have an easy way to do it with a different device if you have multiple CD drives.  As I said in the Readme, if you make images from a different device every time, it wouldn't really have any advantages over manually typing the whole string for mkisofs every time.  Anyway, I even made a launcher bash script and wrote an installer file that put all of the files in a neat little folder and creates a symlink to the launcher, and I made an uninstaller that removes all of the files.  I've ran my own installer on my Ubuntu machine and tested it and it seems to run fine to me.  I plan on eventually making a version with a gui, but this is what I've put together for myself to use so far.

My question to you is, would this tool be helpful in some instances, or is it just something that might be useful for me but not too many other people?  Also I'm not very familiar with Macintosh computers.  I've used them and know that OSX is Unix based, but that's about it(they've always been too expensive for my blood).  Does OSX come with mkisofs so this could run in a Mac environment, or should I tell the oscheck() function to apply to Mac as well?  If so what is the output of sys.platform on a Mac machine?  

I've created a tarball with all of the files in it which you can [download here](http://147.133.214.88:8001/Software/Linux/makeiso.tar.gz) to look at or use if you want.  [Here is a screenshot](http://i2.photobucket.com/albums/y45/dudeman41465/Computer%20Screenshots/makeiso.jpg) and if you don't feel like downloading the file(it's only 42.5 kB) here is the source code of just the program file:

```

#This is a program that will make it easier and faster to create .iso images
#of CDs or DVDs.  It's a python frontend for mkisofs that assumes some common
#arguments and saves you the time of manually typing all of it into the terminal.
#Marcus Dean Adams (marcusdean.adams@gmail.com)
import os
import string
import sys
def main():
    #This is the heart of the program that actually creates the iso image.
    print ""
    print "MakeISO CD/DVD Image Maker"
    print "If you need help don't forget to read the Readme.txt file in /usr/makeiso"
    print ""
    name=raw_input("What is the name of the CD/DVD? ")
    print ""
    location=raw_input("Where do you want to put the image? ")
    print ""
    os.system("mkisofs -r -J -o '%s/%s.iso' /media/cdrom0"%(location, name))
    print ""
    eject=raw_input("Do you want to eject the CD drive?(y or n) ")
    eject=string.lower(eject)
    if eject=='y' or eject=='yes':
        os.system("eject /media/cdrom0")
    print ""
    print "Finished!"
def oscheck():
    #This runs first to make sure the user is running a compatable operating system.
    if sys.platform=="win32" or sys.platform=="win64":
        print "Sorry, this script is for use only on Unix based operating systems"
        print "The commands executed by this script are only valid in such an"
        raw_input("environment.  Press Enter to exit...")
    else:
        main()
oscheck()

```

---

### Post by gerowen on 2006-11-14
I changed it so that on install it asks the user, and if they want, it puts an icon on the desktop so they can launch it via point and click.

---


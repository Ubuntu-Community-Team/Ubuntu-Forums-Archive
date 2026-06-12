---
title: "Partimage tool"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-04-27
Hello

can anybody help me with the tool called Partimage?

i understand how to use the tool until the point where it asks for a location to put your image file into...

the location screen speaks about server ports and things.....instead of just opening a "browse drives" dialogue for my local computer...

do i need to know the IP number of my local computer or what?

this tool makes an Image file of my entire Linux system...

Vince

---

### Post by southernman on 2008-04-27
Vince, it's been a while since I used this tool and didn't recall having to use IP numbers.

[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage) <--- Have a look there for a VERY brief howto. A more detailed (perhaps doesn't have what your wanting) 

is here ---> [http://www.digitalissues.co.uk/html/os/misc/partimage.html](http://www.digitalissues.co.uk/html/os/misc/partimage.html)

---

### Post by southernman on 2008-04-27
Vince, it's been a while since I used this tool and didn't recall having to use IP numbers.

[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage) <--- Have a look there for a VERY brief howto. A more detailed (perhaps doesn't have what your wanting) 

is here ---> [http://www.digitalissues.co.uk/html/os/misc/partimage.html](http://www.digitalissues.co.uk/html/os/misc/partimage.html)

---

### Post by vinceUUUU on 2008-04-27
Hello

yes...that is helpfull

you see, i want to save the image of my partition on the same drive...just as a large file...

the examples seam to say you should be saving your image to a spare partition...

i don't have a spare partition....i just want to save the image file onto my same hard drive standard Linux partition...

also the example is a bit missleading....it says they are saving the /dev/hda12 partition....but the screenshot is not pointing to those exact phrazes....

it makes no sense...

hmmmm

thanks

Vince.

---

### Post by southernman on 2008-04-27
> **vinceUUUU said:**
> Hello

yes...that is helpfull

you see, i want to save the image of my partition on the same drive...just as a large file...

the examples seam to say you should be saving your image to a spare partition...

i don't have a spare partition....i just want to save the image file onto my same hard drive standard Linux partition...

also the example is a bit missleading....it says they are saving the /dev/hda12 partition....but the screenshot is not pointing to those exact phrazes....

it makes no sense...

hmmmm

thanks

Vince.
There may lie your problem then. IIRC, you can't save a backup image file, to that same partition/drive, which you are wanting to backup. The image would just keep growing as it copies the backup file.... over and over. Capiche? ;)

What your seeing with the IP, is if you want to connect to a server via the internet or locally on your intranet.

Fortunately for me (not so for you), when I used PI the backup was saved to a seperate partition on my large drive that I setup when installing.

You'll need a spare drive/partition, a seperate computer in or outside of your home network, or look into splitting the image to burn to cd/dvd.

Sorry...

---

### Post by vinceUUUU on 2008-04-27
Hello

yes, i understand exactly what you mean.

Is there any other tool you know of that can do what i want?

i know of many backup tools...that create a single large file of your Entire linux OS which can be restored...but is that the same thing as creating an image file of a partition?

it seams the same in principle...

The tool QUIK START creates one single large file of my Linux OS....but is that file an actual partition image file?...or is it in some other format?

The quik start tool can restore the file it makes...in much the same way as tools like partimage.......but is it actually really a true image file of a partition?

the reason i ask is because i want to make a proper image file of my entire Linux partition.....then i want to point a VirtualBOX to start booting into that image file....(so i get an exact copy of my system inside a VirtualBOX)

this is all very simple to achieve.....once i have cleared up the questions above

is a backup file the same thing as a partition image file?

Thanks

VInce.

---

### Post by southernman on 2008-04-27
In reverse order here... ;)

> is a backup file the same thing as a partition image file?Nope, least I don't think so. Partimage is copying your partition, byte for byte, bit by bit. To restore an image from this tool, the new partition has to match exactly in size (think it can be larger, though), as the old partition was.

A backup "file" is just copying the data you select to be backed up.

> The quik start tool can restore the file it makes...in much the same way as tools like partimage.......but is it actually really a true image file of a partition?Can't help you with that one, never heard of the program.

> The tool QUIK START creates one single large file of my Linux OS....but is that file an actual partition image file?...or is it in some other format?Again, never heard of it.

> i know of many backup tools...that create a single large file of your Entire linux OS which can be restored...but is that the same thing as creating an image file of a partition?Again, a file and an image, regarding backups I think are two separate creatures. Don't quote me on that. If a program uses files or images, they'll clearly tell you so in their documentation.

> Is there any other tool you know of that can do what i want?At the moment, all I am aware of that creates an "image" file is partimage. I've been away from heavy power using since Gusty was released... 6 or so months ago.

If all you wanted was a simple backup and restore avenue. The dead easiest can be found here:

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

It's an old thread, but still works like clockwork. Have it saved in my favorites and use it for quick and dirty backup purposes.

---


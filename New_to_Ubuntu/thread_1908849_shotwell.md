---
title: "shotwell"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by Karlof on 2012-01-14
Hi Forum

I have loaded photos into shotwell from a disc via a file

fine everything ok switch off computer

when I return to shotwell I find the library has emptied no pictures

but another file has appeared called the missing file the pictures are in
this file but you cannot do anything with the pictures

What has happened ??

Cheers Karlof

---

### Post by WasMeHere on 2012-01-14
Hi,

Maybe your pictures are stored on a disk that you have not mounted. Or maybe you shut down your computer by force (not allowing it to save all temporary data from RAM and/or swap). Shotwell keeps track of pictures, but does not have an own storage. The files are imported from external media (for example a camera or flash memory card) and stored as regular files in a directory on a partition of (one of) your drive(s), usually a hard disk.

What do you mean by 'loaded photos into shotwell from a disc via a file'? What kind of file?

Have fun finding out :-)
Olle

---

### Post by Karlof on 2012-01-15
Hi Olle

I have solved the problem I loaded the same disc into Fspot
on linux Mint 12 no problem the disc created files as before these were then imported into Fspot also automatically imported into picasa at the same time

As a point of interest Linux Mint 12 is far easier to use regarding installing google earth picasa java and chrome I have 
spent hours trying to install the same programmes in ubuntu 11

 I think linux is great but if it really wishes to challenge
microsoft for the average punter it needs to make it easy to access non linux software especially the popular ones  as above

Cheers Karlof

---

### Post by WasMeHere on 2012-01-15
> **Karlof said:**
> Hi Olle

I have solved the problem I loaded the same disc into Fspot
on linux Mint 12 no problem the disc created files as before these were then imported into Fspot also automatically imported into picasa at the same time

As a point of interest Linux Mint 12 is far easier to use regarding installing google earth picasa java and chrome I have 
spent hours trying to install the same programmes in ubuntu 11

 I think linux is great but if it really wishes to challenge
microsoft for the average punter it needs to make it easy to access non linux software especially the popular ones  as above

Cheers Karlof
Yes, I agree. But let us admit, that this is what many developers try to do all the time. Over a span of a few years, several linux distros have become much easier to use including easier to connect to hardware and other software (think of built-in drivers for hardware, web applications, Wine).

---

### Post by eric-yorba on 2012-01-16
> **Karlof said:**
> but another file has appeared called the missing file the pictures are in
this file but you cannot do anything with the pictures

Missing pictures isn't a "file,"it's a section of the Shotwell UI that shows which images Shotwell can't find.  If the photos are all in there, the photo files were likely moved or unmounted.

Is it possible you did an "import in place" rather than a copy?  That would explain why the photos were gone as soon as you removed the disk.

---


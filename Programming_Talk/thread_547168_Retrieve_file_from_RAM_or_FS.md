---
title: "Retrieve file from RAM or FS?"
date: 2007-09-09
forum: Programming Talk
---

### Post by Krijk on 2007-09-09
This isn't really the proper place, but there are a lot of smart people in Programming.

I've accidently overwritten a tar-file which contains important personal information when running  a script.

Is it possible to retrieve this from RAM? I've got a lot of RAM and I've noticed earlier with the script that the output given had to come from RAM because the files where deleted by the previously run script.

If there's another way to do this, please let me know.

---

### Post by CptPicard on 2007-09-09
Now this is an extremely long shot after an hour, your cache buffers are long gone, but at least you could have 

cat /dev/mem > copy.dat


to dump all of your RAM into a file for further study... I don't know how you are going to find the tar there, but at least you'd have the RAM contents persisted!

Your better chance would probably be to try to analyze the disk for the tar; it's unlikely it's been overwritten yet, although it's been removed from filesystem indexes... (and chances are your RAM dump overwrites the file's remnants..)

---

### Post by DMills on 2007-09-09
The other thing that **MIGHT** save you, is that a file is not deleted until the last application using it closes it, so if you have anything that is still using that file, you can probably find it still linked in /proc/<pid>/fds or similar where pid is the process id of the process that still has the file in use. 

Failing that, pull the plug and get that hard drive to the data recovery people (And I **MEAN** pull the plug, not shutdown (which will write to the disk)), expensive, prone to damage other bits of the filesystem  and sort of last resort but it is probably the only thing left.

I am puzzled by the appearance of being able to read the file from RAM (after it has been deleted) as the kernel is supposed to keep track of that sort of thing and the buffer cache should not be handing out deleted files....  Are you sure about this?

Regards, Dan.

---

### Post by Krijk on 2007-09-10
Thank you all for the suggestions, but alas... no retrieval :(

> **DMills said:**
> 
I am puzzled by the appearance of being able to read the file from RAM (after it has been deleted) as the kernel is supposed to keep track of that sort of thing and the buffer cache should not be handing out deleted files....  Are you sure about this?
Regards, Dan.

I'm pretty sure of this.
When I was testing the script I had one occassion where this happened.

The script basically does:
* retrieve data fromUSB-device
* write files to temporary directory
* modify the files and move them to an alternate location
* remove original files in temp dir

During the testing, I ran the script when the USB-device wasn't present. The original files were removed, but the output was from the previous running of the script.
The only thing I can think of that it was in RAM since both inputdevice and workingdir were emptied, but maybe I drew the wrong conclusion :confused:

---


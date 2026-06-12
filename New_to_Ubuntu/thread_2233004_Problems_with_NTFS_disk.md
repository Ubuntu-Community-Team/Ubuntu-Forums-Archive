---
title: "Problems with NTFS disk"
date: 2014-07-05
forum: New to Ubuntu
---

### Post by darkrapsody on 2014-07-05
Hi. So, I have recently installed Trusty on my PC. I have 2 disks, one for OS's and one for personal files. The first one, has 14.04 & W8 on it.
Everything was working fine, 'til I try to play my whole music collection -which is hosted on my personal files disk, that runs with NTFS- on audacious. At the moment I try this, Audacious stops from time to time and it freezes suddenly and randomly. I run audacious from Terminal and these are the messages I have:


```
mpg123 error in file:///media/gens/Super%20Personal/Musik/Mi%20m%C3%BAsica/Nirvana/Incesticide/Nirvana-%20Sliver.mp3: Error reading the stream. (code 18)

```

```
read failed: Input/output error.
read failed: Input/output error.
read failed: Input/output error.
```


After other attemps to read other mp3 archives from the list, Audacious told me this:

```
mpg123 probe error for file:///media/gens/Super%20Personal/Musik/Mi%20m%C3%BAsica/Pearl%20Jam/Pearl%20Jam-%20Unthought%20Known.mp3: Message: Feed me more input data!
```


And so on. At first, I thought it could be an error on the mounting of my NTFS secondary disk, so after a lil research  I've corrected two possible origins of the problem: The Fast StartUp at W8 (switching to off) and tried to specify the behaviour of that disk, thinkin' it could be some syncronization problem. I'm not quite sure about what I wrote on fstab, since I just paste the text and made modifications acording to my devices ubication and names. So, here's my fstab:

 ```
                                   

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=d7e8b5c9-e317-4560-8a89-3c46528b76c5 /               ext4    errors=remoun$
# swap was on /dev/sdb5 during installation
UUID=02111bc5-b306-4842-a6c3-496697c8cba3 none            swap    sw           $
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /media/gens/SuperPersonal  ntfs noatime 0 0

```


I've made some probes by the trial &error method, so, from this, I could say the error doesn't really change. It still appears randomly.
Trying to copy any file on Nautilus from that disk is quite impossible, and I get this message:

```
Error while copying "Filename". 
There was an error copying the file into "Foldername" 
Details: 
Error splicing file: Input/output error 
```

I'm not quite sure how to proceed from here, since I have no experience on filesystem or mounting devices. 
I really would thank your help. Thanks in advance.

---

### Post by ajgreeny on 2014-07-05
I'm not sure if it will make any difference but there are a lot of spaces in your file names by the looks of the errors.  Normally both OSs, Windows and Ubuntu can deal with that without a problem, but I just wonder if it could be something to do with this.

Thinking by the seat of my pants here, so ignore me if this is just baloney.

---

### Post by Impavidus on 2014-07-05
In particular, there seems to be a space in "Super Personal" (indicated by the %20). In your fstab it doesn't show that space. That space has to be included there, by way of using an octal escape sequence: "Super\040Personal". Or even better, just don't use a space there. However, I don't think that should lead to I/O errors, just mount errors.

---

### Post by Vladlenin5000 on 2014-07-06
Have you tried that same disk elsewhere? It looks like a hardware issue...

---

### Post by mastablasta on 2014-07-07
looks like it's a dualboot system.

try using checkdisk on the NTFS part of disk.

---

### Post by RedRat on 2014-07-07
I had a similar problem recently with audacious too. All of a sudden it would stop mid-song with an error. I thought that it might be a disk error on my NTFS volume on my FreeAgent 1 TB disk that I have attached via a USB mount. Various attempts to get it to play through that song were to no avail until I began a new playlist. the previous playlist I had up was on that I kept using over and over by simply erasing songs and then adding new ones to the list--this had been going on for several months. I added the same album to the new playlist and it all played through with no problem. You might also want to check out Clementine in Synaptic as a different music player. It has some added features, e.g., internet radio, etc. Might want to try it out.

---

### Post by Habitual on 2014-07-07
Disabling fastboot in Windows 8.x may also be warranted, if so enabled.
fast shutdowns are notoriously unreliable from a Linux perspective.

---


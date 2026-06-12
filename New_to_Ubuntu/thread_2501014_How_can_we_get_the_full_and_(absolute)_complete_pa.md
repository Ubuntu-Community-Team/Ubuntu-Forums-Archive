---
title: "How can we get the full and (absolute) complete path to a file for use in terminal?"
date: 2024-09-19
forum: New to Ubuntu
---

### Post by alsacien on 2024-09-19
good day dear ubuntu experts 


pretty new here - and well - i need your help and advice. 

how to get the absolute File Path in Linux:  i have heard about some different ways to get the absolute file paths in Linux command line.
in fact - i need to get comfortable here - i have to solve several task on my linux - so i need to dive into the use of the console: 

the first task:  How can we get the full and (absolute) complete path to a file for use in terminal?

so i need to find out which method can be applied here:  which ways and Methods do we have which different ways to get the full and absolute file paths in Linux terminal!?

this post is all about to get sure - and to ensure that i am on the right path. 


i heard About several Methods: 

**first method: **we can use the readlink-method: 


```
readlink -f test.txt 

```

well sometimes we just Need to get it installed firstly




a simple example might be like so: 


```
thebutch@deleuz:~$ readlink -f test.txt 
/home/thebutch/sample.txt
thebutch@deleuz:

```

we can use the realpath method also in order to get the full path 


well another appropiate method might be the so called realpath method: - with this command is used for resolving the absolute file names. Among other uses, it can show the full path to a file.


```
realpath test.txt 

```


as a example: can we go like so: 

```


thebutch@deleuz:~$ realpath test.txt 
/home/thebutch/test.txt
thebutch@deleuz:~$

```


and now - here i hmm - get a bit confused:  since my friends told me that here we have something with the simlink: well what does tese Methods have to do with the so called symbolic link Concept: 
background: well i have heard that if we use use it with a so called symbolic link, it will show us even more. it will show us the  the real path of the original file. But how can we  force it to not follow the symbolic link?!


and whats the so called sim link here in fact!? 


```
realpath -s filename - (/in our case text.txt 

```



look Forward to hear from you 






**Background:** well i Need toi find out the full path of a file that is in the download-sector of my Notebook




/Downloads/ubuntu.iso

---

### Post by TheFu on 2024-09-19
I'd use **locate**.
For programs that are located inside my PATH, then I'd use **which**.

If you are trying to do it via a script, things are harder, since you cannot assume that locate is installed or that every program on the system is in a directory that is part of the PATH environment variable.  To get the correct answer, is complicated, but to get a likely good-enough answer, is easy.  Whenever I need the easy answer, I let google remind me.  "find location of file linux bash"  . Mostly, you'll get good enough answers.  IME, for the absolute, correct, path to a file, you'll need to find some answers and test if they are hardlinks or symbolic links to decide if the answer is good enough for your needs.

I don't know what "download-sector" means.  You've lost me on that.  Do you mean ~/Downloads/?   <---- that ~/ is very, very, important.

Do you know that if a path starts with a /, then it is an absolute path, but if it starts with **any** other characters, then it is a relative path.

---

### Post by The Cog on 2024-09-20
I note that in "man readlink" is the line: "Note realpath(1) is the preferred command to use for canonicalization functionality."
I also note that realpath always gives the full canonical path whereas readlink provides a relative path.

> But how can we force it to not follow the symbolic link?! How do you get **what** to not follow a symlink? ls and cp don't follow a symlink without the -L argument.

---

### Post by alsacien on 2024-09-20
TheFu and the The Cog good day - happy to hear form you!!

**first of all**: many thanks for the Reply and for sharing your ideas: 

> I don't know what "download-sector" means. You've lost me on that. Do you mean ~/Downloads/? <---- that ~/ is very, very, important.

yeahh - 
>  note that in "man readlink" is the line: "Note realpath(1) is the preferred command to use for canonicalization functionality."
I also note that realpath always gives the full canonical path whereas readlink provides a relative path.

well thanks alot. 

i am just figuring out which path i have to use. 

well ive got a Iso-File in the Downloads and i want to run the following command: 
```
sudo dd bs=4M if=~/Downloads/_my_linux.iso of=/dev/xyz status=progress && sync
```
look forward to any and all ideas.

have a great day... 

yours Alsacien

---

### Post by The Cog on 2024-09-20
> sudo dd bs=4M if=~/Downloads/_my_linux.iso of=/dev/xyz status=progress && sync
Aha! Now we know what you are trying to do. There are two paths you need to worry about. 

Firstly, **if=~/Downloads/_my_linux.iso** - If that's the name of the ISO file, then fine. Is this bit giving you difficulties?

Secondly, **of=/dev/xyz** - That's clearly wrong. The xyz part needs correcting to refer to whatever device you are trying to write the file to. If you get this wrong you could overwrite your hard disk instead, so care is needed. What kind of device are you trying to write to?
Assuming it's a removable drive, you could try running the command **[FONT=Courier New][COLOR="#0000CD"]lsblk -p | grep -v snap[/COLOR][/FONT]** both with and without the drive connected and look for the difference between the two outputs, the one that appears when you plug the drive in. Probably /dev/sd<something>. Pst the output here if you have any doubts at all.

---

### Post by TheFu on 2024-09-20
I'd use
```
sudo cp    ~/Downloads/_my_linux.iso      /dev/sdX

```myself.
Obvisouly, you need to get the "sdX" part correct.  If a USB device, run 
[LIST]
[*]```
dmesg -w
```
[*]plug in the USB storage, look for the dmesg lines for the drive, note them.
[*]then run that **cp** with the target for the newly connected device.  It will be wiped.
[/LIST]
You can add a **sync** at the end, if you like.

If you don't like cp, you can use any tool that copies bits from A to B.  No need to use dd or some fancy GUI tool if you already understand storage device naming conventions.  ISO files get put onto the full device, not a partition.  That's really all you need to know.  Of course, if you screw up the target device, it can be a really bad day for you and the computer.

---

### Post by alsacien on 2024-09-20
hello dear  Woof - and the Foo 

first of all - many many thanks for the quick reply

its so great to see this awesome forum - and you as the supprter - thanks for encouraging me:  i am willing to write a usb (a flash) stick - with a  ISO... 


your in-depth going help is great!!

well i did the folliwng:


```

1828716544 bytes (1,8 GB, 1,7 GiB) copied, 132 s, 13,9 MB/s
dd: error while writing  to '/dev/sdb1': on this device there is no space left
438+0 records in
437+0 records out
1834647552 bytes (1,8 GB, 1,7 GiB) copied, 132,674 s, 13,8 MB/s
[martin@thecomputer-4243f53 ~]$ 

```

hmm - well i need to check if it went okay !?


can i do this with  one of the following commandas


a,  the lsblk command: 
```
lsblk
```


or b. the fdisk-command: 

```
fdisk -l  or parted -l,
```


hmm - do you think i should try another usb - (flash) stick!? 

which step to take - how to proceed from here..

---

### Post by yancek on 2024-09-20
The error you report in post 7 shows you do not have space free on the device to write the iso.  Is there anything (data) on the device?  If so, using dd will overwrite it.  Is the iso smaller than the size of the device?  What is the device you want to write to shown as?  Is it something like sdb, sdc...?  You need to write to the device not a partition meaning /dev/sdb rather than sdb1.  You posted the output of whatever command you used in your last post but neglected to post the actual command so that's not very useful and that output clearly shows it failed.

---

### Post by alsacien on 2024-09-20
good evening dear Yancek 

many thanks for the quick reply 

> **yancek said:**
> The error you report in post 7 shows you do not have space free on the device to write the iso.  Is there anything (data) on the device?  If so, using dd will overwrite it.  Is the iso smaller than the size of the device?  What is the device you want to write to shown as?  Is it something like sdb, sdc...?  You need to write to the device not a partition meaning /dev/sdb rather than sdb1.  You posted the output of whatever command you used in your last post but neglected to post the actual command so that's not very useful and that output clearly shows it failed.


sdb1 - this is (i am pretty sure- my USB-stick

so in the end i tried the folowing 


```

1834647552 bytes (1,8 GB, 1,7 GiB) copied, 132,674 s, 13,8 MB/s
[martin@thecomputer-4243f53 ~]$ sudo dd bs=4M if=~/Downloads/EOS1.iso of=/dev/sdb1 status=progress && sync
```


hmmm - i try another usb- siick and come back to show what happened

your forum is abslout great - i am happy to be here


[B]
update:  [/B]well - believe it or not  - this is what happens with the next usb-stick


```
[sudo] Passwort für martin: 
1937768448 bytes (1,9 GB, 1,8 GiB) copied, 278 s, 7,0 MB/s 
dd: Fehler beim Schreiben von '/dev/sdb1': Auf dem Gerät ist kein Speicherplatz mehr verfügbar
463+0 records in
462+0 records out
1940422656 bytes (1,9 GB, 1,8 GiB) copied, 346,925 s, 5,6 MB/s
[martin@thecomputer-4243f53 ~]$ 


```


funni - but wait - now i take a huge usb-stick

and - with the dd - it will erase everything - wont it !?

---

### Post by TheFu on 2024-09-20
> **alsacien said:**
> 
sdb1 - this is (i am pretty sure- my USB-stick

...

and - with the dd - it will erase everything - wont it !?

sdb1 is a partition, not the whole flash drive.  The whole drive is /dev/sdb

You **must** write to the whole drive.  Yes, everything on it will be wiped/deleted/gone.  

There's no other way that I know to load an ISO, unless you use something like **Ventoy**.  And if you setup a flash drive with Ventoy, THAT program will wipe the flash drive completely as part of the setup, but the resulting flash drive will have 2 "data" parititions (I think), where you can place data and ISOs into  the partitions.  I don't recall whether ventoy creates the data partitions or just leaves empty space.  I do know that my ventoy flash drive has a FAT32 and ext4 data partitions now.  Ventoy is an intermediate-level tool, so might be best to skip it for now.  OTOH, it is nice to have 15 Linux ISOs on a single Flash drive and be able to boot any of them as needed.   But if you are only using Ubuntu, a single, dedicated, flash drive just for to leave the current release on that you use is smart.  If there are ever boot issues, that flash drive (holding the ISO) is going to be what you need to fix it.


And I'll add the warning again using slightly different words. If you don't really understand storage device file names, best to use a GUI tool that will protect you from yourself.  Rufus is popular.  Etcher is another.

---

### Post by alsacien on 2024-09-20
helllo and good day agian 

many many thanks - i have gone totally wrong and thank God you have corrected me



```
dd: Fehler beim Schreiben von '/dev/sdb1': Auf dem Gerät ist kein Speicherplatz mehr verfügbar
463+0 records in
462+0 records out
1940422656 bytes (1,9 GB, 1,8 GiB) copied, 346,925 s, 5,6 MB/s
[martin@thecomputer-4243f53 ~]$ sudo dd bs=4M if=~/Downloads/EOS1.iso of=/dev/sdb status=progress && sync
[sudo] Passwort für martin: 
2898264064 bytes (2,9 GB, 2,7 GiB) copied, 432 s, 6,7 MB/s 
691+1 records in
691+1 records out
2900897792 bytes (2,9 GB, 2,7 GiB) copied, 517,17 s, 5,6 MB/s
[martin@thecomputer-4243f53 ~]$ 



```


now it looks completely different 

awesome many many thanks to all of you 

your forum is so great:KS

---


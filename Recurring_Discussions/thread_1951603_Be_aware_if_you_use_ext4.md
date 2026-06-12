---
title: "Be aware if you use ext4"
date: 2012-04-02
forum: Recurring Discussions
---

### Post by BertN45 on 2012-04-02
If you are in an environment that makes you system crash often, be aware that the default settings in Ubuntu and most other distros of ext4 will corrupt your files.

Ext4 favored speed over data security, too many speed junkies in Linux. Especially if files are written and then renamed, there is a large chance that data is lost. 

For most application designers the rename seems like a good idea, you write the file and if the system crashes you still have the old version. This approach seems only vulnerable during the rename and that looks like a very short moment in time. 

Unfortunately in ext4 the rename is executed and journalled, while the data still might be partly or completely in the cache in memory and it can take 30-60 seconds before that is written to disk, Hence the high chance of corrupted files. After the crash the new file seems to be there, but its content is corrupt. So with ext4 you will create corrupted files, but you can do it very fast :(  

see:
[http://lwn.net/Articles/322823/](http://lwn.net/Articles/322823/) 

The next changes should make the ext4 file system more secure for your data and the behavior should be almost equal to ext3. I have adapted my ext4 settings as follows, 

[COLOR="Blue"]changing the journalling file structure on disk.

sudo tune2fs -ojournal_data /dev/sda1

and add the bold part to the entry in /etc/fstab as follows,

# / was on /dev/sda1 during installation
UUID=af8c719f-9a9c-473f-881e-d9aad93d6765 / ext4 **data=journal,**errors=remount-ro 0 1
[/COLOR]
I think it is not smart to reduce the reliability of your file system, if you introduce a major new release. I think in countries like mine you loose data and it will take a long time before you realize, what is going on. I remember that I had to remove a lot of music mp3 and wma files that had zero length and that makes me angry. Music that I have lost forever, because by now also my back-up has been corrupted.

**So if you have system crashes or the electricity fails, be aware that ext4 by default will corrupt your files.**

I will go back to ext3.

---

### Post by QIII on 2012-04-02
Three year old "news".

---

### Post by BertN45 on 2012-04-02
Well for me and I am convinced for many others it is new. If I knew, I would not have lost approx. 20 tracks of my music collection.

I should have been warned, when I selected ext4 during install.

For ex window users it surely is completely unexpected and I am sure that Microsoft would not have said: OLD NEWS.

---

### Post by wojox on 2012-04-02
Did you have a question?

---

### Post by RJARRRPCGP on 2012-04-02
Looks FUDish to me, because Ext3 and later IIRC, has journalling on by default.  

(Of course, that's true with FAT32, LOL) 

One of my PCs, which has Debian Squeeze with Ext4, shut down and rebooted because of a loose power cord and I didn't notice file corruption.

---

### Post by 3Miro on 2012-04-02
I have used Linux as a main system since 2008. I switched to ext4, when it was still in beta (9.04). I own multiple machines and I have experience all kinds of power outages, never a single file corruption. Are you sure this is what happened to you?

---

### Post by Dangertux on 2012-04-02
Well... While what the OP is saying is true in some cases, it's unlikely that the case would be realistic for anyone here.

Raise your hand if you're running a pre 2.6.30 kernel and mounting ext4 filesystems...

No seriously more recent kernel versions force fsync() more frequently if they discover particularly long periods of data caching. This doesn't completely fix the problem, as data corruption can still occur on ANY filesystem. That being said I think the vast majority of the burden here lies on developers to develop applications properly to current standards, as opposed to just "doing it the way they used to."

If you want to blame a file system, blame gfs , it's an easy target ;-)

---

### Post by uRock on 2012-04-02
I have had many power failures where I was praying that my data was safe. Upon booting I have always found everything in order. I have had the power fail and my documents, which were being automatically backed up by LibreOffice, were restored to the latest point.

---

### Post by CharlesA on 2012-04-02
> **uRock said:**
> I have had many power failures where I was praying that my data was safe. Upon booting I have always found everything in order. I have had the power fail and my documents, which were being automatically backed up by LibreOffice, were restored to the latest point.
Heh. I had issues with my server a week or so ago where we lost power and the machine would reboot instead of power off on halt, so basically it got forcefully powered off when the UPS battery ran out. No data loss.

---

### Post by BertN45 on 2012-04-02
> **wojox said:**
> Did you have a question?

No only a warning

---

### Post by sammiev on 2012-04-02
I live where the tree line stops and polar bears start and power outages are very often and can last for days. Never had trouble with loosing data to-date. Want to test laptops or desktops... send your equipment here.

---

### Post by BertN45 on 2012-04-02
> **RJARRRPCGP said:**
> Looks FUDish to me, because Ext3 and later IIRC, has journalling on by default.  

(Of course, that's true with FAT32, LOL) 

One of my PCs, which has Debian Squeeze with Ext4, shut down and rebooted because of a loose power cord and I didn't notice file corruption.

Journalling only works when it is done without compromise, ext4 delays the allocation of space for a file to gain speed for some times up to 30-60 seconds, so it is vulnerable during that relative long time, because everything remains in cache.

Well it is all a matter of chance (mathematics). In Europe or the USA you will not notice any problem, because of the stable environment and the reliability of the electricity net. I have over 20 power failures per week. I think for 1 years ext4 is the default now. I had around 20 corrupted audio files, but I had over 1000 power fails during that year. That would mean a chance of 1 in 50, that the file gets corrupted, so in Eurpe or the USA you will not notice it.

I only started investigating when I detected that I lost work for folding@home project. That are jobs running for days and they are check pointing each 5 - 30 minutes. I lost work on my two Ubuntu desktops, but not on my laptop (battery takes over) and not on my last Windows system (ntfs). That project knows that for their work ext3 is more reliable then ext4, so they advice to use ext3.Then I started to investigate and found the problem and all the old discussions about speed against data security (ext4 against ext3). 

So I decide to warn everybody, who lives in developing countries, ext4 might not be the best solution for them.

---

### Post by QIII on 2012-04-02
Are you quite sure that the corruption was due to the power failure per se, or the interruption of a read/write cycle when the power failed, which would likely cause corruption no matter the file system?

---

### Post by yetiman64 on 2012-04-02
> **BertN45 said:**
> Well it is all a matter of chance (mathematics). In Europe or the USA you will not notice any problem, because of the stable environment and the reliability of the electricity net. I have over 20 power failures per week. I think for 1 years ext4 is the default now. I had around 20 corrupted audio files, but I had over 1000 power fails during that year. That would mean a chance of 1 in 50, that the file gets corrupted, so in Eurpe or the USA you will not notice it.

20 power failures / week. Wow, surely any filesystem constantly exposed to that will cop a hiding eventually. **Consider using a Uninterruptable Power Supply Unit if you don't want corruption**. I like the others above that have mentioned this have had many hard power downs, and a few power outages (not as extreme as 20p/week) with no corruption. 

Only time I had any corruption of an ext4 FS was when I hastily hot swapped a laptop drive in an external dock used for a main backup of mine. Took 2 days to repair but got every single file back. The dock was advertised with "Hot Swapable" but it wasn't till later I realized it was primarily designed for use with Windows and Mac (Damn fine print and blurry eyesight - not a good combo).

Really does appear to me the problem is not with the filesystem but your power supply and any corruption could be avoided with a ups unit. Cheers.

---

### Post by BertN45 on 2012-04-03
> **Dangertux said:**
> 
That being said I think the vast majority of the burden here lies on developers to develop applications properly to current standards, as opposed to just "doing it the way they used to."

If you want to blame a file system, blame gfs , it's an easy target ;-)

In this case it is the right target. If you validate the quality of complex software system, you look at performance, structure, but one of the most important thing is transparency and does it work in the way the normal user expects.

The ext4 design completely lacked this last quality. On top of it, it tries to remedy bad programming practices. In the past if I wanted to transfer data between two programs and performance was an issue.  I used shared memory, messaging or pipes. I would never write small files and expect that to be fast. The performance of that bad programming habit is ext4 now trying to improve and solve. To minimize the chance on file corruption for as long as I can remember (40+ years) people have used the open, write ... write, close and rename construct. That construct using the defaults settings in ext4 is punished by increasing the chance of file corruption. That construct works fine in e.g. ext3 and ntfs.

Ext4 is not transparent and does not behave in the way a user expects, so the quality of the designs lack these very important attributes. Pointing to standards that do not forbid it or saying that the programmer should change 40 years old habits shows a certain disdain for the normal user. Besides it requires thousands of programs to be changed just for ext4.

---

### Post by BertN45 on 2012-04-03
> **QIII said:**
> Are you quite sure that the corruption was due to the power failure per se, or the interruption of a read/write cycle when the power failed, which would likely cause corruption no matter the file system?

Yes I am sure, besides a disk has enough energy stored to complete the current sector and to retract the heads. The whole idea of a journalling system is to restore the file to a consistent state. There is always a chance on corruption, but in ext3 and ntfs, it is much smaller then in ext4. In ext3 data and journal on disk are updated each n seconds, default=5. In ext4 the journal is written also each 5 seconds, but the data is sometimes kept in memory for 30 seconds or more.

---

### Post by uRock on 2012-04-03
> **BertN45 said:**
> In this case it is the right target. If you validate the quality of complex software system, you look at performance, structure, but one of the most important thing is transparency and does it work in the way the normal user expects.

The ext4 design completely lacked this last quality. On top of it, it tries to remedy bad programming practices. In the past if I wanted to transfer data between two programs and performance was an issue.  I used shared memory, messaging or pipes. I would never write small files and expect that to be fast. The performance of that bad programming habit is ext4 now trying to improve and solve. To minimize the chance on file corruption for as long as I can remember (40+ years) people have used the open, write ... write, close and rename construct. That construct using the defaults settings in ext4 is punished by increasing the chance of file corruption. That construct works fine in e.g. ext3 and ntfs.

Ext4 is not transparent and does not behave in the way a user expects, so the quality of the designs lack these very important attributes. Pointing to standards that do not forbid it or saying that the programmer should change 40 years old habits shows a certain disdain for the normal user. Besides it requires thousands of programs to be changed just for ext4.
I highly doubt Windows would do any better/worse in your conditions. I have lost data while running Windows and having a power outage. It happens. That is why we back up our work. If power outage is such an issue in your area, then a UPS should be an integral part of your systems.

---

### Post by philinux on 2012-04-03
> **sammiev said:**
> I live where the tree line stops and polar bears start and power outages are very often and can last for days. Never had trouble with loosing data to-date. Want to test laptops or desktops... send your equipment here.

Sheesh you really live in the middle of nowhere, Bet it's beautiful though. Even street view hasn't been there yet. At least you got the mainline railway. How far is it to the nearest "big" town.

Bet there's some good fishing nearby?

ON Topic> I've used ext4 from when it was recommended. I'v had a few hard reboots in between and the odd power failure.

I've not seen anything amiss.

---

### Post by QIII on 2012-04-03
I am entirely unconvinced.

With the number of power outages you describe, I am actually surprised that you have not encountered more file corruption than you have.

You still have not convinced me that your file corruption is any greater than what would be expected using any file system given the circumstances.

Strangely, the loss of only 20 audio tracks seems rather fortunate to me under your electrical infrastructure conditions.

---

### Post by Dangertux on 2012-04-03
> **BertN45 said:**
> In this case it is the right target. If you validate the quality of complex software system, you look at performance, structure, but one of the most important thing is transparency and does it work in the way the normal user expects.

The ext4 design completely lacked this last quality. On top of it, it tries to remedy bad programming practices. In the past if I wanted to transfer data between two programs and performance was an issue.  I used shared memory, messaging or pipes. I would never write small files and expect that to be fast. The performance of that bad programming habit is ext4 now trying to improve and solve. To minimize the chance on file corruption for as long as I can remember (40+ years) people have used the open, write ... write, close and rename construct. That construct using the defaults settings in ext4 is punished by increasing the chance of file corruption. That construct works fine in e.g. ext3 and ntfs.

Ext4 is not transparent and does not behave in the way a user expects, so the quality of the designs lack these very important attributes. Pointing to standards that do not forbid it or saying that the programmer should change 40 years old habits shows a certain disdain for the normal user. Besides it requires thousands of programs to be changed just for ext4.


Well unfortunately, that is sometimes the way of things, and while we're at it, let's look at a more relevant and recent (you know ...Some time in the last 2 years) resource that explains the proper method of insuring data integrity on an ext4 filesystem..

> 
						Unlike ext3, the ext4 file system does not force data to disk on  transaction commit. As such, it takes longer for buffered writes to be  flushed to disk. As with any file system, use data integrity calls such  as fsync() to ensure that data is written to permanent storage.


From : [http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/newfilesys-ext4.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/newfilesys-ext4.html)

Hope this helps.

---

### Post by wolfen69 on 2012-04-03
Meh, not worried. Do backups and get on with your life.

---

### Post by cariboo on 2012-04-03
In the op's original thread here:

[http://ubuntuforums.org/showthread.php?t=1949753&highlight=origami](http://ubuntuforums.org/showthread.php?t=1949753&highlight=origami)

He stated he was running folding-at-home with data being written to the drive every 3 minutes.

Most of the suggestions made in this thread, have already been made in the other thread.

---

### Post by CharlesA on 2012-04-03
> **cariboo907 said:**
> In the op's original thread here:

[http://ubuntuforums.org/showthread.php?t=1949753&highlight=origami](http://ubuntuforums.org/showthread.php?t=1949753&highlight=origami)

He stated he was running folding-at-home with data being written to the drive every 3 minutes.

Most of the suggestions made in this thread, have already been made in the other thread.
Thanks for the link. :)

---

### Post by BertN45 on 2012-04-15
After approx. 10 power fails, I lost work again on the PC with the ext4 default setting, PCs  with ntfs and ext4 mounted with mode=journal survived, more or less according to my expectation.

---

### Post by BrokenKingpin on 2012-04-17
I have been running EXT4 since it was released and I have had no issues... love it.

---


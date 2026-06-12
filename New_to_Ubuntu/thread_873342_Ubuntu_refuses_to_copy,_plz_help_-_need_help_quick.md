---
title: "Ubuntu refuses to copy, plz help - need help quickly"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Syndacate on 2008-07-28
I had to back up a drive, it was NTFS, I backed it up to a folder on my Desktop.

I then formatted the drive via a windows machine into NTFS format, then rebooted in Ubuntu and went to copy everything back onto the drive.

Before I did anything I did a recursive chmod to make sure it didn't run into any problems:

```
sudo chmod -R 777 *
```

Then I went to copy it all back.

```
sudo cp * ~/Desktop/EXTERNAL
```

And it copies for a bit, then I get a ******** of fail:

```
cp: cannot create directory `/home/syndacate/Desktop/EXTERNAL/backup 3a': Input/output error
cp: cannot create directory `/home/syndacate/Desktop/EXTERNAL/batch3': Input/output error
cp: cannot create directory `/home/syndacate/Desktop/EXTERNAL/bcpc cars': Input/output error
cp: cannot create directory `/home/syndacate/Desktop/EXTERNAL/BJPrinter': Input/output error
`~BLANK.ZIP' -> `/home/syndacate/Desktop/EXTERNAL/~BLANK.ZIP'
cp: cannot create regular file `/home/syndacate/Desktop/EXTERNAL/~BLANK.ZIP': Input/output error
`BOB.jpg' -> `/home/syndacate/Desktop/EXTERNAL/BOB.jpg'
```

And it just goes on and on and fails at every single file until it gets to the end.

I need this drive operational tomorrow - I didn't expect Ubuntu to give me any ******** - appears I was most definitely wrong.  In a jam, whatever is the most stable will fail.  I've never seen anything like this.  Content size is approx 17Gb in case that matters.

*Whatever can go wrong, will go wrong, at the worst possible time.*

---

### Post by ajmorris on 2008-07-29
> **Syndacate said:**
> I had to back up a drive, it was NTFS, I backed it up to a folder on my Desktop.
 
I then formatted the drive via a windows machine into NTFS format, then rebooted in Ubuntu and went to copy everything back onto the drive.
 
Before I did anything I did a recursive chmod to make sure it didn't run into any problems:
 
```
sudo chmod -R 777 *
```
 
Then I went to copy it all back.
 
```
sudo cp * ~/Desktop/EXTERNAL
```
 
And it copies for a bit, then I get a ******** of fail:
 
```
cp: cannot create directory `/home/syndacate/Desktop/EXTERNAL/backup 3a': Input/output error
cp: cannot create directory `/home/syndacate/Desktop/EXTERNAL/batch3': Input/output error
cp: cannot create directory `/home/syndacate/Desktop/EXTERNAL/bcpc cars': Input/output error
cp: cannot create directory `/home/syndacate/Desktop/EXTERNAL/BJPrinter': Input/output error
`~BLANK.ZIP' -> `/home/syndacate/Desktop/EXTERNAL/~BLANK.ZIP'
cp: cannot create regular file `/home/syndacate/Desktop/EXTERNAL/~BLANK.ZIP': Input/output error
`BOB.jpg' -> `/home/syndacate/Desktop/EXTERNAL/BOB.jpg'
```
 
And it just goes on and on and fails at every single file until it gets to the end.
 
I need this drive operational tomorrow - I didn't expect Ubuntu to give me any ******** - appears I was most definitely wrong. In a jam, whatever is the most stable will fail. I've never seen anything like this. Content size is approx 17Gb in case that matters.
 
*Whatever can go wrong, will go wrong, at the worst possible time.*
 
hi there,
to mount your windows partition, are you using the ntfs kernel module, or the ntfs-3g drivers? (post /etc/fstab if you dont know and that ntfs drive is mounted automatically)
 
AJ

---

### Post by Syndacate on 2008-07-29
> **ajmorris said:**
> hi there,
to mount your windows partition, are you using the ntfs kernel module, or the ntfs-3g drivers? (post /etc/fstab if you dont know and that ntfs drive is mounted automatically)
 
AJ

I mounted it manually.

I did it the same way I've done it many times in the past with my NTFS formatted externals.

```
sudo mount -t ntfs-3g /dev/sde1 ~/Desktop/EXT
```

---

### Post by vanadium on 2008-07-29
You need the -r option to copy directories recursively. For "mirrorring" directory trees, I tend to prefer the rsync command

rsync -av <sourcedir> <destinationdir>

(<destinationdir> must exist)

---

### Post by Syndacate on 2008-07-29
> **vanadium said:**
> You need the -r option to copy directories recursively. For "mirrorring" directory trees, I tend to prefer the rsync command

rsync -av <sourcedir> <destinationdir>

(<destinationdir> must exist)

I did use the -r flag on some of them I think, but either way.

Should it matter?

Those directories I posted are 1st level directories, they're not inside something else, it's having trouble creating the directories and files.

I suppose I'll try it with rsync though.

---

### Post by decoherence on 2008-07-29
mount the drive and try making a few new files and using it in other ways. if you can't, i'd start replacing components.

also, since you've already wiped the drive once, maybe wipe it again as ext2/3 format. if it works that way, it pretty much rules out hardware as an issue.

io errors SHOULD indicate a hardware problem or else there are some very serious bugs (or something very weird about your system)

---

### Post by Syndacate on 2008-07-30
> **decoherence said:**
> mount the drive and try making a few new files and using it in other ways. if you can't, i'd start replacing components.

also, since you've already wiped the drive once, maybe wipe it again as ext2/3 format. if it works that way, it pretty much rules out hardware as an issue.

io errors SHOULD indicate a hardware problem or else there are some very serious bugs (or something very weird about your system)

That's very possible, the hard disk was loud, but it wasn't having any issues when I backed it up.

I ended up formatting it with Windows, but Windows froze when I tried copying all 17Gb at once onto the hard drive, so I copied it little by little and eventually got it all onto the disk.

Not exactly a fan of what i had to do, but desperate times call for desperate measures, I had to get that hard disk back to the guy today.

If the io errors you said, should indicate a hardware problem, that's very possible, the hard drive was very loud, and was probably on its way out the door.

This incident made me ask a question, maybe you have the answer, not looking to make a new thread over something so trivial...but does the ability to write to NTFS mean it can put/copy files to it, or just write the NTFS file system?

---

### Post by decoherence on 2008-07-30
Yes, it can put/copy files to an NTFS filesystem as well as create the filesystem.

cheers,

---

### Post by bodhi.zazen on 2008-07-30
> **decoherence said:**
> Yes, it can put/copy files to an NTFS filesystem as well as create the filesystem.

cheers,

You should not copy to a FAT/NTFS partition for backing up as these file systems do not preserve permissions.

For backup you should consider tar or using the -p flag :

```
cp -p source destination
```

Better would be to use tar, compress the archive. You can then put the archive onto a ntfs partition if you wish .

[uhelp]community/BackupYourSystem[/uhelp]

[http://www.linuxguide.it/commands_list.php?Commands_by_Argument:Backup](http://www.linuxguide.it/commands_list.php?Commands_by_Argument:Backup)

---

### Post by Syndacate on 2008-07-30
> **bodhi.zazen said:**
> You should not copy to a FAT/NTFS partition for backing up as these file systems do not preserve permissions.

For backup you should consider tar or using the -p flag :

```
cp -p source destination
```

Better would be to use tar, compress the archive. You can then put the archive onto a ntfs partition if you wish .

[uhelp]community/BackupYourSystem[/uhelp]

[http://www.linuxguide.it/commands_list.php?Commands_by_Argument:Backup](http://www.linuxguide.it/commands_list.php?Commands_by_Argument:Backup)

It all depends on your needs.  This was a windows guy, with a windows hard disk, I didn't need to back up permissions.  I keep all my storage parts NTFS, so I can access them from anywhere.

---


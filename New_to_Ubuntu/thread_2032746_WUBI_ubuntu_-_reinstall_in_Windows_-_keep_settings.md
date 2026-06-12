---
title: "WUBI /ubuntu - reinstall in Windows - keep settings?"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by abexman on 2012-07-24
Posted here but have not gotten any help. Mabye my question is too newbie....
[http://ubuntuforums.org/showthread.php?p=12118596](http://ubuntuforums.org/showthread.php?p=12118596)

If I reinstall Wubi within Windows 7, would that completely wipe out my previous install? I know root.disk gets overwritten. But if I reinstall and then use my previously backed up (backed up now, in unbootable state) root.disk file. Or would that likely just result in me continuing to not be able to boot? In other words does this root.disk likely contain my corrupted boot configuration?

---

### Post by bcbc on 2012-07-24
The root.disk contains the whole Ubuntu install. So yes, if you reinstall and replace the new one with your damaged one there will be no change from what you see today.

Maybe you should try to get some help from the person whose tutorial you followed by posting in that Howto thread or sending a PM to the original poster of the HowTo to visit your support thread.

Also your boot repair failed to show any Ubuntu files... instead it showed a corrupt partition so maybe that has something to do with it:
```
sdc6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Mounting failed:   ntfs-3g-mount: mount failed: Device or resource busy
ntfs-3g-mount: mount failed: Device or resource busy
```

---

### Post by abexman on 2012-07-25
Thank you. I think I am just going to install a separate Ubuntu partition and uninstall Wubi. I don't have much to save in Wubi anyway. 

I did have Windows XP on this machine previously, will need to investigate.

If I want to make sure my Ubuntu can boot safely, is there a section of boot.disk that only concerns booting that I can backup alone for later re-install? Most of my files are on separate hard drives anyway.

---

### Post by bcbc on 2012-07-25
> **abexman said:**
> If I want to make sure my Ubuntu can boot safely, is there a section of boot.disk that only concerns booting that I can backup alone for later re-install? Most of my files are on separate hard drives anyway.

No. If you can fix your partition and find the root.disk you can copy your own data off it... that's about the only useful bits you can backup. Reinstalling ubuntu is trivial - installing and setting up programs you use, and restoring data is not.

If you find your root.disk you can probably repair it as well, but that depends on a lot of things. And if you have nothing on there then it's easier to reinstall. 

I'd say your first task is what's on that damaged partition - is it visible from Windows and can you recover your data. Otherwise you might want to investigate tools like testdisk or photorec.

---

### Post by abexman on 2012-07-25
Yes I can access all my files via Windows. I guess I'll just grab what I need and do a reinstall of Ubuntu without Wubi.

---

### Post by Paqman on 2012-07-25
If you back up the whole contents of your /home you could simply paste that back into your new systems and all your settings would be restored.

By default all your settings and preferences live in hidden folders under /home/username. Go to your home folder and hit Ctrl-H to make them visible. They're mostly just text files, so can be backed up and restored easily.

If you have multiple users it's possible you would get a problem with permissions after doing this, but the easy solution is to force ownership of all files in the home folder to yourself. You can do this from the permissions tab of the folder properties dialog (right click > properties) or by doing the following in a terminal:
```

sudo chown -R username:username ~

```
(~ is just a shorthand for /home/username btw)

---

### Post by bcbc on 2012-07-25
If you can see the root.disk in windows then you can open it readonly from windows using this: [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/)

I'm still puzzled why the bootinfoscript can't see that partition though.

And if you can mount the root.disk then, yes, backing up /home as paqman suggested will work. But I guess you'd have to see the partition to do that.

---


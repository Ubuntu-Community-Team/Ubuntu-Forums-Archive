---
title: "copying files to flash"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by frog3764 on 2013-12-30
Happy New Year to the Group - I am running a dual boot system with W7 and 12.4 LTS.  Since Ubuntu is the default boot system, that is where most of my work is done.   In Windows (before Ubuntu) when I copied files from my desk top to my 1GB flash to transfer to a second pc, the process is very fast and takes only a few seconds depending on the size of the file of course.  This morning I downloaded a 16.2 MB exe Windows file from Ubuntu to be copied to my 1 GB flash to be transferred to my other pc.  This copy took many minutes to complete.  I know from experience that in Windows that would only take a few seconds.  It's the same for zip files.  Very fast in Windows but Ubuntu takes many minutes longer to do.  I get a progress bar window showing the progress of the file being copied and it seems to stop part way.  I usually just close it and find that the files were copied anyway, but again, this process is terribly slow compared to Windows.  Almost every day I have several files I have downloaded and need to copy to my other pc.   All input here is appreciated.

Jim

---

### Post by electrohandyman501 on 2013-12-30
With Win7 you can have 'write caching' enabled that will cause file transfer to appear to be faster than it actually is. That can put you at risk of data loss if you disconnect the flash drive before the actual transfer if fully completed as it runs in the backround after your popup window closes.

You can search the forum for 'write cache' and check it out and explore your options with Ubuntu.

---

### Post by Bucky Ball on 2013-12-30
The PCs are on the same network? You could try a file transfer using FTP of some other means. I use Filezilla myself. ;)

---

### Post by frog3764 on 2013-12-31
Hey Bucky Ball - Thanks for your input.  I keep the second pc "internet disabled" account that's for my games.  So I find the copying is much faster than enabling the other pc and then disabling it again.  Sometimes during the day I might have to do it again, so copying is the best way.

Jim
Happy New Year

---

### Post by Impavidus on 2013-12-31
As far as I know, both systems can write to usb drives in two ways: write directly (aka synchronous) or cache the write, only guaranteeing all data has been written when you unmount or sync or savely remove the drive or something like that (aka asynchronous). I thought that the default for Windows was to write immediately and for Linux to cache. However, the default may have changed, I don't really know.

Still, in whatever way the files are copied to the usb drive, several minutes seems excessively long for just 16 MB.

You write you have the problem with both exe and zip files. Are there any file types that don't give you this problem? The file copy process doesn't care about file types, so that would be peculiar and suggest something is going on besides copying the files. Did you install a virus check to protect your off-line Windows pc? Just a wild guess.

---

### Post by frog3764 on 2013-12-31
Hey Impavidus - Thanks for your input.  The only files I usually copy are zip, exe, and some jpegs.  No matter what the file type, it takes Ubuntu a much longer time to copy to the flash drive.  Sometimes the file size will be several hundred megabytes too, or maybe several files that size, so this delay is very annoying.  So if the problem is a write cache issue, as suggested by electrohandyman501, how might I solve this with Ubuntu?  I did search here but didn't find anything concerning this problem.  

Jim

---

### Post by sudodus on 2013-12-31
What file system is there on the flash drive?

Usually linux works fast with FAT32 and linux file systems (ext2, ext3, ext4), but slower with NTFS, because it is a proprietary file system of Microsoft, and the NTFS driver of linux is not as efficient as that of Windows.

---

### Post by frog3764 on 2013-12-31
Happy New Year Sudodus - This flash when in Windows, the last time I noticed the properties, was Fat32.  But ubuntu properties show it as msdos.  The flash is used constantly on both systems and back and fourth.

---

### Post by sudodus on 2013-12-31
Happy New Year frog3764 :-)

Right now I have no more guess why Ubuntu is slower than Windows.

Maybe you can test with different tools. One good tool for copying is rsync (and it can also show the speed).

See ```
man rsync
```

---


---
title: "Backing Up My Ubuntu OS"
date: 2015-04-12
forum: New to Ubuntu
---

### Post by RobGoss on 2015-04-12
Hello I was wondering how I can backup my Ubuntu os for safe keeping. I have an external hard drive with 320 GB of storage.
I used it on windows and it works OK but I try to connect it to my Ubuntu OS and it seems a but confusing because the files look so different.

Question? If I'm using this external storage device with Ubuntu do I also need to load the CD that came with the external hard drive in order to get it working.

My next question would be if I do need the software disk that can with the drive how would I load it up using Ubuntu?

Thanks so much

---

### Post by yancek on 2015-04-12
Have you created a partition with a Linux filesystem on it on the external drive which you can use to backup?
The CD that came with the storage device is probably designed to only work with windows and I doubt it will do anything from Ubuntu.  Boot Ubuntu and open a terminal.  Run this command and post the output here with the external drive plugged in:  sudo fdisk -l(Lower Case Letter L in the command)


Also, could you be more specific about what you mean by 'the files look so different'.  In order to write to the drive, you would need to use sudo or change ownership or permissions for the mount point.

---

### Post by RobGoss on 2015-04-12
I don't believe I've created a partition and I'm not really sure how to do this.

What I mean as far as the files looking different is they're not not labeled as they are in windows, example I folders on this ex drive labeled old pictures and when I view the file using Ubuntu I don't see them. All I see is files like this, COV 0030. ER and I can view anything.

Thanks for any help on this matter.

---

### Post by Vladlenin5000 on 2015-04-12
The pevious post is generally correct but goes beyond what a newbie understands and it doesn't address other simple things...
First of all, the reason why it looks different it's because in Ubuntu you're using a different file manager software and different file type associations and different icons. So, yes, it must look quite different. The important point, however, is whether or not you can a) read all of your contents and b) write to the same drive, in order to use it as an external storage.
The drive is most likely formatted with NTFS. Such file system, albeit proprietary, is fully supported in Ubuntu. 
The CD is most likely useless, as explained before, but the good news is you shouldn't need any additional software.

Please post the results of the aforementioned command just to be sure.

---

### Post by user_of_gnomes on 2015-04-12
> **robert159 said:**
> I don't believe I've created a partition and I'm not really sure how to do this.

What I mean as far as the files looking different is they're not not labeled as they are in windows, example I folders on this ex drive labeled old pictures and when I view the file using Ubuntu I don't see them. All I see is files like this, COV 0030. ER and I can view anything.

Thanks for any help on this matter.

What exactly are you seeing on that hard drive? Ubuntu should be able to read your external hard drive but it sounds like there might be a problem with the file system.

---

### Post by RobGoss on 2015-04-12
> **user_of_gnomes said:**
> What exactly are you seeing on that hard drive? Ubuntu should be able to read your external hard drive but it sounds like there might be a problem with the file system.


Hello I'm seeing files with the following extensions, **Pad 0783.NG and Cov 0004, ER**
there're a lot of files like this but I can't view them. I do have a number of pics on this drive and I'm assuming that's them...

---

### Post by user_of_gnomes on 2015-04-12
Can you access these files under Windows?

---

### Post by RobGoss on 2015-04-12
> **user_of_gnomes said:**
> Can you access these files under Windows?

Yes with Windows I have no problem, I know things are a bit different with Linux but I can't figure out what's the problem. I'm assuming you mean access the file when I use Windows correct?

---

### Post by user_of_gnomes on 2015-04-13
```

```> **robert159 said:**
> Yes with Windows I have no problem, I know things are a bit different with Linux but I can't figure out what's the problem. I'm assuming you mean access the file when I use Windows correct?

Did you use the software under Windows to encrypt your hard drive?

---

### Post by RobGoss on 2015-04-13
I just password protected the drive nothing else.

Someone also suggested I use Clonezilla to backup my data have you ever use this software before? It looks simple enough. I was reading the documentation and it says you run the software from a live media or use stick and save the iso file of your system to a external hard drive.

---

### Post by Vladlenin5000 on 2015-04-13
> **robert159 said:**
> I just password protected the drive nothing else.

Yeah, like that isn't bad enough. Whether you use Windows native tools or third-party's, it's ENCRYPTION we're talking about...
Now you need to open the password protected files in Windows and backup somewhere else without password. You can't read it in Linux (or Mac) otherwise.

---

### Post by user_of_gnomes on 2015-04-13
> **robert159 said:**
> I just password protected the drive nothing else.

Someone also suggested I use Clonezilla to backup my data have you ever use this software before? It looks simple enough. I was reading the documentation and it says you run the software from a live media or use stick and save the iso file of your system to a external hard drive.

You should use [dd]("https://wiki.archlinux.org/index.php/Disk_cloning") instead of clonezilla, it's much more simple.

Anyhow, you encrypted the drive with propietary software so you're probably not going to be able to access the data from within Linux.

---


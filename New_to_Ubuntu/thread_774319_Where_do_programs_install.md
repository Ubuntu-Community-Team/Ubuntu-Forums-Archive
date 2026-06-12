---
title: "Where do programs install?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by styphon on 2008-04-29
Hi,

I had a search of the forums and the 7.10 documentation (couldn't seem to find 8.04 docs yet, can't expect everything) and I've not been able to solve my query.

I'm a long time Windows user and obviously programs install to program files by default and I know how to customise this. What I don't know is how to do this in Ubuntu. Where do programs install to? Also, can you customise where they go to (without mass editing of config files, if it is config files then I'll learn later on)?

Thanks in advance,

---

### Post by sayakb on 2008-04-29
Check the /usr/bin and /usr/share/appname for executables/config files.

---

### Post by Monicker on 2008-04-29
> **styphon said:**
> Hi,

I had a search of the forums and the 7.10 documentation (couldn't seem to find 8.04 docs yet, can't expect everything) and I've not been able to solve my query.

I'm a long time Windows user and obviously programs install to program files by default and I know how to customise this. What I don't know is how to do this in Ubuntu. Where do programs install to? Also, can you customise where they go to (without mass editing of config files, if it is config files then I'll learn later on)?

Thanks in advance,

Most programs are /usr/bin, /bin, or /usr/local/bin.  Programs which require root privileges will be in /usr/sbin/, /sbin, or /usr/local/sbin.  Changing where a progam gets installed would require modification of the Ubuntu packages.

To find out where a particular program is located, from a terminal:
```
which programname
```

---

### Post by styphon on 2008-04-29
Excellent. Thanks a lot guys. I guess I'll leave them to install in the default locations for now :lolflag:.

---

### Post by |{urse on 2008-04-29
Don't forget /sbin, usr/local/sbin  and /usr/sbin 

> Linux discriminates between 'normal' executables and those used for system maintenance and/or administrative tasks. The latter reside either here or - the less important ones - in /usr/sbin. Locally installed system administration programs should be placed into /usr/local/sbin.

---

### Post by PeterJS on 2008-04-29
> **styphon said:**
> Hi,

I had a search of the forums and the 7.10 documentation (couldn't seem to find 8.04 docs yet, can't expect everything) and I've not been able to solve my query.

I'm a long time Windows user and obviously programs install to program files by default and I know how to customise this. What I don't know is how to do this in Ubuntu. Where do programs install to? Also, can you customise where they go to (without mass editing of config files, if it is config files then I'll learn later on)?

Thanks in advance,

In linux files are arranged according to function rather than what program they are associated with. So in windows everything GIMP related will be in c:\Program Files\Gimp. In linux however GIMP will be in multiple places, gimp iself will be at /usr/bin/gimp, but will have libraries in /usr/lib/, and icons and other resources in /usr/share, and probably some files other places as well. The [FHS](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) defines where and why things are in a linux file system.

As for moving things apt/synaptic don't support that as putting things in non-standard locations, as this isn't very helpful. If you put programs in a non-standard location the system won't know where to look for them, the same for libraries. You can take a little bit more liberties with shared resources like icons, but having them in standard locations makes them easier to use and more likely to "just work".

---

### Post by styphon on 2008-04-29
> **PeterJS said:**
> In linux files are arranged according to function rather than what program they are associated with. So in windows everything GIMP related will be in c:\Program Files\Gimp. In linux however GIMP will be in multiple places, gimp iself will be at /usr/bin/gimp, but will have libraries in /usr/lib/, and icons and other resources in /usr/share, and probably some files other places as well. The [FHS](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) defines where and why things are in a linux file system.

As for moving things apt/synaptic don't support that as putting things in non-standard locations, as this isn't very helpful. If you put programs in a non-standard location the system won't know where to look for them, the same for libraries. You can take a little bit more liberties with shared resources like icons, but having them in standard locations makes them easier to use and more likely to "just work".

Thank you. That FHS read was very helpful.

With regards to moving the location of programs, from within Windows it was beneficial for me to have them on a separate partition, along with games and documents on further partitions. I found that this helped performance and allowed me to spread things over other drives. Would I see similar benefits in Linux, and is it even possible, to do this? I know /home can be mounted on a separate partition, but what about programs?

---

### Post by ukripper on 2008-04-29
For big programs such as eclipse, check your /opt directory

---

### Post by aheckler on 2008-04-29
It is possible to make partitions for almost any directory under /. However, the benefit of doing so for directories other than /home is almost nil, at least in my experience. Also, you can check out the directory structure link in my sig for a shorter explanation of what lives where.

---

### Post by PeterJS on 2008-04-29
> **styphon said:**
> Thank you. That FHS read was very helpful.

With regards to moving the location of programs, from within Windows it was beneficial for me to have them on a separate partition, along with games and documents on further partitions. I found that this helped performance and allowed me to spread things over other drives. Would I see similar benefits in Linux, and is it even possible, to do this? I know /home can be mounted on a separate partition, but what about programs?

That's actually one of the defining separations between the primary hierarchy at /, and the secondary hierarchy at /usr/. / must absolutely be local to the machine for it to boot, but /usr/ can safely be mounted as a remote file share (possibly even read only and shared between multiple machines) via nfs or some other method. That said there's no reason that / and /usr/ can't be on separate disks. I don't know how much of a performance gain there would be, but it's certainly possible.

---

### Post by styphon on 2008-04-29
> **aheckler said:**
> It is possible to make partitions for almost any directory under /. However, the benefit of doing so for directories other than /home is almost nil, at least in my experience. Also, you can check out the directory structure link in my sig for a shorter explanation of what lives where.

Thanks, I've bookmarked that link for referral. 

> **PeterJS said:**
> That's actually one of the defining separations between the primary hierarchy at /, and the secondary hierarchy at /usr/. / must absolutely be local to the machine for it to boot, but /usr/ can safely be mounted as a remote file share (possibly even read only and shared between multiple machines) via nfs or some other method. That said there's no reason that / and /usr/ can't be on separate disks. I don't know how much of a performance gain there would be, but it's certainly possible.

OK, I was just thinking size wise for partitions because I normally install over several HDD's with either 36GB or 74GB (I like my Raptors). I don't know what it's like with space on Linux (excluding /home) but I know it got tight in Windows. Eventually I intend to either find a Linux alt program, or Wine if I can't use the Linux alt program. It might cause some spacing issues on a 36GB partition.

---

### Post by forrestcupp on 2008-04-29
Basically, you just need to forget everything you know about how Windows works.  Linux file hierarchies are completely different, and unless you fully understand what you're doing, you shouldn't mess with how things install.

Along with the **which** command given earlier, which tells you where the binary is, you can use the **locate** command.
```
locate firefox
```will tell you every directory that anything that has to do with firefox is installed.  When you try that command, you'll understand why you need to just leave things the way they are and be happy that it works.

---

### Post by styphon on 2008-04-29
> **forrestcupp said:**
> Basically, you just need to forget everything you know about how Windows works.  Linux file hierarchies are completely different, and unless you fully understand what you're doing, you shouldn't mess with how things install.

Along with the **which** command given earlier, which tells you where the binary is, you can use the **locate** command.
```
locate firefox
```will tell you every directory that anything that has to do with firefox is installed.  When you try that command, you'll understand why you need to just leave things the way they are and be happy that it works.

lol, yea, I see what you mean with the whole "Leave things the way they are". I didn't intend on editing or changing where they install, I just wanted to know if it was possible. And with the partitions I'm running in dual-boot so I was just thinking about how to do it and what I can do with Linux. There's also the part of me that just has to know how it works, which was inquisitive about the file structure of Linux.

---

### Post by |{urse on 2008-04-29
wouldnt it be possible to group binaries and libs etc. all in one directory with the correct symlinks (ln -s) created? If so tht'd solve one of current problems making repackageable .debs. So i could keep copies of all original files in one dir that the prog is actually running in and repackage a prog as needed? Or is there already a tool to do this?

---

### Post by forrestcupp on 2008-04-29
> **styphon said:**
> There's also the part of me that just has to know how it works, which was inquisitive about the file structure of Linux.That's a great thing.  That inquisitiveness will help you learn a lot.  The thing about Linux is that different distros have their own way of doing a file hierarchy.  Like in Ubuntu, the most common place to put a program's binary file is /usr/bin.  But other distros put them in /usr/local/bin.  That's one reason for incompatibilities.

> **|{urse said:**
> wouldnt it be possible to group binaries and libs etc. all in one directory with the correct symlinks (ln -s) created? If so tht'd solve one of current problems making repackageable .debs. So i could keep copies of all original files in one dir that the prog is actually running in and repackage a prog as needed? Or is there already a tool to do this?That would be a major pain beyond what it is worth.  You can find an archive of every deb you have downloaded and installed with apt in 
/var/cache/apt/archives.  Unless you have removed them.

---

### Post by |{urse on 2008-04-30
I did not know that! very nice thank you! I was more leaning toward being able to make changes to the programs and repackage for identical hardware configurations but still very helpful to know.

---


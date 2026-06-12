---
title: "Ext Driver for Windows or NTFS driver for Ubuntu"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by JoyceBabu on 2008-05-01
I recently installed Ubuntu 8.04 on my system after two days struggle. Ofcourse, the problem was not with Ubuntu or Windows, but with me :). Anyways, now that I have installed Ubuntu, I am full of doubts. Can someone plz clarify me on these?
My first doubt is about the drives shared by both Ubuntu and Windows. Can someone plz suggest me which of the following is best option?
* Format the drives as Ext3 and use Ext2ifs or Ext2fsd on windows
* Format as NTFS and use NTFS-3g on Ubuntu
* Format as Fat 32
Since I am new to the Linux Operating System, I won't be completely switching to Ubuntu suddenly.

My second question is about installing a development LAMP server on Ubuntu. Can someone plz tell me which all packages I should install. I am confused by all those packages having the term 'apache' in it :confused:.

Thanks in  advance.

---

### Post by Paqman on 2008-05-01
Hardy can read/write to NTFS, so that'd be the easiest option. The only downside is you'll get fragmentation, so it would pay to occasionally boot in Win and run a defrag.

There are ext3 tools for Windows like [ext2ifs](http://www.fs-driver.org/), but i've not used them a great deal. They seem stable enough.

---

### Post by PeterJS on 2008-05-01
> **JoyceBabu said:**
> I recently installed Ubuntu 8.04 on my system after two days struggle. Ofcourse, the problem was not with Ubuntu or Windows, but with me :). Anyways, now that I have installed Ubuntu, I am full of doubts. Can someone plz clarify me on these?
My first doubt is about the drives shared by both Ubuntu and Windows. Can someone plz suggest me which of the following is best option?
* Format the drives as Ext3 and use Ext2ifs or Ext2fsd on windows
* Format as NTFS and use NTFS-3g on Ubuntu
* Format as Fat 32
Since I am new to the Linux Operating System, I won't be completely switching to Ubuntu suddenly.

I would go with NTFS, ntfs write support is good enough that you won't damage the disk, the only reason I'd shy away from ext3 under windows is I've heard it's not so good about permissions and ownership. And FAT32 would be terrible under both, don't bother.

> 
My second question is about installing a development LAMP server on Ubuntu. Can someone plz tell me which all packages I should install. I am confused by all those packages having the term 'apache' in it :confused:.

Thanks in  advance.

In Synaptic Package Manager (System > Administration > Synaptic Package Manager), in the edit menu there is an option to mark packages by task. One of those tasks it LAMP server, if you select that the system will handle getting all the right packages installed (this is just a GUI frontend to the tasksel program Ubuntu server uses to setup tasks and services).

---

### Post by JoyceBabu on 2008-05-01
Thanks a lot. That was really quick.

In that case, I am going to reformat the shared drives back to NTFS. Will try the LAMP option too. Thanks.

BTW, While installing, I have set mount points for the shared drives as /Media/G and /Media/H(because I was trying ext2ifs at that time). Will reformatting cause any trouble?

---

### Post by Hospadar on 2008-05-01
I use ntfs in linux and the ext drivers for windows, I've never had any corruption or instability issues with either, but I'd prefer to format something ntfs if I was going to use it in both os's.

I do this for two reasons,
One: ubuntu comes with ntfs already, it's easier to do that downloading installing and restarting windows
Two: if you ever use that drive in another machine (like let's say you need to plug it into someone else's machine for recovery), either that machine will be a windows machine which you may or may not have priviledges to install stuff on, and you won't be able to use the win ext drivers, or it will be a linux machine that will read ntfs just fine.

So it's really a personal preference thing, and as mentioned above, you will need to use windows to defrag now and then, but I don't think that's a super big deal.

---

### Post by stchman on 2008-05-01
> **JoyceBabu said:**
> I recently installed Ubuntu 8.04 on my system after two days struggle. Ofcourse, the problem was not with Ubuntu or Windows, but with me :). Anyways, now that I have installed Ubuntu, I am full of doubts. Can someone plz clarify me on these?
My first doubt is about the drives shared by both Ubuntu and Windows. Can someone plz suggest me which of the following is best option?
* Format the drives as Ext3 and use Ext2ifs or Ext2fsd on windows
* Format as NTFS and use NTFS-3g on Ubuntu
* Format as Fat 32
Since I am new to the Linux Operating System, I won't be completely switching to Ubuntu suddenly.

My second question is about installing a development LAMP server on Ubuntu. Can someone plz tell me which all packages I should install. I am confused by all those packages having the term 'apache' in it :confused:.

Thanks in  advance.

I would go with an NTFS shared partition using ntfs-3g.

Leave the Windows system drive alone.  You can mount it with read only no write.  Like wise in Windows you can install Diskinternals that gives you read access to EXT3 partitions.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Follow my tutorial on partition mounting.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by MongooseCage on 2008-05-01
Yeah, ntfs-3g FTW. FAT32 sucks its terribly slow and ext3 isn't perfect. 

BTW, how do you start a thread? I haven't been involved in a forum before.

---

### Post by JoyceBabu on 2008-05-01
> **MongooseCage said:**
> BTW, how do you start a thread? I haven't been involved in a forum before.
Visit any forum, say [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") (current forum) and click the [New Thread]("http://ubuntuforums.org/newthread.php?do=newthread&f=326") Button.

---


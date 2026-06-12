---
title: "Ubuntu won't let me use my partition (I'm confused as hell here)"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Thre365ive on 2008-05-29
Hi, everybody. I just recently installed Ubuntu on my laptop. I was using Vista and just got sick of MS. I've got it installed just fine (using it now, actually) and got rid of Vista. The problem now, though, is that I can't use the partition that Vista was on. I've went through GParted and formatted it to an ext3 primary partition (primary was the only choice I had.) It automatically names it as /dev/sda1. I've got Linux installed on another partition, but I'm not 100% sure which one. Right now I've got /dev/sda4 as an extended partition, /dev/sda5 as an ext2 partition /dev/sda6 as an ext3 partition (says the mount point is / - I'm assuming that this is where Linux is?) and /dev/sda7 as swap space.

As it stands now it looks great in GParted, but I can't write anything to /dev/sda1 and that's 3/4 of my HDD. If I didn't explain this very well, I'm sorry. I'm decent with MSWindows, but I'm a total n00b when it comes to anything else. If you ask some questions, I should be able to answer them, although I may need some guidance. I could also get a screenshot showing what's going on if that'll help.

Thanks in advance for any answers.

---

### Post by wolfen69 on 2008-05-29
it is a permissions problem, being that it is ext3. that is why i always make my storage drives/partitions Fat32 or NTFS. then any OS will be able to read/write without any hassles.

maybe someone else will have another answer to get it going. then again, you can always change that partition to another file system.

---

### Post by drs305 on 2008-05-29
Please post the results of 
```
mount
```
```
cat /etc/fstab
```
```
sudo blkid
```

---

### Post by Thre365ive on 2008-05-29
So if I just format it to a Fat32, it should work just fine?

---

### Post by Thre365ive on 2008-05-29
> **drs305 said:**
> Please post the results of 
```
mount
```
```
cat /etc/fstab
```
```
sudo blkid
```

And exactly what will this do? Sorry if I seem untrusting, but I'm a little paranoid since I don't know what's up with Linux yet. I'd also like to get to the point where I don't have to ask questions anymore, and to do that I'm gonna have to understand the commands better.

---

### Post by drs305 on 2008-05-29
> **Thre365ive said:**
> And exactly what will this do? Sorry if I seem untrusting, but I'm a little paranoid since I don't know what's up with Linux yet. I'd also like to get to the point where I don't have to ask questions anymore, and to do that I'm gonna have to understand the commands better.

These commands will show us how each partition is formatted, who is allowed to read and write to them, and the blkid shows the UUIDs. I usually ask for that just because formatting sometimes changes these and they become unavailable. 

None of these commands will do anything but provide information; they won't alter anything.

It's okay to ask... ;-)

By the way, if you aren't familiar with the forum, you would post the results between CODE delimiters, which you get by clicking the # symbol as you type your message.

---

### Post by drs305 on 2008-05-29
I'm about to log out, but from what you stated above (and without seeing fstab), your linux system is indeed mounted, as you surmised, on sda6. We call "/" root in linux.

You said you wiped out Vista, so this is a pure linux machine? You can leave it all formatted to ext 2 or 3. There are programs now that will allow windows to view ext2 and ext3 formats and linux apps that will let you view windows formats.

Since sda1 is the one you can't access, check that the uuid in the results of the blkid command and the uuid in fstab for /dev/sda1 match. Find the /dev/sda1 entry. You should see something like the following to ensure you have the proper permissions. On my machine, /media/data is my mountpoint. The mount point you have must physically exist. If it doesn't you need to make it and change ownership to yourself (others can give you the command for that):

```

# Entry for /dev/sda1 :
UUID=0a82b5fc-6e0f-47f9-a63d-47c627006e17 **/media/data ext3 defaults,user 0 2**
```



Finally, I'll recommend a couple of web sites that have great information on linux. The first is an individual's efforts that covers most of the major issues you are likely to have quetions about regarding initial linux installation and setup. The second is the ubuntu hardy wiki:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

Got to run. Someone will help you out. Good luck, and welcome to ubuntu.

---

### Post by Thre365ive on 2008-05-29
I ran your commands and now I have a $500 paperweight. I ran mount and cat /etc/fstab then it shut down immediately. Now I can't even turn my PC on. WTF happened?

---

### Post by Aesir09 on 2008-05-29
mistake to remove windows.

you'll never know when you'll need it.

well at least for me (student and gamer)

---

### Post by Dougie187 on 2008-05-29
Wow.... If you ran those commands and it f'ed up your computer then you need to check your spelling of them. Because none of them would mess up your computer. If you want to check, just google the name of the commands.

or when you get back to linux, type
man *command*

You should explain your new problem more. Also, if you are complaining that you cant use your computer, you can always reinstall it. And you can recover the files using the live cd.

Remember, don't bite the hand that feeds you.

---

### Post by Thre365ive on 2008-05-29
Yeah, I'm a jackass. I'm on a laptop, and apparently one of my dogs had pulled my power cord out of the surge protector. It was a very weird coincidence. So I'll run the commands again and post the results. I'll just need a couple minutes to switch PCs.

---

### Post by Dougie187 on 2008-05-29
Heh, ok. Glad to find out your laptop isn't complete garbage now.

---

### Post by Thre365ive on 2008-05-29
Ok, it's not letting me copy/paste the results, so I'm gonna have to type it out. Which part do you guys need? I'm assuming everything between the fstab and the end?

And does this board use UBB code? Such as [ b ] bold [ /b ] or [ quote ] quotes [ /quote ]? If so, would the code I need just be code *content* /code?

---

### Post by Dougie187 on 2008-05-29
It uses [ CODE ] and [/ CODE ]

I would try to post everything. If you want to copy and paste try using ctrl+insert for copy and shift+insert for paste as well.

---

### Post by Thre365ive on 2008-05-29
```
dunner@36fuckin5:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/dunner/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dunner)
dunner@36fuckin5:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7387c491-e57d-495d-808d-114ebb5049d8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=22746ebc-c26b-4fef-8264-2dfe5e237e28 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
dunner@36fuckin5:~$ sudo blkid
[sudo] password for dunner: 
/dev/sda1: UUID="767f70b3-d7a7-4f4f-9032-a93bd01fffac" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="e8744242-c8eb-4fd2-83f1-ab3ed657de4e" TYPE="ext2" 
/dev/sda6: UUID="7387c491-e57d-495d-808d-114ebb5049d8" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="22746ebc-c26b-4fef-8264-2dfe5e237e28" 
```

That's what I got. Thanks for the tip on the copy/paste. Also, if you'd want to help on the interpretation of this, or a link to an explanation, that'd be awesome. I'd love to get to the point where I answer more questions than I ask.

---

### Post by Thre365ive on 2008-05-29
Are we allowed to bump threads? If not, I won't do this anymore.

---

### Post by Dougie187 on 2008-05-29
You can bump. I think the ideal times for a bump is about 1 per day or something like that. 

To explain the commands,
mount, gives informaion about what is mounted, where and with what permissions.

cat simply prints out a copy of the file, you cated /etc/fstab which is the file that gives information to the OS about what it should mount as the file system.

and then blkid (i am not very familar with this command so this is really just a guess) gives your physical drives, partitions included, along with their UUIDs

---

### Post by Thre365ive on 2008-05-29
Awesome. Thanks. I believe I've got it working (switched it over to Fat32), but there are a couple partitions that I don't quite understand, don't think I need, and I don't know how to get rid of them. Like I have one that's about 74 mb that just has a "Lost & Found" on it that I can't read.

My goal here is to have one partition to hold Linux, one for swap space and one for my media/programs.

If need be, I can run another fstab to show you what I've changed.

---

### Post by drs305 on 2008-05-29
I've returned and I have to admit the first entry that I read when I got back was that running the commands I gave you trashed your system. What a sick feeling.  Anyway, what is it that you need now?

Since you are messing with partitions, I would highly recommend making a separate home partition, but you can do it later if you wish. Just if you are still thinking of changing around the partitions, now would be a good time to consider it. The advantages and how to do it are described here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

So where were we?

Added: You asked about codes for bold, etc. When you open a post, the commom symbols are available at the top of the entry. B, I, U, etc.

You mentioned changing fstab. Fstab merely points to places on the partitions and assigns things such as who owns the mounted partition, etc. It doesn't physically change anything. Did you mean you changed the uuid's to match?

The Lost+Found is just a folder created on each partition to handle broken bits of information that the file system might use to recover corrupted data.

---

### Post by Thre365ive on 2008-05-29
Well, right now, I've switched my drive (the one that's around 60 gigs) to a Fat32, which is letting me run it. But I still can't make a usable ext3 or ext2 partition from it, which is what I'd like to eventually do. I've got a couple partitions that I don't quite understand, and I'd like to get rid of them if I can. Fstab gave me this:

```
dunner@36fuckin5:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/dunner/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dunner)
/dev/sda1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda5 on /media/disk-1 type ext2 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)
dunner@36fuckin5:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7387c491-e57d-495d-808d-114ebb5049d8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=22746ebc-c26b-4fef-8264-2dfe5e237e28 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
dunner@36fuckin5:~$ sudo blkid
[sudo] password for dunner: 
/dev/sda1: UUID="483F-0075" TYPE="vfat" 
/dev/sda5: UUID="e8744242-c8eb-4fd2-83f1-ab3ed657de4e" TYPE="ext2" 
/dev/sda6: UUID="7387c491-e57d-495d-808d-114ebb5049d8" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="22746ebc-c26b-4fef-8264-2dfe5e237e28" 
/dev/sda2: UUID="ec3feca1-a800-4c25-b1ee-24a7c97b63a8" TYPE="ext3"
```

And thanks for the tips on the coding. It's exactly how I'm used to with other BBSes, which is nice.

I didn't change anything in fstab. I'm not 100% sure what a UUID even is.

---

### Post by drs305 on 2008-05-29
Are you familiar with gparted? Nevermind, I just reread your first post. It's on the LiveCD and the SystemRescueCD, which I strongly recommend you make at some point ( [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) )

You can see your disk usage with the following command:
```
df -Th
```

And just to summarize (more perhaps for our benefit):
sda1 = 60GB fat32
sda2 = ? ext 3
sda6 = home
sda7 = swap

Is it possible you still have a windows recovery partition on the computer? And am I correct that you don't want or need any vestiges of windows on this machine?

---

### Post by Thre365ive on 2008-05-29
I've been working with GParted all day. 

Another problem is that my right-click somehow got disabled during all this. I don't remember doing anything to disable it, nor do I remember screwing up any commands. I don't know what's up there.

If you'd like, I could get a screenshot of what GParted's looking like right now.

---

### Post by Thre365ive on 2008-05-29
> **drs305 said:**
> Are you familiar with gparted? That is the usual method of partitioning in linux.

You can see your disk usage with the following command:
```
df -Th
```

And just to summarize (more perhaps for our benefit):
sda1 = 60GB fat32
sda6 = home
sda7 = swap

So these are the essentials? I'd like to get it down to just the essentials and add everything extra to sda1.

---

### Post by Thre365ive on 2008-05-29
> Is it possible you still have a windows recovery partition on the computer? And am I correct that you don't want or need any vestiges of windows on this machine?

It is very possible. I really don't know what the other ones are for.

And you're correct - I want as little as possible to do with Microsoft.

---

### Post by drs305 on 2008-05-29
> **Thre365ive said:**
> So these are the essentials? I'd like to get it down to just the essentials and add everything extra to sda1.

Yes. Your root ( / ) and home are currently on sda6 and your swap is on sda7. Those are the only 2 you need. Everything else can either be combined into sda6 (root) or better yet, as you planned,  made into a data partition. Of course, any vestiges of windows or the windows recovery partitions will be removed and unrecoverable.

Moving and resizing always involve some risk of data loss, so if you have somewhere to copy your valuable files you should do so before continuing with gparted.

---

### Post by Thre365ive on 2008-05-29
Cool, that's what I was wanting to do anyway. The problem, though, is that it won't let me do anything with my other partitions. For example, in GParted, I click on /dev/sda2 (which has a set of keys beside it, not sure what that means) and I get no options that light up (such as delete or move/resize) to change anything and I can't right click on it.

I guess what I really need to do is to combine sda1, sda2, sda4, sda5 and sda8 (which I've just created as a Fat32) into one partition on sda1.

And any idea about the lack of a right-click option? It's not just in GParted, it's all of Linux that's doing it.

---

### Post by drs305 on 2008-05-29
> **Thre365ive said:**
> Cool, that's what I was wanting to do anyway. The problem, though, is that it won't let me do anything with my other partitions. For example, in GParted, I click on /dev/sda2 (which has a set of keys beside it, not sure what that means) and I get no options that light up (such as delete or move/resize) to change anything and I can't right click on it.

I guess what I really need to do is to combine sda1, sda2, sda4, sda5 and sda8 (which I've just created as a Fat32) into one partition on sda1.

And any idea about the lack of a right-click option? It's not just in GParted, it's all of Linux that's doing it.

The only thing I can think of for the right click is to go to System, Preferences, Mouse and see if there is something obvious there. You dog didn't unplug it, did he (sorry - couldn't resist). 

As far a gparted, I know sometimes people forget to highlight/select the partition graphic at the top before trying to do something and gparted won't allow anything to happen until they do. You might post a picture of what you see.

---

### Post by Thre365ive on 2008-05-29
Lol, no dog this time. I've got a touchpad. ;) I've got everything that's not replacable on sda6, so I'm not worried bout losing any data.

[Here's the screenshot.](http://i113.photobucket.com/albums/n240/36fuckin5/Screenshot.png)

I realized that I had them mounted, so I unmounted them and it gave me some options, but I still can't delete sda5, which I'd like to. It says to unmount any logical partitions with numbers higher than 5.  Also, when I delete sda1 and sda8 (both Fat32) they make seperate unallocated space. How could I combine them?

---

### Post by drs305 on 2008-05-29
Here is my recommendation:

Start a new thread, entitled Partition Advice or something like that. Explain that linux is currently mounted on sda6 and swap is on sda7. State that you would like to create 3 partitions, with sda1 as root if possible while retaining the files, sda2 as a data partition. I don't know where the swap would be best. You will get some pretty good answers from people a lot better equipped to handle partitioning questions than I am.

Good luck, and welcome to ubuntu.

---

### Post by Thre365ive on 2008-05-29
Ehh, not quite what I wanted to hear, but I appreciate you acknowledging your limits instead of just wasting both of our time. I guess I'll get another thread up now.

---


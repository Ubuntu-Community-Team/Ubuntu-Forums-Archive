---
title: "Fat32 mounting problem in 8.04..fstab editing"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Dissel on 2008-05-12
Hi,

I want to mount 2 fat32 partition.....i,e **/dev/sda11** to **/media/sda11** and **/dev/sda12** to **/media/sda12**

& when I edit my /etc/fstab with this line "**/dev/sda11 /media/sda11 vfat uid=1000,gid=1000,umask=0000 0 0**" A message appear telling 'You have no enough previllage to mount this volume'.

I forget to assign mount point during installation so everytime (After bootup) I need to click to those Fat32 volume and then it mount...It is a bit irritating.

So can anyone please direct me the exact line which i put in the fstab and solve my problem.

HDD stat @ Gparted
[IMG]http://i130.photobucket.com/albums/p266/dissel_2007/gpated.png[/IMG]


Here is the Fstab :-



[IMG]http://i130.photobucket.com/albums/p266/dissel_2007/fstab-1.png[/IMG]


Here is the Fdisk -l


[IMG]http://i130.photobucket.com/albums/p266/dissel_2007/fdiskl.png[/IMG]


Thanks In Advnce.

---

### Post by skymera on 2008-05-12
You can mount the volumes with sudo.

```
 sudo mount /dev/<device> /media/whatever 
```

---

### Post by Dissel on 2008-05-12
^^^Thanks for replying.

Got that, It didn't require any cmd, those volume can be mounted just 2 click ahead.



1st I backup the fstab the file using cp /etc/fstab /etc/fstab.bak

2nd I edit the fstab by using :- sudo gedit /etc/fstab.

& when I edit my /etc/fstab and put this line "**/dev/sda11 /media/sda11 vfat uid=1000,gid=1000,umask=0000 0 0**" A message appear telling like this '**You have not enough previllage to mount this volume**'.

Any help ?

When I first use Ubuntu i,e Ubuntu 6.10 the above line/edit worked well without any problem.

I want to use fstab way, So It can automatically mount every time without need any command/mouse click.

---

### Post by bubba_169 on 2008-05-12
You need to add the option "user" in fstab on the lines for your FAT drives. This should let anyone without root privelages mount that drive ... in theory :)

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html") is a very helpful site when in your situation

---

### Post by Dissel on 2008-05-12
^^^
From where can you please elaborate ?

Or can you please share the command / necessary steps how to do that ?

Any link will be helpful.

Thanks in advance.

---

### Post by Thanoulis on 2008-05-12
You can also make the mountpoint available to you:
```
sudo chmod 770 <the full path of the mountpoint>
```

---

### Post by bubba_169 on 2008-05-12
The link I gave should explain all but all I mean is when editing your fstab in gedit, under the <options> column you need to add a "user" in there...

Here is an example fstab line that might work for you, try commenting out your current sda11 line and pasting this below it...

```
/dev/sda11 /media/sda11 vfat defaults,user,auto 0 0
```

---

### Post by Dissel on 2008-05-12
thanks all for replying here.....
Thanks a million to the bubba_169......it worked for me.

use chmod command in terminal,but it not work for me....may be I don't know how to use it.


what I did after the guidence took from you people.

For making the mount point.
> 
sudo mkdir /media/sda11
sudo mkdir /media/sda12


then fstab editing
> 
/dev/sda11 /media/sda11 vfat defaults,user,auto 0 0
/dev/sda12 /media/sda12 vfat defaults,user,auto 0 0


Now it worked like a charm.....:guitar::guitar::guitar:

---

### Post by Dissel on 2008-05-14
[COLOR="Red"][SIZE="5"]Please Help.......[/SIZE][/COLOR]

**Now the above two fat32 partition is read only for me and the owner is root**.
In my PC I am the only user....

So **How can I make it Write enable or what are the necessary steps/Command to do that ?**
As far as I know fat32 partitions came by default read/write enable.

Here is Permission tab:-

[IMG]http://i130.photobucket.com/albums/p266/dissel_2007/permission.png[/IMG]

Here is the new fstab :--

[IMG]http://i130.photobucket.com/albums/p266/dissel_2007/newfstab.png[/IMG]

---

### Post by Dissel on 2008-05-14
I tried "rw" "users" syntax,but it not worked.....Please help...
Thanks in advance.

---

### Post by oedha on 2008-05-14
what if sudo chmod -R 777 /media/sda11

or go to [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Dissel on 2008-05-14
^^^^
Execute your command in terminal,but there is no effect,Should I restart ?

According to fellow member bubba_169's procedure in [**post #7**]("http://http://ubuntuforums.org/showpost.php?p=4940011&postcount=7") mounting was successful and automatic....but Today I realized that I don't have the permission to write in the partition...coz the owner is root.

**My only question how I can enable write permission of those 2 Fat32 volume ?**

I read the link given from the tuxfiles website where they clearly stated that "*[SIZE="2"]defaults -- Uses the default options that are rw, suid, dev, exec, auto, nouser, and async[/SIZE]*."

But It seems not worked for me.

---

### Post by oedha on 2008-05-14
fat32 usually easy to be handled.....
can you post the output of ls -lu /media ?

---

### Post by Dissel on 2008-05-14
Here is my ls -lu /media.

[IMG]http://i130.photobucket.com/albums/p266/dissel_2007/ls-lu.png[/IMG]

---

### Post by oedha on 2008-05-14
where ???

---

### Post by Dissel on 2008-05-14
^^^You mean ls -lu /media/sda11 ?
or what ?

I can't get it....I thought it was a command at terminal.

---

### Post by mandrill on 2008-05-14
This will explain it all.....
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Dissel on 2008-05-14
^^^^
did this but no result.Still the fat32 vol are write disabled.

> /dev/sda11 /media/sda11 vfat defaults,user,auto,fmask=0177,dmask=0077,uid=1000 0 0
/dev/sda12 /media/sda12 vfat defaults,user,auto,fmask=0177,dmask=0077,uid=1000 0 0

---

### Post by Stefan Stryjecki on 2008-05-14
Hi Dissel. I had the same problem. This is the fstab line working for me:

> /dev/sda2	/media/DANE	vfat	rw,users,uid=1000,umask=022,noatime	0 0

Of course substitute the disk and the mounting point with the ones you need.

---

### Post by Dissel on 2008-05-14
@Stefan Stryjecki,

Thanks it worked for me.

Now fstab entry look like this.

> /dev/sda11 /media/sda11 vfat rw,users,uid=1000,umask=022,noatime 0 0
/dev/sda12 /media/sda12 vfat rw,users,uid=1000,umask=022,noatime 0 0

---

### Post by Stefan Stryjecki on 2008-05-14
Hey. I'm glad it worked. Click on the little star in the right bottom corner of my post, if you would - this way there will be proof that for once I helped somebody ;)

---


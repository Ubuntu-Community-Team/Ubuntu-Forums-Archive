---
title: "gparted problem in Ubuntu 18.04 LiveUSB Session"
date: 2018-09-30
forum: New to Ubuntu
---

### Post by merlinmagic2018 on 2018-09-30
So the oldest thread was from 2017 in the top google results when searching   " gparted can' resize ntfs "  

Or something like that.... maybe I wasn<t specific enough in my research

But here is the problem.

LiveUSB session  --------> 

terminal  ------------>  sudo gparted 

can't recognize partition ( from windows 7 ntfs partition )

so ------------>   mkdir   windows
                      sudo mount /dev/sda2    ( the windows partition )   /home/ubuntu/windows
                      cd windows
                      ls  

WOW ! It's there !!!! It's alive !!!! lol

ok

now ------------ >   sudo gparted
                        
now , partition is there, recognized, but locked for resizing because it is, obviously, mounted 

so i quit gparted first ( otherwise can't unmount it and that's the next logical step right ! )

and then  ------------ >  sudo umount /dev/sda2

ok it works. it's not there anymore in ~/windows

so let's try again

--------------------- >   sudo gparted

................. doh .

Still not recognized .

Ok . What do I do ???

how can I resize a windows 7 ntfs partition WITHOUT using another tool or windows tools .........

I want this to work with gparted

logically duh

so please, don't give me the old 2010 to 2017 answers.

There has to be a fix for this. 

Or then, it IS a bug.

Thank you for your time !

---

### Post by wildmanne39 on 2018-09-30
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by merlinmagic2018 on 2018-09-30
while I wait, i'll just go resize within windows itself........ windows 1  ,  Ubuntu 0   ........... haha

but I just prefer Ubuntu and gparted .

Let's find a fix !!


..... moved to new to ubuntu....... ok then i'll just go here 

[https://github.com/GNOME/gparted](https://github.com/GNOME/gparted)

thx for the help

---

### Post by merlinmagic2018 on 2018-09-30
or should I say here

[https://github.com/MerlinMagic2018/gparted](https://github.com/MerlinMagic2018/gparted)

---

### Post by wildmanne39 on 2018-09-30
Hello, I am not an expert in the matter but I am pretty sure that all resizing of partitions of windows have to be done in windows not because of a bug in Ubuntu software but because of windows.

---

### Post by oldfred on 2018-10-01
Usually gparted will resize NTFS, if it does not need chkdsk, nor is hibernated. And fast start up in Windows 8 or 10 is also hibernation. Also you cannot have Windows proprietary dynamic partitions. 
But there are occasions where users have had issues with gparted and resizing Windows partitions. 

So we suggest using Windows tools for Windows & Linux tools for Linux. Or use Windows to resize NTFS partition.

---

### Post by yancek on 2018-10-01
I would also suggest using windows tools to modify a windows partition based on my experience.  The last time I used a Linux tool (Parted Magic) to resize my windows was unbootable.  So now I resize windows partitions with their Disk Management tool and run chkdsk after rebooting to verify it still boots.

 > I want this to work with gparted

What you and I 'want' isn't going to make it happen. It will depend on the developers/programmers at microsoft and the developers/programmers of GParted.  This isn't a 'problem' with Ubuntu or GParted, it's just better to use windows tools for windows and Linux tools for Linux.  Gparted and other tools often work for these tasks, if it doesn't use the tools created specifically for the purpose.

---


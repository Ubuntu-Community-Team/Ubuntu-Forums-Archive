---
title: "Please help me!! Everythings gone..."
date: 2008-08-19
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-08-19
someone please help 

my 'my documents' on my external hard drive has emptied - nothing, just an empty folder

thats EVERYTHING of mine gone - I keep all my work and files in that folder on my external...

my GCSE coursework - due in in 2weeks has gone.. all 40 pages - everything.

PLEASE can someone help me find out where its gone - or at least how - im desperate...

im going to post all of my recent terminal commands incase they help.

PLEASE any suggestions!


[COLOR="Red"]**------------------------------> _SKIP TO POST #55 FOR THE LATEST DEVELOPMENT/PROBLEM - HELP REQUIRED - *BIG TIME!* CHEERS_**[/COLOR]

---

### Post by littlepr on 2008-08-19
> **phantomjoker said:**
> someone please help 

my 'my documents' on my external hard drive has emptied - nothing, just an empty folder

thats EVERYTHING of mine gone - I keep all my work and files in that folder on my external...

my GCSE coursework - due in in 2weeks has gone.. all 40 pages - everything.

PLEASE can someone help me find out where its gone - or at least how - im desperate...

im going to post all of my recent terminal commands incase they help.

PLEASE any suggestions!


I hope you didn't perform a format on the external or type this on the terminal window:

rm -rf  /my documents folder

---

### Post by finer recliner on 2008-08-19
was there a hidden file called ".Trash-<username>" added to your external harddrive? is there anything in there?

when did this happen?

what else is missing?

what did you recently install?

---

### Post by foska on 2008-08-19
> **phantomjoker said:**
> someone please help 

my 'my documents' on my external hard drive has emptied - nothing, just an empty folder

thats EVERYTHING of mine gone - I keep all my work and files in that folder on my external...

my GCSE coursework - due in in 2weeks has gone.. all 40 pages - everything.

PLEASE can someone help me find out where its gone - or at least how - im desperate...

im going to post all of my recent terminal commands incase they help.

PLEASE any suggestions!


I wonder if this is a joke!!!!!!  If his name is anything to go by....

---

### Post by phantomjoker on 2008-08-19
ok, heres all my recent terminal commands (in reverse order)

```

glib-config failed
sudo apt-get install libglib1.2-dev
 ./configure
cd cinepaint-0.22-1
./config
 install /cinepaint-0.22-1
 install /cinepaint
 install --help
install -cinepaint
./configure
 iwconfig
sudo /etc/init.d/networking restart
sudo iwconfig wlan0 rate 54M
 lsmod | grep ndiswrapper
 sudo sh wirelessfix.sh
cd bcmwl5
 lsmod | grep ndiswrapper
sudo rmmod ndiswrapper
cd/~
sudo rmmod ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo ndiswrapper -i bcmwl5.inf
cd bcmwl5
sudo rmmod ndiswrapper
 sudo gedit wirelessfix.sh
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo ndiswrapper -i bcmwl5
 cd bcmwl5
unzip bcmwl5.zip
wget http://home.nc.rr.com/thehinnants/stuff/drivers/bcmwl5.zip
sudo ndiswrapper -r bcmwl5
ndiswrapper -l
gksu gedit /etc/modules
 sudo rm /etc/modprobe.d/blacklist-bcm43
gksu gedit /etc/network/interfaces
sudo ndiswrapper -i bcmwl5.inf
cabextract sp33008.exe
sudo apt-get install cabextract
cd ndis_temp
mv sp33008.exe ndis_temp
mkdir ndis_temp
 wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
gksu gedit /etc/modprobe.d/blacklist-bcm43
sudo modprobe ndiswrapper
sudo depmod -a
 sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 
 sudo hdparm -B 200 -S 240 -M 254 /dev/sdb1
df -Th | grep dev
gksudo gedit /etc/rc.local
iwconfig
sudo /etc/init.d/networking restart
gksudo gedit /etc/rc.local
iwconfig
sudo /etc/init.d/networking restart
gksudo gedit /etc/rc.local
iwconfig
sudo /etc/init.d/networking restart
gksudo gedit /etc/rc.local
iwconfig
gksudo gedit /etc/rc.local
 sudo update-initramfs -u
sudo rm -rf /etc/modprobe.d/blacklist-bcm43
gksudo gedit /etc/rc.local
sudo iwconfig wlan0 rate auto
sudo update-initramfs -u
 gksu gedit /etc/modprobe.d/blacklist-bcm43
 hdparm -B 200 -S 240 -M 254 /dev/sdb1
 df -Th | grep dev
lsmod | grep bcm
 lspci 
```

(theres more - but I think this happened after i typed in code this far back)

---

### Post by suprfish on 2008-08-19
As posted above, check for a .Trash folder on the external hard drive. What were you doing when this happened?  What format is the hard drive?

> **foska said:**
> I wonder if this is a joke!!!!!!  If his name is anything to go by....

That is hardly constructive.

---

### Post by phantomjoker on 2008-08-19
PLEASE dont say this is a joke! please.... come on...

um, happened within the last 48 hours - I recently saved a file to that folder, and so I know everything was there.

everything else on my external is ok...

---

### Post by theyranos on 2008-08-19
Assuming you're not joking, I've had some luck in the distant past recovering mysteriously-gone files with this: [http://www.student.dtu.dk/~s042078/magicrescue/](http://www.student.dtu.dk/~s042078/magicrescue/)

And, magicrescue is in Universe, so you can 

apt-get install magicrescue

---

### Post by phantomjoker on 2008-08-19
im searching for a '.trash' file/folder now...

---

### Post by phantomjoker on 2008-08-19
recently i have tried to install cinepaint... but nothing else. a few updates, but nothing that looked malicious.

I have also not downloaded any files so - i don't think that could be it...

---

### Post by suprfish on 2008-08-19
> **phantomjoker said:**
> im searching for a '.trash' file/folder now...

It should be located on your ext hd named .Trash-Username (or .Username-Trash, can't remember).

---

### Post by phantomjoker on 2008-08-19
installing magic rescue.

---

### Post by phantomjoker on 2008-08-19
my hard drive just unmounted itself!...

---

### Post by phantomjoker on 2008-08-19
how do i use magicrescue - its not in my applications...

---

### Post by djxcon on 2008-08-19
You did mention that this was an external drive so... Something similar has happened to me.  First try the recommendations in the post and then consider the following:  

Were you writing something to the external drive and then unplugged, unmounted, etc, before the file was done being written?  If so, I have hosed up an external drive myself by unplugging a drive before it was safe to do so.  In the past, I had to mount the external to a Windows partition and then I could see my data.  If you have a Windows computer, try that instead.

---

### Post by suprfish on 2008-08-19
What format is the hd? It could be crashing- any funky noises coming from it? What is the manufacturer? Do you use it often?

---

### Post by phantomjoker on 2008-08-19
suprfish - i use it for everything... my internal memory is small so i save everything to external... the only noises coming from it is the sound of it spinning... i cant remember what make or type!

---

### Post by phantomjoker on 2008-08-19
i did recently transfer documents off my external to my mobile... and the files came over all screwed up on my phone.. so i might have pulled it out to early.. but i did unmount my mobile first so...

---

### Post by phantomjoker on 2008-08-19
please keep helping, im doing a reboot to see if i can remount my harddrive.

please help

thankyou

---

### Post by suprfish on 2008-08-19
> **phantomjoker said:**
> how do i use magicrescue - its not in my applications...

[http://www.linux.com/feature/126525](http://www.linux.com/feature/126525)

---

### Post by finer recliner on 2008-08-19
try plugging the external drive into a windows machine. is it possible that you MOVED your documents to your phone, instead of COPY?

---

### Post by phantomjoker on 2008-08-19
no - i only copied a few files from my external - from ANOTHER folder, so my docs was never touched....

---

### Post by theyranos on 2008-08-19
Two questions:

Is the other stuff on the external drive still there? (Folders besides "My Documents")

If not, is the partition still there? (typing **sudo fdisk -l** from a terminal with the drive plugged in can answer this question)

---

### Post by djxcon on 2008-08-19
Do you have another computer with Windows installed that you can try?

---

### Post by phantomjoker on 2008-08-19
yes, i can access all the other folders and files on the external.

i will try it on a windows now...

---

### Post by phantomjoker on 2008-08-19
it might sound strange - but is there any way of finding out whether it has been deleted?

like a registry of all recent delete actions?

---

### Post by nothingspecial on 2008-08-19
Like other people have said - whilst browsing the folder called /media/disk (or whatever your drive`s called) press ctrl + H. This will show any hidden files on it.
Is there one called .trash?
Is your stuff in there?

---

### Post by phantomjoker on 2008-08-19
its not appearing in windows. And no - i've looked for all the hidden files and folders, nothing!

---

### Post by phantomjoker on 2008-08-19
in windows when i try and open my documents - on the external - it says 

My documents is not accesable

The file or directory in corrupt or unreadable




I no this isn't a windows forum but if ANYONE knows of a windows based program to try and restore it - i would forever love!! PLEASE :S

---

### Post by nothingspecial on 2008-08-19
If your drive is ntfs, in Ubuntu -


```

sudo apt-get install ntfsprogs
```

Then
```


sudo ntfsfix /dev/where your drive is
```

You can check where your drive is using

```

sudo fdisk -l
```

---

### Post by phantomjoker on 2008-08-19
how do i find out what type of external i have?

also - what does that do?

thank you

---

### Post by nothingspecial on 2008-08-19
If I type ```
sudo fdisk -l
``` I get 



```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6edfd38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30d73ab4
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6edfd38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30d73ab4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c937cb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c937cb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS
```


My external drives are /dev/sdb
and /dev/sdc
As you can see both are 500.1 gb in size.
They are both HPFS/NTFS

/dev/sda is my internal hard drive of 120 gb

---

### Post by phantomjoker on 2008-08-19
i rebooted with my external plugged in - and switched on - and got this messege

> Network manager: <info> caught termination signal
Network manager: <debug> [lots of numbers.lots more numbers] nm_print_open_socks(): open sockets
list:
Network manager: <debug> [lots of numbers.lots more numbers] nm_print_open_socks(): open sockets
List: Done
Network manager: <info> Deactivating device wlan0
Network manager: <WARN> nm_hal_status_change_assertion 'cb_data->data->dbus connection' failed
Network manager: <WARN> nm_hal_status_change_assertion 'cb_data->data->dbus connection' failed

Then it froze - or just stopped - then i rebooted, but turned my external OFF before, and it started up fine?!

---

### Post by phantomjoker on 2008-08-19
i'll have to tell you my output in a minute - my external is plugged into my windows computer.

it says it the folder with the missing contents is corrupt?!

---

### Post by phantomjoker on 2008-08-19
```
 mckenzie@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13681367

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        2432     9767520   83  Linux
/dev/sda3            2433        7297    39078112+   5  Extended
/dev/sda5            2433        2494      497983+  82  Linux swap / Solaris
/dev/sda6            2495        7297    38580066   83  Linux

Disk /dev/sdc: 1014 MB, 1014497280 bytes
65 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0x6f737bb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         953      990704    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(967, 64, 32) logical=(952, 39, 32)

[COLOR="Red"]Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ae28609

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS[/COLOR]

```

red writing is my external - its NTFS

---

### Post by Canis familiaris on 2008-08-19
I am not really sure of your problem but the following link may help:

[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by theyranos on 2008-08-19
It might've been trying to fsck the drive while it was stopped. Run ```
sudo fsck -r /dev/sdb1
```  That should give you a beter idea of what's wrong, and it might even repair the problem. 

If that can't find/fix the problem, the first two commands nothingspecial suggested in [this post](http://ubuntuforums.org/showpost.php?p=5622625&postcount=29) will install some ntfs-specific file system tools and run a scan with those tools, respectively. (Replace **/dev/where your drive is** in nothingspecial's code with **/dev/sdb1**)

---

### Post by phantomjoker on 2008-08-19
theyranos - i got the following

mckenzie@ubuntu:~$ sudo fsck -r /dev/sdb1
[sudo] password for mckenzie: 
fsck 1.40.8 (13-Mar-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdb1
mckenzie@ubuntu:~$

---

### Post by phantomjoker on 2008-08-19
also followed nothingspecial's idea - got the following 

> mckenzie@ubuntu:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
The following packages were automatically installed and are no longer required:
  libtagc0 libavahi1.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mckenzie@ubuntu:~$ sudo ntfsfix /dev/sdb1
Refusing to operate on read-write mounted device /dev/sdb1.
mckenzie@ubuntu:~$ 


---

### Post by theyranos on 2008-08-19
Try ntfsfix again but with the drive unmounted:

```

sudo umount /dev/sdb1
sudo ntfsfix /dev/sdb1

```

---

### Post by phantomjoker on 2008-08-19
i have followed the instructions on the site 

[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/]("http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/")

and it is finding and recovering files - whether they are right - i don't know - estimated time till completion - 1h40mins

---

### Post by phantomjoker on 2008-08-19
25h till completion :|

---

### Post by suprfish on 2008-08-19
> **phantomjoker said:**
> 25h till completion :|

It has gone up from 1h 40m to 25h?

---

### Post by phantomjoker on 2008-08-19
yes... but it has gone down now to 2h49mins        ugh!

---

### Post by phantomjoker on 2008-08-20
None of the above has worked - i just tried to 'ntfsfix...' but it came up with

Volume is corrupt. You should run chkdsk.

so i did 

chkdsk --help

and got

bash: chkdsk: command not found


any ideas? please!

---

### Post by Canis familiaris on 2008-08-20
> **phantomjoker said:**
> None of the above has worked - i just tried to 'ntfsfix...' but it came up with

Volume is corrupt. You should run chkdsk.

so i did 

chkdsk --help

and got

bash: chkdsk: command not found


any ideas? please!

Did you get this message in Ubuntu?
chkdsk is a Windows program so you will need to use it in Windows.

This is the last link I know which I think I could recommend.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Sorry for not being more helpful.

---

### Post by finer recliner on 2008-08-20
chkdsk is for windows: [http://en.wikipedia.org/wiki/Chkdsk](http://en.wikipedia.org/wiki/Chkdsk)
fsck is the linux equivelent.

---

### Post by phantomjoker on 2008-08-20
so i had an insight - i have booted into bartPE and preformed a chkdsk - it faulted - i think my data tables (cant remember if thats the right name) are faulting.

Because music tracks are all muddled - tracks have merged together and turned corrupt.

---

### Post by suprfish on 2008-08-20
Keep bumping, go to the IRC channel, hopefully someone more knowledgeable can help. Also, there are loads of NTFS data recovery programs for Windows, though I haven't a clue which to recommend. ([ZAR]("http://www.z-a-recovery.com/partition-recovery-tutorial.htm"), [VirtualLab]("http://www.download.com/VirtualLab-Data-Recovery/3000-2248_4-10610841.html?hhTest=1&cdlPid=10801131"), [Recover Files]("http://www.download.com/Recover-Files/3000-2094_4-10715455.html?hhTest=1&cdlPid=10715456"), there are many). You might have more luck with those since NTFS is native to Windows...

---

### Post by phantomjoker on 2008-08-20
ok - thanks - new problem!

i am recovering data but only have 512mb of free space - how do access my second partition - it should be visable, but im used to windows, and so don't know where to find it!! HURRY! my computer is deleting itself!

---

### Post by Potatoj316 on 2008-08-20
for recovering deleted windows files you can use recuva.  I suggest you install it to a removable drive (because you can) and so you dont overwrite any files that you want to keep.  Then use it to scan your drive that has the "deleted" files on it.  

also I still dont think your computer will delete itself.

---

### Post by phantomjoker on 2008-08-20
ok - this is what my computer has deleted (by itself)

6 gcse coursework peices, over 200 photos, all graphic designs i have made - i am now trying to undelete what it has done....

im using photorec to restore it all hence i am where i am now - i have found my other partition - saved as temp.

---

### Post by phantomjoker on 2008-08-20
ok - so i found the source of the problem - a corrupt partition table

> Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b93a530

Disk /dev/sdb [COLOR="Red"]doesn't contain a valid partition table[/COLOR]


i am recovering data but need to sort this out - any ideas??

---

### Post by nynoah on 2008-08-20
Was I reading correct when you said you had 512 MB free of 500gig hard drive.  How much free space was there on that drive before all this started?

---

### Post by nynoah on 2008-08-20
The reason I ask is NTFS tends to corrupt and take a dump on files if you do not leave 10% free space as a buffer.

---

### Post by phantomjoker on 2008-08-21
no, it was my files being recovered that took up all the memory.



So here is where i am - 

i have a 120G external that is failing, corrupting and loosing data

I have 5 hard drived all plugged into a computer which is running of bartPE

i have 110G of important documents and files to save by transfering them onto the hard drives - which currently total 80GB (small hard drives)

I cannot transfer files because as they are corrupt! (aparently)

So whats next?

Im going to try and burn another copy of BartPE, and see if it runs smoother

Im going to then - if that works, save my files and fix the partiton table

If that the above cant be succeded, i will loose over 4 years of un-backed up data - some of which, as the original post says, is GCSE coursework.




Has ANYONE got suggestions of how to save this remaining data?

thanks guys.

---

### Post by suprfish on 2008-08-21
bump/[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")?

---

### Post by jose158 on 2008-08-21
Is there the possibility that someone has hacked your computer and messing with you by deleting your stuff?

---

### Post by phantomjoker on 2008-08-23
i am using photorec - testdisk is not so efficient.

- and yes, there could be a possiblity, but i doubt it

---


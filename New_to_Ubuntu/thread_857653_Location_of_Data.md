---
title: "Location of Data"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Canuck90 on 2008-07-12
Well after installing Ubuntu, deleting Windows in the process, and unsuccessfully attempting to recover some files, it appears I have used up about half of my internal hard drive space. Is there a way to access this data and remove it, I believe it is the data I recovered, but was too useless to keep. Is it possible it is in lost+found. I'm not worried about getting any data back at this point, I just want to free up space so I can begin replacing lost data. The System Monitor is listing the drive twice essentially, once as /dev/sda1 and the other as gvfs-fuse-daemon. I tried to get into root to look at lost+found, but that isn't working for some reason. Any ideas?

---

### Post by cariboo on 2008-07-12
You can use the following command to look in lost+found directories:

```
gksu nautilus
```

This will open a window with root privileges.

Jim

---

### Post by bab1 on 2008-07-12
I believe that lost+found is for data dumps when there is a crash.  If you are looking for where the data is (not what it is), try ```
df -h
``` and 
```
du -h
```

"df" will tell you how much data is on each partition and "du" will list the data of the various directories (with the directory total at the end).  So, if you wanted the amount of data in /home you would use the incantation ```
du -h /home
```

---

### Post by Canuck90 on 2008-07-14
Still no luck, I have two partitions, one for Windows ~30GB, the other for Ubuntu ~60GB. My /home says it contains ~2GB and there is only ~14 GB free, where is my other 44GB? When I look at the properties of the Files System it says it contains 210GB and there is 14GB free. The 210 seems to come out of no where. How much space does Ubuntu take up itself? 

On an unrelated note, can anyone explain why when I click on Trash while in a window with root privileges everything comes to a screeching halt until I force that window to close, after which everything is super slow and jerky until I restart.

---

### Post by Cannaregio on 2008-07-14
> **Canuck90 said:**
> Still no luck, I have two partitions, one for Windows ~30GB, the other for Ubuntu ~60GB. My /home says it contains ~2GB and there is only ~14 GB free, where is my other 44GB? When I look at the properties of the Files System it says it contains 210GB and there is 14GB free. The 210 seems to come out of no where. How much space does Ubuntu take up itself? 

Investigate using system --> Administration --> partition editor
> **Canuck90 said:**
> 
On an unrelated note, can anyone explain why when I click on Trash while in a window with root privileges everything comes to a screeching halt until I force that window to close, after which everything is super slow and jerky until I restart.
"a window with root privileges" is a "sudo nautilus", I presume.
Btw, the correct command should be 
```
[COLOR="Blue"]gksudo[/COLOR] nautilus
```

That's no way to work.
Check your trash using the terminal instead.

```
cd .local/share/Trash
```

and delete everything in sight.

Also note that there's another "root" trash folder in [COLOR="Blue"]/root/.Trash[/COLOR]. Anything you delete while running nautilus as root lands there.
Note that you should [COLOR="#0000ff"]NEVER[/COLOR] delete things while root, else you [COLOR="Blue"]WILL[/COLOR] soon or later damage your system. But if you did, you'll find those items in their "root" [COLOR="#0000ff"].Trash[/COLOR] folder, not in "your" normal one. This "root" trash folder DOES NOT EXIST in your system until you delete something as root.

In your case I guess and hope that emptying BOTH .Trash folders could help.

---

### Post by Canuck90 on 2008-07-14
It lists 3 partitions:

ext 3  / Size 59 Used 43 Available 16
ntfs /media/disk Size 30 Used 3 Availavle 27 boot
extended Size 3

The thing I can't figure out is the used 43GB, having only installed Ubuntu yesterday and downloaded 2.5GB of music this number should be much lower than it is, shouldn't it?

---

### Post by Cannaregio on 2008-07-14
> **Canuck90 said:**
> It lists 3 partitions:

ext 3  / Size 59 Used 43 Available 16
ntfs /media/disk Size 30 Used 3 Availavle 27 boot
extended Size 3

The thing I can't figure out is the used 43GB, having only installed Ubuntu yesterday and downloaded 2.5GB of music this number should be much lower than it is, shouldn't it?

It should indeed. 
If you did not install a lot of stuff and if you did not delete as root a lot of stuff. See my answer above and check both your .Trash folders.

Anyway, to give you a rough idea, in my own laptop I slowly went from 5 Giga to 50 after (a lot of) installs.

---

### Post by Canuck90 on 2008-07-14
When I run df -h it says my partition /dev/sda1, mounted on / is size 59GB, 49GB is used, and 7.9GB is available, but when I run du -h / the directory total listed at the end is 14GB, shouldn't this number be 49GB if I had actually used that much space. As of now I haven't separated my /home into it's own partition, I don't have a .Trash in root as I haven't deleted anything in root, and my other Trash is empty. Something that might be related to this problem is that when I run df -h, there is a partition called gvfs-fuse-daemon mounted on /home/scott/.gvfs of size 59GB with 49GB used and 7.9GB available.

---

### Post by Canuck90 on 2008-07-18
Anyone else have any ideas on this topic? When I am in the / directory in the file browser and select all the folders and view the properties the total size is under 4GB, yet the partition editor, among other places, still says I have 40 of 60GB used up.

---

### Post by Paddy Landau on 2008-07-19
I don't know if this will help.

The root's trash (on my machine, anyway) is

/root/.local/share/Trash/

---

### Post by RomeReactor on 2008-07-19
> **Canuck90 said:**
> On an unrelated note, can anyone explain why when I click on Trash while in a window with root privileges everything comes to a screeching halt until I force that window to close, after which everything is super slow and jerky until I restart.

Sounds like root's Trash contains those missing GBs of data. One way to be sure, aside from checking the folder itself, is going to 'Applications->Accessories->Disk Usage Analizer'.

---


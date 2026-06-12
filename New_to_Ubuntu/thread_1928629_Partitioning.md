---
title: "Partitioning"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by meduser on 2012-02-20
ok, I am new to kubuntu. I have always been tricked into using Windows.

I set up my HDD as per the instructions, and thought I had designated the whole 250GB HDD to Kubuntu. I am out of room already and it has only been 2 weeks. The HDD is saying that it is full, at
 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             48118664  43838600   1835776  96% /
udev                   1984448         4   1984444   1% /dev
tmpfs                   811744      1040    810704   1% /run
none                      5120         0      5120   0% /run/lock
none                   2029352      1652   2027700   1% /run/shm
/dev/sda6            117863764   2673196 109203396   3% /media/9bf7f8a7-cee0-4d35-a123-fd897674eb5f

as you see, I have lots of empty space. The problem is, I can't access it. The 2673196 used on sda6 is a copy of Kubuntu. I don't know how it got there or why. My os is on sda5. I am not able to access the sda6 drive at all. It says access denied. I have tried running in root, and get the same. Here is what I want to do...
I want to make the sda5 drive to be just for the main OS(kubuntu11.10).
I want to make the sda6 hdd to be the drive where downloads, etc go. I want to empty out the sda6 partition all together, and start fresh. I do not want to start over, and have to reinstall Kubuntu.

I am getting low disk space errors, and can't complete downloads of movies, etc. 

I have used Kubuntu for all of 6 weeks, and have screwed up the boot earlier, and am leery to play with gparted.

Any help for a rookie in training is greatly appreciated.

---

### Post by sudodus on 2012-02-20
Welcome to the Ubuntu Forums,

I'll try to help you.

1. What is filling your sda5 partition? Multimedia files?

2. Your sda6 partition is mounted (and at least readable) according to the output of ***df***. How do you try to access it?

I suggest that you either delete some big file (multimedia file?) or copy it to sda6 and then delete it. So try again to access it! Have you tried commands from a terminal window? If the installed system refuses to work because the system partition is full, you can boot from the install CD or USB drive and copy + delete = move some big files or directories.

---

### Post by meduser on 2012-02-20
ok..first, thank you for your help. Much appreciated.

the sda5 is mostly full of multimedia files. Downloaded programs (like chrome, heidisql, geany, lampp, netbeans, eclipse, mysql, k3b, a few jpegs and I have 5 movies, each about 700mb each. I honestly don't know where all the 46 gb's have gone.) 

My first instinct was to move the downloaded programs to the sda6 partition, but it says access denied.

I then tried to move the 5 movies, and got the same result. I have tried to log in as root, but then I can't find the downloads folder for user1. 

I have tried to delete some movies after copying to usb stick, and it says trash is full, manually remove. My trash is empty as far as I can tell. 

46 gbs should be large enough for the main OS, and the files needed?

I have the 110 gbs partition sitting there, almost empty, and I also have a swap partition of 68.07gb at sda1. I should have more than enough space.

---

### Post by HavarN on 2012-02-20
The problem seems to be that you use the rather small sda5 partition for both your system files and your personal files /home.

I think you could move your home files to sda6 and mount that patition as /home

Mount points are set in the /etc/fstab file. Run from a terminal:
```
sudo kate /etc/fstab
```

Add a line to /etc/fstab like
```
/dev/sda6    /home    filesystem    defaults    0    0
```Replace filesystem with the filesystem of your partition.

You can find the filesystem of sda6 with
```
sudo parted -l
```

when you are finished editing your fstab, you can move your files and remount the partitions.
```
sudo mv /home/* /media/9bf7f8a7-cee0-4d35-a123-fd897674eb5f
sudo umount /media/9bf7f8a7-cee0-4d35-a123-fd897674eb5f
sudo mount -a
```

---

### Post by sudodus on 2012-02-20
> **meduser said:**
> ...
I have tried to delete some movies after copying to usb stick, and it says trash is full, manually remove. My trash is empty as far as I can tell. 

Maybe you have some problem with the trashcan, maybe a lot of junk there. Check the following directory and its subdirectories
```
~/.local/share/Trash
```
> 
46 gbs should be large enough for the main OS, and the files needed?

Yes, definitely
> 
I have the 110 gbs partition sitting there, almost empty, and I also have a swap partition of 68.07gb at sda1. I should have more than enough space.
That is where you should keep your multimedia files
> 
46 gbs should be large enough for the main OS, and the files needed?

Yes, definitely
> 
I have the 110 gbs partition sitting there, almost empty, and I also have a swap partition of 68.07gb at sda1. I should have more than enough space.
That is where you should keep your multimedia files

---

### Post by mastablasta on 2012-02-20
hmmm strangemess. what you are saying is you didn't create a separate home partition during install. what you should have done is dedicate well about 46GB to system (eventhough think that is quite a lot and probably 20-25Gb should do, but ok) and the rest should be a home partition. if you created a home partition when you installed the OS all your downloads and files would then automaticly go there.

if you have an empty windows partition arround you could try moving files to it. Cause it seems to me liek you have at least 6 partitions (total) on your disk. am i correct?

---

### Post by sudodus on 2012-02-20
Wait a minute, do you really have a swap partition of 68.07gb at sda1?

Please post the output of ```
sudo fdisk -lu
``` within [code] tags (use the # icon at the top of your editing window).

---

### Post by meduser on 2012-02-20
This is what sudo fdisk -lu

I also have a second hdd, which is sdb( 80 gigs on sata, this drive has windows 7 on it, and ubuntu 11.04 on a dual boot. It is out of my other pc, and I am taking some pictures off and wiping it)

Now, I moved the movies and such over to sdb6

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6fa56fa5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   142749707    71374822+  82  Linux swap / Solaris
/dev/sda2       142751742   488396799   172822529    5  Extended
/dev/sda5       390625280   488396799    48885760   83  Linux
/dev/sda6       382240768   390621183     4190208   82  Linux swap / Solaris
/dev/sda7       142753653   382234544   119740446   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ec77ec7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848    93287453    46540303    7  HPFS/NTFS/exFAT
/dev/sdb3        93288448   125240108    15975830+   7  HPFS/NTFS/exFAT
/dev/sdb4       125241342   156301311    15529985    5  Extended
/dev/sdb5       125241344   153747455    14253056   83  Linux
/dev/sdb6       153749504   156301311     1275904   82  Linux swap / Solaris

```

---

### Post by sudodus on 2012-02-20
> **meduser said:**
> This is what sudo fdisk -lu

I also have a second hdd, which is sdb( 80 gigs on sata, this drive has windows 7 on it, and ubuntu 11.04 on a dual boot. It is out of my other pc, and I am taking some pictures off and wiping it)

Now, I moved the movies and such over to sdb6


But sdb6 is a swap partition. Did you really move your movies to a swap partition? Do you mean sda7 (according to ***fdisk***)? And how come sda6 is mounted according to your first post. It should be sda7. Did you change something on that HDD after you ran ***df*** (and posted its output in your first post).

And finally: Now that you moved the movies, can you run Kubuntu again? Then try to find the trashcan directory. Keep all subdirectories but remove all files in two subdirectories.

Check what is there (when started from the hard drive)
```
ls -l .local/share/Trash/files/*
ls -l .local/share/Trash/info/*
```
and remove
```
rm .local/share/Trash/files/*
rm .local/share/Trash/info/*
```
and check again if it is empty. Maybe you need to run as superuser:
```
sudo rm .local/share/Trash/files/*
sudo rm .local/share/Trash/info/*
```

If this does not work, your system might have the trashcan in a different place.

---

### Post by sudodus on 2012-02-20
Or are we mixing up the two disk drives?

---

### Post by meduser on 2012-02-20
To tell you the truth, I do not know what the heck is happening.

I had originally tried to move the movies to sda6. I was told access denied. I typed the help request, and then tried to move the movies over to my second hdd (sdb 80 gb/ sata). Half way through moving the movies, the pc froze. I restarted the pc, Kubuntu started back up. I was able to see the 2nd hdd(80gb sata), as well as the 1st hdd(250gb, pata). I finished transferring the movies, over to the second hdd. It is in a partition that is 15.2gb in size. Looking at the numbers for sdb, the sdb6 drive looked right for the size of it. Looking at gparted it shows it being sdb3 as the 15.2gb partition.

I can't find the original sda6 drive. If I go into gparted, the /dev/sda7 partition has a yellow triangle with a black exclamtion in it, says unknown, 114.19gb. I am assuming that is my drive I was talking about at the beginning. So, somehow, the 11+ gb partition is lost? Can I format this drive? the drives listed in gparted under the 250gb WD pata drive (sda) are:
```

/dev/sda1   linux-swap    68.07gb
/dev/sda2   extended      164.82gb
/dev/sda7   unknown        114.19 gb
unallocated unallocated   3.04gb
/dev/sda6   linux-swap    4.00gb
unallocated unallocated   2.00gb
/dev/sda5   ext    /      46.62gb      

```

don't know if that helps....looks like I have deleted the partition, and now it needs to be formatted. I don't know why I have so many partitions. I didn't make them. I was trying to give the whole 250gb hdd to this pc. 

Also, the size of the partitions looks screwed up.

it is reading as over 350gb, but the hdd is only 250gb. 

I'm a confused newbie....;P

---

### Post by larrypg on 2012-02-20
Hello,

I know you do not want to reinstall but right now your partitions are so messed up it seems to be the easiest thing to do.  You have multiple swaps one of which is just a tad to large and small partitions of unallocated space and just a general mess.  

If you want to use the whole drive then you should maybe make a 20g or 30g partition and make it /.  You should make a 4g (depending on how much ram you have) partition and make it swap.  The rest of the drive you can make as /home which will give you plenty of space to put movies and config files etc.  

Just a thought.

---

### Post by meduser on 2012-02-20
I don't want to reinstall right now, because I am a student, and I am learning how to use Ubuntu. If I have to reformat and start over, I am going to waste a day, and lose what I have here.

When I was installing Ubuntu, I set the partition as it asked, and I have 4gigs of ram. I just clicked my way through, and I didn't set anything to just 2gb. I was hoping to have the home directory, or whatever directory I am to put my files into being over 200gbs.I just feel I have too much on here now to start over.

I was hoping for an easy way to expand the partitions or to setup the partitions correctly. I have no issues losing most of what is on here. Between dropbox, and usb's, I can pull most off that I want to keep. I just don't have the time, as it is midterms right now. It seems to be alot of updating and installing when starting new.

I just don't know how I ended up with so many partitions.

---

### Post by mastablasta on 2012-02-21
either you installed it a couple of times on same disk or you didn't partition it propperly during install. i tihnk you porbably created sda1 as swap while you ment to assign root to it.

if you clicked your way thorugh using automatic settings only then /Home is not set on sepaarte partition. ofcourse one can easilly set it later. and i would do it like that if you need to reinstall and don't know how to paritition in Linux.

i would reformat the whole drive or at least delete all partitions and start fresh. it is really a mess there. you can backup your settings and all installed programmes. so when you reinstall (instalatons typically takes about 15-20minutes) you can then copy the installed programmes back or if you backed them up into a list set it for new download and install. you can leave this overnight so you don't loose too much time. 

if you have a problem with slow connection then you can also back up the programmes i believe.

you can use mintbackup tool: [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)

you can also wait if there is someone that knows a bit more about how to change file system and partition designations in Linux. or you can try IRC channel for help if relevant people here don't spot your thread.

---

### Post by sudodus on 2012-02-21
> **mastablasta said:**
> ... i would reformat the whole drive or at least delete all partitions and start fresh. it is really a mess there ...
+1

When you have time enough, start all over deleting all partitions and design the partitions according to advice given.
--
0. So when you are ready for it, start a new thread at the Ubuntu Forums and ask people to help you. I would suggest

1. backup all valuable files

2. start a live session from your install CD or USB drive
- delete all partitions using gparted
- create new partitions according to what you want after asking for advice (use gparted)

3. install Kubuntu, and when asked about partitions, select the manual method 'other method' or whatever it is called, and select the partition[s] you want for the file system / (and maybe /home). If there is a swap partition, it will be selected automatically.

---

### Post by meduser on 2012-02-21
no, my network speed is very fast. I can download at over 40mb/sec. That is not the issue with reinstalling. I have finally gotten the pc to a state that I like, and it is going to take alot to get it back to this.

So my original install was Ubuntu 11.10, and I then added the KDE environment to it. Should I just install Kubuntu? I am not fond of the unity environment, and I like the KDE setup. I have tried Fedora, and didn't really like it, as there was just so much to install. Any suggestions? I have come to the conclusion that I am going to have to reinstall, and want to get it over with ASAP so that I can go back to a working pc.

Thanks again for all the advice.

---

### Post by sudodus on 2012-02-21
Yes, I would suggest that you download the Kubuntu iso file and test it live before deciding to install. You might even try a few different versions: 10.04 LTS, 11.04, 11.10 (the newest official version) and 12.04 LTS (now at alpha stage). Do not install 12.04 yet, but try it live. I like the LTS versions because of their stability.

There are several recent threads at the Ubuntu Forums, that discuss how to partition a drive for [KLX]ubuntu with or without dual boot with Windows.

I suggest you should have at least the same size of swap as of ram, in your case 4-6 GB. This makes it possible to hibernate and to run tasks that need a lot of memory. I know some people would say you need less. So you should decide if you want to hibernate your computer before making the swap partition.

On my computers I have no separate /home partition, but I have a separate data or media partition (with NTFS if there is dual boot with Windows, otherwise ext3). Many people like to have a separate /home partition, so this is the time for you to decide what you want.

---

### Post by meduser on 2012-02-21
thanks for your help. I have wiped the drive, and am trying to get the partitions setup right. I have started another topiuc on partitions, here:
[http://ubuntuforums.org/showthread.php?p=11707382&posted=1#post11707382](http://ubuntuforums.org/showthread.php?p=11707382&posted=1#post11707382)

Thanks again for your guys advice. I am trying to get this setup right and have the perfect environment for what I am doing.

Med

---

### Post by meduser on 2012-02-23
So, 2 days into this "20 min" reinstallation, and nothing is going right. 

I can't install Ubuntu software center..gives me errors.

"Another application seems to be using the package system at this time"

The kubuntu install took over 3 hours....and not much is working right. I can't send emails, the clocks on each screen are not keeping same time, and I still don't have half the software installed onto my box that I require for school. ..

this is why I didn't want to reinstall to change my partitions. It has turned into a nightmare, and I am losing my whole week farting around on this. No matter what I do I am getting errors. I am having system crashes, and the trash can keeps just shutting down and a crash report comes up. 

Frustrated does not even begin to describe how I am feeling at this point.
```

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x367393e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   388821015   194307084    7  HPFS/NTFS/exFAT
/dev/sdb3       388823040   389847039      512000   83  Linux
/dev/sdb4       389847040   488397167    49275064    5  Extended
/dev/sdb5       389849088   488396799    49273856   8e  Linux LVM

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000700a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480010239   240004096   83  Linux
/dev/sda2       480012286   488396799     4192257    5  Extended
/dev/sda5       480012288   488396799     4192256   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ec77ec7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdc2          206848    93287453    46540303    7  HPFS/NTFS/exFAT
/dev/sdc3        93288448   125240108    15975830+   7  HPFS/NTFS/exFAT
/dev/sdc4       125241342   156301311    15529985    5  Extended
/dev/sdc5       125241344   153747455    14253056   83  Linux
/dev/sdc6       153749504   156301311     1275904   82  Linux swap / Solaris

```

That is my drive info..is that at least looking correct? sda is my linux hdd...the other 2 have windows on them, and I need to transfer files from them before I can wipe them.....

Please anyone with a heart, help a guy who is very quickly falling behind on his University courses.

---

### Post by sudodus on 2012-02-23
> That is my drive info..is that at least looking correct? sda is my linux hddYes it looks all right. One big linux partition and a small swap partition. It should work.

Sorry that it takes such a long time. I suggest you make a priority list and install the most important things first ... and maybe leave the less important things so that it will not take too long time until you can return to the university courses.

To install Software Center, try
```
sudo apt-get install software-center
``` might work. If not, try to install the applications you want directly (tell which programs you need now)!

And if you need help with something else, please explain the situation! More details increases the chance that you get good help.

---

### Post by Ji Ruo on 2012-02-23
It has been a long time since I have tried using the Ubuntu software center (like 2-3 years!). I will usually install using the command line. My recommendation is to have a look at the Ubuntu Guide Wiki linked in my signature, they have a separate section for Kubuntu and it covers the applications you might want comprehensively and how to install them. It is the best way to start off with Ubuntu imo. For proprietary programs with Linux versions you can usually get and install them from the website and many of them will have an installer made for Ubuntu. I believe these will usually be more recent than the ones in the software center. But, software centre might be easier for you if you can get it to run - sorry that I'm not able to help there.

You can also search for applications you might want if you know them by name, by going to a terminal (Kmenu > Applications > System > Terminal) and entering (as an example):
```
sudo apt-cache search firefox
```
then if you see the application there that you want
```
sudo apt-get install firefox
```
and if you need to uninstall it
```
sudo apt-get remove firefox
```
I find the terminal useful enough to have on my panel, you can do it by right clicking on it in the Kmenu and choosing the option.

Some advice for when you want to transfer your files from the Windows installs. You can do it with Dolphin, the file manager, but you need to do it as a superuser. To do this, press Alt+F2 to open a launch bar and type in the text box:
```
kdesu dolphin
```
Put your password in at the prompt and then you will be able to access the Windows drives/partitions and copy and paste. Pressing F3 while in Dolphin will give you a second tab, so you can also have your home folder open. If you open Dolphin like this it will start in the root folder, to get to your user home folder go to /home/your_user_name. From there you have your Documents, Pictures, Videos etc plus whatever other folders you might wish to create.

My final advice is don't be too hasty to delete your Windows installs. Being able to use Linux for everything is great but hard to accomplish as a beginner. At the very least make sure you have everything fully working and all data transferred. Once its gone it might be difficult or impossible to get back.

---

### Post by meduser on 2012-02-23
I thank everybody for the help they have offered.


I want to fully submerse myself into the Linux society. I like the layout of the system, and have been unhappy with Windows and having to follow their demands for a while now.

I have four PC's in this house, so I am never without a computer. However, one is my sons laptop, and I feel like I am reading his diary everytime I use it for anything. 

Another is my wife's..same feeling...lol/ My Win7 pc is being used for emulation and as a DNS server for the house. 

The courses I am taking are quite intensive for a 20 year class one truck driver vet. A disease in my spine has led to a need for a change in career, so I chose computers..lol. I am studying Linux, PHP/ My SQL, javascript, java, and networking all at the same time. Quite difficult for me as a year ago I thought java came best as a double double in a cup. Overwhelmed is just the beginning of it. 

So for me to have a pc setup for my school I am looking at needing PHP/ Mysql/ lampp/ Eclipse/ Java/ a text editor, which I really liked notepad++ for windows last semester. My wifes laptop would struggle with all that as she only has 1.5gbs of ram. 

My sons pc, I can't rely on...as it's his and he plays with it so I can't put school work on it. That leaves me with 2 pcs, and the one running as a server is in the basement, and it's too cold down there for me to be for extended periods, as my back spasms. 

That leaves the pc I have Linux on. It has 4gbs ram, and is only 2 months old. I have it running, and have everything back that I needed, but the problem this morning was a dependencies issue. I ended up just starting al over again, and have it running right ow...I think.

For the most, I like the layout and feel of the Kubuntu system. 

As far as windows goes..I am not overly concerned right now about changing them. I can boot to win7 if needed thought the grub, and I can access both hdd through media on my linux system. 

Just frustrated, as I had set out a list of goals for the week, and have completed none of them, and it is Friday tomorrow.

Again..thanks to all who have helped me out. I have a ton of questions, and I do not fear experimenting with the system, but that can also lead to issues..lol...;P

---

### Post by mastablasta on 2012-02-24
no problem just ask them if you can't find the asnwer on google. someone willprobably knwo it.
 
also ther are (ubuntu, kubuntu...) IRC channels where more helpful people reside...

---

### Post by meduser on 2012-02-24
> **mastablasta said:**
>  
also ther are (ubuntu, kubuntu...) IRC channels where more helpful people reside...

I must have eaten a bowl of stupid for breakfast, as I can not find the irc channels at all.

I have searched by typing Kubuntu IRC, and it brings me back to this thread..lol

On the good side, I am learning a lot.

---

### Post by maheshtatva on 2012-02-24
before i was using kubuntu (downloaded the 32 bit version) my screen got become black when computer starts. after all the combat i started using ubuntu 11.10 gnome classic interface my battery life is much better and it is very fast.

---

### Post by meduser on 2012-02-25
> **mastablasta said:**
>  
also ther are (ubuntu, kubuntu...) IRC channels where more helpful people reside...
where do I find these IRC channels. I have tried searching the site for them, but only get threads returned that have mentioned them.
Thank you in advance for your help.

---

### Post by oldfred on 2012-02-25
I have not used IRC, but some info:

Here are a couple of community docs on the IRC channels:
[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)
[https://help.ubuntu.com/community/XChatHowto](https://help.ubuntu.com/community/XChatHowto)

---

### Post by cryptotheslow on 2012-02-25
A couple of days you posted this:

```

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x367393e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   388821015   194307084    7  HPFS/NTFS/exFAT
/dev/sdb3       388823040   389847039      512000   83  Linux
/dev/sdb4       389847040   488397167    49275064    5  Extended
/dev/sdb5       389849088   488396799    49273856   8e  Linux LVM

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000700a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480010239   240004096   83  Linux
/dev/sda2       480012286   488396799     4192257    5  Extended
/dev/sda5       480012288   488396799     4192256   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ec77ec7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdc2          206848    93287453    46540303    7  HPFS/NTFS/exFAT
/dev/sdc3        93288448   125240108    15975830+   7  HPFS/NTFS/exFAT
/dev/sdc4       125241342   156301311    15529985    5  Extended
/dev/sdc5       125241344   153747455    14253056   83  Linux
/dev/sdc6       153749504   156301311     1275904   82  Linux swap / Solaris

```

Is that how things still are?

If so it looks like you have somehow ended up with 3 Linux installations - one at sdb3, one at sda1 and one at sdc4.

You also appear to have Windows installed twice - on both sdb1 & 2 and sdc1, 2 & 3.

From Kubuntu can you post up the output to these commands (in code tags):

```
mount -l

cat /etc/fstab

 cat /boot/grub/grub.cfg

```

---

### Post by meduser on 2012-02-25
> **oldfred said:**
> I have not used IRC, but some info:

Here are a couple of community docs on the IRC channels:
[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)
[https://help.ubuntu.com/community/XChatHowto](https://help.ubuntu.com/community/XChatHowto)

perfect, thank you. Much appreciated

---

### Post by oldfred on 2012-02-25
When you have multiple drives and/or multiple installs it is often worthwhile to run boot info script to both document system and better understand where boot loaders and systems are installed.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

or:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by meduser on 2012-02-29
> 

Is that how things still are?

If so it looks like you have somehow ended up with 3 Linux installations - one at sdb3, one at sda1 and one at sdc4.

You also appear to have Windows installed twice - on both sdb1 & 2 and sdc1, 2 & 3.



Hi and thanks for your help. No my pc is not like that any more. I had my main drive(sdb)and then added the other two. I have changed the pc's those drives where in, and have a fresh install of windows 7 on one of them. I want the pc I use for school, etc to have lots of space, so the sda and sdc drives are going to be erased, and formatted. They both had dual boots on them, so thats why they both show a linux os, and a windows. The problem I was having was the partitioning of the sdb hdd, and I ended up just saying the heck with it, and formatted the drive, and started over. I now have a swap drive of just over 4gigs, and the rest is for Kubuntu. I runs a lot better now, and no crashes or issues to speak of.
So, I am fixed up and running fine.

Wish I could figure out burning DVD's from AVI's and I'd be set.

I'll mark this as solved. Thanks again for all who helped and gave suggestions.

---


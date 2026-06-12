---
title: "help with organizing data"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by nerdinator on 2012-06-02
Hello.
I have a new laptop which has Windows 7 pre-installed.
I plan to copy all the music,videos,projects and all that from my old computer to my laptop.

I will be installing Ubuntu 12.04 along with Win7.
So I'll create a partition in the C drive for Ubuntu. 
But I have some questions of how much I must shrink the volume by and where I should store my data.

1.After I allocate some space for Ubuntu in C drive,will all the Ubuntu related files,softwares I later download for Ubuntu via Software Center or Synaptic or however, exist physically in new partition created?

2.The partition I'm going to create is a real physical one right? I mean, the hard disk will physically have 3 sectors one of which is the Ubuntu drive right?

3.Lets say I keep my personal data in the new Ubuntu drive, like Documents or Desktop and I later remove Ubuntu,will this data get removed likewise?

4.Which is the recommended place to store my personal data? Mount the other 2 drives and put it there?  Or put it in my Desktop or Documents directory in Ubuntu?

5.I find it extremely confusing that my old drives in Windows when mounted in Ubuntu ,find themselves in the media directory in root. If the root is supposed to mean to partition created for Ubuntu,how can it have the other partitions as sub-directories?

Thank You.

---

### Post by inashdeen on 2012-06-02
1. First off, you wont be having the partition inside C drive, unless of course if you use Wubi. it will be beside C. and yes, all the files install from USC, synaptic and apt-get will be in your laptop. you can use it even if it is offline .

2.Yes, it will, provided you dont use Wubi, the most probable format you will use is ext4

3.Yes, unless you back them up. 

4. As for me, i prefer having my basic data in ubuntu on ubuntu, and windows on windows. however, i kept all my movies in another partition so that i can access them from both ubuntu and windows. some people prefr to create another partition /home so that it wont get affected even if you upgrade your ubuntu. 

5.they are basically not meaning root. they are mounted in /dev. basically as device. seems legit right.

---

### Post by Bucky Ball on 2012-06-02
Welcome. You need to read up about dual-booting to gain a better understanding before diving in:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

There's a start. And if that doesn't, this should answer all your questions:

[http://au.search.yahoo.com/search?p=dual%20boot%20windows%20ubuntu&fr=altavista&fr2=sfp&pqstr=dual%20boot%20windows%20ubuntu]("http://au.search.yahoo.com/search?p=dual%20boot%20windows%20ubuntu&fr=altavista&fr2=sfp&pqstr=dual%20boot%20windows%20ubuntu")

Shrink Windows 7 with Windows software, not Linux/Ubuntu. Leave free space to put Ubuntu partitions on, don't create anything inside C or anywhere else. Just shrink the partition.  

Common for Ubuntu install is:

/ = root partition, where the system goes (20Gb should be fine);
/home = where your personal stuff goes (large as you like);
/swap = 2Gb plenty.

To do custom partitions choose 'Something Else' during the install. Reason for having a separate  /home is so if you want a reinstall, no, your personal data won't be killed, it will remain in /home and the contents of / will be replaced (by an OS install). 
  
Don't worry about mount points until you need to (and you probably won't). Ubuntu will take care of that (generally) during the install. The mount points for Ubuntu I mentioned above are defaults in the partitioning section of the install or you can create /whatever. Win partitions can be clearly seen in that section; they are NTFS or FAT32. Don't go near them and you're fine. Win partitions will generally be mounted (or you can mount them) when you boot into Ubuntu. 

Yes, you are creating real, physical partitions, but one thing to remember ... you can only have three primary partitions on one physical hard drive. Therefore, if this is going to be a problem, make the fourth an extended partition (which can theoretically contain as many virtual drives/partitions as your hardware can handle). 

Ubuntu and all its related partitions can exist happily in an exended partition on virtual partitions ... Windows will not (without some serious tweaking). That's best on first drive, first primary partition. ;)

* As inashdeen mentioned Wubi; you don't want to go for that by what you are explaining. You want a genuine dual boot so download the Ubuntu desktop ISO, burn to disk, boot from disk, 'Try Ubuntu' to see how it runs on your system. It can be installed by clicking the icon on the desktop.

---

### Post by nerdinator on 2012-06-02
I'm sorry for saying "creating a partition in C" , while I actually meant alongside C but after shrinking C.
And also,I currently actually have an extra partition(D drive) where I used to save all my personal data in  windows.
And all Ubuntu things I know are from using it on my** old desktop.**


@[COLOR=Black][inashdeen]("http://ubuntuforums.org/member.php?u=1200448")[/COLOR],
Thank You for your reply.
1. In my laptop, yes ,but in my Ubuntu partition? That is what I asked.

2.So I'll want to choose ext4 in Disk Management(Shrink Volume menu)?

4.Like I said above, I have a D drive on Windows. Is what you are doing similar to going to the mounted volume in Ubuntu corresponding to D drive in mine and storing your personal data (when on Ubuntu)?

And you say partition/**home**. Is this "home" same as a partition drive on Windows? 
I'm planning to use Ubuntu mainly,so it might a better idea for me I guess.

5. I'm sure I find my mounted volumes(C and D on windows) in  /media.

---

### Post by nerdinator on 2012-06-02
> **Bucky Ball said:**
> 
Common for Ubuntu install is:

/ = root partition, where the system goes (20Gb should be fine);
/home = where your personal stuff goes (large as you like);
/swap = 2Gb plenty.

To do custom partitions choose 'Something Else' during the install. Reason for having a separate  /home is so if you want a reinstall, no, your personal data won't be killed, it will remain in /home and the contents of / will be replaced (by an OS install). 
  
Don't worry about mount points until you need to (and you probably won't). Ubuntu will take care of that (generally) during the install. The mount points for Ubuntu I mentioned above are defaults in the partitioning section of the install or you can create /whatever. Win partitions can be clearly seen in that section; they are NTFS or FAT32. Don't go near them and you're fine. Win partitions will generally be mounted (or you can mount them) when you boot into Ubuntu. 


Thank You Bucky Ball!
I did read on the web about it but still have many questions unanswered.

/home is not part of the root directory? It doesn't belong to the partition created for Ubuntu?  I don't understand why you have written /home separately from /?

And should I specify a /swap partition explicitly ? I don't think I read that in the howtos on ubuntu.com. I thought it was taken care of.

On Windows I could clearly see what a partition meant because it showed the drives at the top-most level. So I could understand that the hard disk is divided into them. But on here, I don't understand it clearly. There is a / which contains many directories many of which are supposed to be of use to softwares and Ubuntu itself. If I create a partition on Ubuntu, where will I see it?

---

### Post by inashdeen on 2012-06-02
1. yeah definitely. so long it is not a cloud storage, it will be in your ubuntu partition. No worries on that. the only clause is that windows don't read ubuntu partition, which is again good, if you are thinking bout privacy, but bad when talking about moving files between windows and Ubuntu. 

2.Most advisable is of course ext4. ext3 is obselete, while btrfs is... quite unstable i could say.
UPDATE : you won't find ext4 i suppose on Disk management on Windows. Windows hate Ubuntu and you can't find a Ubuntu option in there. :(

4.Like I said, I don't store personal, daily use data on another partition.I prefer what in Ubuntu to stay in its own Ubuntu partition along in its / (root), while my Windows file stuck in its C drive.  You will understand why when you have used ubuntu sometimes. the major problem is that, Ubuntu don't mount external partition until you tell it to (by clicking on the partition). which is good for security purposes, but bad for auto setting and etc. What I do install in the external partition is things which I share between my windows and Ubuntu.
A simple example is movies. Sometimes I watch movie on Windows, sometimes on ubuntu, so here is where I need to have the D for. Other thing is when I need to transfer a data from my Ubuntu OS to my Windows, I simply put it in D and restart to windows. Like I said, Windows dont read Ubuntu partitions. But Ubuntu do read Windows patition. 

You DON'T have to write a separate /home. when you run a ubuntu CD, unlike any other OS, it will write the /home in the root directory. some people doesn't like it to be in the root, since you know,

 root = core = could get damaged = reformat = files need to backup time 
and again. 
But I personally don't mind + don't care cause so far, since ubuntu 11.04, my Ubuntu praise lord has never get damaged. If I want to upgrade i rarely used the system upgrade but rather backup my files, install a new version of Ubuntu and restore them back. 


**Ubuntu and partition**
Now. let me explain generally about a ubuntu partition. what is / (root)? it is not a partition by itself. the partition is the ext4, ext3, NFTS stuff. the root is where you core system is installed. from this root, you can choose to either put subdirectory, like /home, 

or 
kinda loop another partition who happens to have a /home to your current core system, which is /.

this explains how can, the windows partition, or even a CD,maybe a USB modem or even a USB pendrive, which is of course an external media can be seen in the root. they are not directly in the root, they are just, mounted to it. that is why you can see them in /media or /dev . 

**Do you need to specify explicitly /swap? **

technically no. Ubuntu is great at the job. He knows what to do. So long you are using the *"install alongside Windows"* option. 

If you are installing a Ubuntu system manually, say, you create an empty ext4, then install Ubuntu, there is when you need to specify the swap. you probabily will do this on subsequent clean install of Ubuntu, not on your first time installing Ubuntu. 

p/s: Swap is somewhat similar to drive boost on Windows

---

### Post by Paqman on 2012-06-02
> **nerdinator said:**
> 
5. I'm sure I find my mounted volumes(C and D on windows) in  /media.

Actually you'll find them in both /dev and /media.

Linux uses a couple of ideas from it's Unix background:
[LIST=1]
[*]Mount points
[*]"Everything is a file"
[/LIST]

A mount point is somewhere you can attach part of a filesystem. For example, when you plug in a USB stick it automatically mounts to a folder in /media. But you can also choose to mount anything pretty much anywhere. For example, you could mount a partition in your machine to a folder in /media, or in /mnt, or your could create a whole new location called /ilikesausages and mount it there. Linux is very flexible.

By "everything is a file" I mean that within Linux everything (even hardware) is represented as a file. So a physical device such as a hard drive will have a representation in /dev. To actually use the filesystem on that device you'd still need to mount it somewhere.

Hopefully that's clear enough for you. It's a bit abstract but you'll pick it up pretty quick once you see it in action.

---

### Post by inashdeen on 2012-06-02
Seriously, It took me a looong time to understand the linux hierarchy. But once you understand, you will be awed by its beauty . Right Paqman ? ;)

---

### Post by Paqman on 2012-06-02
> **inashdeen said:**
> Seriously, It took me a looong time to understand the linux hierarchy. But once you understand, you will be awed by its beauty . Right Paqman ? ;)

I just like that I really can mount a share from my server full of sausage recipes at /ilikesausages. Take that Windows! Bam!

---

### Post by inashdeen on 2012-06-02
coool. let me see, mounting my D (sda4) on /iloveubuntu 

<3 awww,, true love <3

---

### Post by Bucky Ball on 2012-06-03
> **nerdinator said:**
> 
/home is not part of the root directory? It doesn't belong to the partition created for Ubuntu?  I don't understand why you have written /home separately from /?

This has been kinda explained. It can be a directory inside / and by default is. Putting it on a separate partition avoids losing it if you reinstall the operating system.

> **nerdinator said:**
> And should I specify a /swap partition explicitly ? I don't think I read that in the howtos on ubuntu.com. I thought it was taken care of.

If you let Ubuntu automatically install, it is. If you manually partition during the install, you will create /swap manually (and if you want to create /ilikedwarves then you need to do 'Something Else' and manually partition during install. (You can create that directory/partition later, of course.) One benefit of partitioning manually is that you can set sizes and mount points yourself rather than let Ubuntu set ones you might not particularly want. 

> **nerdinator said:**
> There is a / which contains many directories many of which are supposed to be of use to softwares and Ubuntu itself.

/ partition _***IS***_ Ubuntu. That's where you install the operating system to and it contains your software. The heart of the install. It contains everything (apart from /swap) unless you create a separate /home or other partitions.

> **nerdinator said:**
> If I create a partition on Ubuntu, where will I see it?

You can see it or any partitions you have on there now by using Gparted, the partition editor. (I'm presuming you have booted from the install cd and 'Try Ubuntu'? If not, I strongly advise it. You will find Gparted (not sure where in 12.04 if you're using that) and you can have a look around. Get the feel of things and plan what you are going to be doing (always plan an install: write it down rather than doing it on the fly as thats when mistakes happen ;))

If you create a partition called /mince, /mince will appear in your file manager in a pane on the left (or should) when you have installed Ubuntu. Or, you can navigate to where you created it using the file manager (usually partitions are mounted in /media, a directory inside /). 

Hope that helps.

---

### Post by nerdinator on 2012-06-03
I read in much detail what you all have written and I decide to store my personal data in an separate partition (D on windows) mounted on Ubuntu.

I also want my /home to be on a separate partition shown alongside the root since I don't want to lose data if something goes wrong with the OS partition. So in effect I'll want to put my stuff in "Documents", "Downloads" etc. directories provided Ubuntu but actually make them go to my extra partition.


As for installing I'll create a small partition for Ubuntu** using Disk Management in Win7 **and choose ext4 file system. I'll boot from  my USB drive where Ubuntu is there .

In my new laptop  there is already an extra partition (D drive). I want to put my personal stuff there physically.  

Bucky Ball said I must choose 'Something else' during the installation to create custom partitions. But I already have that partition done( D drive). All I need is to make it appear as a /home mounted not in /media (but more like Paqman's ).

Please help me out here.

Oh and I am really sorry if I'm still missing out on something. I'm trying hard to read and understand.

---

### Post by Bucky Ball on 2012-06-03
You're getting there. D will not be /home as it is an NTFS or FAT partition, which Linux doesn't use. You might be able to get around this by using symlinks to folders on D from you /home directory in / (if you know what I mean). 

Nutshell: you have a /home directory in / but the folders 'Documents' 'Pictures' etc are actually empty but linked to directories in /D. Once you have installed D should be mounted already (you don't need to do anything so don't worry about it). If you do need to do something to get it mounted it is really easy and you can just ask. It is unlikely you will need to. The install should pick up all your partitions/drives (including your Windows install and add it to the selections you get when you boot).

Do not bother making partitions for Ubuntu with Windows. For a start, Win has no idea what an EXT* partition is. It can't create them or read or write to them. Keep this in mind. If you want to share data on a partition between Ubuntu and Win then you need an NTFS partition (which both can read and write to). D\ would be the obvious choice. ;)

---

### Post by inashdeen on 2012-06-04
I think for start, just keep it simple. don't bother building a partition in D and try to link it to Ubuntu. its easy, yet will be extra confusing for new user. its better to just allow Ubuntu installer to do that job. Plus, I agree with Bucky Hall. Windows won't read your Ext4 partition.

---

### Post by Bucky Ball on 2012-06-04
> **inashdeen said:**
> ... don't bother building a partition in D ... 

The D partition already exists. 

> **inashdeen said:**
> its better to just allow Ubuntu installer to do that job. 

Allowing the installer to dictate terms you may not end up with what you want. AND I wouldn't trust 12.04 installer to do as it will with partitions and hard drives, personally. I've never done and 'automatic' install (except the very first one with 7.04). Puts everything on / an creates generic sized /swap. I ALWAYS use a separate /home partition and that is impossible with auto install. ;)

---

### Post by birdie1234 on 2012-06-04
I'm sure I find my mounted volumes(C and D on windows) in /media.

---

### Post by inashdeen on 2012-06-04
@Bucky Hall. I mean , don't bother, symlink to D.

I do believe that its too much info to separate /home for him as of now. let him explore bit by bit. after all, Windows too put documents, pictures, adn etc in the root. when he is used to Ubuntu, then he can separate home. just an idea. :)

---

### Post by nerdinator on 2012-06-04
I read about Symlinks and it seems to be a simple command in the Shell  which I can execute after the installation. I plan to use them after  installation. So,that should solve the problem of where to store my  personal data. It will on the D drive physically but via a symlink in my  /home in Ubuntu. That rules out a need for any partition for my  personal data. Right?

**(i)** I read [here]("http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/") that it is alright to create a partition on Win7 using Disk Management , for **Ubuntu's system files(not my personal data) .** Is it going to make a difference whether I do it in Windows and install there or during the Ubuntu installation? 

**(ii) And** about the installation, I found that there can be 4 partitions already existing in a new laptop.
1. System reserved
 2. OS restore partition used to restore OS to factory settings
 3. Windows C Disk
4. Windows D Disk
(are these primary?)

I read that there cannot be more than 3 primary partitions. One has to  be a logical one.  But a new partition for my Ubuntu system files should  be primary,right?
 
> 
I ALWAYS use a separate /home partition and that is impossible with auto install. :wink:
Don't you use Symlinks ? A separate /home partition? This is confusing me.  
Lets say I don't have a D drive and I choose 'something else' during the  installation and allot some space to the root,swap and home, by  creating new partitions  for them . Now where is this home going to be  seen? Under root? 
Will  there be drive on Windows that corresponds to this? 
Would even home have be mounted every time?

---

### Post by inashdeen on 2012-06-04
>  I read here that it is alright to create a partition on Win7 using Disk Management , for Ubuntu's system files(not my personal data)

i) what will you do when you are on that disk management is that is creating an empty space rather than an ext4 for Ubuntu. when you want to install Uuntu, then it itself will create an ext4. it is a good practice to clean an empty space for Ubuntu before installing Ubuntu. in fact, that is the best.

>  And about the installation, I found that there can be 4 partitions already existing in a new laptop.

Yes, but amazingly, I got 6 partition on my laptop.cool huh? how did i do it? well simply, I created an extended partition. A system can only have 4 partition, true, but 1 extended partition is considered one despite having so many partition inside. it is like a container where you can sacculate to make smaller room inside.In other way, you can say that An extended partition behave like a primary hard disk, except that you can create sooo many smaller partition inside it, which is great.
 in my system, I have
1)system reserved (primary)
2) C (primary)
3) D (primary)
5) Extended having :
   i) Ubuntu partition 
   ii)Swap
   iii) Chakra partition

in short, unlike Windows, Ubuntu doesn't need to be installed into a Primary partition. it can happily sit in an extended partition. 

> Lets say I don't have a D drive and I choose 'something else' during the installation and allot some space to the root,swap and home, by creating new partitions for them . Now where is this home going to be seen? Under root? 
now, you don't need to create new partitions for them, autoinstall will create those files **inside** root. think of it of how Windows create My Documents, My Videos, My desktop inside C.They were not new partitions, they were simply, files.and yes, you can see them in the root. right when you open the root, the folder home can be seen inside it. 

> Will there be drive on Windows that corresponds to this? 
Windows can't do anything. they can't read an Ext4. There will be no drive on drive in windows that will corresponds to them.

> Would even home have be mounted every time?
No you don't. since they are on in the same partition as the root, they will be automounted, reducing many errors in daily usage

---

### Post by nerdinator on 2012-06-04
> **inashdeen said:**
> 

now, you don't need to create new partitions for them, autoinstall will create those files **inside** root. think of it of how Windows create My Documents, My Videos, My desktop inside C.They were not new partitions, they were simply, files.and yes, you can see them in the root. right when you open the root, the folder home can be seen inside it. 


Windows can't do anything. they can't read an Ext4. There will be no drive on drive in windows that will corresponds to them.


No you don't. since they are on in the same partition as the root, they will be automounted, reducing many errors in daily usage

This is if I choose "install alongside Windows" (auto install). 
But I was asking about Bucky Ball's case. He chose "something else" during installation and uses his own /home partition. And he doesn't use Symlinks. Now that is interesting because he gets to keep the good organization of having a home without all the subdirectories and yet keep it isolated from the system partition (should something go wrong with it). 
He doesn't use the volume mounting method(i.e. ,mounting the space corresponding to D) or Symlinks. I don't know about any other way.
Hope I'm not being unclear. Sorry.

---

### Post by inashdeen on 2012-06-04
> This is if I choose "install alongside Windows" (auto install). 
But I was asking about Bucky Ball's case. He chose "something else" during installation and uses his own /home partition. And he doesn't use Symlinks. Now that is interesting because he gets to keep the good organization of having a home without all the subdirectories and yet keep it isolated from the system partition (should something go wrong with it). 
He doesn't use the volume mounting method(i.e. ,mounting the space corresponding to D) or Symlinks. I don't know about any other way.
Hope I'm not being unclear. Sorry.

Ok, let say you want to have a separate /home,**[B] on Ubuntu Live CD (means not on Windows Disk Management)**[/B], first you must allocate some space then create an ext4 partition and when asked for mount point, point it to /home.

 next create a second partition and for mount point , use / (root). third, build a third partition and point it to /swap.

 then just choose the /(root) and install Ubuntu there. AFAIK, Ubuntu will automatically detect the premade /home partition and settle the rest of the issue without need to manually create symlink after that.

Of course,judging by amount of partition you have, you have no choice but to use extended partition for the job

---

### Post by nerdinator on 2012-06-04
And the disadvantage with this method is that I won't be able to view this "/home" on Windows where as I will able to view a mounted partition( extended partition: D drive) on both OSes. Am I right?

---

### Post by inashdeen on 2012-06-04
Yes.

---

### Post by Bucky Ball on 2012-06-04
Example: /home/documents in / (root) on Ubuntu's EXT4 partition (which Windows can't see) is symlinked to a directory /d/home (where /d is an NTFS or FAT32 partition) then you will be able to see all the info on /d as NTFS or FAT can be read/written to by Windows (and Ubuntu)..

Hope that makes it a bit clearer. Sounds like you have the idea of the symlinks worked out (yes, it is easy) and yes, this will negate the need for a separate /home partition (as /d would be acting like one anyhow).

---

### Post by nerdinator on 2012-06-05
Thank You both , Bucky Ball and inashdeen!
That helped a lot.
My installation  didn't go well though. I see this "partition misaligned by 512 bytes" warning on Disk Utility. I made a new thread for that.

---

### Post by Bucky Ball on 2012-06-05
[http://ubuntuforums.org/showthread.php?t=1635018&page=1](http://ubuntuforums.org/showthread.php?t=1635018&page=1)

From post #28 might be useful but the thread should give you some clues. It at least explains what's happening. One person suggests leaving that much free space before the partition (eg 512Kb). 

Is the install actually running? Can you boot it? What is the link to your thread about this?

---

### Post by nerdinator on 2012-06-05
[here]("http://ubuntuforums.org/showthread.php?t=1996796") is the thread.

> Is the install actually running? Can you boot it?

Well,I can run the installed Ubuntu fine. I can also boot it from a USB drive and "try it". Both ways,it is good.

I can choose Ubuntu from the GRUB menu and run it fine.
The problem is the mess from the partitions and this warning.

---


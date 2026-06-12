---
title: "Getting into Ubuntu, but also want to back up..."
date: 2008-07-08
forum: New to Ubuntu
---

### Post by RollingStar on 2008-07-08
Hi there guys 'n' gals, I've recently obtained Ubuntu to back up a crashed windows hard drive, and my gosh I'm glad it crashed! Ubuntu is just plain awesome, and once I've backed my windows stuff up online I'll get a new hard drive and create a partition on that for Ubuntu as well as windows.

Right now I'm just trying to back everything up to my online storage account, but this is proving difficult!

Here's my situation - a part of windows has corrupted so I cannot boot it, but luckily my personal files are all still intact. I got Ubuntu to access the drive and put my stuff online. I've visited the tutorial section of this site, and found a code that allows me to access my windows hard drive, but it came up with an error, something about safely ejecting my hard drive in windows first. I tried the force code, but this didn't work as I didn't have administrator rights.

I also did not know my hard drive name the first two times I tried the code, and used different codes from Google, so there are two useless folders which I cannot delete due to the admin problem. Here's where I need your help!

Firstly, how do I obtain admin rights. I'm running off Live CD v7.10 today for the first time and I haven't created an account or anything. Secondly, will deleting these useless folders be safe? And even better, can I delete the folders they're in? (mkdir and media, which are both empty apart from the useless folders inside. I think the codes I used created them). 

Lastly, is it safe to use the force code (once I do eventually get admin rights and use the other code to access my HDD), I hope I won't corrupt anything more. 

Thanks for reading and I eagerly await your expertise! Please bear with my extreme lack of Ubuntu knowledge, I'm totally out of my comfort zone!

Ash. :guitar:

P.S by codes I mean the codes used in Terminal.

---

### Post by RollingStar on 2008-07-08
Please guys, there's a lot of personal stuff on my drive, is there no one who can help?

---

### Post by Afkpuz on 2008-07-08
There are 2 ways to make your harddrive readable in linux.  The 3rd I am not sure about, but it won't hurt to try

1.) Get a hold of a windows install disc (upgarde or clean install is fine, just not a system restore disc) and use microsoft's repair utility

2.) Force it to mount in linux

3.) (Not sure if this works, but might) Use Gparted




**FOR THE WINDOWS REPAIR METHOD**

Boot off the windows install disc and then when it gives you the choice to "repair" or something like that, take it.  I think its the first prompt you get when you boot from the disc.  

It will ask for your administrative password.  Chances are, if you don't know what it is, you didn't set one, so just leave it blank.  Once in a command prompt, type this.  Substitute "volume" for the drive name, like "C"
```
chkdsk volume:/r
``` 

Then, wait for eons and try to access the drive again in linux.  The repair could take a very long time.  
Here's microsoft's own page about how to repair a disc. [http://support.microsoft.com/kb/315265]("http://support.microsoft.com/kb/315265")






**Force it in linux**

I'm afraid I can't be specific in this area, but follow the guidelines given in that error message that you posted earlier.  If you post exactly what it said, I could be more specific.  But you would just paste whatever command the message gave you into the command line.  If you want to take this route, paste the exact error message and then I can help more.





**Gparted**
You can either boot from a gparted live CD or from an ubuntu live CD

To get to Gparted in Ubuntu: Goto System>Administration>Partition Editor

Then, once in gparted, use the drop down box in the top right to select the right hard drive and then right click on the partition that has your data on it.  Select "check" and I think it will try to fix the errors.  Not sure if this one works with windows drives (nfts), but I know it was able to fix errors on my linux drive (ext3)



Hope that helps.



P.S. You should wait more than an half and hour before bumping a thread.

---

### Post by RollingStar on 2008-07-08
Thanks a lot for the help, basically I'm trying to mount my HDD in Linux and then back up, heres is the codes I'm using and what I'm getting. 

ubuntu@ubuntu:~$ cd /mnt 
ubuntu@ubuntu:/mnt$ sudo mkdir windrive
ubuntu@ubuntu:/mnt$ sudo mount -t ntfs /dev/sda2 /mnt/windrive -o &#8220;umask=022&#8243;
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /mnt/windrive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /mnt/windrive ntfs-3g defaults,force 0 0
ubuntu@ubuntu:/mnt$ 

The guide then tells me to use the code 'ls windrive3', but this does not work. 

ubuntu@ubuntu:/mnt$ ls windrive
ubuntu@ubuntu:/mnt$ mount -t ntfs-3g /dev/sda2 /mnt/windrive -o force
mount: only root can do that

It seems as if I need to be logged in as 'root', whatever that is! 

Hope this helps you, 

Ash.

---

### Post by Afkpuz on 2008-07-08
Ok, well let me explain what "root" means.  In linux, there are permissions set on all files and folders.  So important files, like system files, are protected from being deleted.  Only the **root** user has the permission to delete/modify them.  So, to do what you want, you need to execute the command with root privileges.  It's very easy, just add "sudo" before the command.  So, this is what you need to paste into the command line to mount your drive.  

```
sudo mount -t ntfs-3g /dev/sda2 /mnt/windrive -o force
```

Try that out

---

### Post by RollingStar on 2008-07-08
Success! I could kiss you! Now to get backing up!

Is there anyway to add rep to your profile or thank for usefull posts, I have seen these features on other forums and I would be happy to do so for you! 

THANKS AGAIN! :-D

---

### Post by Afkpuz on 2008-07-08
If you want to thank me, click on the little star looking medal in the bottom right of any of my posts.  That's it.  Glad to help

---

### Post by RollingStar on 2008-07-08
Done for all posts. Thanks again.

---

### Post by RollingStar on 2008-07-08
Okay, so my online uploader needs Java to upload folders at a time. If I don't use Java, I'll have to do it one by one which will take a looong time! 

To my understanding you can't use Java in Live CD, so I need to install Ubuntu. I tried this, and got as far as the option ''How do you want to partition the disk'' and it has defaultly selected 'Guided - install to whole disk''  . Does this mean it will wipe my windows partition aswell? Or will it create a new partition. 

I just need the go ahead so I can go ahead and install this baby.

---

### Post by RollingStar on 2008-07-08
Sorry for another bump, but a simple answer will do!

---

### Post by RequinB4 on 2008-07-08
> **RollingStar said:**
> Okay, so my online uploader needs Java to upload folders at a time. If I don't use Java, I'll have to do it one by one which will take a looong time! 

To my understanding you can't use Java in Live CD, so I need to install Ubuntu. I tried this, and got as far as the option ''How do you want to partition the disk'' and it has defaultly selected 'Guided - install to whole disk''  . Does this mean it will wipe my windows partition aswell? Or will it create a new partition. 

I just need the go ahead so I can go ahead and install this baby.

You are correct -- "install to whole disk" will PERMANENTLY DELETE every partition, file, and operating system, including windows, on your hard drive.  This INCLUDES recovery partitions for windows.

If you want to keep a certain partition (ie, windows...), then you need to shrink the windows partition and use the available free space, which you can do under manual or GParted

---

### Post by arpanaut on 2008-07-08
That is correct...BUT!

If the windows partition is corrupted then gparted will not resize... AND!

Until the data that needs to be extracted from that partition is extracted then nothing should be done that may compromise that data.

Suggestions...
Find an online data store that does not require Java
Go buy an external drive to extract your data to.

If you have unpartioned space on the drive say 5-10 G then you will be able to install Ubuntu there.

Good Luck!

---


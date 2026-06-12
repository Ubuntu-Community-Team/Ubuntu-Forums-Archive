---
title: "How to work with files in dual boot setup"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by mindarson on 2013-12-12
Hello, I am an absolute beginner at Linux/Ubuntu. I am using a dual boot setup between Win7 and Ubuntu 12.04. Win7 is what I have always used before.

When I boot into Ubuntu, I can easily access all my files in the Windows partition in the file manager. What I'm seeking is a way to fully integrate all my old files into my new Ubuntu OS. For example, when using Rhythmbox to play my music files, I cannot find a way to 'load' the files into Ubuntu so the Rhythmbox app can just play them, like Windows currently does for me. Instead, if I want to hear a song, I have to go into the Windows partition and select each file individually. I can't even build a playlist!  

I hope what I'm asking is clear. When I used Windows, I did not have to go into a partition to access my files and folders. They were just ... there - wherever I put them. Is there a way to set Ubuntu up like this with those same files, without the brute force method of copying and pasting? (Seems to me that would be a waste of my computer's space, anyway?) 

Thanks for any guidance you can give!

---

### Post by Bucky Ball on 2013-12-12
Well, you can create a 'shared' partition so the files are just 'there' for any install, Win or Linux. Create an NTFS partition and put your music on there.

Generally, a shared/data partition is used because Win can't read/write EXT partitions. 

For clarity, you have all your personal data in folders in Windows? I presume your Win partition takes up most of the drive? If it does, go into Windows and shrink it, create a data partition with the free space, move your files onto there, share between OSs.

---

### Post by mindarson on 2013-12-12
> **Bucky Ball said:**
> Well, you can create a 'shared' partition so the files are just 'there' for any install, Win or Linux. Create an NTFS partition and put your music on there.

That's actually exactly what I wanted to do, and it's what I thought I was doing. See, I installed Ubuntu 12.04 from an image on a USB. I chose the option 'Install alongside Windows', because I thought I would be able to boot into Ubuntu and just have my existing files (which, yes, is in folders in Windows) there waiting for me. Which they are, just not in as convenient a structure as I'd anticipated.

Is it possible/advisable to uninstall Linux and redo the process, creating a NTFS partition? If so, do you know a resource that could help me with that, off the top of your head? 

> For clarity, you have all your personal data in folders in Windows? I presume your Win partition takes up most of the drive? If it does, go into Windows and shrink it, create a data partition with the free space, move your files onto there, share between OSs. 

Yes, all my data is in folders in Win7. The Windows partition does take up more of the drive. However, the install process I did was EXTREMELY simple, user-friendly, automated, etc. I believe it did explain that it would shrink the partition for me. 

Do you recommend I uninstall and start over with a true shared partition?

---

### Post by mastablasta on 2013-12-12
no need to uninstall. just create a new partition on windows side of disk (if you have soem space available - 2 times defragment and use windows disk manager to create new extended NTFS parittion)

what do you mean convenient structure? is the data in my documents perhaps? you could mount that point or put a shortcut to it so you can find it faster. otherwise partitions are just mounted same as in windows and you see what you see in windows (with advanced file manager that show all files etc. )

---

### Post by sotiris2 on 2013-12-12
I think Rhythmbox should be able to search a folder for music even if its in an ntfs, as long as he chooses that folder from Edit->Preferences->Music->Folders to watch  or whatever. 

The only catch is that first we will need to walk him through mounting his ntfs partition through fstab so that it is always available to rhythmbox. I need to go now so i can't offer more details yet. I will be back in a few hours but I think the other posters can easily guide you through that procedure which is a bit faster and does not require, repartitioning etc.

---

### Post by mastablasta on 2013-12-12
oh yeah another option is to automount NTFS partition on system boot. now it's only mounted when you select it in ubuntu file manager i believe. a bit of "sourcery" is needed to do that...

have a look here for GUI setup: [http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)
editing fstab file: [http://www.liberiangeek.net/2012/12/automatically-mount-ntfs-partitions-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/12/automatically-mount-ntfs-partitions-in-ubuntu-12-10-quantal-quetzal/)

---

### Post by sotiris2 on 2013-12-12
Ok lets make a mini-tutorial. First out the partition's UUID. 

  Run Gparted (if you dont have it install it via ubuntu software center or open a terminal (ALT+CTRL+T) and paste

```
sudo apt-get install gparted
```

  It will ask for your password. Write it normally, it wont show anything (not even *) but it is receiving it and press enter. You may have to press Y for yes (it will ask if you are sure you want to install it or something similar). 

  Then run gparted. It will show you a list of partitions on your hard drive. Find your partition (check filesystem column for ntfs) and right click on it. Select 'Information' from the right-click menu. The resulting windows has the partition's UUID . Copy that and paste it somewhere handy. You can close Gparted now, we wont need it no more.

Then make a folder in your own home folder. Name it as you wish, i will refer to it as [COLOR=#0000ff]folder[/COLOR]
Now open a terminal again (alt+ctrl+t) and paste this line

```
gksudo gedit /etc/fstab
```

Again enter your password. A program much alike notepad will open with a text file.
Paste the following in a new line after the last already existing. 

UUID=[COLOR=#00ff00]AAAAAAAAAAAAAAAA[/COLOR] /home/[COLOR=#ff0000]user[/COLOR]/[COLOR=#0000ff]folder[/COLOR]        ntfs    defaults,uid=[COLOR=#ff0000]user[/COLOR],gid=[COLOR=#ff0000]user[/COLOR] 0       0

Where [COLOR=#00ff00]AAAAAAAAAAAAAAAA [/COLOR]is the UUID you found out via Gparted.
[COLOR=#ff0000]user [/COLOR][COLOR=#000000]is your username[/COLOR] 
[COLOR=#0000ff]folder[/COLOR] [COLOR=#000000]is the name you gave the folder you created.

 Now save and close gedit. After you reboot folder should contain everything in your windows partition. If that is not good enough (say because your files are buried under Document&Setting/user/Documents etc..) you can right click on any folder and click 'make a link'. This will make a shortcut to that folder which you can place wherever you please for easy access. Since we made ubuntu automount the partition the link will always work without you having first to manually visit the partition. Then you can point Rhythmbox at your windows partition's music folder and it will built a library. (check my first post).
[/COLOR]

---

### Post by Bucky Ball on 2013-12-12
@sotiris: I like the mini-tutorial but the link mastablasta posted says it with pictures:

[http://www.liberiangeek.net/2012/12/...antal-quetzal/](http://www.liberiangeek.net/2012/12/...antal-quetzal/)

PS: 'sudo blkid' is another way to get the UUIDs using a terminal. ;)

---

### Post by sotiris2 on 2013-12-12
i know sudo blkid but i thing it's output can be confusing to a non cli comfortable person. Hey I had made a picture too i just forgot it :p

---


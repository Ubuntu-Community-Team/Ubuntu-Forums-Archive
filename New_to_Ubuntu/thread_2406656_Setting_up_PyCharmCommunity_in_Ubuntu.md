---
title: "Setting up PyCharmCommunity in Ubuntu"
date: 2018-11-23
forum: New to Ubuntu
---

### Post by alejandro202 on 2018-11-23
Hello Ubuntu Community. I've just started to use Ubuntu and recently I did a post about my disappointment with Ubuntu. I was glad to see quick response from the community and I'll will use this forum to sole my problems when using Ubuntu.

I am a Computer Science Student which likes to code, I mostly code in Python and used "PyCharmCommunity" when I had WIN10. I found "PyCharmCommunity" on the "Ubuntu Software" and went ahead and clicked install. Firstly, when trying to open a .py file from a USB the folder manager wouldn't let me look into the files of peripheral devices. This not only happens with "PyCharmCommunity" but also with other software like "KeePassXC". Secondly, when trying to print Hello World using "PyCharmCommunity" an error will pop up because no python interpreter could be found. As far as I am concerned python comes per-installed on Ubuntu. I don't know how to solve this problem. If anyone can help please feel free to do so.


I'm using Ubuntu 18.04.1 LTS.

[SOLVED] PyCharmCommunity Python Interpreter dir is inside /usr/bin  ([https://youtu.be/cVROiVgR_qg?t=452](https://youtu.be/cVROiVgR_qg?t=452))
[UNSOLVED] Unable to browse files of flash drives when file manager is opened through application. Nothing found inside /media.

---

### Post by oldfred on 2018-11-23
New users should try to use software that is in Ubuntu's repository first. 
That will have a lot fewer issues than software installed from anyplace else.

I tried to find pycharm in Ubuntu and it is not in the repository.

For Python I use Geany, but have to change a few settings to make it for python. Change tabs to spaces in editor, in projects, & in when saved. New version defaults to python3.
I am able to just copy code, save it  as .py file & run it in Geany. Or write my own code. 

I also use keepassx and keepassxc without issue, but installed from Ubuntu. How did you install it?

---

### Post by alejandro202 on 2018-11-24
Thanks for your reply.
The problem I have with KeepPasss is that when trying to open files through the open option it wont let me select peripheral memory devices. [IMG]https://imgur.com/a/44bTZ4Q[/IMG] ([https://imgur.com/a/44bTZ4Q](https://imgur.com/a/44bTZ4Q)). How can I access my flash memories?

---

### Post by The Cog on 2018-11-24
If you have mounted your flash devices, the contents are probably visible in /media/lemur. You have to mount the flash device before you see its contents, and generally do this just by clicking its icon on the left.

---

### Post by alejandro202 on 2018-11-24
Thanks for your reply.

I have connected all my pendrives to a USB Hub. I'm able to read them through the "FIles" application. Within the "FIles" application, a small icon appears next to my Flash Drives, when I place my cursor on top og it displays "Unmount". I went to /media and it is empty.

---

### Post by The Cog on 2018-11-24
OK, while you have one of the flash drives open so you can read the files, open a command prompt and enter the command **lsblk** which will show you all the drives and their mount points. If you can't figure out which one is the flash drive, remove it and run the same command and look to see what has disappeared. Or you can paste the outout here and we can try to figure it out.

---

### Post by alejandro202 on 2018-11-24
"NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0    13M  1 loop /snap/gnome-characters/103
loop1    7:1    0   3,7M  1 loop /snap/gnome-system-monitor/57
loop2    7:2    0 483,6M  1 loop /snap/libreoffice/90
loop3    7:3    0 270,4M  1 loop /snap/pycharm-community/99
loop4    7:4    0 173,3M  1 loop /snap/spotify/26
loop5    7:5    0  14,5M  1 loop /snap/gnome-logs/45
loop6    7:6    0    13M  1 loop /snap/gnome-characters/139
loop7    7:7    0   2,3M  1 loop /snap/gnome-calculator/180
loop8    7:8    0  87,7M  1 loop /snap/keepassxc/49
loop9    7:9    0  34,6M  1 loop /snap/gtk-common-themes/818
loop10   7:10   0  88,2M  1 loop /snap/core/5897
loop11   7:11   0   2,3M  1 loop /snap/gnome-calculator/260
loop12   7:12   0  98,9M  1 loop /snap/telegram-desktop/291
loop13   7:13   0  34,7M  1 loop /snap/gtk-common-themes/319
loop14   7:14   0 140,7M  1 loop /snap/gnome-3-26-1604/74
loop15   7:15   0    45M  1 loop /snap/core18/442
loop16   7:16   0 140,9M  1 loop /snap/gnome-3-26-1604/70
loop17   7:17   0  14,5M  1 loop /snap/gnome-logs/37
loop18   7:18   0  86,9M  1 loop /snap/core/4917
loop19   7:19   0   3,7M  1 loop /snap/gnome-system-monitor/51
loop20   7:20   0 135,8M  1 loop /snap/discord/79
loop21   7:21   0 148,4M  1 loop /snap/photoscape/6
loop22   7:22   0 169,4M  1 loop /snap/gimp/61
sda      8:0    0 119,2G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2   8:2    0 118,8G  0 part /
sdb      8:16   0 931,5G  0 disk 
&#9500;&#9472;sdb1   8:17   0 879,7G  0 part 
&#9492;&#9472;sdb2   8:18   0  12,8G  0 part 
sdc      8:32   0   1,4T  0 disk 
&#9492;&#9472;sdc1   8:33   0   1,4T  0 part 
sdd      8:48   1  14,5G  0 disk 
&#9492;&#9472;sdd1   8:49   1  14,5G  0 part /media/lemur/OS
sde      8:64   1   962M  0 disk 
&#9492;&#9472;sde1   8:65   1 961,7M  0 part /media/lemur/KEYPASS
sdf      8:80   1  14,9G  0 disk 
&#9492;&#9472;sdf1   8:81   1  14,9G  0 part /media/lemur/DUCKY A

"

---

### Post by The Cog on 2018-11-24
So you have three disks currently mounted under /media, called OS, KEYPASS and DUCKY A. Why do you say /media is empty? What do these this commands tell you? :
```
ls -l /media/lemur
ls -l /media/lemur/KEYPASS
```

---

### Post by alejandro202 on 2018-11-24
ls -l /media/lemur returns:
"total 56
drwxr-xr-x 5 lemur lemur 32768 ene  1  1970 'DUCKY A'
drwxr-xr-x 4 lemur lemur 16384 ene  1  1970  KEYPASS
drwxr-xr-x 5 lemur lemur  8192 ene  1  1970  OS"

ls -l /media/lemur/KEYPASS returns:
"total 1312
-rw-r--r-- 1 lemur lemur     24 nov 11 21:12  autorun.inf
-rw-r--r-- 1 lemur lemur 577278 nov 21 22:00  deleteme2.kdbx
-rw-r--r-- 1 lemur lemur 107593 nov 11 21:11  pass.ico
-rw-r--r-- 1 lemur lemur   5391 nov 23 21:25  passwords.txt
drwxr-xr-x 2 lemur lemur  16384 nov 11 20:52  Portable
drwxr-xr-x 2 lemur lemur  16384 ago  6 23:38 'System Volume Information'
-rw-r--r-- 1 lemur lemur 559790 nov 23 21:36  ubuntu.kdbx"

All of my flash drives are mounter correctly. I can see their location through the "Disks" Application. But when I want to open files from KEEPASSX or other software. If I go to /media there is nothing. ([https://imgur.com/a/lTfc3QW](https://imgur.com/a/lTfc3QW))

---

### Post by The Cog on 2018-11-24
Sorry but I don't understand that. I just put a .kbdx file on a flash drive here and KeePassX shows it just fine. It won't show the file if I rename it to .kbdz, but your files look to be named OK. But then you say that KeePassX doesn't even show the names of the folders like KEYPASS inside /media/lemur and I can't think why that might be.

---

### Post by oldfred on 2018-11-24
On my system it did not directly show my flash drive.
But if I went to / and then /media and /media/fred it showed flash drive and in that my .kdbx file.

---

### Post by deadflowr on 2018-11-24
Please post the output for
```
snap interfaces pycharm-community
```
You have the snap package variant, which may have some restrictions.
Depending if it's opened up (with the classic mode) or if it's set with the default snap values of very confined.

Luckily it's fixable to allow more open access to the snap packages.

---


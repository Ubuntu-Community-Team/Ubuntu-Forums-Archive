---
title: "Advice For Messed Up System"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by acimi66 on 2013-03-11
Jeezzz, where do I begin. I'm running 12.10
It started with a warning notice that my / "root Partition" was at 96% full. I checked it with Gparted and sure enough. I did some reading on resizing the partition but then I thought well maybe I've just got too might old **** on my computer.
So I had a look in the software center and yes I found multiple image editors, MP3 players and some other stuff. I also noticed I had multiple programming editors, from when I was looking at trying some of out. I see I have python 2.7 and 3.2 so I go ahead and uninstall python 2.7. I get a window that says these files will also be affected.I don't check it and just say go ahead.#-o

I lost unity and any way of using the computer. I manage to reinstall unity, but it is very unstable I also lost other programs. My windows are now flat and with color almost like in some sort of safe mode. I just turn my computer back on and it said could not log in to "ubuntu". When I got into terminal mode (ctrl + f2) I found unity was not installed, so I did apt-get and manged to get back into my desktop.

My / root partition is at 85% ( 4 Gb swap + /home 354Gb unused). So I am wondering do you think It is acting up beccause it doesn't have enough space on / i.e. not saving unity OR did I mess up the system with un-installing stuff  (stuff I thought was redundant, mind you).

I would love some advice on this.

---

### Post by Cheesemill on 2013-03-11
A large number of the core components of Ubuntu depend on Python, when you uninstalled it all of these programs got uninstalled as well (you will have been warned that this was going to happen in the dialog box you ignored).

Try the following command, it should reinstall all of the programs that were removed...
```
sudo apt-get install ubuntu-desktop
```

---

### Post by acimi66 on 2013-03-11
Hey Cheesemill,
Thanks for the response. That has certainly brought back the soft dark corners I remember so well, as my desktop.

But as to the question of space on /root does 85% full start to slow the system down?

Any thoughts

---

### Post by DuckHook on 2013-03-11
85% full root partition does not bode well. Assuming you use ext4, the file system is exceptionally good at keeping itself minimally fragmented until you breech the 80% usage number. Thereafter, it will start to fragment your files which will slow you down permanently. Ubuntu will also give you no warning as you approach 100% and will just one day stop working. With HDDs as cheap as they are these days, time to consider a cheap upgrade. We have no idea of your current disk size or config so the only way to give further advice is if you provide more info:```
df -h
```

---

### Post by tgalati4 on 2013-03-11
No space = no linux.

---

### Post by acimi66 on 2013-03-11
Thanks for the help. yes it is ext4 .

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   16G  1.9G  90% /
udev            1.9G  8.0K  1.9G   1% /dev
tmpfs           767M  1.2M  766M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  1.5M  1.9G   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sda6       436G   82G  333G  20% /home

I have plenty of space on the extended partition but the swap sits between it and root, so I am not sure about resizing root.
I could go through and uninstall some older programs...

What do you think?

---

### Post by alphacrucis2 on 2013-03-11
Check that your log files aren't getting filled up with some repeating error message. 16gb seems a lot for the system + typical programs you would install.

---

### Post by DuckHook on 2013-03-11
> **alphacrucis2 said:**
> Check that your log files aren't getting filled up with some repeating error message. 16gb seems a lot for the system + typical programs you would install.

+1

16 GB is more than sufficient. I suspect log files also. most of them are located in /var/log

---

### Post by acimi66 on 2013-03-11
Any file in particular that I am looking for?

Is the a command for checking log error messages?

I tried this command:
ls -lSr = files by size
these are  the two biggest

-rw-rw-r--   1 tony tony  5331095 Mar  4 19:18 C:\nppdf32Log\debuglog.txt
-rwxrwxr-x   1 tony tony 82787328 Feb  2 15:20 netbeans-7.3rc1-javase-linux.sh

---

### Post by DuckHook on 2013-03-11
First, a word of warning:


Be prepared for some geeky and obscure techno-stuff. When you go through log files, you are peering into the guts of the OS.


Here's how I would approach it:


1. Using your file manager, bring up the properties of the /var/log directory. This will show you how large the directory is. If, as I suspect, this one directory is gigabytes in size, then you know that some rogue process or service is acting up and writing scads of log data to one of your log files.
2. Repeat the above process with all subdirectories under /var/log.
3. Set your file manager to details list mode and scan each of the log files. The bloating file(s) should stick out like a sore thumb based on its/their size.
4. You can open log files with gedit. You can also use log viewer.
5. Look for recurring log entries. Rogue apps/services generate log bloat by recording repeating errors continuously. The culprits should be obvious. Aside from such general observations, it is impossible to give specific instructions because we don't know what is generating the errors (if any).
6. Obvious keywords are: error, segfault, fatal, etc.
7. If you find a likely candidate and it is too obscure for you to guess its cause, post the segment back to this thread and/or Google for it. Google is often exceptionally accurate on such matters provided you give it a long enough data string to search for.


It's well past midnight where I am and I will be travelling all of tomorrow. I'm sure others on this forum are more than willing to assist.


Good luck!

---

### Post by acimi66 on 2013-03-12
Hey DH thanks for the idea but no luck.Have a safe trip.

The /var folder was only 1.3 Gb and the /log folder was only 17.7 Mb.
I went and check the properties on every folder in / but the /home folder was the only one with any weight 81Gb which is what shows up on here  /dev/sda6       436G   82G  333G  20% /home from previous post results.

Now I really am baffled, not that that is saying much.

So the only thing that has happened lately was...

I had to use gksudo nautilus to move a lot of files Gbs worth, to an sd card that had permission restrictions. the only way it would let me move the file was to pull the file into the folder that Nautilus opened then I could move them onto the disk. Once I had the files on the disk I "moved to trash" from the window that Nautilus had opened. When I checked gksudo nautilus just now, it was empty, I tried to empty the trash from with that window I got and error message saying  

THE FOLDER CONTENTS COULD NOT BE DISPLAYED. Sorry,could not display all the contents of "trash": Operation not supported

Is the culprit in there somewhere?

Anyone got any ideas?

---

### Post by alphacrucis2 on 2013-03-12
Ah. The culprit is probably that if you delete files from nautilus under gksu then the file get dumped into the "root" login trash folder. Root's home folder is under /root not under /home. IIRC "empty trash" under gksu nautilus doesn't work. What I would do is as follows.

1. Start up a terminal and then enter the following command (sudo interactive mode):

```
sudo -i
```

2. Navigate to root's trash folder (enter the command exactly including the dot in front of local and the capital T):

```
cd /root/.local/share/Trash/files
```

Make sure the bash prompt changes to look something like this:

```
root@............:~/.local/share/Trash/files#
```

You can list what is there via 

```
ls -l
```

3. Now erase the files. Warning this command is extremely dangerous run as root - make sure you are in the right directory as per the bash prompt above.

```
rm -rf *
```

---

### Post by Cheesemill on 2013-03-12
The following command is useful for finding out which directories are using all your space...
```
du -h --max-depth=1 | sort -hr
```
I actually have it as an alias for du on my system.

It will show the total size of all of the sub-directories in your current location, sorted by size (largest first).
```
rob@raring:/mnt/data$ du -h --max-depth=1 | sort -hr
253G   .
69G    ./videos
52G    ./isos
43G    ./backups
38G    ./music
30G    ./vms
20G    ./downloads
2.5G   ./pictures
1.7G   ./SteamLibrary
75M    ./Books
32M    ./documents
2.9M   ./USB Maplin Backup
72K    ./bin
16K    ./lost+found
rob@raring:/mnt/data$
```

---

### Post by acimi66 on 2013-03-12
Well I made it as far as you showed but when i run the rm -rf command it just goe back to 
[email]root@tony-Satellite-L650:~/.local[/email]/share/Trash/files# 


root@tony-Satellite-L650:~# cd /root/.local/share/Trash/files
[email]root@tony-Satellite-L650:~/.local[/email]/share/Trash/files# ls -l
total 172
-rw-r--r--  1 root root  31399 Jan 24  2010 Arrawarra_point.jpg
drwxr-xr-x 27 root root   4096 Mar  7 23:14 books
-rw-r--r--  1 root root   2636 Mar  7 20:01 gparted_details2.htm
-rw-r--r--  1 root root   4534 Mar  5 19:19 gparted_details.htm
drwxrwxr-x  3 root root   4096 Mar  5 19:02 Mer-plasma-active
drwxr-xr-x 39 root root   4096 Mar  7 22:14 Music
drwxr-xr-x 39 root root   4096 Mar  7 22:14 Music.2
-rw-rw-r--  1 root root 104671 Mar 17  2012 shining Photography Ocean Waves wallpapers.jpg
drwxrwxr-x  2 root root   4096 Jun 12  2012 URTEXT
drwxrwxr-x  2 root root   4096 Jun 12  2012 URTEXT.2
[email]root@tony-Satellite-L650:~/.local[/email]/share/Trash/files# rm -rf
[email]root@tony-Satellite-L650:~/.local[/email]/share/Trash/files#

At least I know there are 172 files But the files are still there. ? what did I do wrong ?

---

### Post by Cheesemill on 2013-03-12
That command is missing a character, it should be...
```
rm -rf *
```

---

### Post by acimi66 on 2013-03-12
[SIZE=7]YES!!![/SIZE]


Satellite-L650:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G  7.2G   11G  42% /
udev            1.9G   12K  1.9G   1% /dev
tmpfs           767M  1.2M  766M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  2.9M  1.9G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda6       436G   82G  333G  20% /home

Cheesemill, alphacrucis2, DuckHook you guys rock!!
Thanks so much for your help. And that's why I love linux. No matter how much I can **** it up someone is there to help.
Cheers

P.S. How do I mark this as SOLVED?

---

### Post by arpanaut on 2013-03-12
Just remember that if you are deleting stuff from a root nautilus, say, "gksu nautilus" 
you will need to run that command from time to time to keep root's trash from filling up again.

---

### Post by alphacrucis2 on 2013-03-12
> **Cheesemill said:**
> That command is missing a character, it should be...
```
rm -rf *
```

Whoops! Thanks Cheesemill - I missed that :redface:

---

### Post by DuckHook on 2013-03-13
> **Cheesemill said:**
> The following command is useful for finding out which directories are using all your space...
```
du -h --max-depth=1 | sort -hr
```

Awesome command. Thanks for sharing it. Very useful and should be used whenever someone inquires on these forums about troubling lack of disk space. It's going into my collection of crazy-useful commands.

---

### Post by squakie on 2013-03-13
The "solved" option isn't in the thread tools right now because it wasn't working.  What you can do is:

- go to your very first opening post in the thread
- select edit, then select advanced
- changed the title to have [SOLVED] at the front
- save the change

---

### Post by techvish81 on 2013-03-13
use bleach bit (root) to clean your system often, untill you reinstall with a better partition scheme.

---

### Post by DuckHook on 2013-03-13
> **techvish81 said:**
> use bleach bit (root) to clean your system often...

If you know what you are doing, bleachbit can be very useful, but it can also be dangerous especially in the hands of new users who are unfamiliar with Linux. Example: it will delete old kernels that could be useful to fall back on if new updates break the OS. I would recommend that new users temporarily avoid both bleachbit and computer janitor until they are more familiar with the OS. Ubuntu does not accumulate nearly as much cruft as Windows and does not need to be cleaned with the same vigour, which is what bleachbit and computer janitor were designed for.

@OP

If you are forced to delete files using gksudo nautilus, then a simple method to bypass the trash altogether is to select the file and use <Shift>+<Delete>. This key combo has the same effect as```
sudo rm -f
```but without the dangers of the command line (which gives you no view of the actual files you are deleting). This is a far better way for new users to delete permanently. However, be forewarned that any file deleted this way is not retrievable because it has not been shuffled off to the trash.

---


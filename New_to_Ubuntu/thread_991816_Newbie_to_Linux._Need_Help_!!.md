---
title: "Newbie to Linux. Need Help !!"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by gaurav200x on 2008-11-24
Dear All,

I have just switched to Linux from Windows and need help. I have installed Xubuntu 8.10 and need help regarding certain things.

1) I am unable to run any media files, viz. .mp3, .avi, etc. Will I need to install my hardware drivers for that? (I checked up for any proprietary drivers and found none). I am also told I will need to install some deb files. Kindly guide.

2) I am unable to install any softwares. When i try to run any software, it is taken over by 'Archive manager' or 'Software sources' and i don't know how to install any software. Kindly guide on this too.

3) My hdd has two partitions, the first one having Xubuntu and the second one having my media files. Now i assume that the 2nd partition needs to be internally mounted. Can this be set to happen automatically, everytime i reboot my PC. At present, i have to open the totem media player and open the directories in the 2nd partition for it to be visible in /media.

4) At times, some windows get hanged while operating. Even when i tried to kill/stop the process, it didn't work. Despite a long time, there was no response and ultimately i had to reboot my machine. Kindly advice what can be done in such situations.


p.s. i know its a lot to ask, but i have just started learning linux and would need the help of this community for that :)

Thanks in advance.

---

### Post by Tom--d on 2008-11-24
1. Go to Add/Remove and install Gstreamer (You will see which ones to install, it says the codec).

2. I recommend looking in Add/Remove and Synpatic Package Manager. Its not like windows you have to go searching for software, its all in a thing called repositories. It sorts all the information for programs. Click them - Install them.

Also, In ubuntu, your Looking for a .deb file. This file will install on the system.
A tar.gz is normally source code. If not, extract it and file out whats in side.

3. Someone with better knowledge could help you better. There is a file called /etc/fstab . With your partition in there (This is the bit I don't know how) it will automatically Mount at start up.   

4. Open System Monitor and then kill the process from there.


Ps. Hey, don't worry. Thats why were here ;) Also, Its a totally different OS. Your not going to learn it over night.

---

### Post by beno1990 on 2008-11-24
> **gaurav200x said:**
> Dear All,

I have just switched to Linux from Windows and need help. I have installed Xubuntu 8.10 and need help regarding certain things.

1) I am unable to run any media files, viz. .mp3, .avi, etc. Will I need to install my hardware drivers for that? (I checked up for any proprietary drivers and found none). I am also told I will need to install some deb files. Kindly guide.


Open Synaptic package manager (in System on the XFCE menu)

When inside, do a search for mp3; this should find a package which gives you MP3 support.

> 
2) I am unable to install any softwares. When i try to run any software, it is taken over by 'Archive manager' or 'Software sources' and i don't know how to install any software. Kindly guide on this too.


As above, on the XFCE menu, go to Synaptic package manager under system.

> 
3) My hdd has two partitions, the first one having Xubuntu and the second one having my media files. Now i assume that the 2nd partition needs to be internally mounted. Can this be set to happen automatically, everytime i reboot my PC. At present, i have to open the totem media player and open the directories in the 2nd partition for it to be visible in /media.


By default, a partition without a specified mount point will be mounted in /media/. If you want to change that, you'll have to download a partition manager and change the partition to have a mount point somewhere else on your filesystem. But be warned; editing your paritions can be dangerous!

> 
4) At times, some windows get hanged while operating. Even when i tried to kill/stop the process, it didn't work. Despite a long time, there was no response and ultimately i had to reboot my machine. Kindly advice what can be done in such situations.


On the XFCE menu, you should be able to find a system monitor. If you find the program on the processes list, you can right-click and force kill the program.

---

### Post by L Campbell on 2008-11-24
> **gaurav200x said:**
> Dear All,

I have just switched to Linux from Windows and need help. I have installed Xubuntu 8.10 and need help regarding certain things.

1) I am unable to run any media files, viz. .mp3, .avi, etc. Will I need to install my hardware drivers for that? (I checked up for any proprietary drivers and found none). I am also told I will need to install some deb files. Kindly guide.

2) I am unable to install any softwares. When i try to run any software, it is taken over by 'Archive manager' or 'Software sources' and i don't know how to install any software. Kindly guide on this too.

3) My hdd has two partitions, the first one having Xubuntu and the second one having my media files. Now i assume that the 2nd partition needs to be internally mounted. Can this be set to happen automatically, everytime i reboot my PC. At present, i have to open the totem media player and open the directories in the 2nd partition for it to be visible in /media.

4) At times, some windows get hanged while operating. Even when i tried to kill/stop the process, it didn't work. Despite a long time, there was no response and ultimately i had to reboot my machine. Kindly advice what can be done in such situations.


p.s. i know its a lot to ask, but i have just started learning linux and would need the help of this community for that :)

Thanks in advance.

This should help you:-

[http://www.psychocats.net/ubuntu/mp3](http://www.psychocats.net/ubuntu/mp3)

---

### Post by gaurav200x on 2008-11-24
> **Tom--d said:**
> 1. Go to Add/Remove and install Gstreamer (You will see which ones to install, it says the codec).

2. I recommend looking in Add/Remove and Synpatic Package Manager. Its not like windows you have to go searching for software, its all in a thing called repositories. It sorts all the information for programs. Click them - Install them.

Also, In ubuntu, your Looking for a .deb file. This file will install on the system.
A tar.gz is normally source code. If not, extract it and file out whats in side.


The thing is that my machine doesn't have an internet connection and i browse from a cafe. I did try to install the codecs ' G Streamer' but when there is a dialogue box which says 'i will need internet connection to continue' i get stuck.

Is it possible to download the same and then transfer to my laptop in a pen drive?

How do i get the .deb files?

---

### Post by krtica on 2008-11-24
I'm a beginner on Ubuntu as you.
I can answer you on 2). :D
Click on Application -> Add/Remove... and "Add/Remove Applications" window will appear. There you can Install/Uninstall most of thing you need.
You can change options by the label "Show:" and choose how "wide" and what kind of "applications collections" ("repositories", I think)you wanna use/install/uninstall. You can also use "Search:" option, which I found very useful.
Only in rare occasions you will need to install some application which is not listed there. Then, try to find .deb installation file, which you can simply install by double-clicking.
If you are unable to find .deb, then you will probably find some archive file, like .tar.*. You can simply uncompress archive by double clicking on archive, or right-click and "Extract Here". Than you maybe will need additional searching and help for using Terminal.

Hope that I help... :???:

(My God! I'm so late. :D)

---

### Post by madsc89 on 2008-11-24
> **gaurav200x said:**
> Dear All,

I have just switched to Linux from Windows and need help. I have installed Xubuntu 8.10 and need help regarding certain things.

1) I am unable to run any media files, viz. .mp3, .avi, etc. Will I need to install my hardware drivers for that? (I checked up for any proprietary drivers and found none). I am also told I will need to install some deb files. Kindly guide.

2) I am unable to install any softwares. When i try to run any software, it is taken over by 'Archive manager' or 'Software sources' and i don't know how to install any software. Kindly guide on this too.

3) My hdd has two partitions, the first one having Xubuntu and the second one having my media files. Now i assume that the 2nd partition needs to be internally mounted. Can this be set to happen automatically, everytime i reboot my PC. At present, i have to open the totem media player and open the directories in the 2nd partition for it to be visible in /media.

4) At times, some windows get hanged while operating. Even when i tried to kill/stop the process, it didn't work. Despite a long time, there was no response and ultimately i had to reboot my machine. Kindly advice what can be done in such situations.


p.s. i know its a lot to ask, but i have just started learning linux and would need the help of this community for that :)

Thanks in advance.

1: You have to install a package with those codecs. Open a terminal (applications -> accessories) and enter ```
apt-get install gstreamer*
```

2: In ubuntu, everything is installed in packages, see if your program is located in synaptic.
What kind of programs are you trying to install? i.e. exe

3: Open a file browser, and navigate to /media/disk

4: It is necessary to know what causes the problem, and which program it is. Try opening through terminal, just write the program's name, and the program will open. try to reproduce the crash, and post the output of the terminal here.

---

### Post by beno1990 on 2008-11-24
> **gaurav200x said:**
> The thing is that my machine doesn't have an internet connection and i browse from a cafe. I did try to install the codecs ' G Streamer' but when there is a dialogue box which says 'i will need internet connection to continue' i get stuck.

Is it possible to download the same and then transfer to my laptop in a pen drive?

How do i get the .deb files?

You can get all Ubuntu packages manually from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

However, this won't do any dependency resolution so you'll need to resolve the dependencies by hand based on what it tells you on the package's page.

---

### Post by Tom--d on 2008-11-24
> **beno1990 said:**
> You can get all Ubuntu packages manually from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

However, this won't do any dependency resolution so you'll need to resolve the dependencies by hand based on what it tells you on the package's page.

There are quite a few packages you need to download.

Its best just to do it through Add/Remove with internet. It will be done in like 10 seconds :D

The reason you cannot play MP3's on a default install of Ubuntu is due to licensing.

---

### Post by hyper_ch on 2008-11-24
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by gaurav200x on 2008-11-24
> **Tom--d said:**
> There are quite a few packages you need to download.

Its best just to do it through Add/Remove with internet. It will be done in like 10 seconds :D

The reason you cannot play MP3's on a default install of Ubuntu is due to licensing.

I think the following should be the necessary package
```

http://packages.ubuntu.com/intrepid/i386/gstreamer0.10-plugins-farsight/download
```

How do i install a .deb file ?

---

### Post by beno1990 on 2008-11-24
Just double click it and a package manager will open with an "install package" option. :)

---

### Post by gaurav200x on 2008-11-24
> **beno1990 said:**
> Just double click it and a package manager will open with an "install package" option. :)

I hope it's the correct package.

---

### Post by gn2 on 2008-11-24
> **gaurav200x said:**
> The thing is that my machine doesn't have an internet connection and i browse from a cafe.

In which case Ubuntu is far from the best distro for your needs.

If you can download (or get a CD in the mail) and install [Linux Mint]("http://www.linuxmint.com/download.php"), all your media files will be playable without all the problems of finding all the required Ubuntu packages yourself.

There is an Mint Xfce edition similar to Xubuntu.

---

### Post by Tom--d on 2008-11-24
> **gn2 said:**
> In which case Ubuntu is far from the best distro for your needs.

If you can download (or get a CD in the mail) and install [Linux Mint]("http://www.linuxmint.com/download.php"), all your media files will be playable without all the problems of finding all the required Ubuntu packages yourself.

There is an Mint Xfce edition similar to Xubuntu.

+1

If there is no internet at all to Ubuntu, Linux Mint comes with codecs and a lot more on it.

---

### Post by Michael.Godawski on 2008-11-24
If you still want to use the one and only original Ubuntu, have a look at the community documentation dealing with restricted formats:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

But I agree: Linux without Internet can be challenging.

---

### Post by allenbradley on 2008-11-24
simpler still. Download VLC. It supports mp3 without the gstreamer codecs. You can get it from 
[HTML]http://linux.softpedia.com/progDownload/VLC-Download-2608.html[/HTML]

Another solution : Download Wine and use Foobar.

---

### Post by Tom--d on 2008-11-24
VLC has many dependencies as well..#-o

---

### Post by Wickd on 2008-11-24
Answer to Question 1: 

Just add your media files to Rythmbox and it should automatically ask you to download the corresponding codecs.


Answer on Question 3

Can you see the partition at all? If you go to Places --> Computer, do you see your second partition and can you mount it?

If you get a "permission denied" error message open your terminal and type the following;

sudo nautilus

When this opens, open the partition and go to properties. Under the Permissions tab change the "Owner" section to your username and set the folder access to Create and Delete Files

If that's not it, what type of file system is it? NTFS?



Hope that helps
Cheers

---


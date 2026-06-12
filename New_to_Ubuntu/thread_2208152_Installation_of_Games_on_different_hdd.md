---
title: "Installation of Games on different hdd"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by gradyrus on 2014-02-26
Hello all new ubuntu 13.10 (linux) user here. I have a custom built pc with a 120GB SSD HyperX, 60GB SSD HyperX and a 3TB HDD. My question is I want my 120GB SSD for my Ubuntu and my 60Gb SSD for my World of Warcraft install and my 3TB HDD for other games such as Steam, Spotify FTB ect. How do i chose a different HDD(SSD) to install the different programs to, I am sorry if this has already been answered elsewhere i have tried searching for it on google with no luck. If someone has a step by step guide for this I would be most greatly appreciative.

---

### Post by ajgreeny on 2014-02-26
I do not think it is possible to do that in any simple way using Linux as the filesystem does not work in the way that Windows does and there is no similar folder to the **Program-files**, or whatever it is called in Windows.

You might be able to get somewhere near what you need by using a separate partition for /usr on the appropriate disk, which is where all the program/application files go, but even doing that would not allow you to put WOW on one disk and all the rest on another disk, and using that method is a gross oversimplification of how it's done in Linux, so you may need to rethink things a bit more.

---

### Post by gradyrus on 2014-02-27
hmmm so no customization where you want to install and run things from, surely there must be some sort of open source software that allows this to be a reality???

---

### Post by jones quest on 2014-02-27
You can automount your hard drives in /etc/fstab, then make symbolic links to you games on those mount points.

 For instance as WoW is a windows game it lives in: /home/<username>/.wine/drive_c/Program Files (x86)/<WoW or something like this>. 

You move that folder over from your hard drive A to your hard B. And make a symlink:  ln -s </media/Wow/WoW> </home/<username>/.wine/drive_c/Program Files (x86)/<WoW>

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://askubuntu.com/questions/214643/help-with-creating-symbolic-link](http://askubuntu.com/questions/214643/help-with-creating-symbolic-link)

---

### Post by Impavidus on 2014-02-28
You can use symbolic links and some programs accept command line arguments or environment variables to tell them they have to read their data files from a non-standard location, but there is no easy way to move specific programs or program data to other parts of the file system. You could move /usr/share/games to a different partition if you want – it contains the data files of most games – but I don't think it will do much good.

On Linux and Unix, most files are stored in specific directories based on their usage patterns, whereas Windows keeps files belonging to the same applications together. This has been a long standing tradition. Advantages of the Linux way are that, for example, two machines, one 32 bit and the other 64 bit, can have their own versions of an executable, but share their data files from a network drive, that rarely modified files (like executables) can be kept in more secure locations whilst still allowing ordinary users to add data files/add-ons, etc. The downside is that it sometimes gets a bit complicated to keep track of all files belonging to any specific application.

---


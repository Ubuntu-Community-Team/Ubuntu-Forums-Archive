---
title: "Install Button Disabled"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by Anamica on 2012-08-06
Hello guys im new to ubuntu and this forum.I ve win 7 and ubuntu 12.04  both 64 bit as dual boot

My Sys config is 

Sony VAIO 36EH
4GB RAM
Intel core i3-2350M 2.30Ghz processor and 500 Gb HD
nVidia 512MB graphics


My problem is ever since i installed ubuntu i cannot install any softwares using the software center. I thought about connecting to internet and then solve it but i cant do that as well as wvdial is not present in my Ubuntu.. Im using huawei e182e datacard with BSNL sim in it.

If I insert my data card it doesnt show thats its detected i.e i dont get any popups like in windows. But using the network option i configured it with default options but cannot dial a conncetion.

I tried to download the wvdial package separately using windows and tried to install it with Ubuntu, since the install button is not working im unable to connect to Internet too. I have no access/resources to Wifi connection. Im trying everything for 3 days and I dont wanna give up.. Please help me guys:confused:

---

### Post by audiomick on 2012-08-06
I gather you have the problem that you can't install what you need to get your internet connection working because you have no internet connection.

It is not clear to me from your post: is the connection you are trying to get working a dial-up connection?

The Huawei card you refer to; is that what is also referred to as a 3G dongle? And BSNL a mobile phone provider?

Any rate, you wont be able to install anything from the software centre until you get some form of internet connection happening.

---

### Post by Anamica on 2012-08-06
Thanks for your quick response audiomick.. huawei e182e is a dial up connection and its a 3G dongle and im using BSNL provider.. i downloaded the wvdial package but i cannot install it using Software Center as the INSTALL BUTTON DISABLED . how do i do it manually im completely a newbie to linux so if im going to use the command line to install a software , how do i do it? commands please? also suggest me how to use the path in terminal like if im having wvdial package in d: drive.. thank you

---

### Post by audiomick on 2012-08-06
Ok, first of all, I think your Huawei 3G dongle should actually work, but we'll leave that for the minute.

What is the package for wvdail that you have? Is it a .deb package, or is it perhaps a .tar or .tar.gz?

Additionally, I gather you can  open the windows partition that referred to as d: drive using the file manager in Ubuntu. Is this true?

---

### Post by Anamica on 2012-08-06
Its a .deb package i ve downloaded it from this site [http://www.ubuntuupdates.org/package/core/precise/main/base/wvdial](http://www.ubuntuupdates.org/package/core/precise/main/base/wvdial)
i clicked on 64 bit deb package and downloaded it

yes sir i can see the windows partition in my Ubuntu file manager as 112gb space and not named as any drive

I ve installed Ubuntu in a 40 gb free space which i allocated separately for it.. i ve installed win 7 in c drive.. during the installation it asked for a mount point name which i gave "/" as the name. im not sure its the name or something but its shown in a list box and i ve chosen the first one i.e "/"

---

### Post by audiomick on 2012-08-06
Ok.

I think you can install it straight from the windows partition, but I personally would copy it across to the Linux partition first. I have ocassionally had odd behaviour when trying to do things with files on Windows partitions.

Do this:
Boot in to Ubuntu.
Open the file manager Nautilus. This means go to "places" and open your home folder.

In Nautilus, the file manager, if you press F3 you get a split window. I find this very useful for copying files. Press F3 again to get back to a single window. Open your home folder, press F3 to get a split window and navigate to your Windows partition where the package you want to install is. Drag the package across to the Linux side, and close down the windows side.

I am not qute sure here, but I think you now should be able to simply click on the .deb package. I believe this will cause the software centre to open and go ahead and install the package. If this is not the case, then it will be a right click on the package and choose "open with" out of the context menu and tell it to open with the software centre. Any rate, it is a pretty automatic process that should be easy to work out.

Regarding the names of your partitions: The terminology C: or D: and so on is Windows terminology. Those are names that windows uses for partitions, but do not have any particulare relevance in Linux. 

Your drive has a partition table on it. Windows associates those C: type of labels to the partitions in the table. Linux calls the partitions things like sda1, sda2, sdb5, or whatever. Basically, sd can be understood to mean a hard drive, sda is the first drive, sdb the second and so on. On sda, the partition sda1 is the first, sda2 the second. sdc4 would be the fourth primary partition on the third drive.

I would rather not go into primary, extended and logical partitions here. There is plenty of info about that in Wikipedia and so forth. Suffice to say that sdx1 to sdx4 are primaries, and logical partitions start at sdx5.

The second part is the Directory tree. 
[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview")

A partition is mounted to a position on the directory tree. It is possible to have the whole directory tree on one partition. This is how your computer is set up. The partition that ubuntu is on is therefore mounted at / because that is the start of the tree. 

It would be theoretically possible to have every folder in the tree on it's own partition. This would be a little silly, though. What is very common is to have your /home partition on a seperate partition. To do this, you would have had to have 2 partitions prepared, or created them during the install, and told the installer to mount the partition where you want the operating system to be at / and the partition that you want to use for your personal folder to /home.

Anyway, enough of that for now. I hope you get the package installed.

---


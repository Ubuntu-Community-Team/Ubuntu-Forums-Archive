---
title: "Sync your BlackBerry to your linux machine"
date: 2008-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Lord Xeb on 2008-08-04
A note to everyone: Please help with any of the problems that some people get, I am not very good with these kind of things and I made this tutorial based on several others and my experience. Also, make sure you are entering the PIN in right.

Note: this app(s) will work the following devices/programs: 
Molorola 
Windows CE devices
Nokia Mobile Devices
Opie
IrMC Mobile Devices
SyncML over HTTP
SyncML over OBEX Client
Palm Devices
And synchronization with handhelds using GPE
Google Calender Sync
LDAP Addressbook sync
Java Enterprise System Calender Server
Sunbird/Mozilla Calender Sync

First off, you will have to download some software and have a little bit of fun trying to get it all to work:

I used this site to get them and get some help configuring the parts and pieces: [http://www.linux.com/feature/123251](http://www.linux.com/feature/123251)

Now then, the parts and pieces.

You will need to add in these source files into the repositories: 
```
echo 'deb [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main'  |  sudo tee -a /etc/apt/sources.list
echo 'deb-src [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) feisty main'  |  sudo tee -a /etc/apt/sources.list
```
Update: This may be why some of you are having problems:
```
 gpg --keyserver [hkp://subkeys.pgp.net/]("http://subkeys.pgp.net/") --recv-keys CB210090B029CB84
gpg --export CB210090B029CB84 | sudo apt-key add -
```Then do:

```
sudo apt-get update
```Now download the packages that are needed. I will just tell you how to do it with the synaptic. Just go and type in in 'opensync' and install all the packages that are '0.22-feisty'. I know, you are not supposed to mix the repos but this is the only way. Also, I recommend using kitchensync since it is much easier and nicer to use than the gui provided for msynctool.


Next, we need to make sure we have the libusb libraries:

```
sudo apt-get install libusb-0.1-4 libusb++-0.1-4c2 libusb-dev libusb++-dev
```Next, download and install the following (I will post the universal ones (the kind that can be used on most Ubuntu varients):

[http://downloads.sourceforge.net/barry/libbarry_0.13-1.2_i386.deb?modtime=1217433545&big_mirror=0](http://downloads.sourceforge.net/barry/libbarry_0.13-1.2_i386.deb?modtime=1217433545&big_mirror=0)

[http://downloads.sourceforge.net/barry/barrybackup-gui_0.13-1.2_i386.deb?modtime=1217433325&big_mirror=0](http://downloads.sourceforge.net/barry/barrybackup-gui_0.13-1.2_i386.deb?modtime=1217433325&big_mirror=0)

[http://downloads.sourceforge.net/barry/barry-util_0.13-1.2_i386.deb?modtime=1217433460&big_mirror=0](http://downloads.sourceforge.net/barry/barry-util_0.13-1.2_i386.deb?modtime=1217433460&big_mirror=0)

[http://downloads.sourceforge.net/barry/libbarry-dev_0.13-1.2_i386.deb?modtime=1217433629&big_mirror=0](http://downloads.sourceforge.net/barry/libbarry-dev_0.13-1.2_i386.deb?modtime=1217433629&big_mirror=0)

[http://downloads.sourceforge.net/barry/libopensync-plugin-barry_0.13-1.2_i386.deb?modtime=1217433710&big_mirror=0](http://downloads.sourceforge.net/barry/libopensync-plugin-barry_0.13-1.2_i386.deb?modtime=1217433710&big_mirror=0)

You must install the first link before you can install any of the others.


Since that is all out of the way, we need to get down to business. First off, you must find out the PIN number of your device. You can do that by simply going to terminal and typing after connecting your device: 

```
btool -d 'Browser Folders'
```It should give you a readout like this: 
```
nathan@nathan-laptop:~$ btool -d 'Browser Folders'
Blackberry devices found:
Device ID: 0x809ea00. PIN: 123ee774, Description: RIM 8100 Series Colour CDMA Handheld
Using device (PIN): 319ee762
Raw record dump for record: 8a17e602
    00000000: 06 00 26 00 40 02 44 01 01 00 02 e6 17 8a 00 14  ..&.@.D.........
    00000010: 00 00 81 d6 e2 b7 60 00 0d 57 41 50 20 42 6f 6f  ......`..WAP Boo
    00000020: 6b 6d 61 72 6b 73                                kmarks

Raw record dump for record: 2c692a88
    00000000: 06 00 2d 00 40 02 44 01 02 00 88 2a 69 2c 00 1b  ..-.@.D....*i,..
    00000010: 00 00 81 d6 e2 b7 60 00 14 42 6c 61 63 6b 42 65  ......`..BlackBe
    00000020: 72 72 79 20 42 6f 6f 6b 6d 61 72 6b 73           rry Bookmarks

```Where it says 'PIN; Then a series of numbers in HEX (ex: 123ee774). That is your PIN. Next, lets make a backup of your blackberry shall we? Go to terminal and type the following while your blackberry is plugged into your computer:

```
barrybackup
```You will get a window that looks like below:
[IMG]http://www.linux.com/var/uploads/Image/articles/123251-1.png[/IMG]


It should see your device and put the pin in automatically, if not, just enter in your PIN, and click 'backup'. You can put this just about anywhere you want. just got to configure it. I will let you figure it out since it is rather straight forward.

Next, lets setup msynctool. Just type in the following:

```
msynctool --addgroup Blackberry
msynctool --addmember Blackberry barry-sync
msynctool --addmember Blackberry file-sync
msynctool --showgroup Blackberry
```This will get that up and going but it still needs to be configured for it to sync.

Do the following to do that:

```
msynctool --configure Blackberry 1
```The 1 stands for the first 'member' that you added, which will be the barry-sync. You will get something like what is down in the attachments. The here you see '319ee762' that is where you put your PIN (again) and you are set (well, if you have a password, add that into by how it says, if not, remove it completely). Next, we want to set up the file-sync:


```
msynctool --configure Blackberry 2
```You should get something like this:

```
<config><path>Path_to_where_you_want_your_stuff_to_go</path><recursive>FALSE</recursive></co$

```There, now you are ready to go. Have fun and feel free to experiment. Also, feel free to give me feedback on anything I need to fix or add. 


I give thanks to Joe Barr who created that article.



Note, this guide can be modified for Fedora as well.

Edit: Thanks to  itmanvn for providing the following link:

1. Download the lastest barry-0.13: [http://sourceforge.net/project/showf...ease_id=616724]("http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564&release_id=616724")

2. Syncing your BlackBerry with Evolution
[http://www.netdirect.ca/software/pac...barry/sync.php]("http://www.netdirect.ca/software/packages/barry/sync.php")

---

### Post by itmanvn on 2008-08-09
thanks for posting this :D

---

### Post by mrufino1 on 2008-08-11
Thanks for posting this guide! I am almost there- I have it installed, but I can't seem to get msynctools to work with my blackberry yet. When I run the configure programs, what exactly am I doing with them? I erased the line saying "PIN number goes here" (paraphrased) and replaced it with my pin number, and entered 1 in the lines for calendar sync and contact sync, but if that is right, where am I saving this? I don't use evolution right now, but will so I can sync my blackberry (I have only had it for 2 days, so I am new to blackberry, less than a year on linux and not the best in the command line but learning). Then, on the blackberry 2 configure, where am I sending the files? Am I looking for the default evolution path? When I run msynctools it says it can't do it, but I know the blackberry is recognized so once I figure out the configure I am sure it will work. Your post said to see the attachments but I didn't see any. Thanks a lot!

---

### Post by itmanvn on 2008-08-12
> **mrufino1 said:**
> Thanks for posting this guide! I am almost there- I have it installed, but I can't seem to get msynctools to work with my blackberry yet. When I run the configure programs, what exactly am I doing with them? I erased the line saying "PIN number goes here" (paraphrased) and replaced it with my pin number, and entered 1 in the lines for calendar sync and contact sync, but if that is right, where am I saving this? I don't use evolution right now, but will so I can sync my blackberry (I have only had it for 2 days, so I am new to blackberry, less than a year on linux and not the best in the command line but learning). Then, on the blackberry 2 configure, where am I sending the files? Am I looking for the default evolution path? When I run msynctools it says it can't do it, but I know the blackberry is recognized so once I figure out the configure I am sure it will work. Your post said to see the attachments but I didn't see any. Thanks a lot!

1. Download the lastest barry-0.13: [http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564&release_id=616724](http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564&release_id=616724)

2. Syncing your BlackBerry with Evolution
[http://www.netdirect.ca/software/packages/barry/sync.php](http://www.netdirect.ca/software/packages/barry/sync.php)

---

### Post by mrufino1 on 2008-08-12
Thanks, I did figure out how to configure it and I ran what is suggested. It is hanging in the middle of syncing though. It looks like my blackberry is disconnecting in the middle of the process, because it asks in the middle of the sync if I want to run mass storage mode again. Also, how long does resolving the conflicts take? The hard drive just starts working nonstop and I left it for over 20 minutes with nothing seeming to be progressing. It said it had resolved the conflicts. I guess if it is finding an address on my laptop in evolution and on the BB it is trying to decide which to use? I entered 1, which should be evolution if it was the first member I added, right? 
Is it possible that there are some fields within evolution that are not present on the blackberry (BB only has one mobile number slot for instance) and that is causing a problem? Or is this a problem with my ubuntu machine (IBM T41, 8.04)
The reason I am trying to do this is to avoid entering all of my contacts with the blackberry's keyboard. I have my schedule synced with google calendar, which is fine for me, and for contacts I really just want a backup and as I said, to avoid having to enter all of my info with the blackberry keys. However, I would like to get this to work just on principle. I am not too good rooting around in linux yet but I will give the debugging steps a try, hopefully I can follow them. Thanks!

PS- I should mention that I also tried kitchensync and it did the same, that was last night, I thought that was a KDE-Gnome thing but it was the same issue as using Barry.

---

### Post by Lord Xeb on 2008-08-13
To be honest with you, I have no idea. I do not use evolution so I wouldn't have the fuzziest of an idea. I can try to look into it, but I am not going to promise anything.

---

### Post by mrufino1 on 2008-08-13
What do you use if you don't use evolution? I don't have any affinity for evolution, but it is there.

---

### Post by Lord Xeb on 2008-08-14
Umm.... Honestly I do not know. I haven't found anything that I can use for that e_e but there is a sunbird sync thing for Mozilla's Sunbird calender :D

---


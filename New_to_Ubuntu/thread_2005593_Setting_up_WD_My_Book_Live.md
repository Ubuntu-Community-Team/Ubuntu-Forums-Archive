---
title: "Setting up WD My Book Live"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by Shadius on 2012-06-17
Hey everybody! :)

I need help setting up my WD My Book Live. I had bought this Home Network Drive when I was only using Windows XP. I no longer use Windows XP since discovering Ubuntu , but I dual-boot Windows XP and Ubuntu 12.04 LTS (Precise Pangolin) because my brother still uses Windows XP. I imagine setting up the WD My Book Live in Windows is just hooking it up and then inserting the CD provided and then following the instructions. How would I set it up in Ubuntu? 

Also, I don't know if the WD My Book Live Home Network Drive is compatible with Ubuntu Linux as the box says: > Compatibility: 
Windows XP, Windows Vista, or Windows 7
Mac OS X Leopard or Snow Leopard

It doesn't list Linux in the compatibility list. 

Here's a link to the [WD My Book Live]("http://store.westerndigital.com/store/wdus/en_US/DisplayProductDetailsPage/categoryID.56857900/subCategory.56858300/parid.56796900/catid.56857800"). I have the 2 TB one. Thank you in advance for your help.

---

### Post by PhantomTurtle on 2012-06-17
This might help - [http://ubuntuforums.org/showthread.php?t=1603439]("http://ubuntuforums.org/showthread.php?t=1603439").

---

### Post by Shadius on 2012-06-18
Thanks. I did some searching and from that it gave me the idea to look under **Places**>**Network** (I'm using GNOME Classic (No effects) DE). The WD My Book Live shows up there, but when I double-click on it to access it, here's what I'm provided with: see screenshot. This is the first time I'm installing the WD My Book Live, so I don't know what I'm supposed to do from here. Is this asking me to set up a password or am I supposed to already have a password? I don't really understand. :(

---

### Post by retchid on 2012-06-23
Try going into set up on windows For the wd I am sure I called my workgroup Retchid the same as my Ubuntu log on.  - although I did get access through another Ubuntu computer with a different profile so may not be the issue.

(set up is in software folder on the wd - just un tick  the map network drive so it doesn't put another link on your desktop)

Or maybe type 192.168.2.105 then settings then network then workgroup (the default was "WORKGROUP") you can also access this in firefox in ubuntuu (I Guess if you cant then you will have to use windows)

I had no problems with setting up on Ubuntu 10.4  fiirst time and don't recall having to enter a password so perhaps it is just a workgroup name problem.  After clicking the my book live icon under networks a public folder will be shown and within that are the shared folders.

Only got mine last week - thought I would have problems with Linux but none at all (except not being able to fathom out Opensuse Network dialogue boxes and hence removing Opensuse and going back to UBUNTU 10.4 which I was doing anyway)

Works good with jail broken iPad 2 with Xbmc also 

Hope that helps

Note - this was a new install of ubuntu 10.4 dual boot with windows (as I could not get opensuse to find my drive at all) so there was no baggage causing problems 

Ps Xbmc works fine for streaming
Also rythymbox remembers the path and does not need to have the folders remounted on reboot which was a pleasant surprise

Sorry can't post a pic but am streaming music from it as I type In Ubuntu

---

### Post by Shadius on 2012-06-23
> **retchid said:**
> Try going into set up on windows For the wd I am sure I called my workgroup Retchid the same as my Ubuntu log on.  - although I did get access through another Ubuntu computer with a different profile so may not be the issue.

(set up is in software folder on the wd - just un tick  the map network drive so it doesn't put another link on your desktop)

Or maybe type 192.168.2.105 then settings then network then workgroup (the default was "WORKGROUP") you can also access this in firefox in ubuntuu (I Guess if you cant then you will have to use windows)

I had no problems with setting up on Ubuntu 10.4  fiirst time and don't recall having to enter a password so perhaps it is just a workgroup name problem.  After clicking the my book live icon under networks a public folder will be shown and within that are the shared folders.

Only got mine last week - thought I would have problems with Linux but none at all (except not being able to fathom out Opensuse Network dialogue boxes and hence removing Opensuse and going back to UBUNTU 10.4 which I was doing anyway)

Works good with jail broken iPad 2 with Xbmc also 

Hope that helps

Note - this was a new install of ubuntu 10.4 dual boot with windows (as I could not get opensuse to find my drive at all) so there was no baggage causing problems 

Ps Xbmc works fine for streaming
Also rythymbox remembers the path and does not need to have the folders remounted on reboot which was a pleasant surprise

Sorry can't post a pic but am streaming music from it as I type In Ubuntu

What I did was, I went on my Macbook Pro, and found the WD My Book Live, and set it up on the Macbook Pro. I came back to Ubuntu, went into Network, and entered the credentials and I see my folders. I don't know if this is the proper way of setting it up. I've come across some threads that say to install Samba (I don't know what that is), and I've did some research on AFP and found that it means Apple Filing Protocol. I'm just wondering how would you set up this WD My Book Live if Ubuntu was your only operating system? Thanks for your help.

---

### Post by Shadius on 2012-06-30
Anyone know how to set this up solely using Ubuntu?

---

### Post by wallaroo on 2012-06-30
Hi Shadius,

The 'Compatibilty' list is just for the included software, which is written only for Windows or Mac (not needed for Linux). The OS on the box itself is Linux so if you wanted to connect the pure 'linux way' you could use SSH to bring up a terminal session on the MYBOOK, then set up NFS connections.

However you don't need to go to that level, a simple CIFS mount on your Ubuntu box is sufficient for general use.

The default share on the MYBOOK is named 'Public' and as the name suggests allows anyone to connect to the share. 

On your Ubuntu box..
- Create a mount point in /media
e.g. 
```
sudo mkdir /media/mybooklive
```- then mount it as a 'CIFS' mount
i.e. 
```
sudo mount -t cifs -o username=,rw,users,uid=1000 //mybookipaddress/Public /media/mybooklive
```(uid is your Ubuntu uid - usually 1000)
(mybookipaddress is the ip address of the MYBOOK device)
(You may need to install the 'cifs-utils' package first).

- to make it mount at boot, add the mount to the /etc/fstab file.
i.e.
```
//mybookipaddress/Public /media/mybooklive cifs rw,username=,uid=1000 0 0
```Note: I have found that when I need to transfer large or lots of files to the MYBOOK, it's best to use FTP because it's more stable. CIFS and NFS mounts are fragile and tend drop out or freeze at the worst possible times.

---

### Post by Shadius on 2012-06-30
> **wallaroo said:**
> Hi Shadius,

The 'Compatibilty' list is just for the included software, which is written only for Windows or Mac (not needed for Linux). The OS on the box itself is Linux so if you wanted to connect the pure 'linux way' you could use SSH to bring up a terminal session on the MYBOOK, then set up NFS connections.

However you don't need to go to that level, a simple CIFS mount on your Ubuntu box is sufficient for general use.

The default share on the MYBOOK is named 'Public' and as the name suggests allows anyone to connect to the share. 

On your Ubuntu box..
- Create a mount point in /media
e.g. 
```
sudo mkdir /media/mybooklive
```- then mount it as a 'CIFS' mount
i.e. 
```
sudo mount -t cifs -o username=,rw,users,uid=1000 //mybookipaddress/Public /media/mybooklive
```(uid is your Ubuntu uid - usually 1000)
(mybookipaddress is the ip address of the MYBOOK device)
(You may need to install the 'cifs-utils' package first).

- to make it mount at boot, add the mount to the /etc/fstab file.
i.e.
```
//mybookipaddress/Public /media/mybooklive cifs rw,username=,uid=1000 0 0
```Note: I have found that when I need to transfer large or lots of files to the MYBOOK, it's best to use FTP because it's more stable. CIFS and NFS mounts are fragile and tend drop out or freeze at the worst possible times.

Thanks for your reply. What are CIFS and NFS?

---

### Post by wallaroo on 2012-06-30
They're network access protocols, used for sharing.
CIFS = Common Internet File System
NFS = Network File System

Each have their pros and cons - CIFS is simpler.
NFS needs a bit more setting up on both the server and client boxes.

---

### Post by Engawl on 2012-06-30
You are not right. I am assured. Write to me in PM, we will discuss.

---

### Post by Shadius on 2012-06-30
Is there an alternative way of setting it up, maybe without using the command-line as well? Just trying to see all the options I have.

---

### Post by wallaroo on 2012-07-01
Well, there isn't much to 'setup' but going back to your second post and the screen dump you showed, if you bring this up again and  just leave it at 'Connect anonymously' and press 'Connect' the drive should be automatically mounted and you should be able to read and write to it.

If you want to change settings or create new users, new shares etc, you can do so using your web browser by entering the IP address of the MYBOOK device as the web address. This will bring up the MYBOOK configuration.
You can use this to also manage the media server that comes with the box ('Twonky' on my box).

(I have tested this and it works fine).

---

### Post by Shadius on 2012-07-01
> **wallaroo said:**
> Well, there isn't much to 'setup' but going back to your second post and the screen dump you showed, if you bring this up again and  just leave it at 'Connect anonymously' and press 'Connect' the drive should be automatically mounted and you should be able to read and write to it.

If you want to change settings or create new users, new shares etc, you can do so using your web browser by entering the IP address of the MYBOOK device as the web address. This will bring up the MYBOOK configuration.
You can use this to also manage the media server that comes with the box ('Twonky' on my box).

(I have tested this and it works fine).

Oh okay. Gotcha. So with Ubuntu Linux, there's really nothing to setup for the WD My Book Live? Just plug it in and do what I did before. That seems easy. I assume when I click "Connect", it connects to the IP address and that is how I'll know what the IP address is? I've read a little bit about Twonky. I have to do some more reading from the manual.

---

### Post by wallaroo on 2012-07-01
You can get its IP address either by connecting to your router and listing the connected devices,
or, as you say, after it's mounted...
e.g.
```
arp -n
```

---

### Post by retchid on 2012-07-14
[http://192.168.2.105/UI/](http://192.168.2.105/UI/)

Assuming your router has similar ip address

Change 105 to 100, 101, 102 ......etc until GUI  comes on in the browser

Assuming its plugged in to the router


Cd only works on pc and mac 

But the cd does not do much anyway as set up is mainly through browser the cd just helped detect the drive and mounts it on windows

If your Linux does not detect it

Change the workgroup name in the GUI 

Mine is working on Ubuntu 10.4 in places network ........

In mac puppy  on my netbook used pnethood.  Then entered workgroup name and password

Posted to help anyone who cannot get it working

So it does work on Linux it's just not immediately obvious how to access it.

---

### Post by Shadius on 2012-07-14
Thanks for the help. It's working! :) I was wondering, what's the fastest way to transfer files to the My Book Live? I have a 1 TB HDD that I would like to transfer the files to the My Book Live. I imagine that would take forever.

---

### Post by m3topaz on 2012-07-14
Thank you for the post, wallaroo

I grabbed a 3TB mybooklive earlier today, my important stuff is moving over - using rsync - to a share mounted exactly as you described.

Much appreciated!

---

### Post by snydez on 2012-11-14
> **wallaroo said:**
> Hi Shadius,
--8<--
However you don't need to go to that level, a simple CIFS mount on your Ubuntu box is sufficient for general use.

The default share on the MYBOOK is named 'Public' and as the name suggests allows anyone to connect to the share. 

On your Ubuntu box..
- Create a mount point in /media
e.g. 
```
sudo mkdir /media/mybooklive
```- then mount it as a 'CIFS' mount
i.e. 
```
sudo mount -t cifs -o username=,rw,users,uid=1000 //mybookipaddress/Public /media/mybooklive
```(uid is your Ubuntu uid - usually 1000)
(mybookipaddress is the ip address of the MYBOOK device)
(You may need to install the 'cifs-utils' package first).

- to make it mount at boot, add the mount to the /etc/fstab file.
i.e.
```
//mybookipaddress/Public /media/mybooklive cifs rw,username=,uid=1000 0 0
```Note: I have found that when I need to transfer large or lots of files to the MYBOOK, it's best to use FTP because it's more stable. CIFS and NFS mounts are fragile and tend drop out or freeze at the worst possible times.

ah thank you for posting this.

---

### Post by bayvista on 2012-11-30
z

---

### Post by m3topaz on 2012-12-30
In case you want to mount the Shared Music folder, it can also be done as a CIFS mount:

1) Create a mount point e.g. mybookmusic
2) Mount the shared folder with:
sudo mount -t cifs -o username=anonymous,password=,rw,users,uid=1000 '//MyBookLive.local/Public/Shared Music' /mybookmusic
[Use the IP address instead of 'MyBookLive.local' if you want.]
3) You can move your music over with rsync:
rsync -avv /home/yournamehere/Music/ /mybookmusic

You might need to login to the MyBookLive to nudge the server up to date:
Settings-Media-Twonky-Status-Rescan

Once done, the music you sync'd over will be available to all through the public music share.

---

### Post by vanadium on 2012-12-30
Mounting the cifs share of the mybookworld just goes fine using nautilus: file - connect to server - Type: Windows share, Server: MyBookWorld, Share: (for example) Public.
Of course, you must have configured the shares, users, permissions etc using the web interface.

---

### Post by streamheat on 2013-03-31
Dude, you so seriously rock. Thank you for letting me sleep tonight.

---

### Post by Kamylo on 2013-06-22
Engawl,

  I am new to linux and don't  know really anythink about IT. If you already have find out how to  install wd My Book Live in linux, would you mind giving me the recipe?

Thanks,

Kamylo

---

### Post by thewimreaper on 2013-10-05
i just bought one, got home, connected with the browse network option in the file manager and ........ works perfectly.

i love linux :)

---

### Post by Karl_Churchill on 2013-10-20
Thank you for the *MyBookLive_.local_* clue.  I've been seeking this for weeks.  
I am running this on Ubuntu v11.04.  So note that the cifs-utils package must be installed for this to work.
:popcorn:

---


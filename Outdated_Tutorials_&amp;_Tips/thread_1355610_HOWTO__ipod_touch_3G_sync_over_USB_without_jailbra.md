---
title: "HOWTO : ipod touch 3G sync over USB without jailbraking"
date: 2009-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by manuw2009 on 2009-12-15
Hi everyone,

After hours of googling, I eventually succeded in setting up an USB connection with my new ipod touch 3G, WITHOUT jailbreaking nor compiling stuff !

the following PPA saved my life :

[https://launchpad.net/~pmcenery/+archive/ppa?field.series_filter=karmic]("https://launchpad.net/%7Epmcenery/+archive/ppa?field.series_filter=karmic")
This basically enabled my follow marcan's guide without the compilation steps :
[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)
especially StoneCut 's tutorial (BIG thanks)
and will provide with gvfs 1.5 which basically enables rhythmbox to mount the ipod/iphone

All credits should go to 
[B][SIZE=3]Paul McEnery, stonecut & marcan
[/SIZE][/B]

Here we go :
1.Add 
deb [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) karmic main
to your sources list

2. Install the following necessary packages
$   [COLOR=blue][FONT=&quot]sudo apt-get install gvfs gvfs-backends gvfs-bin  gvfs-fuse libgvfscommon0 ifuse libgpod4 libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-udev libusbmuxd1 usbmuxd[/FONT][/COLOR]

3. Create the ipod mount point with user rw access rights
$ sudo mkdir /mnt/my_ipod_or_iphone_mount_point
$ sudo chmod 777 /mnt/my_ipod_or_iphone_mount_point/
(here, mount point is "ipod" i.e. $ sudo mkdir /mnt/ipod && sudo chmod 777 /mnt/ipod/)

4. Edit the FUSE config file.
$ sudo gedit /etc/fuse.conf
-> Remove the &#8220;#&#8221; in front of &#8220;user_allow_other&#8221;, save and exit.
Next, open &#8220;System&#8221; -> &#8220;Administration&#8221; -> &#8220;Users and Groups&#8221; in Ubuntu Menu. Click on the little key at the bottom to unlock it for making changes. Then, select your username and click on &#8220;Manage Groups&#8221;.
Find the &#8220;fuse&#8221; group and double-click on it. Make a checkmark next to your name in the window that opens. Click on OK and close all dialogs. You&#8217;re now in the &#8220;fuse&#8221; group.
Next, completely log out and in again &#8211; do a reboot to be safe. This is important !
Open up a terminal again. Let&#8217;s verify we&#8217;re really in the &#8220;fuse&#8221; group:

We can now mount the phone as regular user after connecting it (run &#8220;ps ax | grep usbmuxd&#8221; to verify that usbmuxd is listening if you want):
$ ifuse /mnt/ipod/

We can also unmount as regular user (a sudo shouldn&#8217;t be necessary):
$ fusermount -u /mnt/ipod/

5. Prepare ipod itunes directory :
Ok, now mount the device with &#8220;ifuse /mnt/ipod/&#8221; (if not still mounted) and create the &#8220;iTunes_Control/Device&#8221; directory:
$ mkdir /mnt/ipod/iTunes_Control/Device/
Then, get your UUID:
$ lsusb -v | grep -i iSerial
It&#8217;s the first number and should be 40 characters long. Then, run:
$ ipod-read-sysinfo-extended
(mountpoint here is /mnt/ipod/)
This should generate a file named iTunes_Control/Device/SysInfoExtended.
Make sure it&#8217;s not empty and whatnot; it should be a large-ish plist (XML file) with a bunch of info.
$ fusermount -u /mnt/ipod/

6. Reboot your computer

7. Plug the ipod : you should see it appear on the desktop
and it should now be
a/ directly mounted in rhythmbox and you can add music files (transfer rate still slow but acceptable)
b/ mounted in gtkpod but you'll have to launch the "ifuse /mnt/ipod".
c/ NOT visible in amarok 2.2.1 and still haven't figured out why...
rhyhmbox is unable to remove music files, so please use the previous gtkpod part either to remove files or add videos to the ipod.
Hopefully amarok will handle it soon so everything can be performed from the same app (and gtkpod is a real pain !).

8. That's all folks

Hope this helps,
manuw

---

### Post by amirhomayoun on 2009-12-17
Great! Thanks!

Works on iphone 3g. After restarting Rhythmbox recognized the iphone. It can play songs directly from it. I also could add songs to the phone. It's a little bit slow but even that it's great!

---

### Post by Kelito7777 on 2009-12-18
When I input the string; "$ ifuse /mnt/ipod/" I get an error message that the file is not found. I followed all the steps to this point. Is there something I missed...help...please.

---

### Post by manuw2009 on 2009-12-18
Hi Kelito7777,

You have to create the mount point manually in order to use the ifuse command, e.g :

$ sudo mkdir /mnt/my_ipod_or_iphone_mount_point

(here, mount point is "ipod")

I'm not sure you need it if you're not using gtkpod though (as rhythmbox is recognizing the iphone/touch through gvfs without manually running ifuse).

Anyway,

Would anyone have a clue on how to make it work with amarok 2.2.x as well ?
I believe amarok is running through kde's solid and not gvfs (gnome thingy) which is not seeing the ipod/phone...
Does anyone have an idea on how to make that work (even through a script) ?
Thank you in advance

---

### Post by mattack on 2009-12-20
> **manuw2009 said:**
> Hi Kelito7777,


Would anyone have a clue on how to make it work with amarok 2.2.x as well ?
I believe amarok is running through kde's solid and not gvfs (gnome thingy) which is not seeing the ipod/phone...
Does anyone have an idea on how to make that work (even through a script) ?
Thank you in advance

Or Amarok 1.4... I'm currently syncing my iPod Touch via a Windows VM. :|

---

### Post by eriqjaffe on 2009-12-21
I've added the PPA, but when I try to run the apt-get command, I get a "Couldn't find package libgpod" message...

---

### Post by manuw2009 on 2009-12-22
Hi
well I think it's namely "libgpod4". I actually did the thing through synaptic...
I guess you'd better do the same
let me know if this works for you then

---

### Post by Nburnes on 2009-12-22
This is great news!

---

### Post by fischflosse on 2009-12-22
Hi all,

Thanks for the solution, manuw2009! It would be so great if I could synch my iPod from Ubuntu, but I'm having some problems following the steps.

I'm getting stuck at mounting it. The command "ifuse /mnt/ipod/" returns an error message: "fusermount: user has no write access to mountpoint /mnt/ipod". But I followed all the previous steps, including making this user part of the fuse group. Rhythmbox sees my iPod, but I cannot add stuff, and deleting stuff seems to only corrupt the data on the iPod somehow (the songs are still visible, they just won't play). 

Any suggestions would be highly appreciated.

---

### Post by musicman10489 on 2009-12-24
I was very excited to see this thread and tried it out immediately. But I have run into a decently sized issue: I can sync music to my itouch just fine. But after the syncing has completed and I have removed the device most albums on the itouch seem corrupted. When I try to listen to a song it will play the first 3-7 seconds of the song and then switch to the next song and repeat this process all the way through the album. The whole time it does this the screen shows that it is playing the first song I chose like normal.

Kinda strange...

---

### Post by GavinIvey on 2009-12-24
Not sure what I'm doing wrong here.

2. Install the following necessary packages
$   [COLOR=blue][FONT=&quot]sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod libiphone-utils libiphone0 python-iphone ibplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-udeb libusbmuxd1 usbmuxd[/FONT][/COLOR]


and I get:

don@don-desktop:~$ sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod libiphone-utils libiphone0 python-iphone ibplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-udeb libusbmuxd1 usbmuxd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ifuse
don@don-desktop:~$ 

Any help would be greatly appreciated.

---

### Post by Mandor_ on 2009-12-24
Interesting note: if you happen to have an iPhone that's jailbreaked and has OpenSSH installed, you can use this guide to tether the iPhone's internet connection. The usbmuxd package (which gets installed along with iFuse) comes with a nifty utility called iproxy that allows you to create a tunnel to the device:
```
iproxy 2222 22 &
```This creates a tunnel from port 2222 to the port your iPhone's OpenSSH listens on by default.
Next use SSH to create a SOCKS proxy to the tunnel:
```
ssh -D 1080 -p 2222 root@localhost
```Now all you have left to do is to set Firefox's proxy settings: SOCKS v5 proxy on host 127.0.0.1 and port 1080.
Also in about:config, set *network.proxy.socks_remote_dns* to true. Voilà!

---

### Post by patrickcage on 2009-12-26
> **fischflosse said:**
> 

I'm getting stuck at mounting it. The command "ifuse /mnt/ipod/" returns an error message: "fusermount: user has no write access to mountpoint /mnt/ipod". 



I had the same problem, so I used:

```
chown username:fuse /mnt/ipod/
```

to change the ownership of /mnt/ipod/ from root to me.

---

### Post by SvenBuntu on 2009-12-27
Does this work for the 3.1 fw?

---

### Post by manuw2009 on 2009-12-27
Sure, my ipod touch has the 3.1.1 firmware

---

### Post by patrickcage on 2009-12-28
> **SvenBuntu said:**
> Does this work for the 3.1 fw?

I'm using the latest 3.1.2 firmware with no problems.

---

### Post by matog on 2009-12-28
Does it work with the iPod Touch 1G?

---

### Post by iaguy2 on 2009-12-29
I have a 3g ipod touch and I didn't need to do the mounting with 9.10.  So I didn't need to do the ifuse commands.  I used Synaptic to install the packages listed in this thread.  I don't know if clicked something extra, but I'm thankful I don't have to do the ifuse commands.  So my mkdir was where gvfs mounted it in my home directory. 

mkdir /home/mason/Mason%27s Ipod/iTunes_Control/Device/

also run the ipod-read-sysinfo-extended to there.

Rhythmbox sees it and I can play music off of it.  If I try to drag files to it or make playlists it actually copies the files to the iPod but they are not seen by the ipod.  So I switched to gtkpod and it seems to be working as far as adding songs to the ipod. Gtkpod says that it is ignoring the extended data and that has me worried.

---

### Post by carlosgs91 on 2009-12-29
,

---

### Post by SvenBuntu on 2009-12-29
Just a heads up to people that already have jailbroken iphones. A lot of the directories already exist. I ran into problems because the Device directory's owner was root and not mobile. This is probably due to playing around using ssh with root. Same with artwork files. Changed all to mobile and it works a treat with fw 2.x. 

As for speed, I know it's not as fast as under itunes but it beats using wireless transfer...

---

### Post by pemadorje on 2010-01-03
musicman10489, I had the same issue as you. I was just testing this method out and synced 1 or 2 songs with Ubuntu (while leaving a lot of other music on the phone that had been previously synced via iTunes in Windows). The songs that I synced via Ubuntu could play fine but all of the other music would only play about 5 seconds before skipping to the next song. The conclusion that I've reached is that all of your music should be synced with iTunes OR Ubuntu/Rhythmbox (but not a mixture of the two). For example, I removed all of the music from my phone and then re-synced my entire music collection using Ubuntu and now everything works fine. It seems that the phone was not happy when I tried to sync only a few songs with Ubuntu while leaving other songs on the device from iTunes. If all of your music is synced using the Ubuntu/Rhythmbox method, I think this issue goes away.

---

### Post by musicman10489 on 2010-01-03
Yeah I noticed that also! When I went back and re-added albums using Rhythmbox they stopped skipping. Thank you though for addressing that issue. I also noticed that if the songs in an album are listed by title or anything other than track number when you transfer them, that's the way they show up on the itouch. 
Thank you again for replying!

---

### Post by webzurd on 2010-01-04
Works great! I finally have enough iphone functionality in Linux to be useful. Now I need a full iTunes replacement...

Sandro

---

### Post by matog on 2010-01-04
What am I supposed to do here?

> $ ipod-read-sysinfo-extended
(mountpoint here is /mnt/ipod/)

I do
> $ lsusb -v | grep -i iSerial
  iSerial                 3 3d8a3c0eff99c98fd48a9d27157cf2689ca3aca2
  iSerial                 3 058F0O1111B1
  iSerial                 1 0000:00:02.1
  iSerial                 0 
  iSerial                 1 0000:00:02.0

And then
> ipod-read-sysinfo-extended 3d8a3c0eff99c98fd48a9d27157cf2689ca3aca2 /media/ipod/

and get:
Couldn't read xml sysinfo from 3d8a3c0eff99c98fd48a9d27157cf2689ca3aca2

---

### Post by tim.inman on 2010-01-05
This doesn't seem to work anymore (even after fixing spelling errors) It won't install libusbmuxd or usbmuxd due to confilcts:

Others are experiencing the same: [http://ubuntuforums.org/showthread.php?p=8615667#post8615667](http://ubuntuforums.org/showthread.php?p=8615667#post8615667)

Help?

sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod4 libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gvfs is already the newest version.
gvfs-bin is already the newest version.
gvfs-bin set to manually installed.
gvfs-fuse is already the newest version.
libgvfscommon0 is already the newest version.
libplist++1 is already the newest version.
libplist-utils is already the newest version.
python-plist is already the newest version.
libusb-1.0-0 is already the newest version.
libusb-1.0-0 set to manually installed.
libusb-1.0-0-dev is already the newest version.
libusb-1.0-0-dev set to manually installed.
The following packages were automatically installed and are no longer required:
  libplist0 libmtp8 media-player-info
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgpod-common
The following NEW packages will be installed:
  gvfs-backends ifuse libgpod-common libgpod4 libiphone-utils libiphone0
  libusbmuxd1 python-iphone usbmuxd
0 upgraded, 9 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/1,605kB of archives.
After this operation, 5,272kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libusbmuxd1 libiphone0 usbmuxd gvfs-backends ifuse libgpod4 libgpod-common
  libiphone-utils python-iphone
Install these packages without verification [y/N]? y
(Reading database ... 329734 files and directories currently installed.)
Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.0-0ubuntu1~ppa2_i386.deb) ...
[U][B]dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.0-0ubuntu1~ppa2_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k[/B][/U]
Selecting previously deselected package libiphone0.
Unpacking libiphone0 (from .../libiphone0_0.9.5-1ubuntu1~ppa2_i386.deb) ...
Unpacking usbmuxd (from .../usbmuxd_1.0.0-0ubuntu1~ppa2_i386.deb) ...
[B][U]dpkg: error processing /var/cache/apt/archives/usbmuxd_1.0.0-0ubuntu1~ppa2_i386.deb (--unpack):
 trying to overwrite '/lib/udev/rules.d/85-usbmuxd.rules', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k[/U][/B]
Selecting previously deselected package gvfs-backends.
Unpacking gvfs-backends (from .../gvfs-backends_1.5.1-0ubuntu1~ppa2_i386.deb) ...
Selecting previously deselected package ifuse.
Unpacking ifuse (from .../ifuse_0.9.5-1ubuntu1~ppa2_i386.deb) ...
Selecting previously deselected package libgpod4.
Unpacking libgpod4 (from .../libgpod4_0.7.3+git20091215+teuf-master-0ubuntu1~ppa1_i386.deb) ...
Selecting previously deselected package libgpod-common.
Unpacking libgpod-common (from .../libgpod-common_0.7.3+git20091215+teuf-master-0ubuntu1~ppa1_i386.deb) ...
Selecting previously deselected package libiphone-utils.
Unpacking libiphone-utils (from .../libiphone-utils_0.9.5-1ubuntu1~ppa2_i386.deb) ...
Selecting previously deselected package python-iphone.
Unpacking python-iphone (from .../python-iphone_0.9.5-1ubuntu1~ppa2_i386.deb) ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
hal start/running, process 4731
Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.0-0ubuntu1~ppa2_i386.deb
 /var/cache/apt/archives/usbmuxd_1.0.0-0ubuntu1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dbo117 on 2010-01-06
Hi, I have a different problem :D

Rhythmbox is detecting my iPod Touch, I can play music off it and I can add songs.  But my iPod's music player isn't detecting any of the music.  I check my space quotas before and after, and the space gets used up, I just can't play the songs from my iPod:lolflag:

---

### Post by andersq on 2010-01-06
Hi.

First of all, Great Work! Since I now only use my iPod Touch (First generation and firmware 3.0, 32GB, jailbroken) as a remote for my MPD server (through MPoD), this would expand it's use a lot.

However I'm running into problems at one point.

When connecting the iPod to make the ifuse commands the iPod seems to mount by itself nicely, but I have no write access to the /mnt/ipod/.. directory. I'm not sure I'm supposed to have that, but anyway it seems that the ipod-read-sysinfo-extended needs to be able to write a file. I have tried to change the owner of the /mnt/ipod/ directory. In Nautilus this gives me the option to create things, but I get the folloing error: Error creating directory: Operation not permitted. Same if I use a root Nautilus.

I added myself and root to the fuse users and I changes the owner of the /mnt/ipod with: chown username:fuse /mnt/ipod/ as suggested by patrickcage.

Anyone got an idea?

---

### Post by patrickcage on 2010-01-07
This may sound like *(and indeed may be)* a stupid question, but have you switched off your iPod and turned it on again.
I ask this because mine only mounted (as Apple intended) as a Digital Camera until I turned it off and on, then it mounted as both a camera, and again (as I intended) an iPod.

---

### Post by patrickcage on 2010-01-07
[ apologies, double posted the above post ] :redface:

---

### Post by Ebonhawke on 2010-01-07
I'm trying to follow the instructions above with a brand new 3G touch.  When I try and mount the device (the touch is connected via USB), I get "No device found, is it connected?"

When I plug the USB in, I do get the pop-up window recognizing that I had plugged it in (but saying it's a medium containing digital photos)

---

### Post by Ebonhawke on 2010-01-07
OK - I'm guessing that the reason for my difficulties is that I haven't registered/initialized the iPod yet (first use)

Any suggestions?  (I'm trying to avoid, if at all possible, installing a VM on this machine as I don't have windows/Mac OS software at all)

---

### Post by andersq on 2010-01-07
Yes, tried rebooting the iPod.

I have checked other folders on the mounted iPod and it seems possible to create folders/files in other folders (f.ex. the /mnt/ipod/iTunes_Control/ but not in the subfolder /Device . But I still cannot create the ipod-read-sysinfo-extended file. I guess it is because of the write issues.

Now isn't that odd?

---

### Post by bmatt95 on 2010-01-07
> **matog said:**
> What am I supposed to do here?



I do

And then

and get:
Couldn't read xml sysinfo from 3d8a3c0eff99c98fd48a9d27157cf2689ca3aca2
I get this same error. Any help?

---

### Post by deuz on 2010-01-08
> **Ebonhawke said:**
> OK - I'm guessing that the reason for my difficulties is that I haven't registered/initialized the iPod yet (first use)

Any suggestions?  (I'm trying to avoid, if at all possible, installing a VM on this machine as I don't have windows/Mac OS software at all)

I'm pretty shure it won't work without first initializing it, I think you'll have to find a buddy with iTunes..

---

### Post by deuz on 2010-01-08
> **bmatt95 said:**
> I get this same error. Any help?
& matog 

I got the same error, make shure you've the latest version of "ipod-read-sysinfo-extended" + make shure you've the correct sources

the usage should be with "<device|uuid>" of ipod-read.. 


Now I think it's working for me=)) I'm backing up my library & then I'll try to play some songs I got transferred:p

---

### Post by bmatt95 on 2010-01-08
> **deuz said:**
> & matog 

I got the same error, make shure you've the latest version of "ipod-read-sysinfo-extended" + make shure you've the correct sources

the usage should be with "<device|uuid>" of ipod-read.. 


Now I think it's working for me=)) I'm backing up my library & then I'll try to play some songs I got transferred:p
How do you make sure it's the latest? I can't update it with apt-get, which was the only thing I could think of. My usage says <device> <uuid>, not <device|uuid>.

---

### Post by FireJet on 2010-01-09
> **GavinIvey said:**
> Not sure what I'm doing wrong here.

2. Install the following necessary packages
$   [COLOR=blue][FONT=&quot]sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod libiphone-utils libiphone0 python-iphone ibplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-udeb libusbmuxd1 usbmuxd[/FONT][/COLOR]


and I get:

don@don-desktop:~$ sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod libiphone-utils libiphone0 python-iphone ibplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-udeb libusbmuxd1 usbmuxd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ifuse
don@don-desktop:~$ 

Any help would be greatly appreciated.

Try this:
```

sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod4 libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd libusb-1.0-0

```

All those packages should work

---

### Post by rimongo on 2010-01-09
> **bmatt95 said:**
> How do you make sure it's the latest? I can't update it with apt-get, which was the only thing I could think of. My usage says <device> <uuid>, not <device|uuid>.

Just add the libiphone-dev through synaptic and this will solve it.
The usage is:
#ipod-read-sysinfo-extended <device> <uuid>
i.e. ipod-read-sysinfo-extended fd98145617c113dc15ab151601001ff12354b139 /mnt/ipod

---

### Post by rimongo on 2010-01-09
Just add the libiphone-dev through synaptic and this will solve it.
The usage is:
#ipod-read-sysinfo-extended <device> <uuid>
i.e. #ipod-read-sysinfo-extended fd98145617c113dc15ab151601001ff12354b139 /mnt/ipod

---

### Post by Compintuit on 2010-01-10
I have the same problem. Installing that didn't fix it. gtkpod did start to work, but a lot of things are strange, and it's working very slowly. I deleted some songs, but they remain in the database, and things are wonky. The file still isn't there.

---

### Post by SvenBuntu on 2010-01-10
> **andersq said:**
> Yes, tried rebooting the iPod.

I have checked other folders on the mounted iPod and it seems possible to create folders/files in other folders (f.ex. the /mnt/ipod/iTunes_Control/ but not in the subfolder /Device . But I still cannot create the ipod-read-sysinfo-extended file. I guess it is because of the write issues.

Now isn't that odd?

I had the same error. To re-iterate from my previous post, for some reason the owner of the Device folder (on the Iphone) was root whereas the login uses "mobile" user. Login as root on the device using ssh and change the owner to mobile and you should be able to create files using mobile user. Also, check other folders; my artworks folder and content was owned by root not mobile.

---

### Post by zami on 2010-01-10
> **FireJet said:**
> Try this:
```

sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod4 libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd libusb-1.0-0

```

All those packages should work

Yeah, what he said.  I think there are just a few typos in the handy dandy apt-get line.


ibplist++1
should be
libplist++1

I don't have libgpod, but I do have libgpod4 


also, I don't have the package "libusb-1.0-0-udeb", but I do have
libusb-1.0-0
and
libusb-1.0-0-dev

If you get stumped with the command line, try opening up Synaptic and entering the names in one by one - you might just find it's a simple typo or a version variance.   :)

-zami

---

### Post by zami on 2010-01-10
To the OP
AWESWOME work!!  Thank you, thank you, thank you!!

I haven't manually set a mount point yet. I'm a little leery to do so because after just the first few steps, Rythmbox is loading podcasts into my iPod lickety split, and I kinda don't want to mess that up.

Thanks for your great detective work and excellent how-to!

-zami

---

### Post by zami on 2010-01-10
[COLOR=Silver][COLOR=Black]Nevermind!  My answer is in post #4!
 [/COLOR]
Where the guide says 
> 
We can now mount the phone as regular user after connecting it (run “ps ax | grep usbmuxd” to verify that usbmuxd is listening if you want):
$ ifuse /mnt/ipod/
```
ifuse /mnt/ipod/
```gives me
```
ERROR: the mount point specified does not exist
```Am I supposed to make the mountpoint first?

I ran the "ps ax..." line and can see the iPod detected
3390 ?        S<     0:00 /usr/sbin/usbmuxd -u -U
(Some other items too, but that's the iPod.)


Thanks for any help.  And if I figure this out myself (hah!!) I'll share.[/COLOR]   

-zami

---

### Post by manuw2009 on 2010-01-11
Hi guys,

Fixed a few typo errors in the HowTo (package names).
+ added the mound point creation step which was missing

The only remaining issue for me is to make it work in amarok 2.2, as it doesn't seem to recognize the fuse mountpoint.
Any ideas on how to achieve that ?
Thanx

(I'm getting used to rhythmbox though)

---

### Post by alexmurray on 2010-01-12
Has anyone else noticed while Rhythmbox itself is slow to transfer music files (compared to GtkPod), usbmuxd and gvfs-backend-afc (or something like that) then keep running at 10% CPU each for about half and hour whilst my iPod display's 'Sync in Progress', which I assume is the updating of the actual music database??

(Note I have about 2000 songs in the library which probably doesn't help) - this is on an iPod Touch with version 3.1.2 OS.

Also thought people might be interested to perhaps try out a version of Rhythmbox which actually has support for syncing your music library (i.e. not just copying files from it as it currently does) - currently is in [GNOME git repo]("http://git.gnome.org/browse/rhythmbox/log/?h=media-player-sync") (haven't tried it myself yet, may try tonight if I get time to build it...)

---

### Post by Jhon Butcher on 2010-01-12
Download the free app titled backrounds, it has tons of free downloadable backrounds. also, if you take an iphoto picture and put it on ur ipod when you go to the app photos and if you click on one there is a button on the bottom that says use as backround

---

### Post by zami on 2010-01-12
I just wanted to report that this is working with gPodder, too.

Like gtkpod, you need to
ifuse /mnt/ipod/
and
fusermount -u /mnt/ipod/
before/after every time you plug in/out your iPod, respectively.
(If you try to mount without unmounting first, you get an input/output error.)

gPodder and iPod must have a very different method of marking items as read, because all functions except anything involving "mark/ed as read" works well.  But that said, I haven't seen any program that handles un/read episodes the same as gPodder, so I really expected no less.

Love it, love it, love it!!

Thanks manuw!!

-zami

---

### Post by rohit2412 on 2010-01-12
Thanks so much. Works flawlessly. 
But can please someone answer this

1) I used iproxy earlier in jaunty(which used ssh on usb as mentioned in README in its source) to mount the root filesystem of iphone. Now ifuse seems to mount only mobile directory. Maybe it mounts as user mobile,but is there any way i can mount the root directory using ifuse(along with the plug'n'play thing)

2) Also how can i install an .ipa file directly to my ipod from computer(no cydia,appstore). Should be possible since all cydia would be doing is some version management and file movement. maybe change the ipa file to the corresponding deb file (both are archives of executables..)

Thanks

---

### Post by rohit2412 on 2010-01-12
My mistake...Should look things up before asking:P..

1) easy enough ...there is a --root option in ifuse...Still have to see how it will go with plugnplay thing..but maybe by setting an alias in bashrc itself might suffice

2) there is app called installous for the same..Just need to move the ipa file..

---

### Post by wersdaluv on 2010-01-13
> **manuw2009 said:**
> Hi everyone,

After hours of googling, I eventually succeded in setting up an USB connection with my new ipod touch 3G, WITHOUT jailbreaking nor compiling stuff !

the following PPA saved my life :

[https://launchpad.net/~pmcenery/+archive/ppa?field.series_filter=karmic]("https://launchpad.net/%7Epmcenery/+archive/ppa?field.series_filter=karmic")
This basically enabled my follow marcan's guide without the compilation steps :
[http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)
especially StoneCut 's tutorial (BIG thanks)
and will provide with gvfs 1.5 which basically enables rhythmbox to mount the ipod/iphone

All credits should go to 
[B][SIZE=3]Paul McEnery, stonecut & marcan
[/SIZE][/B]

Here we go :
1.Add 
deb [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) karmic main
to your sources list

2. Install the following necessary packages
$   [COLOR=blue][FONT=&quot]sudo apt-get install gvfs gvfs-backends gvfs-bin  gvfs-fuse libgvfscommon0 ifuse libgpod4 libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-udev libusbmuxd1 usbmuxd[/FONT][/COLOR]

3. Create the ipod mount point with user rw access rights
$ sudo mkdir /mnt/my_ipod_or_iphone_mount_point
$ sudo chmod 777 /mnt/my_ipod_or_iphone_mount_point/
(here, mount point is "ipod" i.e. $ sudo mkdir /mnt/ipod && sudo chmod 777 /mnt/ipod/)

4. Edit the FUSE config file.
$ sudo gedit /etc/fuse.conf
-> Remove the &#8220;#&#8221; in front of &#8220;user_allow_other&#8221;, save and exit.
Next, open &#8220;System&#8221; -> &#8220;Administration&#8221; -> &#8220;Users and Groups&#8221; in Ubuntu Menu. Click on the little key at the bottom to unlock it for making changes. Then, select your username and click on &#8220;Manage Groups&#8221;.
Find the &#8220;fuse&#8221; group and double-click on it. Make a checkmark next to your name in the window that opens. Click on OK and close all dialogs. You&#8217;re now in the &#8220;fuse&#8221; group.
Next, completely log out and in again &#8211; do a reboot to be safe. This is important !
Open up a terminal again. Let&#8217;s verify we&#8217;re really in the &#8220;fuse&#8221; group:

We can now mount the phone as regular user after connecting it (run &#8220;ps ax | grep usbmuxd&#8221; to verify that usbmuxd is listening if you want):
$ ifuse /mnt/ipod/

We can also unmount as regular user (a sudo shouldn&#8217;t be necessary):
$ fusermount -u /mnt/ipod/

5. Prepare ipod itunes directory :
Ok, now mount the device with &#8220;ifuse /mnt/ipod/&#8221; (if not still mounted) and create the &#8220;iTunes_Control/Device&#8221; directory:
$ mkdir /mnt/ipod/iTunes_Control/Device/
Then, get your UUID:
$ lsusb -v | grep -i iSerial
It&#8217;s the first number and should be 40 characters long. Then, run:
$ ipod-read-sysinfo-extended
(mountpoint here is /mnt/ipod/)
This should generate a file named iTunes_Control/Device/SysInfoExtended.
Make sure it&#8217;s not empty and whatnot; it should be a large-ish plist (XML file) with a bunch of info.
$ fusermount -u /mnt/ipod/

6. Reboot your computer

7. Plug the ipod : you should see it appear on the desktop
and it should now be
a/ directly mounted in rhythmbox and you can add music files (transfer rate still slow but acceptable)
b/ mounted in gtkpod but you'll have to launch the "ifuse /mnt/ipod".
c/ NOT visible in amarok 2.2.1 and still haven't figured out why...
rhyhmbox is unable to remove music files, so please use the previous gtkpod part either to remove files or add videos to the ipod.
Hopefully amarok will handle it soon so everything can be performed from the same app (and gtkpod is a real pain !).

8. That's all folks

Hope this helps,
manuw
OMG. This actually works. 

Just need to add ```
sudo
``` to ```
lsusb -v | grep -i iSerial
```

Thanks a lot!!!

---

### Post by Paul Vega on 2010-01-15
Kia Ora

I have had limited success to date with this instructional. I initially had my touch working ok following the instructions but somehow or other I seem to have lost two of the files for synching. In attempting to correct the issue I am now getting the following error that I need assistance to solve;
E: ipod-convenience: subprocess installed post-installation script returned error exit status 1
Can somebody please advise me on how I can repair ipod convenience?

Well I have looked a little deeper and it seems that I have lost two important files that allow transfer of data. When my pod was working correctly (for a short time at least) there were three files in my iPod folder. There is only one now (com.apple.itunes.lock_sync). I gather that the other two were key to getting the files to transfer. At the moment any files I have entered into Rhythmbox are sitting in the playlist on my PC but do not transfer to the pod. The playlist that is on the pod plays and when I disconnect the pod from the PC the playlist dissappears. Has any one got any ideas of what the files that are missing are and how I can get them back?

I have tried to fix my installation of i_pod Convenience as this seems somehow connected to my issue. I run sudo apt-get -f install and receive the following;
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 libnss3-dev libnspr4-dev
  linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ipod-convenience (0.11-0ubuntu1) ...
mkdir: cannot create directory `/home/paul/.gvfs': Permission denied
dpkg: error processing ipod-convenience (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ipod-convenience
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anybody offer advice?

Paul V

---

### Post by soad6 on 2010-01-17
ok followed all instructions and when doing the command:: ipod-read-sysinfo-extended ipod /mnt/ipod/ :: i get couldnt read xml sysinfo from ipod... why am i getting this error but i get a picture of my ipod on the computer and a picture of a camera that says ipod also? isn't there some easier way to just connect the ipod touch 3 G to linux yet?? i mean we have alot of smart ppl out there hasn't someone figured this out yet??

---

### Post by rdunnion on 2010-01-18
I followed this procedure and it worked mostly. I am at the point where I can mount my iPhone 3g but cannot get the phone to recognize the new music. Any ideas?

---

### Post by Marais on 2010-01-18
I've followed these instructions over and over and over again for my Iphone (non-jailbroken) 3G.
I'm on Karmic Koala latest release 9.10 released in October 2009.

It doesn't work as my Iphone mounts as a USB device here :
gphoto2://[usb:002,003]/
:o

I've created and recreated many times mount points :

/media/iphone

including :
/media/iphone/iTunes_Control

/media/iphone/Photos

but can't get the bugger to mount as anything different than the usb:002,003 which apps like gtkpod seem to be "blind" to.

I did succeed to erase all of my data a few times on the device and install a great bug on the Iphone that caused all apps that were downloaded to crash.:( At least it seems Ubuntu is talking to the device.:P

Any ideas?;)

---

### Post by blibben on 2010-01-19
Hi.

Everything's working fine for me except that I get an error message when I start gtkpod: "Extended info will not be used". Gtkpod only detects my music but not my videos. Anyone got an idea?

---

### Post by pansori on 2010-01-23
ok, so i'm getting stuck here:

when i enter the terminal command 
ifuse /mnt/ipod/


i get the reply
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.


any help? thanks in advance!

---

### Post by Jekshadow on 2010-01-25
ipod-read-sysinfo-extended kept segfaulting, so I just used this command to get GTKpod to sync my Music:
```
echo "FirewireGuid: <my 40 character long uuid>" > /mnt/iphone/iTunes_Control/Device/SysInfo
```
(assuming /mnt/iphone/ is where the device is mounted)

---

### Post by ContentSpooling on 2010-01-25
Thanks for this tips. This really help me.

---

### Post by brucewagner on 2010-01-28
AN ALTERNATE - YET ELEGANT - SOLUTION

Sorry for this sidebar, but I think this is very important...

(1)  I say Apple sucks for intentionally making their products incompatible.  Obviously.

(2)  Here's an alternate solution -- one I am using, and I am recommending to everyone:

Use Dropbox. ( shameless referral: [https://www.dropbox.com/referrals/NTMzMTkyOTc5](https://www.dropbox.com/referrals/NTMzMTkyOTc5) )

Here's what I do:   I put all my Music inside a Music folder within Dropbox.  (In fact, I moved EVERY folder in the Home directory... to INSIDE my Dropbox folder!)

From any iPhone, iPod Touch, Android, PC, Mac, ANY device with a browser...

I can simply go to Dropbox.com, log in, touch Music folder, and touch a track to automatically download and then play it!

If you want continuous music....  I simply make my own "mix tape" MP3 files... (long MP3 files that will play non-stop for 20 minutes, or 60 minutes, or whatever... of a collection of my favorite tracks -a playlist contained in one single MP3 file, in other words.)  Touch that one MP3 file and the iPhone downloads it (Fast!)... I can do this just before walking down the steps to the NYC Subway and I have non-stop music for the next hour or two or whatever.

To add music or movies:  Put them on your computer.  (Of course, everything is within your Dropbox folder!)   (Or, you can add them from anywhere from any device with a browser.)

To remove music or movies:   Delete them from your computer.   (Or from any device with a browser.)

This solution is SOOOOO Simple!

I'm sorry, but all this configuration listed in this How To is far too complex for me (not to mention my friends who can barely work a mouse!),...   AND, the results don't sound NEARLY as elegent as "my solution".

:) 

Happy Jamming!

Use Dropbox. ( shameless referral: [https://www.dropbox.com/referrals/NTMzMTkyOTc5](https://www.dropbox.com/referrals/NTMzMTkyOTc5) )

No, I don't work for Dropbox.  I review technology and try to find easier / better ways to do things... simpler.

---

### Post by snares on 2010-01-28
I have a new iTouch 3G Firmware 3.1.2. I recently had it jailbroken and communicated over ssh. worked but it was a pain. This worked great for me. I didn't even go through the whole thing. I stopped at step 4. After I added myself to the fuse group and restarted itouch mounted right in rhythmbox. I was able to move song too itouch and from itouch. podcast work video and audio. apps I can backup with a simple drag and drop. Thanks. Just wondering if its working fine should I just leave it or should I really finish the HOWTO?

---

### Post by LinuXGo on 2010-01-29
Hi, I'm having trouble installing the package libusb-1.0-0-udev. Here's the result that I post;


sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod4 libiphone-utils libiphone0 python-iphone libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-udev libusbmuxd1 usbmuxd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libplist++1 is already the newest version.
libplist-utils is already the newest version.
python-plist is already the newest version.
libusb-1.0-0 is already the newest version.
E: Couldn't find package libusb-1.0-0-udev

What should I do to fix this problem.?

---

### Post by JosephGarrison on 2010-01-31
When I finally got this to work, it was probably one of the best moments of my life.

---

### Post by manuw2009 on 2010-02-01
wow, your life must be amazing !

---

### Post by miko5054 on 2010-02-01
hi 

i can mount it with rhtymbox  and listen to the songs but i cant add anything 
?? 

any suggestions maybe  i did something wrong?

---

### Post by Barbalras on 2010-02-03
Hi!

I've followed the tutorial and when I try to mount the ipod with

sudo ifuse /mnt/ipod/

I get

usbmuxd_get_device_list: error opening socket!
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.

I've googled but non of the solutions seems to work. Any ideas?

---

### Post by Barbalras on 2010-02-03
Hi!

I've followed the tutorial and when I try to mount the ipod with

sudo ifuse /mnt/ipod/

I get

usbmuxd_get_device_list: error opening socket!
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.

I've googled but non of the solutions seems to work. Any ideas?
I'm using Ubuntu Karmic and the Ipod is an Ipod Touch 2G with 3.0 firmware

---

### Post by pertti on 2010-02-03
> **rimongo said:**
> Just add the libiphone-dev through synaptic and this will solve it.
The usage is:
#ipod-read-sysinfo-extended <device> <uuid>
i.e. #ipod-read-sysinfo-extended fd98145617c113dc15ab151601001ff12354b139 /mnt/ipod

This doesn't work for me. I'm stuck in the ipod-read-sysinfo-extended step. I get the 40-digit device ID using:

```

# lsusb -v | grep -i iSerial
...
  iSerial                 3 99d1ef576d7a1a74eb3de2df9ffb310524f4fd0f
...
```

That "99d1ef576d7a1a74eb3de2df9ffb310524f4fd0f" is the <device> that ipod-read-sysinfo-extended asks for, isn't it? Then:

```

# ipod-read-sysinfo-extended 99d1ef576d7a1a74eb3de2df9ffb310524f4fd0f /media/iPod/
Couldn't read xml sysinfo from 99d1ef576d7a1a74eb3de2df9ffb310524f4fd0f
```

I've tried several variations of the 40-digit ID: with UUID=, using dashes ala fstab... None of these work.

If I skip this step, I'm able to browse and listen to the music in my iPod Touch using Rhythmbox. I can copy tracks into the iPod, which can be played then from Rhythmbox. However, these tracks don't show up in the iPod interface. I'm guessing Rhythmbox is not updating the database right, maybe due to the ipod-read-sysinfo-extended step not being done.

Any ideas on this?

---

### Post by fanum on 2010-02-07
Yes, I was having this problem when trying to set up the new iFUSE sync method for gtkpod. Turned out usbmux was not running. type this into terminal and try again:

sudo usbmuxd -f

---

### Post by edmondt on 2010-02-08
There is a better HOWTO at: [http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html](http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html)

iPod Touch iPhone 3G Ubuntu 9.10 in 5 minutes

```

Steps (start here):

   1. IMPORTANT: Using a Windows computer with iTunes, add at least one song to the iPhone via iTunes. This will create the necessary databases in the iPhone for the following steps to work. (Thanks Jon)
   2. Make sure you are connected to the internet.
   3. Open gnome-terminal through Applications --> Accessories --> Terminal
   4. Copy / paste the following in the console:

          sudo add-apt-repository ppa:pmcenery/ppa; sudo apt-get update; sudo apt-get install gvfs libgvfscommon0 ifuse libgpod-common libimobiledevice-utils python-libimobiledevice libplist++1 libplist-utils python-plist; sudo su -c "echo user_allow_other >> /etc/fuse.conf"

   5. You will be prompted to proceed. Type "Y" for yes and hit enter. This will take about 3 minutes on a broadband connection.

      *Note: This will 1. Automatically make the latest fink fuse, aka "fusepod" application available for downlolad, 2. Download and install it, 3. Make it available for non-root users.

   6. Log out of the desktop by clicking the Ubuntu power button in the top Right corner of the desktop and clicking "Log out" (Optionally you may want to reboot).
      Note: Hugh only had success on an 8GB iPhone 3G running 3.1.2 after rebooting.
   7. Log back on to the desktop.
   8. Unlock and plug-in your iPod Touch / iPhone. You will be prompted several times to open the iPod. Click cancel.
   9. Open gnome-terminal through Applications --> Accessories --> Terminal
  10. Create the SysInfoExtended file on the iPod so that application such as RythmBox can use it by copy / paste the following into the console:

          echo -e "\n\nPlease type the name of your ipod:"; read ipod_name; mkdir -p "$HOME/.gvfs/$ipod_name/iTunes_Control/Device/"; ipod-read-sysinfo-extended `sudo lsusb -v | grep 'iSerial' | awk 'length($0)>=68' | awk '{print $3}'` "$HOME/.gvfs/$ipod_name/"

  11.

      *Note: You will be prompted for the name of your iPod Touch / iPhone. This should match the name of the icon on your desktop.
  12. Log out and back into the desktop one last time.
  13. If MP3 support is desired, click this link to enable the "ubuntu-restricted-extras" packages (this can be done at any time).
  14. Launch RythmBox through Applications --> Sound and Video --> RythmBox. Your iPod should list on the left hand side. Drag files to and from as you would in iTunes.

-Tres 

```

---

### Post by manuw2009 on 2010-02-08
Yep
Well it seems more up to date indeed !
I was glad to contribute to the initial effort anyway...
on the amarok front it seems an initial ifuse integration is in progress !
I compiled today's git and it does see my 3G itouch now...provided that my old nano is also mounted
smells like some kind of libgpod init/triggering

---

### Post by Barbalras on 2010-02-09
> **fanum said:**
> Yes, I was having this problem when trying to set up the new iFUSE sync method for gtkpod. Turned out usbmux was not running. type this into terminal and try again:

sudo usbmuxd -f

excellent!!! now it's really working!

I could get it to work with Rhythmbox but not with gtkpod, nothing happens when I click on "Load Ipod(s)". Any ideas?

---

### Post by exup1000 on 2010-02-09
Hi

I am able to mount the device and Rythmbox see the device, but when I would prefer to use GTKPod instead. It sees the device but I cannot load it. (Cannot read data base)
I try to use the command ifuse /mnt/iphone/ but it says

fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

can anyone suggest what this means.

---

### Post by manuw2009 on 2010-02-09
Hi
well I think you don't need to mount it mAnually anymore provided that you have gvfs backend installed
you just have to edit the repo properties in gtkpod and fill in the .gvfs/xxx directory as location

---

### Post by exup1000 on 2010-02-10
So I am struggling with what your are saying, I am quite a newbie to linux.

Sorry could you give a bit more detail in the process.

---

### Post by brucewagner on 2010-02-10
> **exup1000 said:**
> So I am struggling with what your are saying, I am quite a newbie to linux.

Sorry could you give a bit more detail in the process.

The ultimate guide for the newbie:  [http://brucewagner.posterous.com/how-to-wirelessly-synch-an-iphone-ipod-touch](http://brucewagner.posterous.com/how-to-wirelessly-synch-an-iphone-ipod-touch)

---

### Post by Kosmonaut on 2010-02-23
Hi there.

First of all thanks for  this great how.to.

I ran into a problem though:
I have got 2 computers, a laptop and an office PC.
On my laptop everything works fine, meaning I can sync my iPodT with ubuntu. But! I haven't installed the newest version of the software. An apt-get upgrade gives me this: 

```
Die folgenden Pakete sind zurückgehalten worden: (something like: Some packages are held back)
  gvfs gvfs-backends gvfs-bin gvfs-fuse ifuse libgpod-common libgpod-dev
  libgpod4
```
So...I didn't upgrade, since I wasn't sure what would happen....

Now: on my office-pc. I had the same warning, I ignored it and I upgraded the box. (Before I could do so, I had to remove libiphone-utils and install libimobiledevices-utils). (Note: before updating the office-box, the synchr. worked fine!)
Result: My office-pc can see my IpodT as a music-device, but if I try to run rhythmbox, rbox always crashes with following errors:


```
@ubuntu:~$ rhythmbox

** (rhythmbox:31487): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:31487): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

** (rhythmbox:31487): WARNING **: Unbekannte Aktion (2048) in intelligenter Wiedergabeliste wird ignoriert.


** (rhythmbox:31487): WARNING **: Unbekannte Aktion bei 1038242: 800. Es wird trotzdem versucht, weiterzumachen.


** (rhythmbox:31487): WARNING **: Unbekannte Aktion (2048) in intelligenter Wiedergabeliste wird ignoriert.


** (rhythmbox:31487): WARNING **: Unbekannte Aktion bei 1039450: 800. Es wird trotzdem versucht, weiterzumachen.


** (rhythmbox:31487): WARNING **: Unbekannte Aktion (2048) in intelligenter Wiedergabeliste wird ignoriert.


** (rhythmbox:31487): WARNING **: Unbekannte Aktion bei 1040636: 800. Es wird trotzdem versucht, weiterzumachen.


** (rhythmbox:31487): WARNING **: Unbekannte Aktion (2048) in intelligenter Wiedergabeliste wird ignoriert.


** (rhythmbox:31487): WARNING **: Unbekannte Aktion bei 1041830: 800. Es wird trotzdem versucht, weiterzumachen.


** (rhythmbox:31487): WARNING **: Bildgrößen in iTunesDB und ArtworkDB inkonsistent (0+1 != 0)


** (rhythmbox:31487): WARNING **: Bildgrößen in iTunesDB und ArtworkDB inkonsistent (0+1 != 0)


** (rhythmbox:31487): WARNING **: Bildgrößen in iTunesDB und ArtworkDB inkonsistent (0+1 != 0)


** (rhythmbox:31487): WARNING **: Bildgrößen in iTunesDB und ArtworkDB inkonsistent (0+1 != 0)


** (rhythmbox:31487): WARNING **: Bildgrößen in iTunesDB und ArtworkDB inkonsistent (0+1 != 0)

Segmentation fault
```

How can I convince Rbox to cooperate with the Ipodt again. Any help would be great.

---

### Post by Marais on 2010-03-29
After being subscribed to this thread for months I have succeeded!
This is the page that did it :
[http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13](http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13)

I did have some problems, I had some dead repositories that needed to be eliminated and had to manually install usbmuxd and some of its dependencies (libusbmuxd and such), but now my Iphone 3G shows up as such in Nautilus and I can see all of its guts!
Works great in RhythmBox also!
Bye bye wicked Itunes!

---

### Post by fugazi32 on 2010-04-08
> **rimongo said:**
> Just add the libiphone-dev through synaptic and this will solve it.
The usage is:
#ipod-read-sysinfo-extended <device> <uuid>
i.e. #ipod-read-sysinfo-extended fd98145617c113dc15ab151601001ff12354b139 /mnt/ipod

I did *ipod-read-sysinfo-extended 1d8ce5f9ca8126141e5adc7a705822ac2038ee38 /mnt/iphone* but still get: *Couldn't read xml sysinfo from 1d8ce5f9ca8126141e5adc7a705822ac2038ee38*
Can anyone help me get past this stage? :confused:

---

### Post by fugazi32 on 2010-04-08
> **brucewagner said:**
> The ultimate guide for the newbie:  [http://brucewagner.posterous.com/how-to-wirelessly-synch-an-iphone-ipod-touch](http://brucewagner.posterous.com/how-to-wirelessly-synch-an-iphone-ipod-touch)

Cheers for the tip! :D

---

### Post by fugazi32 on 2010-04-08
> **Jekshadow said:**
> ipod-read-sysinfo-extended kept segfaulting, so I just used this command to get GTKpod to sync my Music:
```
echo "FirewireGuid: <my 40 character long uuid>" > /mnt/iphone/iTunes_Control/Device/SysInfo
```
(assuming /mnt/iphone/ is where the device is mounted)

Still didn't work... :(

---

### Post by fugazi32 on 2010-04-10
Bump... :(

---

### Post by brucewagner on 2010-04-10
> **fugazi32 said:**
> Bump... :(

Still... the best / easiest way:  [http://brucewagner.posterous.com/how-to-wirelessly-synch-an-iphone-ipod-touch]("http://brucewagner.posterous.com/how-to-wirelessly-synch-an-iphone-ipod-touch")

:)

---

### Post by gizmoloon on 2010-04-19
when i get to stage 4, it says fuse :missing mountpoint, what am i to do?

---

### Post by Dr.Jobo on 2010-07-15
Hi Im using the OpenSSh via USB cable method, to tether over Iphone 3GS. I installed usbmuxd, but it doesnt work. If im connection my phone to ubuntu (Hardy) it automatically mounts and i can see and access the DCIM folder. 

I start
$ iproxy 5000 22
$ waiting for connection

Then im setting up the ssh tunnel
$ ssh root@localhost -p 5000

After this i got from usbmuxd an error like this:
$ accepted connection, fd = 4
$ usbmuxd_get_device_list: error opening socket!
$ Connecting to usbmuxd failed, terminating.

Plz help me, cause i really need this to be able to work next week. Thanks a lot and greetz

---

### Post by Dr.Jobo on 2010-07-17
So i got it to work, to enter the iPhone shell, like this.

- Connect iPhone via usb
- unmount it using the arrow in Filebrowser
- then sudo usbmuxd -f, then it is connected
- then using iproxy 2222 22
- then
- after that typing in my root password for my iPhone
- then I have the iPhone terminal on my Ubuntu Desktop
- I configured the proxy settings in firefox

But everytime I'm trying to enter a website it throws this error:

channel 3: open failed: administratively prohibited: open failed


Can anyone help me with that ?? Thanks a lot!

---

### Post by Dr.Jobo on 2010-07-17
So here is the solution for the problem above:

- put your iPhone to never switch off mode
- start safari on iPhone

then it should work with firefox via your computer

---


---
title: "Adding a new 4tb HDD to raspberry pi"
date: 2021-03-15
forum: New to Ubuntu
---

### Post by gremlin76 on 2021-03-15
I am running a desktop from a raspberry pi 4. I am trying to run it as a media center on my living room television, In order to do this, I have a 4TB HDD . That I am trying to put all my media into. I cannot 1) figure out how the best way to format the drive, 2) how to get all my music media to play via rhytmbox.

I am mostly new to linux and ubuntu. I am running 20.10 from a micro sd card in the pi. I realize that this is not optimal and have plans to upgrade the O.S. to a SSD once I have finalized the O.S. 

Right now, I just need to get the 4TB HDD formatted to get the media on it for replay.

---

### Post by yancek on 2021-03-16
What do you mean by "best way to format the drive"?  What software to use?  Parted, Gparted, fdisk, gdisk, etc.  What have you tried and what results do you get?  Your post is a bit too vague.  You might indicate what specifically you have done and what the results were.  Until you format and copy the music files to the drive there isn't much any one can tell you about how to play it via rhythmbox.

---

### Post by ActionParsnip on 2021-03-16
If you use Gparted you can make it a big Ext4 partition and mount it using an entry in /etc/fstab

Remember to use the blkid of the file system. You can see this using:
```

sudo blkid

```

The existing fstab entries will be a good guide. Remember to create an empty folder to mount the file system to. I suggest you use:
```

sudo mkdir /data

```

---

### Post by gremlin76 on 2021-03-18
In the past, I used gparted and partitioned the drive into 2 2TB partitions and it was satisfactory. the two partitions were both mounted to mnt/GDrive. However, that drive failed after only 6 months. I had to make the two partitions because it would not format one large one, i forget what filesystem I was using.  I am hoping to eventually make this 4TB monster a network accessible drive, but am a long way from that.

I am starting over with a new (to me) 4TB drive and hope that it lasts a bit longer. 

Why make a /data folder to mount it to? is /mnt not good enough?

I hope this answers some questions.

---

### Post by CelticWarrior on 2021-03-18
> [COLOR=#000000]I had to make the two partitions because it would not format one large one, i forget what filesystem I was using.[/COLOR]
File system here is irrelevant, the problem is using the old MBR ("msdos") partitioning table, really not recommended for large drives due to that limitation exactly.
In Gparted start at the menu Device > Create new partition table... and select "GPT". Then you'll be able to create one single large partition if that's what you want.

---

### Post by mikewhatever on 2021-03-18
Actually, FAT32 filesystem has a limit - 2TB max partiton size. There are better options like ext4, exfat, etc.
There are many ways to create partitions and format them. "The best way is irrelevant", and is a kind of odd way to look for answers. Who cares if it's the best?

---

### Post by gremlin76 on 2021-03-19
Awesome, that worked great. Only trouble now is that root is the only user with access. This computer is my living room desktop and will soon be the media hub for the whole house. I will want other desktops to access this drive, but first i need to put media to access on it. RN i cannot do any of it.

---

### Post by CelticWarrior on 2021-03-19
It happens with Gparted because it runs as root, reason why I often recommend creating/formatting partitions with Disks (runs as user).
Anyway, just do a chown.

---

### Post by TheFu on 2021-03-19
Just to confirm what I think was said above:
[LIST]
[*]Put a GPT partition table onto the HDD
[*]Create a Partition or 2
[*]Format each with ext4 or xfs ; if you don't have a specific need, ext4 is fine
[*]Mount by modifying the /etc/fstab.  Don't use a GUI to mount it on-demand. Doing that would cause the media to be missing.
[*]Use chown + chmod and normal Unix groups to allow multiple userids whatever access to the files and directories you need. [https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) should have steps that are clear.
[/LIST]
/mnt is for temporary use according to standards.  /media and /data or elsewhere would be fine.  /media is for temporary OS mounted USB storage and CDROMs.  But it is your system.  snap packages may only allow access to files in your HOME or the HOME of which ever userid is logged in.

There are great media center software options for TV, Movies, Videos, Music, photos designed for a "10 ft interface".  Most of these work with $20 remote controllers or your smart phone/tablet, but you need to know if you want to playback everything on the video and audio devices directly connected to the Pi or you want the Pi to stream that content to other devices.

R-pi computers are terrible at transcoding content to different video formats. Basically, you'll need all the video files that are over 720p resolution to be in h.264 encoding and either mkv or mp4 containers. Audio format doesn't matter nearly as much unless you want to passthru the audio directly to an AV-Receiver. 

MKV can contain many different audio tracks which can be selected by the playback device. So tracks for AC3/DTS, AC3/DD+ and vorbis and mp3 and aac and mp2 can all be included, if you like. Same for different languages. It is good to help kids learn a new language is they can watch movies in the other language and with captions/subtitles.

Running a "Desktop" on a Pi is less than optimal.

I don't use Ubuntu-anything on my R-Pi devices.  I use OSMC (kodi build for r-pi devices) and mpd (fairly standard audio server with many, many, controllers) on them. They don't have any local media. All media is on the LAN and can be accessed using either NFS or DLNA or mpd protocols.  There are reasons and they work very nice for those uses.

Another user was trying to use a raspberry-pi to be a NAS device for his LAN running samba using the wifi connection. Lots and lots of problems.

You'll want to keep the OS on a microSD card. Don't move it to the 4TB drive. There are reasons.
Please have a backup plan/solution for everything. Media doesn't really allow daily, versioned, backups, but everything else on the system does.  Tomorrow I'm attending a malware/cryptoware training class to learn what I think I already know.  For those, nothing can replace "pulled" backups, that are daily, automatic, and versioned. If the backup is connected to the same system with the crypto-malware, everything could be encrypted.

Anyways, have fun. Learn from the mistakes you and others make. Nobody's media center setup is perfect.

---

### Post by gremlin76 on 2021-03-19
wow... that's a lot. i see what you are saying.
I am using kodi and it performs well-ish. when it does not i use vlc.
kodi is the standby for series and such cuz it helps us keep track.
when that fails we use vlc.


Thanks for that huge disposition of information! i will look back here many times in the coming months.

good to know that i am not alone!

keep learning at coding!

---

### Post by TheFu on 2021-03-19
VLC is pretty heavy for use on a Pi.  Instead, just use mpv or place videos into a separate "Videos" library for Kodi/OSMC and let the built-in player handle playback.

OSMC is an optimized Kodi build (complete OS + Kodi) for raspberry-pi hardware.  By loading Ubuntu, then Kodi, you have two not-so-optimal layers on a fairly low-powered computer. If you use wifi to serve or access media, you'll likely be disappointed too.  I have a 300 Mbps "N" wifi router, but never get better _claimed_ connection speeds than 65Mbps, and actual throughput is probably half that.  But wired connections get within 10% of the expected throughput.  Just be aware that pi v3 might have GigE NICs, but usually 200Mbps is the max possible due to the price/bus architecture trade-offs in the Pi hardware.  I understand the Pi v4 solved that, but I didn't get one for Xmas and honestly haven't outgrown the v2 or v3 Pis we already use for media playback.

---

### Post by gremlin76 on 2021-03-20
Wow Wow Wow! that a lotta info. 

Just for clarification. This is a Pi 4B 8GB. By  desktop i mean just for basic computing and things like this (since my  usual desktop crashed.) I am finding that the Groovy Gorilla actually  has raspberries on his sunglasses and seems to be working great for  this. I tried a few other OS's, however settled on this one because it  was the only one that made it easy to use my usb 5.1 sound card with  s/pdif output to my old amplifier. Sounds great through my 7.2 system.

There is enough information here to keep me busy for a month!

my  external HDD's are attached through a self powered USB hub to the pi  which is wired to the router. The externals are just for A/V media which  is backed up on unconnected HDD's. The 4TB is just so all of it can be  in one place. The OS is still on micro SD in the pi. 

The only  trouble i have in video playback is VLC is better than KODI, but i like  the way KODI manages all the media better. I will look into the formats  of the files that simply do not work on KODI.

Rhythmbox is  working alright for audio, but takes forever to add in all my 80k audio  files. Some have to be added 1 disk at a time. Some just won't go.

---

### Post by TheFu on 2021-03-20
> **gremlin76 said:**
>  
Just for clarification. This is a Pi 4B 8GB.  
<snip>
Rhythmbox is  working alright for audio, but takes forever to add in all my 80k audio  files. Some have to be added 1 disk at a time. Some just won't go.

Kodi should play anything. Really. There shouldn't be any need for vlc, unless you have lots of corrupted video files. VLC does handle those better.  I would encourage you to check out mpv and I suppose there is a GUI that will use mpv - I don't work that way.

---

### Post by gremlin76 on 2021-03-24
Thanks for the mpv tip. i have some recent 1080p files that vlc just couldn't handle. mpv is doing much better. 

Now i just need to re-read the chown command and remember how to mount to a specific folder and i will be back to transferring files to my new drive.

Thanks everybody for the help!

---

### Post by gremlin76 on 2021-05-04
Ha Ha, then my O.S. crashed, I think because the SD card was full. Flashed Ubuntu 20.10 onto a bigger SD and restarted the process. Set the mount point to a folder /data. Got the gpt partition table onto the drive and formatted it to one big partition. Did the chown, I think, but still do not have permission to add files. Can anyone give me pointers , or post a quick link to the right command and how to use it?

---

### Post by TheFu on 2021-05-04
chown only works on POSIX standard file systems, so FAT32, exFAT, NTFS don't work.  For those, Linux fakes the permissions through mount options.  What file system is being used?   It matters.

To determine that, after mounting the storage, run 
```
df -Th
```
A column with the file system used will be shown.

---

### Post by gremlin76 on 2021-05-04
under filesystem it says /dev/sda1 it is in ext4

---

### Post by TheFu on 2021-05-04
So, ext4 is native linux.

20.10 support ends in June. Do you really want to upgrade the OS every 6 months?  That's required if you don't run an LTS release. If you are new to Linux, you really should run a supported, LTS release.  Today, that would be 20.04.  Support for it ends in 2025, assuming you don't use one of the "flavors".

If you want a media player, there are better distros for raspberry pi hardware.  I use OSMC.tv.  It is debian-based and works well on v2 and v3 raspberry pi hardware.  I don't have a v4 Pi and some of the early versions had a few non-standard problems, like the USBc power port wasn't omni-plug. It has a specific way the power cord had to be connected to work.  The r-pi v4 uses more power than earlier models too. I think they've got the 4k video figured out.  If we get a 4k TV/projector, then I'll definitely get a Pi that supports it.

Ok - so with ext4, after you mount the storage, it is just normal Unix permissions, owner, and group controls like have been around since the 1970s.  Learn this stuff now. Don't put it off. In 45 minutes, you can know 90% of Unix file permissions for the rest of your life, but you have to do the work to learn it.  That means actually working through a 15 min tutorial, then creating 3 new users, 3 new groups, mixing and matching users+groups, then spending 30 minutes testing every possible permission mask allowed between the different users until the "click" happens in your brain.  I don't think there's any other way.
If you don't spend the time, you'll never really understand it and that will cause hours, days, weeks, months, years of frustration.  Plus, every popular OS in use today around the world uses the same Unix permissions ... except 1 OS.  All the others are Unix, so this isn't a waste of time and much easier to master than a foreign language, but not as easy to retain as riding a bicycle. Some practice is needed to retain this knowledge, once captured.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is a gentle introduction. Start there. Don't just read it.  Open a few terminals, make a play directory in /tmp/foo and play inside there.  Use "touch file1 file2 file3" to make empty files. You can put text inside them if you like, but at this point, just having the empty files is sufficient to see errors and try all the chown and chmod options.

---

### Post by TheFu on 2021-05-04
BTW, when we post commands that generate output, it is usually so you'll run the command them post the command, all options and the output back here.  There are things that stuff shows that we'll see as issues. Someone new is very likely to misinterpret what the output actually means or miss critical details.

BTW, **ls -al** is the command to see the permissions on Linux systems.  For file access, the permissions of the file AND on the directory holding the files matters.

---

### Post by gremlin76 on 2021-05-04
Yes, I get that on bot counts. I  am indeed new to linux and ubuntu and I have very much liked what few things I have learned so far. I get that full on use of the tutorial and practice, practice, practice is necessary for learning to occour. I am running linux on two pi's and an old p.c. that windows died on years ago. It is hard for me currently to get the output from one command on one machine to the reply to the thread on another. Thank you for your support in my continued learning. Actually, I was already looking at that link after I posted last and just trying to figure out when I would have the time to practice in a quiet space (desktop and media center are in the L.R. and the other pi is in my workshop, I have two young kids as well) I will continue to persevere.

---

### Post by TheFu on 2021-05-05
Are you using **ssh** to connect to any system on your home network from anywhere else?
ssh is how Unix people connect between systems. I haven't typed on any of my raspberry pis in a few years.  Everything is handled either with a remote control or over ssh.

ssh is the swiss-army-knife of system-to-system connectivity.  
Want to run commands remote? ssh
Want to run GUI programs remote? ssh -X  (I run thunderbird and libreoffice on remote systems, but have the window displayed locally)
Want to transfer files between systems?  scp, sftp, rsync (over ssh), sshfs
Want a free VPN from anywhere in the world back into your home network?  ssh
Want to access a web server that is only on your home network from anywhere in the world?  ssh w/ SOCKS proxy
Want a remote desktop?  x2go, which uses the NX protocol and that includes ssh

All ssh authentication can use ssh-keys. This means the connection is highly secure AND very convenient.  I unlock my ssh-keys once a day, then they can be used transparently for all other ssh-based connections.  That's ssh, scp, sftp, x2go, sshfs, rsync and about 20 other tools.  With a little ~/.ssh/config setup, we don't need to know odd names of other systems or memorize IP addresses, usernames, non-standard ports either.  Those settings are automatically picked up by all ssh-based tools.  When long time ssh users learn this, it changes their lives.

Win10 started supporting some of what ssh provides, what, about, 4 yrs ago?  It still lacks many of the most important things, but considering it took MSFT 20+ yrs to make an industry standard version of ssh, we really shouldn't hold our breadth. 

ssh rocks.

---


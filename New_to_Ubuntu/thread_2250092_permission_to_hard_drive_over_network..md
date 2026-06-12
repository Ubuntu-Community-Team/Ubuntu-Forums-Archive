---
title: "permission to hard drive over network."
date: 2014-10-26
forum: New to Ubuntu
---

### Post by jordan30 on 2014-10-26
This is my first time using linux. So far i like it.. I am using xbmcubuntu. I am using it on a computer mainly used for watching downloaded movies / tv. 
It has 2 hard drives, the main one with the xbmc installed and another second drive for my "Media".. 

I am using a laptop with windows 7 and utorrent to download files, i want the files to download the the Media drive.. but i can not figure out how to allow access. I can see the folders on the main drive.. but not the Media drive.. i have tried samba, chmod, and can not figure it out.. i have spent hours watching videos and reading and still can not figure it out... please help..

---

### Post by nerdtron on 2014-10-26
So the Media drive is in Linux, does it contain files already? What is the path to the folder on the Media Drive?

In windows 7, how do you browse/access and save files to the "Main Drive" of Linux.

---

### Post by jordan30 on 2014-10-26
the media drive is not in linux, it was created when i had windows 7 on that computer and has 1.5tb of movies on it. But the linux computer sees it and accesses the movies no problem, 
When i look at the linux computer from my windows laptop. I see the folders on the linux drive.. but do not see the secondary "Media" drive.. I usually look at it through the network.

the path is /media/jordan/Media
when i do: ls -l
drwx---------- jordan jordan

---

### Post by nerdtron on 2014-10-26
I'm still a bit confused on your setup.

> This is my first time using linux. So far i like it.. I am using  xbmcubuntu. I am using it on a computer mainly used for watching  downloaded movies / tv. 
**It has 2 hard drives, the main one with the xbmc installed and another second drive for my "Media"..**

So the xbmcubuntu has 2 drives right? xbmcubuntu sees all the files in the "media" drive? The media drive is not Linux but is currently on the computer witxbmc rigth?


> When i look at the linux computer from my windows laptop. I see the  folders on the linux drive.. but do not see the secondary "Media"  drive..
"How" do you look at linux computer from windows laptop? SSH? remote desktop? Can you post screenshots of your problem?

---

### Post by jordan30 on 2014-10-26
Yes the xbmcbuntu see all the files in the Media drive. The media drive is not linux but in the computer the linux drive is in

I look at the xbuntu computer using the windows laptop. Through network, then selecting the xbmcbuntu computer. It only shows the folders that are created in the linux drive, nothing from the Media drive. I cannot figure out how to give permissions to the network. 
 [IMG]http://s5.postimg.org/f8opkl287/screen.jpg[/IMG]

---

### Post by jordan30 on 2014-10-26
like when i ls -l 
on my media drive.. 
[COLOR=#000000]drwx---------- jordan jordan
[/COLOR]Its not giving permission to any user or group , i try to change it but i cannot. Any help would be awesome.

---

### Post by sandyd on 2014-10-26
sound like you need to force a umask.

Whats the output of
```

sudo blkid
cat /etc/fstab
mount -l
```

---

### Post by jordan30 on 2014-10-27
ok i tried all those commands.. what info are you looking for them?
its on /dev/sdb1   file structure NTFS

---

### Post by nerdtron on 2014-10-28
> **jordan30 said:**
> ok i tried all those commands.. what info are you looking for them?
its on /dev/sdb1   file structure NTFS

We're looking for all the output of those commands so we can analyze your setup and give proper advise. The information you post here are to little or rather on the gui end, we need to dig deep.

---

### Post by mastablasta on 2014-10-28
also if the drive is on Linux computer it means it is mounted on Linux operating system, but is using windows file system (two completely different things).

and now for something completely different - why don't you just install the transmission (or maybe on PC even utorrent app would work) in xbmc and then use your browser to load torrent and download files directly to your XBMC PC? it's either under apps or services. there is also rtorrent if you prefer command line.

why do you want to download to windows and then transfer files to XMBC? Furthermore the issue is either that the disk is not mounted or not shared properly over network (if using samba then you need to setup same workgroup, user access etc.) In my case for some reason SAMBA was slow, so I use FTP instead when I need to connect to the media folder.

---


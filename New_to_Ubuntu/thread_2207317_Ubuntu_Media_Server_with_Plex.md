---
title: "Ubuntu Media Server with Plex"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by rich11 on 2014-02-23
Hello.
I have just built a pc purely as a media server to work with Plex. I've always used Windows but have decided to install Ubuntu to try. My server has a 60gb SSD (for the OS, Plex and other programs) and a 3TB HDD for all my media.
I have a few problems.
1. I need it to boot Plex Media Server up from the start.
2. I need Ubuntu to detect the Media HDD from the start.
3. When i try to add the folders to Plex (from Media HDD) it doesn't show the subfolders. Eg Movies, Kids Movies, TV programs, Music.

P.S I'm a total newbie so i don't know anything about Ubuntu.

Many thanks in advance..

---

### Post by squakie on 2014-02-23
Have you read this link:  [https://forums.plex.tv/index.php/topic/26727-how-to-plex-media-server-on-ubuntu/](https://forums.plex.tv/index.php/topic/26727-how-to-plex-media-server-on-ubuntu/)

---

### Post by rich11 on 2014-02-23
Read through it and it's all jargon to me. Plex is installed ok, i just need it to open when i boot up. Also Plex won't detect the folders on my 2nd HDD drive (Media). I'm seriously considering going back to windows which is a shame because Ubuntu desktop seems quite good, with some usefull features.

---

### Post by tripp98 on 2014-02-23
If plex is installed on the computer it runs in the back ground all the time.  

you should be able to see it from another pc on your network  [http://](http://)[computer name] or [ip]:32400


as for it not picking up the folders/meda from your 2nd drive.  the user that it was installed to probably plex needs access to those files/folders

right click on the folder or files go to properties
permissions
if this computer is secure on your home network give other users full access to the files/folders  then do a quick scan and all your media should show up.

dont give up because its different.  Ubuntu has made working with computers fun again for me

---

### Post by Vladlenin5000 on 2014-02-23
you need two procedures to achieve your goal but fortunately both are quite easy. An introduction is needed, however, in order for you to understand what's in stack here.

First of all you need to understand that unlike Windows, a Linux OS doesn't mount additional partitions automatically. This is by design and due to security concerns. Considering you have your media in a different partition/different drive you need to tell the system to mount it at boot, otherwise you need to mount them - opening them in a file manager does that - before apps can access its contents. How to do that is explained in this official wiki (all you need to know is in the first "chapter" "Per-User Mounts": [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) 

Now the second part - running an app at boot - is even easier. There are already lots of programs that, for your convenience, run on boot. This page explains how to add one: [http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login](http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login)

---

### Post by rich11 on 2014-02-24
Thanks for the info. I have now got my 2nd HDD to mount automatically, and plex autoruns anyway (I can't see it in System Monitor though).
I now need to get plex to see the folders that are on my 2nd HDD. Any Ideas??  Thanks

---

### Post by Vladlenin5000 on 2014-02-24
> **rich11 said:**
> Thanks for the info. I have now got my 2nd HDD to mount automatically, and plex autoruns anyway (I can't see it in System Monitor though).
I now need to get plex to see the folders that are on my 2nd HDD. Any Ideas??  Thanks

You should have everything you need by now. Provided the folders you want in the now mounted 2nd drive are correctly configured in Plex it should work, just work. I have zero experience with Plex tough. Perhaps you could browse their own forum? I vaguely remember it had a Linux section...

---

### Post by whereismymindat2 on 2014-09-12
Hi Rich,
I'm relatively new to "trusty" (years ago I was on think 9x Ubuntu)--however. 

Have you tried the following? 
SRC:[http://aplicacionesysistemas.com/en/instalar-plex-en-ubuntu-12-04/](http://aplicacionesysistemas.com/en/instalar-plex-en-ubuntu-12-04/)

It requires a dependency that's not clearly evident

```
[COLOR=#808080]**sudo add-apt-repository ppa:plexapp/plexht**[/COLOR]
[COLOR=#808080][B]sudo add-apt-repository ppa:jon-severinsson/ffmpeg
sudo add-apt-repository ppa:pulse-eight/libcec                        <------dependency
sudo apt-get update
sudo apt-get install plexhometheater[/B][/COLOR]
```

This is also located in the Synaptic repository, should you desire to pull from there. (I haven't tested my machine yet)
Initial install not working well, thus starting over. 

W.

---


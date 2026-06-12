---
title: "Plex won't read my directory structure"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by johnmaccuish1963 on 2014-05-25
I recently decided to try Plex for my streaming needs, I installed via Software center, started plex and had no problems until it came time to select my Movie and Music directories.
I can not get it to look past /home/lucy where my media mostly resides  eg: /home/lucy/Music
I can get it to go /media/toshiba ext/Movies  and it loads all those and I can play them on the Ps3 no problems.
I have been googling and searching forums now for 2 days and I am no further ahead other than a stress headache,  it seems like a permission issue, I have tried changing ownership of folders to plex, added plex to groups then gave group permissions for folders but nothing I try seems to change anything so I must be doing it wrong. :redface:
I have read this many times and tried to no avail even though I don't completely understand it: [https://support.plex.tv/hc/en-us/articles/200288596-Linux-Permissions-Guide](https://support.plex.tv/hc/en-us/articles/200288596-Linux-Permissions-Guide) 

drwxr-xr-x 71 lucy plugdev    4096 May 25 15:38 . 
drwxr-xr-x 44 lucy plugdev    4096 Jan  6 19:20 Music

lucy@lucy-N61PB-M2S:~$ groups plex
plex : plex plugdev


The only other thing I seen that I know will work is to move all my media out of my home folder in to say my media folder but that would be a very big job, some of my media is linked to transmission and that would mean re-setting the locations, i have done this before and it is not fun.
Some easy to follow suggestion would be appreciated.;)

Ubuntu 12.04 LTS

---

### Post by Morbius1 on 2014-05-25
I don't use plex but does this help in any way: [http://askubuntu.com/questions/150909/plex-wont-enter-my-home-directory-or-other-partitions](http://askubuntu.com/questions/150909/plex-wont-enter-my-home-directory-or-other-partitions)

One strange entry is this:
> This confused me too, but eventually I learned that Plex requires *write* permissions on the file before it will detect it
I read that as "Plex requires write access to read". What kind of a world has this become .........

Anyway you could try and set your Music directory to 775 instead of 755 to see if that statement is true:
```
chmod 0775 /home/lucy/Movies
```

You might also see what permissions are on the other directory to see it it's giving write access to plex:
```
ls -dl "/media/toshiba ext/Movies"
```

---

### Post by johnmaccuish1963 on 2014-05-25
From this link: [http://http://askubuntu.com/questions/150909/plex-wont-enter-my-home-directory-or-other-partitions](http://http://askubuntu.com/questions/150909/plex-wont-enter-my-home-directory-or-other-partitions)  "Yeah, running it as the current user does indeed solve this particular problem" , I don't know how to try this, I run it by opening unity panel and clicking on Plex which then opens a browser window in chrome.


I tried: chmod 0775 /home/lucy/Music and it changed it to drwxrwxr-x 44 lucy plugdev   4096 Jan  6 19:20 Music, from: drwxr-xr-x 44 lucy plugdev 4096 Jan 6 19:20 Music, but Plex still won't go past /home/lucy.


lucy@lucy-N61PB-M2S:~$ ls -dl "/media/TOSHIBA EXT/Movies External"  {Plex reads this}
drwxrwxr-x 40 lucy lucy 4096 May 24 02:23 /media/TOSHIBA EXT/Movies External.  which permissions look the same as newly changed /home/lucy/Music.
so I done a  chmod 0775 /home/lucy which changed it to drwxrwxr-x 71 lucy plugdev 4096 May 25 15:38  from drwxr-xr-x 71 lucy plugdev 4096 May 25 15:38 
stopped plexmediaserver and then restarted it, still no luck. 
Restarted computer, opened plex no change, then noticed I could type in address so I typed /home/lucy/Music and Plex is now loading all my music.
It is going to take awhile, when it is done I will try a movie folder next and see how it goes, whether I have to change permissions or just type in address.

Thanks. :D
John

---

### Post by johnmaccuish1963 on 2014-05-26
*Update: I was able to just enter the path to my movie folders and Plex loaded them no problem even though I could not find them in Plex directory tree, so seems like changing permissions and manual entry of address fixed this for me.
My external drive was a NTFS drive so I had to do this:[https://forums.plex.tv/index.php/topic/72541-plex-media-server-not-seeing-external-hard-drive/](https://forums.plex.tv/index.php/topic/72541-plex-media-server-not-seeing-external-hard-drive/)

Sudo bkid  {to get uuid #}
[COLOR=#555555][FONT=helvetica]Create a directory in /media named externaldrive: sudo mkdir -p /media/externaldrive
[/FONT][/COLOR][COLOR=#555555][FONT=helvetica]Create an entry in /etc/fstab {sudo gedit /etc/fstab} that looks like this:
 UUID=7896A36E96A32C16 /media/externaldrive ntfs-3g defaults,permissions,auto 0 1 { I copied and pasted this line in to fstab, changed uuid to my #}[/FONT][/COLOR]
[COLOR=#555555][FONT=helvetica] save and close fstab[/FONT][/COLOR]
[COLOR=#555555][FONT=helvetica]Unmount your USB drive, then run from command: sudo mount /media/externaldrive
[/FONT][/COLOR]
lucy@lucy-N61PB-M2S:/$ sudo chmod -R 0775 media {recursively changed all permissions in Media folder}
Opened Plex and could click on my folders to add, did not have to enter address in bar.

Thanks for putting me on track. :D
John

---


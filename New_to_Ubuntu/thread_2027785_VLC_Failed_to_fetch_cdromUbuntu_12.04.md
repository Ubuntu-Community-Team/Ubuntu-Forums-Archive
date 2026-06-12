---
title: "VLC Failed to fetch cdrom://Ubuntu 12.04"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by trevorthomas on 2012-07-17
Hi all, 
Have downloaded VLC. but not able to play movie and getting this code

Would be grateful for your help on this

Trevor

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by sanderj on 2012-07-17
The error message is from the the software repositories, has not to do with VLC.

So: what happens when you type "vlc" on the command line?


Getting rid of the error:

Assuming you have *installed* Ubuntu (and you're not running from a live CD / USB-stick), do this:

Start "Software Center". Clikc on Edit -> Software Sources. That will give an pop-UNDER (so minimize or close Software Center) with "Software Sources". 
In "Software Sources", Click on the first tab "Ubuntu Software", and at the bottom, UNcheck "cdrom with ...". Then close Software Sources.

---

### Post by mastablasta on 2012-07-17
it could also be that CDrom device is mounted on another point. go to settings in VLC and try changing the direcotry for CD rom. 
 
for me i think it mountis it on /scr or something like that. not on /cdrom

---

### Post by trevorthomas on 2012-07-18
Sorry Guys, 
Still no luck with vlc.
When I open vlc and click play it opens a screen in which I choose /dev/dvd.  when I ok that the title bar will quickly change to the title of the movie and then back to vlc. 

If I try to make another selection such as /dev/cdrom it brings up a fail message. 

any help appreciated. 

Trevor

---

### Post by sanderj on 2012-07-18
What's on the CD / DVD?

Can you play a .avi or .mpg with your VLC? In Nautilus, right-click on a .avi or .mpg, and select "Open with VLC".

---

### Post by NikTh on 2012-07-18
Hi , 
try this : 
Go to Update manager > settings > other software and UN-tick the CDrom 12.04 boxes. Close update manager.
Then open a terminal (Ctrl+alt+t) and copy-paste these commands from here to your terminal (one at time , one line = one command) 
```
sudo apt-get update ; sudo apt-get upgrade
sudo apt-get install --reinstall vlc 
``` 
If errors occurred post them here. 

Then try to open vlc again and play a movie.
Thanks

---

### Post by Hadaka on 2012-07-18
Hi,  the reason it is starting then stopping is due to the encryption
on the dvd movie. Have you loaded Ubuntu Restricted Extras from the
sotware center? if you have loaded the restricted extras and its still stopping,
try this

```
 
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb 
```

```
 
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb 
```

---

### Post by trevorthomas on 2012-07-20
hi guys and gals, 
tried everything recommended and still no go, 

this is my latest message when I try to start

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not read -1/4 blocks at 0xff9d.[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]any help appreciated[/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by trevorthomas on 2012-07-20
also just got this message

dpkg: error processing libdvdcss2_1.2.9-2medibuntu4_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libdvdcss2_1.2.9-2medibuntu4_amd64.deb
trevor@trevor-Latitude-E6500:~$

---


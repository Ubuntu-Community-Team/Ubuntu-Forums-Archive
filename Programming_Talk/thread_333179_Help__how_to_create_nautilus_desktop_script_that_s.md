---
title: "Help : how to create nautilus desktop script that support s &quot;open with&quot;"
date: 2007-01-07
forum: Programming Talk
---

### Post by 3togo on 2007-01-07
I wrote a very simple bash script to generate playlist and play the list using mplayer.
I also created a desktop script. However, I could not make it available on context-menu. 

 Any idea?

jc@jc-desktop:~$ cat /usr/local/bin/jplayer
#! /bin/bash
find . -name "*.avi" -print > playlist.txt
sort playlist.txt > playlist_sorted.txt
gmplayer -really-quiet -vf expand=0:-60:0:0 -playlist playlist_sorted.txt

             
jc@jc-desktop:~$ cat /usr/share/app-install/desktop/mplayer-playlist.desktop 
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=MPlayer Movie Player(AutoPlayList)
GenericName=Multimedia player
Comment=Multimedia player
Comment[de]=Multimedia-Player
Comment[es]=Reproductor multimedia
Comment[fr]=Lecteur multimedia
Comment[it]=Lettore multimediale
Icon=mplayer.xpm
TryExec=gmplayer
Exec=jplayer
Terminal=false
Categories=GTK;Application;AudioVideo;Audio;Video;Player;TV;
MimeType=application/ogg;application/x-ogg;application/sdp;application/smil;application/x-smil;application/streamingmedia;application/x-streamingmedia;application/vnd.rn-realmedia;application/vnd.rn-realmedia-vbr;audio/aac;audio/x-aac;audio/m4a;audio/x-m4a;audio/mp1;audio/x-mp1;audio/mp2;audio/x-mp2;audio/mp3;audio/x-mp3;audio/mpeg;audio/x-mpeg;audio/mpegurl;audio/x-mpegurl;audio/mpg;audio/x-mpg;audio/rn-mpeg;audio/scpls;audio/x-scpls;audio/vnd.rn-realaudio;audio/wav;audio/x-pn-windows-pcm;audio/x-realaudio;audio/x-pn-realaudio;audio/x-ms-wma;audio/x-pls;audio/x-wav;video/mpeg;video/x-mpeg;video/x-mpeg2;video/quicktime;video/vnd.rn-realvideo;video/x-ms-afs;video/x-ms-asf;video/x-ms-wmv;video/x-ms-wmx;video/x-ms-wvxvideo;video/x-msvideo;
X-AppInstall-Package=mplayer
X-AppInstall-Section=multiverse
X-AppInstall-Popcon=35
jc@jc-desktop:~$

---

### Post by Keith Hedger on 2007-01-16
try puting the script in ~/.gnome2/nautilus-scripts then you can use right click to run the script on selected files/folders
if you want to know what variables are set for your script try scipts>open scripts folder, form nautilus and click on "show more details"

---


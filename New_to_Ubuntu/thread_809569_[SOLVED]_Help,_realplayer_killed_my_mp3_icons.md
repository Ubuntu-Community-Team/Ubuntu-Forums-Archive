---
title: "[SOLVED] Help, realplayer killed my mp3 icons"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Stefanie on 2008-05-27
i'm using the noia warm icon theme on gnome (ubuntu 7.10). i installed realplayer to listen to radio streams, and now the default icon for mp3's has changed to a realplayer one. how can i get the noia icon back? i tried reinstalling the icon theme, but that didn't help...

i would also like to know how i change the AWN icons. i tried by right-clicking and selecting change icon, but that only changes the icon for the running instance of the program.

---

### Post by sayakb on 2008-05-27
Look into /usr/share/icons/iconname/size/mimetypes folder and replace the MP3 icon there if it might have changed.

---

### Post by Stefanie on 2008-05-27
thanks. realplayer really messed things up, but now it's ok.

---

### Post by sayakb on 2008-05-27
If your problem has been solved, please mark the thread as Solved.

---

### Post by dwasifar on 2008-05-30
> **Stefanie said:**
> i'm using the noia warm icon theme on gnome (ubuntu 7.10). i installed realplayer to listen to radio streams, and now the default icon for mp3's has changed to a realplayer one. how can i get the noia icon back? i tried reinstalling the icon theme, but that didn't help...

i would also like to know how i change the AWN icons. i tried by right-clicking and selecting change icon, but that only changes the icon for the running instance of the program.

I had the same problem with Realplayer's installation setting up all sorts of default icons without asking.  I looked at its logs and found 173 xdg-icon-resource commands forcing its icons into the desktop icon system.

Needless to say I was not amused.

Fortunately the log provided enough information to reverse the damage.  Here is how to do it.

1) Open your text editor (gedit will do fine).
2) Copy the text below and paste it into your editor:

```

#!/bin/sh
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-ram
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-rm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-au
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mp4
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-ra
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 text-realtext
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-avi
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-mov
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-rv
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-swf
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-x-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-vorbis+ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-x-theora+ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-m4a
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-m4a
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mp4
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-rn-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mpg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-mpg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mpegurl
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-mpegurl
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-scpls
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-scpls
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-windows-acm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-windows-pcm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 text-vnd.rn-realtext
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-vnd.rn-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-realaudio-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realaudio-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realmedia-vbr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realmedia-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realsystem-rmj
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realsystem-rmx
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 image-vnd.rn-realpix
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-vnd.rn-realvideo
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-vnd.rn-realvideo-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-aac
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-x-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-smil+xml
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-streamingmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-x-streamingmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-sdp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-basic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-au
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-3gpp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-3gpp-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-3gpp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-3gpp-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-amr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-amr-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-amr-wb
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr-wb
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-3gpp2
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-3gpp2
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-x-real-video
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-mpeg4-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-ram
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-rm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-au
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mp4
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-ra
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 text-realtext
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-avi
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-mov
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-rv
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-swf
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-x-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-vorbis+ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-x-theora+ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-m4a
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-m4a
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mp4
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-rn-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mpg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-mpg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mpegurl
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-mpegurl
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-scpls
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-scpls
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-windows-acm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-windows-pcm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 text-vnd.rn-realtext
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-vnd.rn-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-realaudio-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realaudio-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realmedia-vbr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realmedia-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realsystem-rmj
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realsystem-rmx
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 image-vnd.rn-realpix
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-vnd.rn-realvideo
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-vnd.rn-realvideo-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-aac
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-x-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-smil+xml
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-streamingmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-x-streamingmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-sdp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-basic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-au
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-3gpp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-3gpp-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-3gpp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-3gpp-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-amr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-amr-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-amr-wb
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr-wb
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-3gpp2
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-3gpp2
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-x-real-video
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-mpeg4-generic
xdg-icon-resource forceupdate

```

3) Save it as an .sh file.  (I named mine fixicons.sh.)
4) Set it executable (right-click, Properties, Permissions, and check Executable).
5) Double-click to run.

This should reverse all RealPlayer's icon mischief, but results are not guaranteed.  You may want to check the RealPlayer install log for yourself first.

As for changing icons in AWN: change the icon first in the application shortcut you dragged to the launchbar when you added it to AWN, and then re-add it.

---

### Post by Stefanie on 2008-05-31
thanks a lot for your useful script!

---

### Post by sarang on 2008-06-15
Thanks a lot!

---

### Post by subaruwrc01 on 2008-06-15
I find it's much easier to use VLC to listen to radio streams.

---

### Post by rofthorax on 2008-07-15
Found out that the copy buffer for clipboard is limited, best to just save this page out to a file and copy everything between the "pre" tags.. 

I was thinking about putting a script on my web page,  but I don't if anyone would use it..

You'd think there would be a feature in Ubuntu like this.. I mean, you've got it in web servers, look up "mime-types", all you need is a icon name to mime type correlation.. Or if you are really picky a icon name to "file" command correlation. Then some easy to use GUI centered around it. 

Having to change images for every resolution is a sign of bad coding practice..

---

### Post by badhat on 2008-09-18
Hello,

I had the same problem after installing RealPlayer11GOLD. Dwasifar's script did eliminate the symlinks and icon files in those mimetypes directories, and it appears to fix everything in Nautilus. Yet I still see the icons in Thunar. So far I do not see how to bring Thunar up to date; I would appreciate if anyone knows how and posts it.

BTW there is an uninstall script provided with Helix/RealPlayer. I read about it near the bottom of this page: [INDENT][https://player.helixcommunity.org/2008/help/playerfaq.html]("https://player.helixcommunity.org/2008/help/playerfaq.html")[/INDENT]
It says to do:
[INDENT]sudo -i
/opt/real/RealPlayer/postinst/postuninst.sh
rm -rf /opt/real/RealPlayer/
[/INDENT]

(That does not restore the icons in Thunar either.)

---

### Post by stoneybridge on 2009-01-27
just a post script but seems they knew about this "bug" nearly 5 years ago!!!

[https://helixcommunity.org/projects/player/forums/entry/604](https://helixcommunity.org/projects/player/forums/entry/604)

"In the real world, the spec could probably use a bit of tweaking."

err yeah just a bit..

---


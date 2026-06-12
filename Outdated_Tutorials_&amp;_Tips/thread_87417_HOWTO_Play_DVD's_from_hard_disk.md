---
title: "HOWTO: Play DVD's from hard disk"
date: 2005-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Humanoid on 2005-11-08
Someone has maybe noticed that MPlayer and Xine won't always play DVD's correctly from the hard drive.

Solution is Totem-Xine. Choose 'Open Location' from the programs and choose the path to the movie where the AUDIO_TS and VIDEO_TS are. Now your DVD should play correctly.

To play DVD-image, you should mount it with -o loop. :)

---

### Post by Dotrig on 2005-11-08
try to install VLC
sudo apt-get install vlc-*

---

### Post by RSX311 on 2005-11-08
[QUOTE=Humanoid]Someone has maybe noticed that MPlayer and Xine won't always play DVD's correctly from the hard drive.

Solution is Totem-Xine. Choose 'Open Location' from the programs and choose the path to the movie where the AUDIO_TS and VIDEO_TS are. Now your DVD should play correctly.

To play DVD-image, you should mount it with -o loop. :)[/QUOTE]

I tried that and I get an error msg "Totem could not play 'file:///home/rsx/Movies/Batman/VIDEO_TS.BUP'.  There is no plugin to handle this movie."  Any ideas?

I have libdvdcss2 installed already, I can play each individual .vob files but just can't watch them all as a movie.

---

### Post by Humanoid on 2005-11-09
[QUOTE=RSX311]I tried that and I get an error msg "Totem could not play 'file:///home/rsx/Movies/Batman/VIDEO_TS.BUP'.  There is no plugin to handle this movie."  Any ideas?

I have libdvdcss2 installed already, I can play each individual .vob files but just can't watch them all as a movie.[/QUOTE]

You have this directory /Batman. Is there AUDIO_TS and VIDEO_TS directories under it? Seems like it's trying to open just VIDEO_TS.BUP but I think it requires these two directories. Try it out.

(Normal DVD's haven't got .BUP and .VOB files in the root directory)

---

### Post by RSX311 on 2005-11-09
[QUOTE=Humanoid]You have this directory /Batman. Is there AUDIO_TS and VIDEO_TS directories under it? Seems like it's trying to open just VIDEO_TS.BUP but I think it requires these two directories. Try it out.

(Normal DVD's haven't got .BUP and .VOB files in the root directory)[/QUOTE]

oh I think you're right, all the files are just under /Batman, I'll move it under /Batman/VIDEO_TS

Thanks!

---


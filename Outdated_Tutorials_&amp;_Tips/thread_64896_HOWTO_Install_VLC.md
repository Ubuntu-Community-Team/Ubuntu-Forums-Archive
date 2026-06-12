---
title: "HOWTO: Install VLC"
date: 2005-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Goober on 2005-09-12
[VLC Website](http://www.videolan.org/vlc/)

This HOWTO is meant to show you how to Install VLC, which is my personal favourite Multimedia player.  MPlayer is all well and good, but I prefer VLC.

1 - Make sure that you have Repositories Added: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

2 - Open a Command Terminal.  Type "sudo apt-get install vlc"

3 - To use VLC, type "vlc" in a command line.  Or go to Applications -> Sound and Video -> VLC (It has the little Orange Cone symbol by it)

Ok, that's all, short and sweet.  Any questions, just ask.

---

### Post by juanej on 2005-09-12
[QUOTE=Goober][VLC Website](http://www.videolan.org/vlc/)

This HOWTO is meant to show you how to Install VLC, which is my personal favourite Multimedia player.  MPlayer is all well and good, but I prefer VLC.

1 - Make sure that you have Repositories Added: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

2 - Open a Command Terminal.  Type "sudo apt-get install vlc"

3 - To use VLC, type "vlc" in a command line.  Or go to Applications -> Sound and Video -> VLC (It has the little Orange Cone symbol by it)

Ok, that's all, short and sweet.  Any questions, just ask.[/QUOTE]
I just intalled it and when i try to watch a movie with subtitles everything seems fine but subtitles appear for some dialogs and dissapear for other. I already try with another avi and same problem.
BTW they are .srt subtitles

---

### Post by Nano on 2005-09-12
[QUOTE=juanej]I just intalled it and when i try to watch a movie with subtitles everything seems fine but subtitles appear for some dialogs and dissapear for other. I already try with another avi and same problem.
BTW they are .srt subtitles[/QUOTE]

Let me guess. The subtitles you're trying to see are not english subtitles and the dialogs that show up don't have any extended character (lika accents, ñ, ¡¿, etc.), right?

---

### Post by MBro on 2005-09-12
I'm having trouble getting VLC to play any audio, it works in every other app but not vlc.  It's weird.  Using nforce2

---

### Post by RastaMahata on 2005-09-12
[QUOTE=Nano]Let me guess. The subtitles you're trying to see are not english subtitles and the dialogs that show up don't have any extended character (lika accents, ñ, ¡¿, etc.), right?[/QUOTE]
 yeah. what's the solution.

---

### Post by kingsidy on 2005-09-13
maybe this is going to help. when i installed VLC, there was two versions: one of them was just vlc and the other one is called VLC for GTK. when i played dvds i noticed that there was no sound from the VLC. the VLC for GTK on the other hand had sound. 
so i would say in synaptics, search for vlc for GTK+ and install that one and see if there is a difference.

hope it helps

---

### Post by MBro on 2005-09-13
Wow, that worked, weird.  Thanks.

---

### Post by Goober on 2005-09-14
For the record, I know only how to install VLC, not how to troubleshoot it.  You shall have to ask one of the helpful people around here who actually know what they are doing for help using it.

---

### Post by bored2k on 2005-09-14
[QUOTE=MBro]I'm having trouble getting VLC to play any audio, it works in every other app but not vlc.  It's weird.  Using nforce2[/QUOTE]
 > sudo apt-get install vlc-esd
Go to VLC's preferences, select audio - advanced and point it to use ESound output. Save and restart.

---


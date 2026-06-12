---
title: "HOWTO: Set up Sound Juicer to rip from CD as VBR mp3s"
date: 2008-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Jakey_TheSnake on 2008-10-19
Seeing as there's a lot of topics flying around the forum, I'll make a howto based on my own research. This will tell you how to enable mp3 encoding (i.e. enabling you to rip CDs as .mp3 files), and then overcome the cursed CBR 128kbps that is imposed on you. 

If you open Sound Juicer (called Audio CD Extractor in *Accessories>Sound & Video{/i]) and select [i]Edit>Preferences* the output format box will have a few options, by default none of them MP3. If you hit edit profiles, however, you will see an mp3 option, yet if you select it, you find it cannot be used to encode your mp3s yet (by default). 

To enable mp3 encoding, you need to open a terminal and enter:

```
sudo apt-get install ubuntu-restricted-extras
```

Now you can select the mp3 option. 

However, all mp3's ripped will be CBR 128kbps. 

To change this, we need to go to *Edit>Preferences* again, select edit profiles again and edit the MP3 one. In the "_G_Streamer pipeline" box, replace what is in there with this:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 vbr-min-bitrate=160 vbr-max-bitrate=256 ! xingmux ! id3v2mux
```

You can change your max and min bit rates as you wish by changing the number on the end of the *"vbr-min-bitrate=160"* and *"vbr-max-bitrate=256"* commands (leave syntax as is), it is currently tailored to my liking. 

Hope this helps people struggling with ripping mp3's, 

- Jake

---

### Post by Zer0Nin3r on 2008-11-19
Some good resource links:

[http://wiki.hydrogenaudio.org/index.php?title=Lame#VBR_.28variable_bitrate.29_settings]("http://wiki.hydrogenaudio.org/index.php?title=Lame#VBR_.28variable_bitrate.29_settings")

[http://thebside.ca/?p=280]("http://thebside.ca/?p=280")

---

### Post by hesjnet on 2009-05-11
Thanks! This solved my problems.:popcorn:

---

### Post by Fittersman on 2010-04-19
Thanks, solved my problem as well.

---

### Post by samfuzz on 2010-06-25
just for info

gstreamer lame is now deprecated accordind to this bug :

[https://bugzilla.gnome.org/show_bug.cgi?id=494528](https://bugzilla.gnome.org/show_bug.cgi?id=494528)

if you want quality mp3 rip use instead 
gstreamer lamemp3enc :

[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483)

example :
**audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc quality=0 ! id3v2mux**


[http://wiki.hydrogenaudio.org/index.php?title=LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME)

---


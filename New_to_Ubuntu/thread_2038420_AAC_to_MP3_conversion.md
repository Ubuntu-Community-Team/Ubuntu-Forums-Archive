---
title: "AAC to MP3 conversion"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by JamButty on 2012-08-06
I have Soundconverter and gstreamer installed (all versions listed in Synaptic, including "ugly" set), but all  attempts to convert from AAC to MP3 get "cannot decode stream" errors. VLC can play the cuts without problem. The "comprehensive guide to media" on this site is over 4 years old, so I was leery of that. I found no other info. I am running Oneiric.
Anyone familiar with this?  thanks.

---

### Post by tartalo on 2012-08-06
Does this work? [http://askubuntu.com/questions/35457/converting-aac-to-mp3-via-command-line](http://askubuntu.com/questions/35457/converting-aac-to-mp3-via-command-line)

---

### Post by ron999 on 2012-08-06
> **JamButty said:**
> I have Soundconverter and gstreamer installed (all versions listed in Synaptic, including "ugly" set), but all  attempts to convert from AAC to MP3 get "cannot decode stream" errors. 
Hi
If soundconverter won't do the job, try with **WinFF** instead.

Install WinFF and the extra codecs with this command:-
```
sudo apt-get update && sudo apt-get -y install libavcodec-extra-53 winff
```

---

### Post by JamButty on 2012-08-12
thanx for replies - 
I have FFmppeg (the main point of the ref.  askubuntu article) installed, presumably as part of other packages. It does not appear to be used normally as a standalone program. Its own site describes it as " It is a key component in many multimedia projects". In any event I have not found any reference in how to use it.
As to WINFF - it is strictly a video format converter and will not address the AAC audio format.

---

### Post by JamButty on 2012-08-12
[GNAC]("http://gnac.sourceforge.net/download/")  promises to do this, but is strictly for GNOME, so I am unclear how to install this under Oneiric. In attempting I get the following:

> This PPA contains the latest debs of Gnac for Ubuntu. To install Gnac, you must first enable the PPA on your system:
1. Open Software Sources (System->Administration->Software Sources)
2. Navigate to the "Third Party Sources" tab.
3. Click "Add"
4. Enter the APT line below that corresponds to your Ubuntu version that starts with "deb".
5. Click "Add Source"
6. Click "Close"
7. It will prompt you to reload your software cache. Click "Reload".
8. Now install the package "gnac" from Synaptic, or using the command below:
sudo apt-get install gnac


---

### Post by JamButty on 2012-08-12
Ok, [this]("http://creators-guru.blogspot.com/2011/05/ubuntu-how-to-convert-fromto.html") seems to work so far. It employs ffmpeg.

---

### Post by ads52 on 2012-08-12
> **JamButty said:**
> I have FFmppeg (the main point of the ref.  askubuntu article) installed, presumably as part of other packages. It does not appear to be used normally as a standalone program. Its own site describes it as " It is a key component in many multimedia projects". In any event I have not found any reference in how to use it.

Many people use FFmpeg as a standalone program and I would enthusiastically urge you to having a look at its use. If you have it installed, as well as the *libavcodec-extra-53* package that Ron suggested, simply run FFmpeg against the file as follows:

```
ffmpeg -i my_file
```

where of course 'my_file' is the correct path and name of *your* own file. If you can do this I am sure myself or others in this thread can suggest a suitable commandline to convert to mp3.

---

### Post by ron999 on 2012-08-13
> **JamButty said:**
> 
As to WINFF - it is strictly a video format converter...
I don't think so. :P

---


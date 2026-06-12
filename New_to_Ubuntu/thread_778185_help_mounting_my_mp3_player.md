---
title: "help mounting my mp3 player"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Mattevt on 2008-05-01
I have a Sandisk Sansa View Mp3 Player (it's flash storage is that makes a difference). Right now, the only reason I use windows is when I need to sync my music with WMP.

I've seen a couple explanations on mounting it using mtp, or something like that, but I never really understood any of them. I was wondering if someone would take the time to explain to me, step by step, how to set up ubuntu so the player appears as an external storage device, when I plug it into the usb port. (I'm using hardy)

Thanks for any and all advice!

Matt

---

### Post by MicahCarrick on 2008-05-20
Here's some of what I've learned in Ubuntu 8.04 with my Sansa View...


**MSC Mode**
To mount the MP3 player in MSC (mass storage controller) mode, which will enable it to work like any other Flash USB player, slide the power switch into the "Hold" mode and then hold the left direction pad for about 5 seconds and then plug it in. Ubuntu will recognize and mount it like a flash USB drive at '/media/Sansa View'.

To get Rhythmbox to recognize it as an audio player in MSC mode, create a file in the root directory named '.is_audio_player' containing the following text:

```
audio_folders=MUSIC/
folder_depth=2
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg
```

Album art in MSC mode can be embedded in an id3v2.3 tag (you can do this using an application called easytag, however, make sure you change it from id3v2.4 to id3v2.3 in the application's settings).

Album art in MSC mode can also be dropped into the folder to which it belongs with the name 'folder.jpg' (300x300)

As far as I can tell, _playlists are not support on the Sansa View in MSC mode_. If somebody knows differently?


**MTP Mode**
To use the default MTP (Microsoft Transfer Protocol) mode, you need to download libmtp. It might be useful to download mtp-tools and easytag in case you have problems or want to fine-tune things.

```
sudo aptitude install libmp3 easytag mtp-tools
```

Then, you can use it with Rhythmbox by enabling the 'MTP Portable Devices' plugin. This is in 'Edit' > 'Plugins'.

The mtp-tools will give you command-line access to your device. This is a good way to make sure libmtp is working. Type 'mtp-detect' to get a bunch of info about your device. Type 'man mtp-connect' to see a list of all the commands you can use.

If you want to actually mount the device like a filesystem in MTP mode, you can use mtpfs. When I tried this, it was kind of buggy but worked. 

```
sudo aptitude install mtpfs
```

Mount your device:

```
mkdir /media/SansaView
sudo mtpfs -o allow_other /media/SansaView
```

Unmount your device:

```
sudo fusermount -u /media/SansaView
```

I have had trouble working with playlists and albums using MTP mode with Rhythmbox, Amarok, etc. Aside from that, I kind of what an interface to directly organize the Sansa View, without syncing it or including it with my computer's media (mainly because it allows my girlfriend to manager her playlists without effecting my stuff--she's not computer savy). 

Therefore I'm currently working on a GTK-based music organizer for MTP based devices; create and edit playlists, specify album art, etc. (testing it with my Sansa View) It is going well and should have some downloadable files within a couple weeks. I'll update when the project page is up.

---

### Post by Harkainos on 2008-05-24
Does this allow for 'Drag and Drop' music transfer procedures? I was having a little problem with it and wanted to make sure it worked that way.

---

### Post by MicahCarrick on 2008-05-25
I wrote more details about the Sansa View on Ubuntu on my blog: [_Sandisk Sansa View on Ubuntu Linux_]("http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html").

There was a problem with Libmtp where the playlist default extension was zpl and the Sansa View would only recognize .pla, which as been fixed in CVS. So once that's installed, playlist support will work with Amarok and those players.

The application I'm writing, [MOrganize]("http://sourceforge.net/projects/morganize/"), won't be finished for a bit longer but it's currently supporting drag and drop playlist editing as well as album art on my Sansa View. I should be getting some beta source code posted on SF within a week or so.

---

### Post by suitedaces on 2009-03-18
> **MicahCarrick said:**
> Here's some of what I've learned in Ubuntu 8.04 with my Sansa View...


**MSC Mode**
To mount the MP3 player in MSC (mass storage controller) mode, which will enable it to work like any other Flash USB player, slide the power switch into the "Hold" mode and then hold the left direction pad for about 5 seconds and then plug it in. Ubuntu will recognize and mount it like a flash USB drive at '/media/Sansa View'.

To get Rhythmbox to recognize it as an audio player in MSC mode, create a file in the root directory named '.is_audio_player' containing the following text:

```
audio_folders=MUSIC/
folder_depth=2
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg
```

Album art in MSC mode can be embedded in an id3v2.3 tag (you can do this using an application called easytag, however, make sure you change it from id3v2.4 to id3v2.3 in the application's settings).

Album art in MSC mode can also be dropped into the folder to which it belongs with the name 'folder.jpg' (300x300)

As far as I can tell, _playlists are not support on the Sansa View in MSC mode_. If somebody knows differently?


**MTP Mode**
To use the default MTP (Microsoft Transfer Protocol) mode, you need to download libmtp. It might be useful to download mtp-tools and easytag in case you have problems or want to fine-tune things.

```
sudo aptitude install libmp3 easytag mtp-tools
```

Then, you can use it with Rhythmbox by enabling the 'MTP Portable Devices' plugin. This is in 'Edit' > 'Plugins'.

The mtp-tools will give you command-line access to your device. This is a good way to make sure libmtp is working. Type 'mtp-detect' to get a bunch of info about your device. Type 'man mtp-connect' to see a list of all the commands you can use.

If you want to actually mount the device like a filesystem in MTP mode, you can use mtpfs. When I tried this, it was kind of buggy but worked. 

```
sudo aptitude install mtpfs
```

Mount your device:

```
mkdir /media/SansaView
sudo mtpfs -o allow_other /media/SansaView
```

Unmount your device:

```
sudo fusermount -u /media/SansaView
```

I have had trouble working with playlists and albums using MTP mode with Rhythmbox, Amarok, etc. Aside from that, I kind of what an interface to directly organize the Sansa View, without syncing it or including it with my computer's media (mainly because it allows my girlfriend to manager her playlists without effecting my stuff--she's not computer savy). 

Therefore I'm currently working on a GTK-based music organizer for MTP based devices; create and edit playlists, specify album art, etc. (testing it with my Sansa View) It is going well and should have some downloadable files within a couple weeks. I'll update when the project page is up.

Just FAO anyone browsing, this worked for my samsung yp-k3. It's now drag and drop. Thanks micah

---


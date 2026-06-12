---
title: "mkdir not working correctly in batch script"
date: 2010-04-02
forum: Programming Talk
---

### Post by Jordanwb on 2010-04-02
I'm trying to write a batch script to automate recording with VLC (which I have done). I want VLC to put the mp3 into the Recordings folder which is on the desktop. If the folder doesn't exist, create it. However the folder creating part is misbehaving. Script:

```
echo off
set video_device=none
set audio_device=Logitech USB Headset

set video_encoder=dummy
set audio_encoder=mp3

set audio_bit_rate=128
set audio_channels=2

set destination_path=%HOMEPATH%\Desktop\Recordings\
set destination_file=%date:~10,4%-%date:~4,2%-%date:~7,2%.mp3

IF NOT EXIST "%destination_path%" mkdir %destination_path%

"C:\Program Files\VideoLAN\VLC\vlc.exe" --dshow-vdev="%video_device%" --dshow-adev="%audio_device%" --sout=#transcode{vcodec="%video_encoder%",acodec="%audio_encoder%",ab="%audio_bit_rate%",channels="%audio_channels%"}:standard{access="file",mux="raw",dst="%destination_path%%destination_file%"} dshow://
```

If the Recordings folder does not exist, it ends up creating a Documents folder on C:\, a "and", "settings" and "desktop" folder on my desktop, instead of creating a "Recordings" folder on my desktop.

---

### Post by MadCow108 on 2010-04-02
but its been ages since I last wrote a bat file but my guess is your missing the quotes for destination_path after the mkdir

---

### Post by blur xc on 2010-04-02
> **Jordanwb said:**
> I'm trying to write a batch script to automate recording with VLC (which I have done). I want VLC to put the mp3 into the Recordings folder which is on the desktop. If the folder doesn't exist, create it. However the folder creating part is misbehaving. Script:

```
echo off
set video_device=none
set audio_device=Logitech USB Headset

set video_encoder=dummy
set audio_encoder=mp3

set audio_bit_rate=128
set audio_channels=2

set destination_path=%HOMEPATH%\Desktop\Recordings\
set destination_file=%date:~10,4%-%date:~4,2%-%date:~7,2%.mp3

IF NOT EXIST "%destination_path%" mkdir %destination_path%

"C:\Program Files\VideoLAN\VLC\vlc.exe" --dshow-vdev="%video_device%" --dshow-adev="%audio_device%" --sout=#transcode{vcodec="%video_encoder%",acodec="%audio_encoder%",ab="%audio_bit_rate%",channels="%audio_channels%"}:standard{access="file",mux="raw",dst="%destination_path%%destination_file%"} dshow://
```If the Recordings folder does not exist, it ends up creating a Documents folder on C:\, a "and", "settings" and "desktop" folder on my desktop, instead of creating a "Recordings" folder on my desktop.

You are writing a Windows batch file?  Crazy- it's been almost 20yrs since I wrote one of those (and I'm not that old!!)...

I could help if it was a bash script...  sorry.

BM

---

### Post by Jordanwb on 2010-04-02
> **MadCow108 said:**
> but its been ages since I last wrote a bat file but my guess is your missing the quotes for destination_path after the mkdir

That was it.

---


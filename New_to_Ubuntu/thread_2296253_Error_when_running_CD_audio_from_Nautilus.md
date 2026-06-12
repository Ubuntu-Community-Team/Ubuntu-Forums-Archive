---
title: "Error when running CD audio from Nautilus"
date: 2015-09-24
forum: New to Ubuntu
---

### Post by luca40 on 2015-09-24
Hello everybody!

I'm new to this forum and to Ubuntu so I don't know if this error was already reported.
When I put a CD audio in my laptop it doesn't start automatically so I try to read it from the file manager.
Now, Nautilus can see that there is a CD but when I try to read it a pop-up appears which tells this error message:

> Impossibile accedere a «Disco audio» (in Italian this means "impossible to access the CD audio")
> Message did not receive a reply (timeout by message bus)

In spite of this I can read it with VLC without issues.

Does anyone know how to fix it?
Thank you!

---

### Post by ajgreeny on 2015-09-24
Use the dash icon at the top of the launchbar and start typing "details" without the quotes.  In that utility you can set a number of different things including how the system deals with removable media, eg CDs, DVDs, etc.

---

### Post by luca40 on 2015-09-25
> **ajgreeny said:**
> Use the dash icon at the top of the launchbar and start typing "details" without the quotes.  In that utility you can set a number of different things including how the system deals with removable media, eg CDs, DVDs, etc.

I've already set the details of how the system should deal whit it but it doesn't seem to change anything!
When I put the CD in absolutely nothing happens...

---

### Post by mc4man on 2015-09-25
What does this return?
```
gsettings get org.gnome.desktop.media-handling automount
```

---

### Post by Dennis N on 2015-09-25
> When I put a CD audio in my laptop it doesn't start automatically so I try to read it from the file manager.
Now, Nautilus can see that there is a CD but when I try to read it a pop-up appears which tells this error message:

I'm not completely sure what the issue is. Is it that it doesn't start playing automatically, or (as the thread title says) is it that you can't read it with Nautilus? Since you wrote "I can read it with VLC", I gather that the CDs will play in your VLC player?

---

### Post by luca40 on 2015-09-25
> **mc4man said:**
> What does this return?
```
gsettings get org.gnome.desktop.media-handling automount
```

It returns "true"

> **Dennis N said:**
> I'm not completely sure what the issue is. Is  it that it doesn't start playing automatically, or (as the thread title  says) is it that you can't read it with Nautilus? Since you wrote "I can  read it with VLC", I gather that the CDs will play in your VLC  player?

Yes, the thread title isn't the best. Sorry about that!
The problem is that it doesn't start automatically AND it doesn't start opening it from Nautilus even if the file manager tells me that there is a CD audio!
If I open vlc and try to run the CD from it than it starts without any problem.

(sorry if I'm not explaining the issue in a good way but my english is very bad since I've not spoken it for a long time!)

---

### Post by Dennis N on 2015-09-25
This information on audio CDs from Audacity:

> "Audio CDs don't have files or a file system like data CDs and other computer storage media, but consist essentially of a stream of bits on the disc in a single spiral "track" with a TOC (Table of Contents) index."

source: Audacity help.

So Nautilus can't open the audio CD like it can a data CD if that is what you are expecting. Only your multimedia software can read it's contents. Players, rippers, and so on. 

I will look further into the audio cd autostart.

---

### Post by Dennis N on 2015-09-25
I checked my Ubuntu and the setting for what to do when an audio CD is inserted is in: **Settings > System > Details > Removable Media**

You can select an application to use with the CD or other actions - such as Do nothing, or Ask what to do. Mine was set for "Ask what to do", and one of the choices is Open Folder! When I used that, the table of contents of the disk is read and contents extracted and displayed as .wav files (Track 1.wav, Track 2.wav, etc) in nautilus - so it CAN (to my surprise) display them (without song titles, however). These .wav  files are not on the audio CD (it has no file system) but created in **~/.gvfs/cdda mount on sr0**

In terminal:

```
dmn@Roxanne:~/.gvfs/cdda mount on sr0$ ls
Track 10.wav  Track 13.wav  Track 2.wav  Track 5.wav  Track 8.wav
Track 11.wav  Track 14.wav  Track 3.wav  Track 6.wav  Track 9.wav
Track 12.wav  Track 1.wav   Track 4.wav  Track 7.wav

```
 
Interesting stuff. Don't know if this helps, but I learned something myself.

---

### Post by mc4man on 2015-09-25
It is possible you've set audio cd insertion action to always do nothing. If so then change it as mentioned to do what you'd like in System settings > Details > Removable media.
(- if you want vlc to autostart/autoplay audio cd's on insertion  I've never seen it work properly with vlc, while vlc will start & play the cd it won't retrieve cddb info. There is a way around that if that's the case & it bothers you.

---

### Post by luca40 on 2015-09-28
> **Dennis N said:**
> I checked my Ubuntu and the setting for what to do when an audio CD is inserted is in: **Settings > System > Details > Removable Media**

You can select an application to use with the CD or other actions - such as Do nothing, or Ask what to do. Mine was set for "Ask what to do", and one of the choices is Open Folder! When I used that, the table of contents of the disk is read and contents extracted and displayed as .wav files (Track 1.wav, Track 2.wav, etc) in nautilus - so it CAN (to my surprise) display them (without song titles, however). These .wav  files are not on the audio CD (it has no file system) but created in **~/.gvfs/cdda mount on sr0**

In terminal:

```
dmn@Roxanne:~/.gvfs/cdda mount on sr0$ ls
Track 10.wav  Track 13.wav  Track 2.wav  Track 5.wav  Track 8.wav
Track 11.wav  Track 14.wav  Track 3.wav  Track 6.wav  Track 9.wav
Track 12.wav  Track 1.wav   Track 4.wav  Track 7.wav

```
 
Interesting stuff. Don't know if this helps, but I learned something myself.

About that direct Ubuntu shows me a issue, saying that it crashes. So I think that the problem may be related with the direct itself!

---


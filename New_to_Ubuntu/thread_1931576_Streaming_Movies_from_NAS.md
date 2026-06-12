---
title: "Streaming Movies from NAS"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by mazingaz on 2012-02-25
i recently installed Lubuntu 11.10 onto dell mini9 and it is running great however when I try to stream movie from NAS the player just stops and won't play anything.

Do any of you have similar prob???

---

### Post by papibe on 2012-02-25
Are you really streaming or reading the files from a share?

If you are streaming, what kind of service/protocol are you using?

What kind of files are you trying to reproduce, are they HD?

Regards.

---

### Post by mazingaz on 2012-02-25
I have LG NAS server with all the media file stored.  I am only trying to read the file from the NAS server witth lubuntu installed machine.
The Lubuntu sees the folder and see the files stored, but when I try to play it using the gnome player it just stops.

---

### Post by Porcini M. on 2012-02-26
It might just be because the video is too processor-heavy for your computer to handle. Try loading a smaller file from the NAS, like an image file. If that works, then you may need a computer with a faster processor to watch movies.

---

### Post by mazingaz on 2012-02-26
> **Porcini M. said:**
> It might just be because the video is too processor-heavy for your computer to handle. Try loading a smaller file from the NAS, like an image file. If that works, then you may need a computer with a faster processor to watch movies.

not true. i had xp b4 the Lubuntu and was reading avi files fine.

---

### Post by papibe on 2012-02-26
A few thoughts:

In order to play a movie locally you need to:
[LIST]
[*]have the necessary codecs installed.
[*]have enough hardware to reproduce it.
[*]note that there are better player that the stock. I recommend VLC or SMplayer.
[*]for SD movies you don't need much hardware.
[*]for Full HD movies you need a video hardware acceleration, that is, a modern graphic card, and the proper drivers and libraries.
[/LIST]
To play a movie over the network you need to:
[LIST]
[*]Be sure it plays locally first.
[*]have enough bandwidth to reproduce it properly,
[*]that is not usally a problem if you have a wired connection to both the server/NAS and your machine.
[*]In case of a wireless connection things change. In my experience, it's very difficult to reproduce HD movies over wireless unless you have an outstanding signal level. It helps if you have a N wireless router, instead of a regular G router.
[/LIST]
Tell us how it goes.
Regards.

---

### Post by TomatoKetchup on 2012-05-01
Sorry to resurrect an older thread but I had similar issues when using AFP to open files via my NAS.  Switching to SMB solves the problem for me.  I'm not exactly sure why Nautilus chooses AFP over SMB.  Just a thought, if you're still having issues.

---

### Post by jmore9 on 2012-05-01
Try VLC thats what i use for almost everything.

---

### Post by LuigiAntoniol on 2012-05-01
I get a similar error with VLC, but GNOME player has no problems reading media files from a shared drive.

My setup is a laptop running Lubuntu 12.04 64 bit and the shared folder is on a PC running Ubuntu 10.04 64 bit.

The error with VLC is that it cannot "verify" the shared drive, throws up an error about the path, even though I open it using the VLC "open file" menu.  Same error occurs when I right click on the file and say "open with VLC".

Local files are no problem with VLC, though.

And I have all the latest and greatest codecs installed from the Ubuntu repos as well as the Medibuntu repos.

---

### Post by marinara on 2012-05-02
try mounting the share, then retry mplayer on the mounted system

---


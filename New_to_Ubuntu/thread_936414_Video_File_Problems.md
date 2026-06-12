---
title: "Video File Problems"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Noobuntu2008 on 2008-10-02
Hello, short time reader, first time poster. 
As my name suggests, I am new to Ubuntu and am having a few difficulties. I am running Gutsy Gibbon, but am having some trouble opening video files. Whenever I open .mp4 or .avi files (I have only tested these two) with either VLC or the default Movie Player, the files and programs crash upon opening. If you can either give me a solution to my problem or link to a page with a solution, I would be very grateful.

---

### Post by Bachstelze on 2008-10-02
VLC is evil. mplayer is the solution ;)

```
sudo apt-get install mplayer
```

---

### Post by shifty_powers on 2008-10-02
erm, why are you using gibbon?

anyways, try

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by shifty_powers on 2008-10-02
> **HymnToLife said:**
> VLC is evil. mplayer is the solution ;)

```
sudo apt-get install mplayer
```

heh, funny, exactly how i feel about mplayer :P

---

### Post by bobbob1016 on 2008-10-02
It sounds like the videos are corrupted or something, VLC should be able to play them.  Mplayer too, but before taking advice from someone saying "just install something else" try Applications->Accessories->Terminal, navigate to the folder with the videos.  For instance, if the videos are on your desktop, do "cd Desktop" without quotes, and you need a capital D, then type "vlc name-of-the-file-you-want-to-play.mp4" without quotes.  Copy the output here.

---

### Post by tjwoosta on 2008-10-02
i agree mplayer is awesome  (especially with the GNOME MPlayer frontend)


it wouldnt hurt to install the w32codecs

first add the medibuntu repository (this link shows you how)
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

after adding the repository do

```
sudo apt-get update
```

then 

```
sudo apt-get install w32codecs
```
(if you are using 64bit ubuntu you would want to use w64codecs instead)

---

### Post by bobbob1016 on 2008-10-02
> **shifty_powers said:**
> heh, funny, exactly how i feel about mplayer :P

They both have their good qualities, vlc is meant for a gui, so I find it better when I want everything all in one window.  Mplayer is good for my mythbox, and I really like mencoder.

---

### Post by shifty_powers on 2008-10-02
well, i use kubuntu 8.10 these days, so i'm used to kaffiene/amarok/vlc...

---

### Post by eternalnewbee on 2008-10-02
Hi there.
Quick question: why is vlc evil?

---

### Post by Helios1276 on 2008-10-02
> **eternalnewbee said:**
> Hi there.
Quick question: why is vlc evil?

It is evil because it snuck into his house one night and in a MATTER OF seconds stole his PERSONAL files ,leaving him no CHOICE but to brand it evil.

---

### Post by Noobuntu2008 on 2008-10-04
> **bobbob1016 said:**
> It sounds like the videos are corrupted or something, VLC should be able to play them.  Mplayer too, but before taking advice from someone saying "just install something else" try Applications->Accessories->Terminal, navigate to the folder with the videos.  For instance, if the videos are on your desktop, do "cd Desktop" without quotes, and you need a capital D, then type "vlc name-of-the-file-you-want-to-play.mp4" without quotes.  Copy the output here.

Thank You everyone. I know some of you think VLC is evil, but I actually really like it. Either way, bobbob1016, that was my original thought and I did what you suggested, here is the output:

VLC media player 0.8.6c Janus
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 81 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---


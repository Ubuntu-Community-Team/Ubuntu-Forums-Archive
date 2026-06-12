---
title: "VOB crash on media players"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Midgetprawn on 2008-07-24
I am setting up an old Dell Dimension 1Ghz 512 Mb Ram with edubuntu to run in my classroom. I have used VLC before to play videos on XP with this system but now it flashes up then off.
I have installed the medibuntu files and followed the links from that page but still VLC and totem and Mplayer start up and crash immediately.
Is it me?:confused:

---

### Post by Midgetprawn on 2008-07-24
Ok tried something new
sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

but these are coming back as up to date. Any more suggestions?

---

### Post by caljohnsmith on 2008-07-24
Try launching VLC from the terminal (just type "vlc" in the terminal) so you can see what errors it might output before crashing. That will hopefully give some clues.

---

### Post by Midgetprawn on 2008-07-25
Typed in Vlc and tried to open disc and got this 

-desktop:~$ vlc
VLC media player 0.8.6e Janus
[00000297] vcdx access error: fread (): Input/output error
[00000297] access_file access error: read failed (Input/output error)
[00000297] access_file access error: read failed (Input/output error)
[00000297] access_file access error: read failed (Input/output error)
[00000297] access_file access error: read failed (Input/output error)
[00000297] access_file access error: read failed (Input/output error)
[00000297] access_file access error: read failed (Input/output error)

........ repeated for a lot of lines

---

### Post by Midgetprawn on 2008-07-25
I advance at a snails pace but I advance.

Latest output after running vlc dvd:///dev/scd0
 


libdvdread: Elapsed time 0
[00000349] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 86 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


any use?

---

### Post by caljohnsmith on 2008-07-25
So is VLC loading up OK but just crashes/gives problems when you try to access a CD or DVD with video? If that is the case, try using VLC to play a video file on your HDD, and if it works OK, then you know you have a problem reading CDs/DVDs. And if that's the case, try copying/ripping the video from the CD/DVD to your HDD and make sure Ubuntu can do that, and that will tell you whether it is truly a VLC problem or a general problem accessing your CDs/DVDs.

---


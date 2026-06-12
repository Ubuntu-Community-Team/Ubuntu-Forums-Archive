---
title: "Trouble ripping and playing"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by andreygaganov0 on 2013-11-02
Hi, 

I'm trying to rip audio files from a CD onto a subdirectory of the Music directory. My Linux 12.04 LTS 32-bit came with Audacity, Brasero, Banshee, and Rhythmbox. (Yes, not one, four players. Go figure.) I tried playing the audio files with Audacity, Banshee, and Rhythmbox, but they all would freeze, so I would have to force-quit them. I was thinking about copy-and-paste, but I noticed that the icons of those files have a lock on them. So I tried this:

[EMAIL="andrey@owner-VPCSC1AFM:~/.gvfs"]andrey@owner-VPCSC1AFM:~/.gvfs[/EMAIL]/cdda mount on sr0$ sudo cp ./* ~/Music/Scott\ Walker/Tilt/
[sudo] password for andrey: 
cp: cannot stat `./Track 1.wav': Permission denied
cp: cannot stat `./Track 2.wav': Permission denied
cp: cannot stat `./Track 3.wav': Permission denied
cp: cannot stat `./Track 4.wav': Permission denied
cp: cannot stat `./Track 5.wav': Permission denied
cp: cannot stat `./Track 6.wav': Permission denied
cp: cannot stat `./Track 7.wav': Permission denied
cp: cannot stat `./Track 8.wav': Permission denied
cp: cannot stat `./Track 9.wav': Permission denied

... where `~/.gvfs/cdda mount on sr0` is actually the `Audio Disc` feature. I checked out the files' permissions:

[EMAIL="andrey@owner-VPCSC1AFM:~/.gvfs"]andrey@owner-VPCSC1AFM:~/.gvfs[/EMAIL]/cdda mount on sr0$ ls -l
total 588881
-r-------- 1 andrey owner 70223776 Dec 31  1969 Track 1.wav
-r-------- 1 andrey owner 63852208 Dec 31  1969 Track 2.wav
-r-------- 1 andrey owner 93532096 Dec 31  1969 Track 3.wav
-r-------- 1 andrey owner 64468432 Dec 31  1969 Track 4.wav
-r-------- 1 andrey owner 55667248 Dec 31  1969 Track 5.wav
-r-------- 1 andrey owner 81877936 Dec 31  1969 Track 6.wav
-r-------- 1 andrey owner 89611312 Dec 31  1969 Track 7.wav
-r-------- 1 andrey owner 55260352 Dec 31  1969 Track 8.wav
-r-------- 1 andrey owner 28518112 Dec 31  1969 Track 9.wav

... and tried to manually change their permissions, and came up with this:

[EMAIL="andrey@owner-VPCSC1AFM:~/.gvfs"]andrey@owner-VPCSC1AFM:~/.gvfs[/EMAIL]/cdda mount on sr0$ chmod 500 ./*
chmod: changing permissions of `./Track 1.wav': Operation not supported
chmod: changing permissions of `./Track 2.wav': Operation not supported
chmod: changing permissions of `./Track 3.wav': Operation not supported
chmod: changing permissions of `./Track 4.wav': Operation not supported
chmod: changing permissions of `./Track 5.wav': Operation not supported
chmod: changing permissions of `./Track 6.wav': Operation not supported
chmod: changing permissions of `./Track 7.wav': Operation not supported
chmod: changing permissions of `./Track 8.wav': Operation not supported
chmod: changing permissions of `./Track 9.wav': Operation not supported

Is it not allowing me to change permissions because I did not do this as a super-user? So, I tried this:

[EMAIL="andrey@owner-VPCSC1AFM:~/.gvfs"]andrey@owner-VPCSC1AFM:~/.gvfs[/EMAIL]/cdda mount on sr0$ sudo chmod 500 ./*
[sudo] password for andrey: 
chmod: cannot access `./Track 1.wav': Permission denied
chmod: cannot access `./Track 2.wav': Permission denied
chmod: cannot access `./Track 3.wav': Permission denied
chmod: cannot access `./Track 4.wav': Permission denied
chmod: cannot access `./Track 5.wav': Permission denied
chmod: cannot access `./Track 6.wav': Permission denied
chmod: cannot access `./Track 7.wav': Permission denied
chmod: cannot access `./Track 8.wav': Permission denied
chmod: cannot access `./Track 9.wav': Permission denied

=============================================================

So, as you can see, not only do I have trouble playing and ripping CD audio files, but I also have trouble changing their permissions. Any help to redeem this issue would be much appreciated ... before I stupidly install one more extra media player that might make playing the files happen, or an unnecessary ripping program.

 - Andrey.

---

### Post by Dennis N on 2013-11-02
Get a ripper application, like asunder or ripperx, to convert cd audio tracks to music files (mp3 or ogg) on your hard drive. Those are only two of many. Look for these, or search for rip or ripper to find others in the software center.

---

### Post by andreygaganov0 on 2013-11-02
^ There are so many. Is there a stable ripper or two you could recommend that is all-audio-formats- friendly?

---

### Post by Dennis N on 2013-11-02
Sorry for the delay. You really need to try a couple and see what you like. You can have more than one installed. Asunder seems the most popular in the Software center, and I have used it in the past. That would be one you can start with.

---

### Post by Dennis N on 2013-11-02
If you use Asunder, you also need to install the package **lame** or else it will not be able to make mp3 files, just ogg or flac.

---

### Post by andreygaganov0 on 2013-11-02
Thank you so much.

---

### Post by Rob Sayer on 2013-11-03
If you haven't done so already install ubuntu-restricted-extras.  Actually I like the KDE desktop so in my case it's kubuntu-restricted-extras just as an example.  It includes the LAME encoder and flashplugin-installer and a whole bunch of other useful codecs etc.

It's the first thing I install after synaptic.

---

### Post by SeijiSensei on 2013-11-03
The KDE desktop manages ripping for you.  If you insert a CD into the drive, you'll see a window pop up that depicts the CD in all available formats like WAV, Ogg, FLAC, and MP3 if installed, with folders that represent the individual songs and ones that represent the entire disc as a single file.  Ripping the CD comes down to dragging and dropping the files in the preferred folder to the target storage location.  No extra software required!

---


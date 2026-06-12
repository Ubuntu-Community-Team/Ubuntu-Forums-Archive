---
title: "Installing a game and sound problems."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Haioko on 2008-07-29
Hi guys. I've been wanting to install World Of Warcraft on my PC by using this tutorial.

[http://ubuntu-tutorials.com/2006/12/19/how-to-install-play-world-of-warcraft-ubuntu-510-6061-610/]("http://ubuntu-tutorials.com/2006/12/19/how-to-install-play-world-of-warcraft-ubuntu-510-6061-610/")

I was just wondering if you could tell me what the equivelant to Ubuntu's 'program files' folder is. And if I can create a folder in which to save the WoW data and run it on Wine. If you know a better way to do this then please share.

Also I'm having sound problems. I've downloaded the latest software to listen to MP3s and the files are playing. But there is no sound coming out of the speakers.

Cheers guys.

---

### Post by Haioko on 2008-07-29
Anyone?

---

### Post by bobnutfield on 2008-07-29
I don't use games normally, so I am not familiar with WoW, but the "equivalent" feature in Linux to Window's program files is /bin.  A "bin" file is a binary file, or program.  Many, if not most, of the program files used system wide by all users are located in /usr/bin, and many game binaries are in /usr/games.  Usually, when you install a game or program, the data files, or libraries are automatically installed in the correct location (normally /usr/lib/<name of program>) for the program to find them while you are running the program.  If you create your own library folder, the program has to know where to find them.

As far as your sound goes, are you getting any error messages?

Hope this helps

Bob

---

### Post by Haioko on 2008-07-29
Thanking for helping Bob.

I don't get an error message.

---

### Post by bobnutfield on 2008-07-29
OK, the first thing to try is go to System>Preferences>Sound, click one or all of the test buttons one at a time and listen for the sound result.  If you hear sound, then the problem is with the playback software.  Also, make sure the correct device is shown in the Default Mixer box.  Usually, it is ALSA, but if that does not work, try others that are listed.

And, as silly as it sounds, make sure the speakers are not muted.  This can happen on new installations.  I am assuming this is a new or fairly new installation and sound has not yet worked for you.

Bob

---

### Post by Haioko on 2008-07-29
Every time I click test i get this error message.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

---

### Post by bobnutfield on 2008-07-29
Open a terminal and type:

> aplay -l

This will list the sound device as recognized by Ubuntu.  I am sure you know what it is, but enter the command to see if Ubuntu does.

Then, open a terminal and type:

> asoundconf reset-default-card

Then, retest the card in sound preferneces.

Bob

---

### Post by Haioko on 2008-07-29
I actually have no clue what my sound device is. It's onboard.

I can't even download the .PDF manual file from the manufacturer's website

---

### Post by bobnutfield on 2008-07-29
That's OK.  There are a number of ways to determine what sound device you have.  Open a terminal and type:

> lspci

In the list that results will be your sound device.  But, as I mentioned above the aplay -l command will also list the default device if it is recognized by Ubuntu.  If you get the error message that no sound devices were found, then the wrong drivers are being used.  

Bob

---

### Post by Haioko on 2008-07-29
05:00.1 Audio device: ATI Technologies Inc Unknown device aa28

Unknown apparently =/

---

### Post by hyper_ch on 2008-07-29
Follow this guide here:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I used the "copy from windows to linux" approach.. works perfectly.

---


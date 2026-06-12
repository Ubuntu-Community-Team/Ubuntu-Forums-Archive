---
title: "[SOLVED] unable to add new source ( dvd css)"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by freeediver on 2008-08-18
Playing a commercial dvd is my goal.
I have read everything, at least for the past two hours.
I decided to install ( or try to ) medibuntu to have access to the 
files I needed libdvdcss (?)
I was trying to get the HH. listing added to my sources but could not.
I thought i followed the inst. opened 
software sources:
third party software:
selected add:
New box opened with an open Apt line box.
I tried to both type in the command and tried copy/paste.
In ea. case I never received a selection to add this command,
the ADD button on that box never activated. I'm now stuck.
I want to play some netflix commercial dvd movies.
Is there a simple step by step instruction to enable me to play
commercial dvd's with my laptop listed below?
Right now totem is my one and only dvd player.
And what is: vlc player?

? some entries ask me what type architecture I have i386 etc.
How do I find out? I tried the arch entry in the terminal and it came back blank? Stuck again. I have a Toshiba A105-s2031 celeron M
I followed the inst. to discover architecture to the letter,
is it the inst., me, or my comp, for some reason even these simple
tasks are tough?

---

### Post by meanburrito920 on 2008-08-18
have you tried installing from command line? open a new terminal and enter the following commands one line at a time:

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update

sudo apt-get install libdvdcss2

```

That should fix it up.

---

### Post by nicedude on 2008-08-18
You might also need libdvdnav4 & libdvdread3 if you don't have those installed. I use VLC player to play my few store bought DVD's

This command should install both of them for you
sudo apt-get install libdvdread3 libdvdnav4


Hope this helps get you going :-)

---

### Post by wolfen69 on 2008-08-18
> **meanburrito920 said:**
> have you tried installing from command line? open a new terminal and enter the following commands one line at a time:

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update

sudo apt-get install libdvdcss2

```

That should fix it up.

don't forget ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```after the first line.

---

### Post by lisati on 2008-08-18
What has worked for me without the need for adding extra software sources (I use 7.04, Feisty) is the following:
```

sudo aptitude install libdvdnav4
sudo aptitude install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh

```

---

### Post by freeediver on 2008-08-18
Thanks for the quick replies.
After some futzing I got Totem to work after reading a ubuntu inst. page.
I forget which one now I have read so many.
Still totem will play my dvd Except now I dont have any sound.

---

### Post by nicedude on 2008-08-18
I never have liked totem all the times I have tried it. I would recommend Mplayer &or VLC player as better video playback softwares before using totem.

Also if you have sound probs you can try "sudo alsamixer" which will bring up the alsamixer console and you can make sure your volumes are turned up

The other volume control applet that might be needed is opened with this command
gnome-sound-properties

So check those out and see if something in one of those 2 fixes your sound

---

### Post by freeediver on 2008-08-18
I now have vlc installed but totem is still not working properly.
At least I can see and hear dvd's now.
Thanks all for your help and advice, I will likely continue to futz with totem and try to make it work, The Challenge !

---


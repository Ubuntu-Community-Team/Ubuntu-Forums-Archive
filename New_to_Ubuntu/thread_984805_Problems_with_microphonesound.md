---
title: "Problems with microphone/sound"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by kgolyaev on 2008-11-17
I am relatively new to Linux, and I have a problem with the sound card. Namely, the sound itself work fine, but the microphone does not (it's a laptop with build-in mic).

A little bit of details seem to be in order. I have a Toshiba Satellite laptop, model U405D-S2848. My sound card (as given by lspci command) is: 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA). I do not have any problem with listening to the sound, but the microphone completely refuses to do anything for me. 

I tried to read about 20 different forum threads and webpages to find a solution, but I keep running into the same problem - the short solutions (like launching alsamixer and making sure the Capture tab has been maxed out) do not work, and longer solutions seem to be impossible to be applied. 

Many solutions ask me to go to the gnome-volume-control and play around with options. Problem is, all the screenshots I see do not resemble anything like the stuff my system shows me, and hence I cannot apply these longer solutions - when I am told to click the button that is not present on the program window, what should I do?

My bottom line is very simple - is there anyone who really knows how to fix mic problems AND is willing to explain this to a newbie like myself? Thanks a ton in advance!

---

### Post by nhasian on 2008-11-17
if you double click on the speaker icon next to the date in the top right corner, you will get the Volume Control.  Click on the Options Tab.  Try some different Input Sources.  I have 4 different ones on my laptop Mic, Front Mic, Line, and CD.

---

### Post by kgolyaev on 2008-11-17
> **nhasian said:**
> if you double click on the speaker icon next to the date in the top right corner, you will get the Volume Control.  Click on the Options Tab.

Thanks for answering to my call for help, but...

You see, that's exactly what I was saying in my initial post, in the part where I said I could not follow many of the instructions I found. When I launch the Volume Control, there is no Options tab there for me... Any ideas on why it is gone? Here is a screenshot of what I get.

---

### Post by nhasian on 2008-11-18
after a bit of research it looks like your not the only person having trouble with the Azalia sound card.  upgrading to the latest version of ALSA may help

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

grab the drivers, libraries, and utilities:

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.18.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.18.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.18.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.18.tar.bz2)

then go to [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and follow the the instructions under "Update to the Latest Version of ALSA"

---

### Post by kgolyaev on 2008-11-18
**nhasian**

Thanks for trying to help me. I followed all the instructions, but unfortunately I had mixed success. Everything installed quite smoothly, but it did not fix my problem - my microphone still does not work.

Moreover, when I launch the Sound Recorder (to test the mic) before this I used to have a menu which allowed me to select the device that would be used to capture the sound input, and now this menu disappeared (see screenshot).

Nothing seems to work in Skype as well - it offers many different options for sound input (can't make the screenshot - they are shown in the drop-down menu), with some of them Skype just refuses to call, and with the rest it does call, but the other side doesn't hear a word that I say :(

 Maybe I am missing something? But I followed the installation instructions word-for-word and they were quite successful...

---

### Post by kgolyaev on 2008-11-18
As I continue reading, it seems I have some kind of fundamental flaw in my system. 

When I launch alsamixer, and go to the Capture tab, there should be some capture flag beneath the volume bar, as said here: [http://man-wiki.net/index.php/1:alsamixer](http://man-wiki.net/index.php/1:alsamixer)

But I don't seem to have anything like this. Another screenshot shows this clearly. Why could that be the case???

---


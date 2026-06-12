---
title: "LiveDVD - Common problems on 12.04, 12.10, 13.04 and 13.10"
date: 2013-11-18
forum: New to Ubuntu
---

### Post by intealliance on 2013-11-18
Currently, I'm using Win 8 on my ASUS K55VD laptop. I decided to try Ubuntu via Live DVD.

I downloaded and tried Ubuntu 12.04 LTS (recommended by a friend) and one thing I've noticed right away is my laptops headphone-out jack is not working. But when headphone or external speaker is removed, laptop's internal speaker works.

I thought it might be a compatibility problem as 12.04 is a little old so I then tried downloading 13.10 and got the same problem. Laptop's internal speakers are working but as soon as a headphone or external speaker is inserted on the headphone-out jack, it won't work. As if no audio is coming out from the jack.

I then decided to try 12.10 and 13.04 and got the same problem.

Currently, on my Win 8, everything works. Internal speaker is working, headphone-out jack is working when a headphone is plugged in. But on Ubuntu, internal speakers are working but when I plugged in my headphone, no sound is heard from the headphone.

I've tried 12.04, 12.10, 13.04 and 13.10 and got the same problem as tested via Live DVD.

All of these was tested via Live DVD. I haven't tested installing any of these at the moment. I can't afford to install if the out jack won't work as I usually listens to music online and via headphones or via my altec lansing external speakers.

---

### Post by deadflowr on 2013-11-18
How many input/output listings are there in sound settings?
Click the sound icon in the top panel and go to the bottom of the dropdown and click sound settings.

---

### Post by intealliance on 2013-11-18
> **deadflowr said:**
> How many input/output listings are there in sound settings?
Click the sound icon in the top panel and go to the bottom of the dropdown and click sound settings.

I only got 1 input listing and 1 output listing. Speakers Built-in Audio on output and Internal Microphone Built-in Audio on input.

---

### Post by intealliance on 2013-11-21
I downloaded and tried the latest openSUSE 13.1 KDE Live and I still got the same problem. 
Only internal speaker works. Output jacks are not working. No audio is coming out from the output jack.  :(

---

### Post by jdeca57 on 2013-11-21
> **intealliance said:**
> I downloaded and tried the latest openSUSE 13.1 KDE Live and I still got the same problem. 
Only internal speaker works. Output jacks are not working. No audio is coming out from the output jack.  :(

Let's say it's a general Linux problem. It's not unusual that certain hardware doesn't work as well as with the drivers the manufacturer provides with Windows. Often, looking at hardware specs a (partial) solution can be found, but sometimes there is no answer. There exist processors not supported by Linux. Or printers that are classified as paperweight. It's annoying, but if you buy products you want to use with Linux you better check the Internet first.

---

### Post by xeonix on 2013-11-21
Can you try, Installing alsamixer and adjust the volumes once?

---

### Post by simbauad on 2013-11-21
What you could try is adding this line to the end of /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel model=MODEL
where MODEL corresponds to one of these entries: [http://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/tree/Documentation/sound/alsa/HD-Audio-Models.txt](http://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/tree/Documentation/sound/alsa/HD-Audio-Models.txt)
Sorry there are many entries ;) but what you could do is find out what your card is (probably ALC270) and then try those listings. That will considerably reduce your work. Restart after each attempt. Sorry :(.

---

### Post by intealliance on 2013-12-07
> **jdeca57 said:**
> Let's say it's a general Linux problem. It's not unusual that certain hardware doesn't work as well as with the drivers the manufacturer provides with Windows. Often, looking at hardware specs a (partial) solution can be found, but sometimes there is no answer. There exist processors not supported by Linux. Or printers that are classified as paperweight. It's annoying, but if you buy products you want to use with Linux you better check the Internet first.

When I bought my laptop, Linux is not on my mind. A friend of mine recommended me to try Linux, after I have already bought this laptop.

> **xeonix said:**
> Can you try, Installing alsamixer and adjust the volumes once?

I did this, increase all volumes to max, and stil no sound on external speakers.

> **simbauad said:**
> What you could try is adding this line to the end of /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel model=MODEL
where MODEL corresponds to one of these entries: [http://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/tree/Documentation/sound/alsa/HD-Audio-Models.txt](http://git.kernel.org/cgit/linux/kernel/git/stable/linux-stable.git/tree/Documentation/sound/alsa/HD-Audio-Models.txt)
Sorry there are many entries ;) but what you could do is find out what your card is (probably ALC270) and then try those listings. That will considerably reduce your work. Restart after each attempt. Sorry :(.

I'm testing via LiveDVD. Restarting it will undo all changes.

---

### Post by squakie on 2013-12-07
*if* you have the ability to boot from USB, trying using unetbootin and creating an Ubuntu flash drive - and pay attention to the "persistence" file size, making it as large as possible while still leaving plenty of room for Ubuntu.  Perstistence means that the changes you make will be remembered across boots even on this removable media.  Then you can try the changes, reboots, etc., as needed.  Be sure to have your BIOS set to try to boot from USB as the first entry, or at least before the hard disk.

---

### Post by squakie on 2013-12-08
For alsamixer - there is usually a second page you have to use the keyboard to scroll right with.  See if there are any additional inputs and outputs there (some of mine where there).

---


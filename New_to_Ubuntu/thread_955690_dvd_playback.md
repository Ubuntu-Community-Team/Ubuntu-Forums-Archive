---
title: "dvd playback"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by johntravis on 2008-10-22
System/ preferance/ sound, I have sound in all except sound capture.I guess that is stopping the sound from coming thru when playing dvd movies (encrypted). Got a fix or workaround?

---

### Post by Nxion on 2008-10-22
Give this a try
[URL="http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support"]
http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support[/URL]

---

### Post by billgoldberg on 2008-10-22
What codecs did you install to enable encrypted dvd playback?

See codecs link if you don't have them.

--

Are you using PulseAudio?

Try switching to to ALSA (in sound) if it's not a codec issue.

---

### Post by johntravis on 2008-10-22
not sure if i have codecs installed, how do i check?

---

### Post by Nxion on 2008-10-22
> **Nxion said:**
> Give this a try
[URL="http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support"]
http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support[/URL]


Have you tried this yet?

---

### Post by LowSky on 2008-10-22
> **Nxion said:**
> Give this a try
[URL="http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support"]
http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support[/URL]

Just do this like Nxion said to look at. Open a termnial and copy and paste the following commands

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w32codecs

```

---

### Post by billgoldberg on 2008-10-22
> **LowSky said:**
> Just do this like Nxion said to look at. Open a termnial and copy and paste the following commands

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w32codecs

```

Or just one:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get -y install vlc libdvdcss2 ubuntu-restricted-extras w32codecs
```

---

### Post by johntravis on 2008-10-22
did what lowsky stated, copy and pasted the three lines of code into terminal but still no sound with playback of dvd movies

---

### Post by johntravis on 2008-10-22
I noticed the update manager icon so I tried to update and I got this 
 E: dpkd was interupted,you must manually run'dpkg--configure-a' to correct the problem
E:_ cache->()failed,please report.
How do I do this,tried to copy/paste in terminal but nothing

---


---
title: "No dvd playback with mythbuntu ??"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Peterfc on 2008-08-07
Hi All

I have setup a 80gb drive with Ubuntu 8.4 and Mythbuntu. with equal drive size for each. Under Ubuntu using Vcl Media player i can play a Dvd. If i exit Mythbuntu i can play a Dvd with Vcl media player. Under mythbuntu nothing happens when i try to play a Dvd also when i try to import a Dvd nothing happens. I had no trouble loading Cd's and playing. But dvd's nothing happens under Ubuntu and if i exit Mythbuntu dvd's play. The Dvd player was new and boxed when fitted to this test machine. 

Thanks for reading.

Dell dimension 2400 series 80gb h/drive 1gb ram

---

### Post by LowSky on 2008-08-07
you need the medibuntu repos to get DVD playback and extra codec support
in  terminal type these commands
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs
```

---


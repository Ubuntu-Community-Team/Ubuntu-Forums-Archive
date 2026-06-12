---
title: "[SOLVED] Vlc Help!!!"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by moose4204l on 2008-06-15
this is my error why i try to play a purchased season of 24. how do i get my laptop to play it?


VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: 24_SEASON3_DISC1
libdvdnav: DVD Serial Number: 30C3894E
libdvdnav: DVD Title (Alternative): 24_SEASON3_DISC1
libdvdnav: Unable to find map file '/home/moose/.dvdnav/24_SEASON3_DISC1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

---

### Post by hyper_ch on 2008-06-15
(1) add medibuntu repos

(2) install the libdvdcss2 package

---

### Post by durand on 2008-06-15
This should help: [http://www.debianadmin.com/playing-encrypted-dvds-in-ubuntu.html](http://www.debianadmin.com/playing-encrypted-dvds-in-ubuntu.html)

---

### Post by AndrewTheArt on 2008-06-15
[B]
[How To Have DVD Playback, Adobe Flash Plugin, MP3 In Ubuntu 8.04 Hardy Heron In A Single Step ]("http://www.dailygyan.com/2008/04/how-to-have-dvd-playback-adobe-flash.html")[/B]

Try this command - 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w32codecs
```[URL="http://www.dailygyan.com/2008/04/how-to-have-dvd-playback-adobe-flash.html"]
[/URL]

---


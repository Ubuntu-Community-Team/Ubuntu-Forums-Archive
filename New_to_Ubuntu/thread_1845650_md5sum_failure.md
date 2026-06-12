---
title: "md5sum failure"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Esot-Eric on 2011-09-17
Hey chaps, I have a live CD or live USB I suppose, when I downloaded it I checked the iso and also checked the md5sum.txt after I put it on the USB, both came out fine, I decided to just check it once more today and it seems something has gone awry as I now get a message "./casper/initrd.lz: FAILED", all the others pass. How could it have changed? I ran into a bit of a problem whilst using it earlier, could that be the source? I suppose this means I'll have to download the iso and all that again, most bothersome as doing so seems to result in a new drive being created under 'Computer' which says Ubuntu 11.04 ... 712 MB or something along those lines.

---

### Post by Lisiano on 2011-09-17
If you burned the disk/USB you might had a error during the process and the file got a bit corrupted, if the ISO passes just copy paste the file onto the USB. CD/DVD you'll have to reburn it. Also the new drive might probably be the ISO mounted using GVFS. Nautilus does that if you want to look inside the ISO.

---

### Post by Esot-Eric on 2011-09-17
You say it could have been an error in the burning but I checked the md5sum.txt after burning, good to hear I can just copy and paste the iso though, if that's the case I don't see why the ubuntu site would suggest otherwise.

---

### Post by Lisiano on 2011-09-17
Wait. IF the ISO itself is corruped, you should redownload it. IF just a file got corrupted AFTER burning then replace the file. You can try using Torrents, by default it will check the file and fill in the parts it considers wrong.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

PS. Usually torrents provide the file in it's fullest 99.9% times, whenever it fails you can tell it to recheck the file and it will redownload just that 1 part that is corrupted. I suggest uTorrent for Windows, Deluge for Linux.

---

### Post by Esot-Eric on 2011-09-17
Well excellent, that ought to save me a bit of time, still a bit concerned about how it could have got corrupted though, what does a failure in md5sum usually reflect? A poor download/burn or something malicious?

---

### Post by Lisiano on 2011-09-17
Usually a error during a download if the ISO fails, if the md5sum inside the iso fails after burning then the burning had a error. Most of the times these kind of fails mean errors during transmission of data between the server and you or you and your DVD/CD drive/USB port.
If someone really wanted to be malicious and give you a malicious ISO, I doubt the md5sum would fail, since it would be another md5sum generated for that specific ISO. And it's not that hard to manipulate a page to display another CRC. Btw don't be paranoid now. As long as you are downloading at home, your safe.... Well if you don't live in China or have the Russian Federal secrecy agency on your tail.

EDIT: Also the reason why I would recommend Torrents. You can't fake a few hundred people seeding a file and a few hundred more downloading.

---


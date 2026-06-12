---
title: "[SOLVED] How do I convert an .avi file to iPod format?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Neureo on 2008-08-15
I ripped a DVD using AcidRip onto my hard drive. It's in .avi format. What utility can I use to convert it into an iPod-playable format?

---

### Post by LowSky on 2008-08-15
you can rip DVD to Mpeg using acidripper, which the ipod can read. to convert you can use DeVeDe... it in add/remove or synaptic

---

### Post by LeetSpeak on 2008-08-15
or u can go to vixy.net

---

### Post by Martje_001 on 2008-08-15
Simple :)
```
ffmpeg -i filename.avi filename.mov
```

---

### Post by billgoldberg on 2008-08-15
Do yourself a favor and install winff.

If you have ffmpeg installed, remove it first.

```
sudo apt-get autoremove winff --purge 
```

Then add the medibuntu repository by using this command.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

After doing that install [this]("http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=54") package.

Choose the debian/ubuntu installer and double click it to install winff.

---

### Post by FakeOutdoorsman on 2008-08-15
The Ubuntu Wiki has a good [iPod Video Encoding]("https://help.ubuntu.com/community/iPodVideoEncoding") section.

---

### Post by stchman on 2008-08-15
> **Neureo said:**
> I ripped a DVD using AcidRip onto my hard drive. It's in .avi format. What utility can I use to convert it into an iPod-playable format?

The package K9Copy can rip DVDs into MPEG-4 which I believe the iPod can read.  I use K9Copy for all my DVD ripping needs.

---

### Post by Neureo on 2008-08-15
> **FakeOutdoorsman said:**
> The Ubuntu Wiki has a good [iPod Video Encoding]("https://help.ubuntu.com/community/iPodVideoEncoding") section.

Great resource -- thanks! I ended up using the ipodvidenc script. It did its job perfectly and now I have Pirates of the Caribbean successfully loaded onto my iPod. ;)

---


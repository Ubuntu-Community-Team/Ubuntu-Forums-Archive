---
title: "Youtube no sound (i've tried to follow different guides)"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Mobjerkn on 2008-10-08
Hi,
I've searched this forum and found several guides on how to enable sound and video with flashplayer in Firefox. The Video part was really easy but sound I can't manage. So I'm testing on youtube and video runs smooth but sound is none existing.
I've search the forum and also googled it but every guide I've followed seems to not work for me. I'm running the 8.10 Beta ubuntu but I belive that this shouldn't be the root cause. 

All help will be appreciated.
Regards

---

### Post by drowner on 2008-10-08
what version of flash are you using?

I had to install  a package called libflashsupport. Have you tried this?

---

### Post by elmer_42 on 2008-10-08
I know this isn't the greatest solution, but as a last-ditch effort you can use [the]("http://taufanlubis.wordpress.com/2007/10/25/download-videos-from-youtube-using-pytube-in-ubuntu/") [widely]("http://linuxowns.wordpress.com/2008/05/07/pytube-media-converter/") [acclaimed]("http://www.ubuntugeek.com/pytube-best-youtubegoogle-manager-downloader-and-video-converter-for-ubuntu-linux.html") PyTube.

---

### Post by Mobjerkn on 2008-10-08
> **drowner said:**
> what version of flash are you using?

I had to install  a package called libflashsupport. Have you tried this?
I'm using version 9, Ive downloaded version 10 but do I need to uninstall version 9 before installing version 10?
Regards

---

### Post by skompier on 2008-10-08
I had the same problem with 8.10 beta and after adding the Mediabuntu repository, all is working fine.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by crispy_420 on 2008-10-09
I had a similar problem in the past that may or may not be like yours.

Do have a motherboard based sound solution and a pci sound card?

---

### Post by eternalnewbee on 2008-10-09
Try this. It solved my problem right away:

Code:

sudo apt-get install libflashsupport

---

### Post by eternalnewbee on 2008-10-09
Sorry. Just noticed that this had already been suggested...

---

### Post by Mobjerkn on 2008-10-09
sudo apt-get install libflashsupport does not work.
i've got a PCI card. Sound works ok on the system (Mp3's and stuff) but not when using flash player.
Any other ideas?

---

### Post by Mobjerkn on 2008-10-09
Completely stuck here anyone have any idea on what I've done wrong?
Regards
Moo

---

### Post by TomWarrior-D on 2008-10-15
this happens to me when i play a music file the sound goes from youtube or other video sites and then i cant play music or vice virsa :(

---

### Post by Ryadt on 2008-10-15
Try ```
killall pulseaudio
```

---

### Post by kansasnoob on 2008-10-15
> **Mobjerkn said:**
> I'm using version 9, Ive downloaded version 10 but do I need to uninstall version 9 before installing version 10?
Regards

Yes you should remove Flash 9:

```
sudo apt-get remove --purge flashplugin-nonfree
```

Did you find the new Flash 10 Final Release. Philinux just posted links to it here on ABT. And it's available as .deb!

---


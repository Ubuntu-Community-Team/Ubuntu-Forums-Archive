---
title: "[SOLVED] Save files in ubuntu on windows partition?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Nebelhom on 2008-05-12
Hi,

now that I have ubuntu more or less set up in my dual boot I was wondering about a couple of administrative things.

the one that struck me today is, is it possible to save a file when in ubuntu onto my windows partition and whether the file then is still functional (both in ubuntu and windows)? 

I don't want to try cos I'm a big chicken and don't want to break anything now that it took me 2 weeks of wading through editors, BIOS and other unspeakable nightmares to get it working ;)

reason is that I need to use software that doesnt have a really good equivalent in linux (ChemDraw) and I prefer to write my reports in ubuntu and through this get accustomed to the desktop, i.e. I am mostly thinking of HomeOffice files.

Thanks for feedback

---

### Post by SunnyRabbiera on 2008-05-12
well yes its possible assuming you have what is needed.
Hardy comes with ntfs3g by default, so you should be able to write to your windows partition.
Normally if you use a common format like a txt doccument it should not have any issues in windows, ODT might be a bit more troublesome if you dont use openoffice in windows.

---

### Post by Caram on 2008-05-12
It's very possible. Just go to computer, find the NTFS partition, mount the volume, and then you'll be able to save things there.

---

### Post by rockerphil on 2008-05-12
absolutely, i've got 2400+ mp3s on an NTFS (Windows) partition that's on my 2nd hard drive that i had there before i switched to Fluxbuntu from Windows 2000, and i can use the NTFS partition just as easily as my ext2 and ext3 partitions, just make sure you've got ntfs3g installed as stated above and that you've got the partition mounted

---

### Post by Nebelhom on 2008-05-12
Ace! thanks guys. writing reports is just a bit more fun with the right soundtrack and saving to windows partition is a really cool bonus.

@SunnyRabiera: The odt thing isnt really an issue because you can save these files as general word docs. once I have the writing done I just transfer it to micro$oft office and all will be peachy.

---


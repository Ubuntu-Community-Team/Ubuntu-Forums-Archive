---
title: "Ubuntu's strange response to my phone that got me concerned"
date: 2017-12-05
forum: New to Ubuntu
---

### Post by noxvirtox on 2017-12-05
I use a simple Nokia Asha 503 cell phone which has its own OS, and recently I plugged it in for the first time since using Ubuntu (16.04 LTS). While I had plugged pendrives and SD cards before and Ubuntu had no problem reading the data on them, when I tried to read anything from the phone, all the folders had those tiny padlocks on them which apparently means no permission to open them, and I had problems reading the data that was on it. While a video file recorded with the phone played more or less fine, the music folder had no files in it and there was a message about an error reading an artist starting with L (and only this one, for some reason), and in the picture folder only the miniature files were fine, while the actual picture files either didn't open at all or they only displayed a small part on the top, then a pixelated horizontal stripe and the rest was grey, plus the icons didn't show thumbnails. I thought maybe the files were corrupted or something, but I could still  browse the pictures on the phone itself just fine, even zoom them, and  all the music plays normally. I had browsed this phone countless of times on Windows 7 and there were never any problems with it, which is why it got me so confused. Could it be that the phone is infected with some viruses or other nasty things? Or is this a normal thing when connecting to some phones on Ubuntu? I'm really worried. 

PS. Sorry I didn't include any exact error messages but I'd rather not plug this phone in again until I make sure everything is fine.

---

### Post by col48 on 2017-12-07
If you had no permission to open any folders, you would not have been able to open any of the music or video files in them.
Perhaps this OS does not set permissions in a way Linux expects?
Who does Ubuntu say owns the files?  Is it your user, or is it root?
Did you try accessing as root (ie using sudo)?
Could be that files formats are special - but if Windows can read them, Linux should.  Buffering could be an issue.... Proprietary formats could be an issue...
If you solve this one, I'd be interested.

Before making any moves, do a backup.

---

### Post by Holger_Gehrke on 2017-12-07
Since the Nokia Asha series phones had very little internal memory (128M according to Wikipedia) your data is probably on a micro SD card in the phone. Try to take the card out and put it into your PC (you'll probably need an adapter, micro SD to normal size). That might work better. And I wouldn't be too scared of malware. **If** there is some, it's either for the phone (some Java ME thing) or it's gotten in there when you connected the phone to a PC running windows. In either case the probability of the malware being able to run on Linux is very very low.

Holger

---

### Post by noxvirtox on 2017-12-11
I asked the same question on a different forum and it turned out someone also who also had this Nokia model had the exact same problem on Ubuntu, which means it's actually normal and not a virus (well, at least not behind this particular issue, anyway).

Anyway, thanks for all the tips, I'll try them tonight when I'll plug the phone again, but since I only need several photos out of it and I'm going to buy a new phone soon anyway, I think I'll just open them in Gimp, copy their content to new files and delete the originals just in case, I know that there's probably nothing wrong with the phone after all but it won't hurt to take extra precautions.

---


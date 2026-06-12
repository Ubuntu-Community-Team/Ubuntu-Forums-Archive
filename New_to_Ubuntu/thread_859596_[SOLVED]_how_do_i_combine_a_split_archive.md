---
title: "[SOLVED] how do i combine a split archive?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by T2manner on 2008-07-14
i just split my home folder into 3 different .7z files.
how do i combine them so i can extract it?

---

### Post by Hospadar on 2008-07-14
Most zipping programs will handle this automatically, if you use the 7zip command line tool it should handle it automatically.  Probably Document Manager, Ark (the KDE archive manager) or the windows 7-zip client will all handle this just fine.

---

### Post by bodhi.zazen on 2008-07-14
cat part1.7z part2.7z part3.7z >> full.7z

---

### Post by spupy on 2008-07-14
The gnome archiver - file-roller, should be able to handle 7z files. If he can't open them, install the package p7zip. Then open the first archive from the series and click extract. File-roller will automatically find the other parts (in the current folder) and extract the contents.

---

### Post by T2manner on 2008-07-15
okay, I've got p7zip installed
however, when i try to open the file: homebackup.7z.001, it says it can't open that type of file.  If i right click, I don't see extract.


okay i figured it out.

---

### Post by hemantbahirat on 2011-10-22
> **spupy said:**
> The gnome archiver - file-roller, should be able to handle 7z files. If he can't open them, install the package p7zip. Then open the first archive from the series and click extract. File-roller will automatically find the other parts (in the current folder) and extract the contents.


Thanks It works...........

---

### Post by Jubward on 2011-11-29
> **bodhi.zazen said:**
> cat part1.7z part2.7z part3.7z >> full.7z

This solved my problem with my new droid bionic that's been killing me forever! I loved how I could just mount and copy everything over to the sdcard and sdcard-ext on my phone and then it just works, but when I tried to copy over movies larger than 4gb I would get a "File too large" error. I found this strange since I had plenty of free space, so as a workaround I figured I'd just 7z my movies into 4gb volumes. Then that lead to another problem; no archive managing application could handle split volume 7z. I then tried to mount it again and use my computer to extract them but, again, I got the "File too large" error...

All that time I wasted trying to find some super complex solution and the one that works turns out to be 'cat videos.7z.001 videos.7z.002 videos.7z.003 videos.7z.004 >> videos.7z'
After that, ArchiDroid extracted it with no problem! Sorry for not being Ubuntu-related, but I guess it is *nix-y

---

### Post by sammiev on 2011-11-29
I like rar which can be loaded through Synapitic Package Manager.

rar e -y xxxxxxxxxx1.rar where (xxxxxxxxxx1.rar) is the name of the first file. All others will be processed automatically :)

---


---
title: "Iso file compression"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by avnd on 2011-09-25
Hello!

I have ended up downloading so many .iso files of various distros and I'm starting to run out of space on my 120 GB hard disk. 

I was wondering if I could compress these .iso files to save some space. The questions I have are

1. Reading about this on other pages, many people say that .iso files are already very compressed themselves and so it's not possible to compress them anymore. Is this true? If it is, there are no more questions.

2. If one can indeed compress .iso files, what format offers the best balance between compressed size and the time taken to compress and decompress (with more emphasis on the degree of compression although I don't want to be spending hours compressing a 700 MB file to say 550 MB). In that format, to what percentage of the original size (approximately) can one expect the files be compressed to.

3. I also want to know if compression and decompression can damage the files themselves. This is important because most of these images are those of Operating Systems.

Thank you.

---

### Post by Captain Smiley Pants on 2011-09-25
It seems like your best bet would be to make an archive (a bad example would be .zip, try something like p7) and compress the archive as much as possible.

You can't actually compress the .iso itself as it's an image of data, and even if you could you'd end up corrupting the data if it were to change around in that instance.

I'm not actually familiar with archive managers outside of File Roller and 7zip I use at work, so my method might not be that great after all or what you'd like to hear. At this point I'd advise just buying a backup drive, many today come in nice hard drive cases and connect via usb.

---

### Post by Blasphemist on 2011-09-25
No, you will not be able to noticeably compress an iso.

I expect that if you check, you have some iso's that are outdated and could be deleted. Ubuntu for example releases new every 6 months. But, maybe you want old versions for some reason.

Yes as stated above, you could move these iso's off to removable media, cd or usb for example. External usb hard drives are pretty cheap but I wouldn't leave a real cheap one connected all of the time. Even a 16 GB usb jump drive would hold copies of a bunch of distro's.

---

### Post by avnd on 2011-09-26
Thank you for your replies, Captain Smiley Pants and Blasphemist (you two have cool names, btw.. :) )

I figure I'll just leave the .iso files alone, then. In the meantime, I tried compressing some music files that I have with 7-zip and I'm a little disappointed with the results.

I'm working with Ubuntu 11.04 Gnome. I have this folder (size: 2.8 GB) containing music files that are mostly mp3 and a few midi files. They lie in various folder levels under the single parent folder. 

I right-clicked the parent folder under Nautilus and I then clicked on the compress option. I chose .7z as the compression method and clicked 'create'. After a while there was this archive in the parent folder's parent folder. This archive had a size of 2.6 GB.

I was a little disappointed with the degree of compression. I mean, the compressed archive is still more than 90% of the original folder's size. My questions are

1. Am I expecting too much? But I remember reading in places that 7-zip can compress to less than 60% of the original size.

2. Is 7-zip not the optimal file compression method for mp3 files?

3. Am I doing the thing in the wrong way? Is there some other way I should use to 7-zip the folders?

Thanks!

---

### Post by Paqman on 2011-09-26
You're doing it right, it's just that MP3 is already heavily compressed, so you won't be able to squeeze them much.

---

### Post by avnd on 2011-09-26
Thank you, Paqman.

It's a shame that pretty much everthing I have is already in a squeezed format. :D

---

### Post by Blasphemist on 2011-09-26
Actually its a good thing. Otherwise you'd be out of space already.

---


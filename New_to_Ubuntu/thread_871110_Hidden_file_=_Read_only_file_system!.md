---
title: "Hidden file = Read only file system?!?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Commander_Bob on 2008-07-26
I have a Sansa Fuze that works fine with Ubuntu except if there is a hidden file in the root of the device. When there is any hidden files, including trash, when it is mounted it becomes a read only file system. mtab says it is a rw file system but I can not change anything. I have tried sudo. The only way I can get it to work is go into Windows and delete the hidden file.
Any ideas why it is doing this?
Thanks,
Justin

---

### Post by mattismyname on 2008-07-26
By hidden file do you mean that the file begins with a '.' character?  (This is what denotes a hidden file in unix)

Or do you mean it is a hidden file from the Windows perspective?

thanks

---

### Post by Commander_Bob on 2008-07-27
I mean Linux hidden with the '.' character. I first had a problem when I made a file called ".is_audio_player" so it would be recognized as an audio player. That worked but then it became read only. I then removed the hidden file with a windows laptop and it worked again. Another time when I accidentally clicked keep the trash, it became read only. This also happens on my memory cards.

Thanks,
Justin

---

### Post by spicifer on 2008-08-02
I think I've had the same problem with Sansa Fuze. The solution for me has been [to remount the filesystem]("http://spicifer.blogspot.com/2008/07/sandisk-sansa-fuze-8gb-on-ubuntu-804.html") in write mode and remove the files.

---


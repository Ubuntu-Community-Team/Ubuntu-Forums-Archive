---
title: "ISO video file."
date: 2012-07-21
forum: New to Ubuntu
---

### Post by zozza on 2012-07-21
I have a ISO file which is a video.

I have unetbootin but am concerned that it will create a new operating system on the hard drive.

Obviously the video is not an operating system.

How can I get the ISO into a format that is viewable?

Thanks.

---

### Post by NikTh on 2012-07-21
Hi , 

Take a look at here --> [http://ubuntuforums.org/showthread.php?t=1626970](http://ubuntuforums.org/showthread.php?t=1626970) , if that helps

Thanks

---

### Post by exodus_ on 2012-07-21
Hey there,

Some media players are able to play the .iso file directly so long as you have the proper codec to play the content.  What media player do you use?

---

### Post by mcduck on 2012-07-21
ISO file is not a video file, but a disc image, made to be burned to an optical disc (probbaly a DVD since it's supposed to contain video).

Anyway, VLC is capable of playign the video directly from a disc image, so it's a nice option in case you don't want to burn the file to a disc.

---

### Post by wallaroo on 2012-07-21
Or you can just temporarily mount it ..

Depending on the flavour of ubuntu you have, if you right-click on the iso file you may see an 'Open With -> Archive Mounter', just select this and it will mount it and you can access the contents.

If you don't have this option, you can manually mount it as follows ...

mount
```
sudo mount -o loop /full_path_to_iso_file /media/iso
```(just need to create a mount point first e.g. /media/iso)

unmount
```
sudo umount /media/iso
```

---

### Post by zozza on 2012-07-22
Thanks guys - I was able to easily run it via VLC.

Never knew you could do that!  

And it provides the chapter selections, extras, etc.

---


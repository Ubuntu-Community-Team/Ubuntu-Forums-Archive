---
title: "Wallpaper appears sideways"
date: 2016-06-16
forum: New to Ubuntu
---

### Post by rdb3 on 2016-06-16
I set one of my personal pictures of a beach as a wallpaper.  But now the image on the wallpaper shows up sideways.  I right-clicked on the wallpaper but do not see any way to rotate the image 90 degrees to fix it.
Any suggestions?  Thanks.

---

### Post by rdb3 on 2016-06-16
Ok, the only way I was able to fix it was to go back to the photo in Pictures, click on Show image at its normal size, save itand then set as wallpaper.

---

### Post by grahammechanical on 2016-06-16
I was going to ask: What orientation did the image have when opened in Image Viewer? We can use Image Viewer to change the image orientation. In your case it seems that the system was adjusting the orientation to match the aspect ratio of the screen. Just a guess.

Regards

---

### Post by rdb3 on 2016-06-16
> **grahammechanical said:**
> I was going to ask: What orientation did the image have when opened in Image Viewer? We can use Image Viewer to change the image orientation. In your case it seems that the system was adjusting the orientation to match the aspect ratio of the screen. Just a guess.

Regards

When opened in Image Viewer the orientation was correct.  When set as a wallpaper it was sideways.  I tried to rotate it in Image Viewer to see if I could get it to appear right side up, but in all cases it still displayed sideways.

This is what the picture in Image Viewer is described as:

1350 X 2048 pixels
637.9 kB  41%

These pictures were taken with my Android cell phone.
I have tried to set another picture as a wallpaper, and it also appears sideways.  What I mentioned in my post #2 has no effect on correcting it.

---

### Post by Impavidus on 2016-06-16
So the image was taken with the camera rotated about 90 degrees from its normal orientation. I think that the camera software added a bit of information to the image file that any tool displaying the file should rotate it 90 degrees, but the desktop manager doesn't support that instruction, so it displays the file in its original orientation.

As far as I know, it's possible to rotate every image file format (including jpeg) 90 degrees losslessly, so you should be able to get rid of that unsupported rotate-instruction and have it display correctly everywhere. I'm not sure where you can find such a tool for lossless rotation. Maybe ImageMagick can do it.

---

### Post by rdb3 on 2016-06-16
I'll give  ImageMagick a try. It will be my first time using it.  Will post my results with it.  Thanks.

---

### Post by rdb3 on 2016-06-18
Ok, here's how I was able to do it.

I went here:

[http://www.imgonline.com.ua/delete-exif.php](http://www.imgonline.com.ua/delete-exif.php)

It removed all exif data from pic.

I still had to rotate it 90 degrees to straighten it out after removal of exif data.

Wallpapers picked up straight....... did not turn it sideways as exif data that forced a sideways orientation had been removed.

---


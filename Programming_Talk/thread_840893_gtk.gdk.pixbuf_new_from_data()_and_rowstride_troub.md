---
title: "gtk.gdk.pixbuf_new_from_data() and rowstride trouble"
date: 2008-06-25
forum: Programming Talk
---

### Post by | MM | on 2008-06-25
Hi,

I am playing around with a program that stores images as binary strings in a sqlite3 db.  I load the images using gtk.gdk.pixbuf_new_from_data().

This works flawlessly for 95% of all images loaded.  However, some render skewed as i calculate an incorrect rowstride.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=75344&stc=1&d=1214442536[/IMG]

Above is an example of a 50px by 50px RGB jpeg, which i have calculated a rowstride of 150 (50 wide x 3 deep (RGB)).

Now when i load the same image as a pixbuf using gtk.gdk.pixbuf_new_from_file(), pixbuf.get_rowstride() reports a rowstride of 152.  Now i cannot understand how this can be, as 152 divided by 50 does not produce a whole number.

gtk.gdk.pixbuf_new_from_data() will not allow a rowstride of 152 int his case as it reports that the amount of pixel data is less than required by the paramaters.

Anyone have any expierience with this issue?

---

### Post by geirha on 2008-06-26
It pads each row with 0s untill it fills complete words. And by word I mean 4 or 8 bytes (depending on your platform)

150 bytes % 4 bytes == 2
152 bytes % 4 bytes == 0

---

### Post by | MM | on 2008-06-26
ok,thanks for that info.  

So i have to pad the end of each row with the appropriate number of zeros, 2 in this case?
I have been using PIL's tostring() to generate the raw data to be stored.  So is it easier for me just to resize the image to dimensions that will fall on a 4 byte boundary (say, 48 x 48 ) than to try to add zeros to the end of each row.  Seems id have to write my own functional equivalent to tostring() but including the right amount of padding at the end of each row.  This seems like a pain and possibly slowwwww to do in python also.

---

### Post by | MM | on 2008-06-26
Ok, its pretty hacky but i'll just resize to the appropriate size prior to using tostring(), thanks for your advice!

---


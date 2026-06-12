---
title: "file manager that shows exif data in list view?"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by constellanation on 2012-09-28
I've been organizing a few years of misorganized photos and I realized that a very handy thing would be the ability to see some basic exif data from a file manager (preferably date taken) so that I wouldn't have to open thousands of photos in a program to sort them.  

I've been searching around and have only found two options, one is install a python script to nautilus. I tried it and it didn't work. What I found was over 2 years old, and obviously not tried on 12.04.

The other was gnome commander, but again I couldn't find anyway to change the views on list to see exif data.

Surely this is a desirable enough feature that it is out there, right?  Is this feature available? Possible?

---

### Post by JKyleOKC on 2012-09-28
You might search for a package called "fotoxx" which is a combination photo viewer, image repair/modification kit, and EXIF data lister. I'm using it on 10.04.4 with no problem at all, mostly as a viewer. However some of its image editing capability has proved more useful to me than has the GIMP package -- especially its ability to correct several kinds of architectural distortion. And the EXIF listing has two options. One gives only the most significant items while the other gives all of the data that's stored with the image. If the image has no EXIF data, the program will let you know.

---

### Post by constellanation on 2012-09-30
I will be giving this a shot tonight.  Thank you for your reply.  I'm not sure if it's exactly what I want, but the program looks interesting enough to try even if it doesn't do what I want. Hopefully it does however, thank you again!

---

### Post by Wim Sturkenboom on 2012-10-01
> **constellanation said:**
> I've been organizing a few years of misorganized photos and I realized that a very handy thing would be the ability to see some basic exif data from a file manager (preferably date taken) so that I wouldn't have to open thousands of photos in a program to sort them.  

Not the answer to the question but I use jhead to rename photos (in batch mode). Any jpeg is renamed to yyyymmdd_hhmmss_originalname.jpg. That way I don't need anything special when I want to know the date/time when the image was taken.

---

### Post by shreepads on 2012-10-01
f-spot very handily organises all imported photos by date when taken into a year - month - date folder hierarchy...

---

### Post by audiomick on 2012-10-01
I would have suggested f-spot too. You can tell it to search your computer and import everything it finds. It sees the exif data, and sorts the pictures accordingly.

---

### Post by constellanation on 2012-10-01
> **Wim Sturkenboom said:**
> Not the answer to the question but I use jhead to rename photos (in batch mode). Any jpeg is renamed to yyyymmdd_hhmmss_originalname.jpg. That way I don't need anything special when I want to know the date/time when the image was taken.


Going forward, I will most likely be using this, thank you. I can't really think of a reason not to have photos named in that convention, can you?

---

### Post by constellanation on 2012-10-01
> **audiomick said:**
> I would have suggested f-spot too. You can tell it to search your computer and import everything it finds. It sees the exif data, and sorts the pictures accordingly.

> **shreepads said:**
> f-spot very handily organises all imported photos by date when taken into a year - month - date folder hierarchy...

Maybe this is a bit to nitpicky (and a little research on my part would help) but does it physically sort them into their own folders, or is that atleast an option?  I, apparently, at some point thought it would be a good idea to throw hundreds if not thousands of photos into random folders.

---

### Post by shreepads on 2012-10-02
> **constellanation said:**
> Maybe this is a bit to nitpicky (and a little research on my part would help) but does it physically sort them into their own folders, or is that atleast an option?  I, apparently, at some point thought it would be a good idea to throw hundreds if not thousands of photos into random folders.

You point it to a source directory, then choose to copy into your Pictures folder (you can choose not to copy but then that won't meet your purpose)...

It will create a year-month-date sub-folder structure in your Pictures folder and copy the pictures from the source folder into that year-month-date structure..

---

### Post by constellanation on 2012-10-02
I think f-spot will work! Thank you all!

---

### Post by Wray on 2013-01-03
> **constellanation said:**
> I think f-spot will work! Thank you all!

Well, it does sort, but it is pretty crude.  I guess i just got spoiled by PhotoShop browser.
I have become too accustomed to thumbnails.  i would pay for something even close to equivalent.
Any suggestions?
Run PhotoShop for win in linux???  I wish

---


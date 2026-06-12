---
title: "Photo Printing in Ubuntu"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by Martin Houlton on 2011-09-26
Hi

I just had a nightmare trying to print some photos in Ubuntu. First I tried printing in The GIMP. The print dialogue was very hard to use, first I got a picture that went off the bottom left of the paper,with huge margins to top and right, This also had a pronounced yellow colour cast. Then I turned off colour correction (!) and got some photos with more natural colour (if pale), which filled the page, but the photos were too big for the page, and went off the bottom left. I was printing on 5" x 7" paper to a Canon Pixma ip5200 printer.

Eventually I tried printing with Shotwell, at first this looked better, more options were enabled in the print dialogue and I was able to select 5" x 7" paper and portrait/landscape, but when I went to print it insisted on putting the filename at the bottom and huge margins all round, so that the photo was a little postage stamp in the middle.

Finally I copied all the photos into /host, rebooted into Windows and printed the photos in Adobe Photoshop Elements. That wasn't perfect, APE makes me send every photo to print twice, but after a while I got some good photos. That shows that the JPEGs were good, so what on earth was Ubuntu doing?

Can anybody tell me how to get good photos in Ubuntu?

---

### Post by Martin Houlton on 2011-09-29
Oh well, I will just have to boot into Windows when I am doing photos.

---

### Post by Dale61 on 2011-09-29
I use a template created in LibreOffice, then insert the photo to the template.  As I print the same size all the time, I don't have any need to change any settings, so if 5x7 is your regular printing size, try creating a template with the dimensions of the photo, then add a border to the area surrounding the image.  What you should be left with is what looks to be a blank page, but with a bordered area (or two).  Nothing else.

You then open the template, add the image(s) to the bordered area(s), then print as normal. 

We do 90% of our printing whilst using Ubuntu, but when it comes to printing on a CD/DVD, we do that from Windows using CD/DVD specific printing software.

---

### Post by robert shearer on 2011-09-30
Look in the software centre for **gnome-photo-printer** or open a terminal and enter...

```
sudo apt-get install gnome-photo-printer
```

It says it is for multiple photos but is just as happy with one.

You can drag and drop images and adjust size then preview and print.

---

### Post by mikechant on 2011-09-30
I'd agree with Dale61 that printing from LibreOffice, or OpenOffice, (or probably other Linux Word Processors) seems to work well; I've managed it easily without using templates but I expect they're helpful.

---


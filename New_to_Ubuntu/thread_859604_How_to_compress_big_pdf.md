---
title: "How to compress big pdf?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by fredscripts on 2008-07-14
Hi!!!

I've got a huge pdf (809MB) from converting a .djvu file. I want to print it so I need to compress it in some way. I've googled and downloaded some software (PDFCompress and that stuff) but nothing seems to work with that kind of huge PDF.


Any suggestions? :(

Thanks in advance!

---

### Post by TSS on 2008-07-14
Try:
```
tar -czvf compressed.tar your.pdf
```
Slightly easier:
```
gunzip your.pdf
```

---

### Post by fredscripts on 2008-07-14
Thanks for answering!!!

That command will create a new pdf with some few MB that I will be able to open and File->Print...? Because I see a .tar structure, which don't think help me in this. I don't want to compress the file just for space stuff, only for printing (because printing a 809MB pdf goes sooooo slow).

---

### Post by TSS on 2008-07-14
> **fredscripts said:**
> Thanks for answering!!!

That command will create a new pdf with some few MB that I will be able to open and File->Print...? Because I see a .tar structure, which don't think help me in this. I don't want to compress the file just for space stuff, only for printing (because printing a 809MB pdf goes sooooo slow).

Oh, I see what you mean.  The two commands I gave you will make the size of your PDF smaller, but you wont be able to open or print it without uncompressing it first.  What you want is a want to decrease the quality/size of the original PDF so it prints faster?  I can't say I know how to do that, offhand.

---

### Post by fredscripts on 2008-07-14
Yep that's the point, as my PDF is a converted file from an scanned book (images), so every page seems to be a full image, that's why the 809MB impossible-to-print stuff. 

So if anyone know any way to reduce the quality of the pdf in order to print it I would be very grateful.

Thanks!!!!

---

### Post by TSS on 2008-07-14
> **fredscripts said:**
> Yep that's the point, as my PDF is a converted file from an scanned book (images), so every page seems to be a full image, that's why the 809MB impossible-to-print stuff. 

So if anyone know any way to reduce the quality of the pdf in order to print it I would be very grateful.

Thanks!!!!

I've never done this, so I'm just shooting in the dark here...

Try some of the suggestions in this thread: [http://forums.digitalpoint.com/showthread.php?t=129201](http://forums.digitalpoint.com/showthread.php?t=129201)

One of the posters said you could go File > Reduce File Size.  Is that true?

---

### Post by teitur on 2009-05-29
gscan2pdf

as suggested in this thread
[http://ubuntuforums.org/showthread.php?t=804891](http://ubuntuforums.org/showthread.php?t=804891)

I just tried it and it reduced the size of my 500 mb pdf. Just import your pdf-document and click save. You can combine reducing the resolution and image compression in order to reduce the size.

---

### Post by kaibob on 2009-05-30
After posting, I noticed that this is a very old thread that was resurrected by another forum member. I have requested that the moderator remove this post.

---


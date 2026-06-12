---
title: "[Method]Compair one image to another"
date: 2008-06-29
forum: Programming Talk
---

### Post by Pyro.699 on 2008-06-29
Hello,

My script involves acquiring a mass number of images, then stores them in several folder to then be manually sorted. I have used the programming language Java to do so. The script works perfectly at the moment but has a minor flaw, it checks for duplicate images using MD5Sums which requires the two images to be 100% alike. Meaning that its counting the different resolution picture as completely different images. I would like to be able to tell which images are the same through image appearance only, also instead of it being 100% alike, i would like to count images 95% or greater alike, in case of a minor pixel flaw. How would you guys achieve this, because MD5Sums are very iffy.

(I am dealing with numbers of over 10,000 images so it would be nice if the script took a short time to run)

Thanks
~Cody Woolaver

---

### Post by myrtle1908 on 2008-06-29
You're probably going to need to normalize the images.  Can you (on the fly) scale them down, reduce the colour depth to 256, do a PixelGrabber.grabPixels() and compare the rgb int's?

---

### Post by Pyro.699 on 2008-06-29
> **myrtle1908 said:**
> You're probably going to need to normalize the images.  Can you (on the fly) scale them down, reduce the colour depth to 256, do a PixelGrabber.grabPixels() and compare the rgb int's?
I dont think so because some of the images are coming from a website where high resolution and high quality images are being produced. There are JPG, PNG and GIF' would the ubuntu command *diff* be able to play a role?

To continue on what i would like, would be a method or even a class that you run and it would return a double, which could look like 94.32 which would represent 94.32%.

Thanks again
~Cody Woolaver

---

### Post by myrtle1908 on 2008-06-29
I'd say you will run into problems given different image formats.

Perhaps take a look at Java Advanced Imaging  [https://jai.dev.java.net/](https://jai.dev.java.net/) and their forum [http://forums.java.net/jive/forum.jspa?forumID=75](http://forums.java.net/jive/forum.jspa?forumID=75)

Good luck!

---

### Post by Ng Oon-Ee on 2008-06-30
Off the top of my head, from my Imaging classes in university:-

I'd assume if you're comparing two images to see if they're identical and one of them is of a different resolution, they're still the same image except the smaller one is down-sized. If the smaller one is just a crop of the larger image, then you're going to have to use very complicated algorithms.

Anyhow, if the assumption above holds, then I guess you could do a bicubic downsize of the larger image to the smaller image's resolution and do a SAD (sum of absolute differences) compare after normalizing and smoothing). You'd have to specify a threshold which indicates identical images though, because it would be quite impossible to get a SAD of 0.

Just my 0.02

---

### Post by Pyro.699 on 2008-06-30
Thankyou for that post but would something like compairing the pixles in one image to compairing the pixles in anoteher image work?

Like say we have 2 images, each 4x4 pixles.

[quote=Image1]
[[0,0,0],[255,255,255],[0,0,0]],
[[255,255,255],[0,0,0],[255,255,255]],
[[0,0,0],[255,255,255],[0,0,0]]
[/quote]
[quote=Image2]
[[0,0,0],[255,255,255],[0,0,0]],
[[255,255,255],[0,0,0],[255,255,255]],
[[0,0,0],[255,255,255],[0,0,0]]
[/quote]

The reteurn should be 100% because they are the exact same, but lets say we change Image2[1][1]=[255,255,255], then the pixels match at 8/9, which wold be 89% it could compair the rbg color of each element.

Thanks again
~Cody Woolaver

---

### Post by AnRa on 2008-06-30
You should try [findimagedupes](apt://findimagedupes) :)

---

### Post by Pyro.699 on 2008-06-30
> **Pyro.699 said:**
> Thankyou for that post but would something like compairing the pixles in one image to compairing the pixles in anoteher image work?

Like say we have 2 images, each 4x4 pixles.




The reteurn should be 100% because they are the exact same, but lets say we change Image2[1][1]=[255,255,255], then the pixels match at 8/9, which wold be 89% it could compair the rbg color of each element.

Thanks again
~Cody Woolaver
I would prefer to not have to use programs that are not included directly into the main script. It would eat up a ton of system resources to: Open Stream, run script, get data then close the stream. Good idea though, thanks

~Cody Woolaver

---

### Post by myrtle1908 on 2008-06-30
> **Pyro.699 said:**
> Thankyou for that post but would something like compairing the pixles in one image to compairing the pixles in anoteher image work?

Like say we have 2 images, each 4x4 pixles.




The reteurn should be 100% because they are the exact same, but lets say we change Image2[1][1]=[255,255,255], then the pixels match at 8/9, which wold be 89% it could compare the rbg color of each element.  

Thanks again
~Cody Woolaver

Yes, this is the way to do it (as I eluded to earlier).  Just scale your images down to a really small size say 16x16 or 32x32, reduce the colour depth to 16 or 256 colours and compare the pixels.  Obviously there are occasions where this will will fail but will work most of the time.  The higher the colour depth the more chance of success.

---

### Post by Pyro.699 on 2008-06-30
> **myrtle1908 said:**
> Yes, this is the way to do it (as I eluded to earlier).  Just scale your images down to a really small size say 16x16 or 32x32, reduce the colour depth to 16 or 256 colours and compare the pixels.  Obviously there are occasions where this will will fail but will work most of the time.  The higher the colour depth the more chance of success.
I think i will go with this method, could someone explain to me the package and methods i should use. Also, how would scaling the image down to 250x250 and a color depth of 256 work? Thank you all for your help.

~Cody Woolaver

---


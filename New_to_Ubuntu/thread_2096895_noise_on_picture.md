---
title: "noise on picture"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by hnf a on 2012-12-21
hi i have some picture problem both in libreoffice draw and default image viewer that the picture is so noisy but when i look into another image viewer the image become less noisy. and i realize when i print out the image from libreoffice draw it's give same result: have a lot of noise in the image then i print out the same image from windos the image is fine, is this problem fixed by downloading some certain code or anything else? i have ubuntu 12.04

---

### Post by Bartender on 2012-12-21
Hmm, weird, if, as you say, the printer outputs the same flawed images then it's not simply a video driver problem.

Need more input.  Are the images from your camera?  Cellphone?  Off the web?

What kind of images?  Are they .jpg?  .png?  

I've run into a similar situation, but only when dealing with RAW.  I set a DSLR to create RAW files.  In Windows I could use the software that came with the camera and the photos looked fine.  In Ubuntu they either didn't display at all, or looked horrible.

Unfortunately there's more than one kind of RAW file.  Canon, Olympus, Nikon, etc. made things more difficult by adopting their own proprietary RAW formats.  Canon creates files called .cr2 if I recall.  I think Olympus is .orf.  Etc. etc.  

Most people don't take photos in RAW.  .jpg is by far the most popular, and Ubuntu shouldn't have any problem with that.

Can you attach a low resolution image to a post so others can see what happens on their PC's?

---

### Post by Hylas de Niall on 2012-12-21
Seems to me that it isn't an issue with the image in itself, but more like the way apps are displaying/printing them in Ubu/Linux.

---

### Post by hnf a on 2012-12-21
@Bartender:the image is from both web and pocket camera and both are jpg image

---

### Post by sudodus on 2012-12-21
> **Hylas de Niall said:**
> Seems to me that it isn't an issue with the image in itself, but more like the way apps are displaying/printing them in Ubu/Linux.
 
I think so too. A noisy picture is filtered to give a smooth output by some viewing programs.

---

### Post by hnf a on 2012-12-22
this is the picture- the left is shotwell and the right is default image viewer

---

### Post by sudodus on 2012-12-22
> **hnf a said:**
> this is the picture- the left is shotwell and the right is default image viewer
[s]It is only 100x35 pixels and not easy to tell the noise from each pixel. Please upload a bigger picture somewhere![/s]

*Edit*: Sorry, with another browser it was saved with 312x109 pixels. Still hard to see, but much better now :-/

The left (square) picture looks filtered (smoothed). What is to be expected? What's the origin of this picture?

---

### Post by hnf a on 2012-12-22
[http://img824.imageshack.us/img824/4480/noise2.jpg]("http://img824.imageshack.us/img824/4480/noise2.jpg")

---

### Post by sudodus on 2012-12-22
I treated the area in a black frame with two filters in the gimp (with default settings)

- blur (simple blur, not gaussian blur)
- unsharp mask (or blur mask (maybe bad translation))

and as you can see, the right noisy side of the picture looks pretty much like the left one. I think you have picture files that are noisy, and some viewers and printer driver programs process the picture through filters before displaying or printing. Some viewers and printer drivers don't, so you see a difference.

---

### Post by hnf a on 2012-12-23
thanks for reply but i think that will work when the amount images is just a few but i have a lot of image,or can i at least have filter installed on my libreoffice?

---

### Post by sudodus on 2012-12-23
I think it is possible to filter massively if you like. Use can use batch filtering with ***imagemagick convert***. See

[[COLOR="Red"]http://www.imagemagick.org/script/command-line-options.php[/COLOR]]("http://www.imagemagick.org/script/command-line-options.php")

I have used convert, but mainly to change size and quality of pictures, but I could easily find some filtering options to reduce noise. But for certain applications, for example printing, noise or speckles are sometimes added to improve the quality. Anyway, think twice before deleting the original pictures.

-despeckle
-blur
-noise
-sharpen

You can test the following command on your test picture:
```
convert noise2.jpg -blur 3x1 -sharpen 3x1 noise2out.jpg
```
Such a command can be modified and run in a shell-script to convert many pictures every night if you wish.

---

### Post by hnf a on 2012-12-23
thanks for the solution i'll try that but is there any extension or something that automatically filter when you insert the image to libreoffice?

---

### Post by sudodus on 2012-12-23
I don't know. Maybe you can start a new thread with a good descriptive title and ask for help to find a (noise) filter for pictures in LibreOffice.

Probably there is someone at the Ubuntu Forums who knows about that.

---


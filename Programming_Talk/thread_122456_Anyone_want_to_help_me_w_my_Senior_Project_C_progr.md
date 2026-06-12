---
title: "Anyone want to help me w/ my Senior Project? C programming / barcodes / image process"
date: 2006-01-27
forum: Programming Talk
---

### Post by spaceballl on 2006-01-27
Hey all,

So I wonder if anyone out there has experience with this kinda stuff... Basically, my electrical engineering (i have a software systems depth) senior project is to make a program. The program takes a picture, scans the picture for the barcode, extracts the barcode, and reads the data. It is going to be used for medical stuff eventually. I'm supposed to use C to program this.

I have experience w/ C programming, but not with any specific libraries or anything like that. Just some OpenGL stuff, a lot of data structures, etc etc.

So here are my questions... 
how do I import a jpg image w/ C so that I can manipulate?
is there open source bar code scanning software out there? I've done some searching w/out too much luck.

I'd like this progrma to be cross platform. Any help I can get pointing me in the right direction would be AWESOME. Thanks!

-Kevin

---

### Post by briancurtin on 2006-01-27
did you get to choose your project, or was it given to you?

---

### Post by spaceballl on 2006-01-28
i had a bunch to choose from, but i wanted to pick a programming one instead of a circuit design / antenna / wireless project.

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=spaceballl]Hey all,

So I wonder if anyone out there has experience with this kinda stuff... Basically, my electrical engineering (i have a software systems depth) senior project is to make a program. The program takes a picture, scans the picture for the barcode, extracts the barcode, and reads the data. It is going to be used for medical stuff eventually. I'm supposed to use C to program this.

I have experience w/ C programming, but not with any specific libraries or anything like that. Just some OpenGL stuff, a lot of data structures, etc etc.

So here are my questions... 
how do I import a jpg image w/ C so that I can manipulate?
is there open source bar code scanning software out there? I've done some searching w/out too much luck.

I'd like this progrma to be cross platform. Any help I can get pointing me in the right direction would be AWESOME. Thanks!

-Kevin[/QUOTE]

Not sure of any specific libraries you can use.  From some brief web searching I did, it seems like the basic idea in some cases is to scan the barcode as an image, then figure out the widths of the black bars.  It is a little tricky, because a scanned barcode is not going to to have pure black and white pixels.  So the software has to perform some sort of filtering or averaging to compensate.

Does the whole app have to be written in C, or do you just need a C interface to the hardware?  Do you know what type of hardware you are going to use at this point?

---

### Post by jerome bettis on 2006-01-28
[quote=cwaldbieser]Not sure of any specific libraries you can use.  From some brief web searching I did, it seems like the basic idea in some cases is to scan the barcode as an image, then figure out the widths of the black bars.  It is a little tricky, because a scanned barcode is not going to to have pure black and white pixels.  So the software has to perform some sort of filtering or averaging to compensate.

Does the whole app have to be written in C, or do you just need a C interface to the hardware?  Do you know what type of hardware you are going to use at this point?[/quote]

barcodes have been around since about the 60's.  i'm sure a few hours googling for barcode software could get you some direction.

i wish i could give you some coding suggestions, but without knowing what type of information the hardware actually gives you, it's tough to say. does it really give you a jpeg image?  i would think just a matrix of 0's & 1's could tell the story and would be easier for the optical thing to pick up & encode.

---

### Post by spaceballl on 2006-01-28
Thanks for the replies, guys. So here's a bit more info.

As far as the filtering, yes that WILL be very tricky. One of my partners is a digital signal processing wiz so i'm hoping we can apply some of this to image manipulation.

As far as the image goes, the whole point of this is to be able to take pictures of patients w/ toe tags, specifically a 5 megapixel jpeg. Then the program findds the barcode and extracts the data. This is obviously going to be the difficult part of the program.

Thus, I'd really like to just get some basic code down that can input jpegs and read barcodes... Once I understand how those two pieces work, I can get dirty with the code and start figuring out how to filter a barcode out of an image. If you guys have any suggestions, i'm definitely open to them...

-Kevin

---

### Post by Viro on 2006-01-28
The only thing I can suggest is that you take a course on computer vision. The stuff you are trying to do is covered in this field of computer science. Get a few books out of the library on this subject, and you should be covered. :)

---

### Post by spaceballl on 2006-01-28
Hahaha I'd LOVE to take some various courses all related to this subject, but the point of the project is to give me something out of my league, and ten weeks to make it, doing the research as i go along....

---

### Post by gord on 2006-01-28
do your own bloody homework, sheesh :P ;)

---

### Post by spaceballl on 2006-01-28
My "homework" in the words of my mentor is to "try and find some software out there already for image manipulation and barcode scanning. No need to re-invent the wheel. Try programming forums. People are usually willing to help."

---

### Post by Viro on 2006-01-29
To be honest with you, such a requirement of barcode scanning is rather specialized. Do you seriously think this is the best place to ask for information about bar code scanning software? Most of us here are programmers, but it is highly unlikely that we have any knowledge of bar code scanning software. You'd be more likely to find the information you need from a Google search.

---

### Post by spaceballl on 2006-01-29
That's true. I was hoping that someone here would have knowledge about image manipulation, but I think i've found what I need via the GD library. However, I can't get the libraries to be in the right place on my OS X machine so i can't get it to compile, even though i'm SURE that

---

### Post by another_dave_b on 2006-01-29
I can't offer any code suggestions but there was a [Wil Shipley interview ]("http://www.drunkenblog.com/drunkenblog-archives/000581.html")(of Delicious Monster), where he spoke about reading barcodes that you might find useful.

---

### Post by Viro on 2006-01-29
GD meets your needs? I must say I am slightly surprised. It provides very rudimentary features. 

On OS X, you may just want to install GD via fink. It's the easiest way and it handles all the dependencies for you.

---

### Post by spaceballl on 2006-01-30
I'm going to use KDevelop to do this program. What is better than GD??

-Kevin

---

### Post by makhand on 2006-01-30
Can you post some example images? Also, do you understand yet how barcodes work? I mean, would you be able to decode a barcode yourself?

---

### Post by purpleturtle on 2006-02-02
Hey Spaceball,

I did Electronics at university (some years ago now...  In the Borland C compiler days (1994)), and on the C programming course I did, one of the projects I had to do was very similar to yours - finding specific shapes in an image.  Except, all I had to do was FIND the general area of the item in the image. And that was hard enough... :-)

Not wanting to sound like a pesamist, but it sounds like a massive undertaking to get every part of this working from start to finish in the amount of time you have.  I would humbly suggest that you try and break the problem into separate stages, and try and achieve some of the "interesting" parts that are going to get you a good mark for your project. You can always go back and implement the more mundane parts if you have time. (For example if you spend most of the alloted time writing your own awesome routines to read a jpg file into memory, but get nothing else to work, I doubt you would get any great credit for that).

Anyhow, the stages of processing as I would see it are:

1) Reading the image from file into memory
2) Identifying the bar code in the image, chopping this part out of the image and discarding the rest
3) Rotating/straightening out the bar code for subsequent processing (possibly)
4) Reading the bar code. At this point with your manipulated "normalised" image of a barcode, existing software will be able to process the image (Whether you can actually get libraries to do it is another matter, but the technology must exist).

Stages 1, 2, and 3 you could emulate what you would LIKE to achieve in your program with programs like Photoshop by applying thresholding to the image (for example). You could then write the code to work on this preprocessed image to read the barcode.

Personally though, I think the most value would be developing stages 2&3.

By the way, the previous post about "computer vision" is spot on.. This is what you need to read up on.

Anyway, sorry for the long post, and best of luck :-)

---

### Post by spaceballl on 2006-02-02
Thanks for the replies... Well, here's an update on the progress...

I've found a company that was willing to donate its bar code decoding C software toolkit to me (awesome!!!!). It works like a charm so I just need to figure out image processing (finding the barcode in a large image).

I've done some research on this, and rather than trying to find the barcode, i'm going to repeatedly scan the entire image as if a barcode already exists. If the scan fails, it fails, btu when it finds a match, we have a match. I'll keep you all updated. Thanks so much for the support and responses!

If anyone knows anything about image manipulation in C, though, I'd love to hear it...

-kevin

---

### Post by newbie2 on 2006-05-12
[http://lxer.com/module/forums/t/22639/](http://lxer.com/module/forums/t/22639/)
[http://www.kbarcode.net/](http://www.kbarcode.net/)

---

### Post by IYY on 2006-05-13
I don't know much about barcodes, but from an image processing point of view this should be quite simple. I'd suggest converting the images to bitmap, tiff or even raw format. It's much easier to work with. These conversions can be easily done with programs like imagemagick.

---


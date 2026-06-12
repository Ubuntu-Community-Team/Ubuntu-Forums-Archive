---
title: "Convert image to text"
date: 2009-12-18
forum: Programming Talk
---

### Post by dvlchd3 on 2009-12-18
I'm looking for a, preferably open source, program that converts Images to text.  I would also prefer Java, since I'm developing for persons that use a variety of different operating systems, however, if it's open source, I'm sure I'll have fun attempting to port it to Java anyway...

At the very least, has someone come up with an efficient algorithm that will complete this task.  I'm honestly not even sure to begin.

A benefit, for my solution at least, is the program will only need to convert images of numbers to text numbers.  This severely, in my mind, limits the possibilities for mistakes.

I've done some searching around, and only found commercial versions that are typically utilized with a scanner.  I actually want to be able to take a screen shot and convert that.

Hope that made sense - best case scenario:
Open-source Java program that will convert a screen shot of numbers to text.
Worse case, some pseudo-code or rough algorithm that converts pictures to numbers.
Absolute worse case - nothing exists that is open-source...

Does anyone know of such a creature :P

---

### Post by arvevans on 2009-12-18
Seems that what you are looking for might be what is called OCR (Optical Character Recognition) software.  If that is it, there are many programs already available that do this function, including many of the image scanner oriented applications.  Go to your Synaptic Package Manager and do a search for "OCR" to see what is available.  Of course if you just want to play with the software you can download the source code for these applications.
_._

---

### Post by quip on 2009-12-18
> **arvevans said:**
> Seems that what you are looking for might be what is called OCR ...

But the OP asked for software that didn't require a scanner or some kind of optical device, which rules out OCR.

Depending on what other factors you have at play (will the screenshot/image background color be a solid color?  Will it be the same?  Will the numbers be printed on the screen at the same height and width every time?  ...etc...), you might have an easier time hacking something together by taking advantage of your input, if it is rigid enough.

I am not familiar with that type of programming, but I would think you could analyze each pixel, get its color, and put it into a 2D array.  Then, you could go back and analyze the array for patterns that represent certain words.  If your code is efficient enough, you should be able to do it at a reasonable speed.  

Some guys at a company I interned for last summer did exactly that to pull some numbers out of a pdf and decipher them, successfully.  Of course, I then showed them they could use pdf2txt and get the info out of the text file a lot easier...

---

### Post by arvevans on 2009-12-19
OCR does not require a scanner.  OCR works from a bit-mapped image (.bmp files work great).
Color does present some problems for simple OCR software, but not for more complex programs which have capability to do recursive OCR for various colors and/or intensities.

---

### Post by quip on 2009-12-19
> **arvevans said:**
> OCR does not require a scanner.  OCR works from a bit-mapped image (.bmp files work great).
Color does present some problems for simple OCR software, but not for more complex programs which have capability to do recursive OCR for various colors and/or intensities.

True, and I have actually done that (run OCR on a pre-existing or otherwise acquired image).  I guess I just was thinking about the OP saying he/she didn't want to use a scanner...but you are absolutely right.

---

### Post by dvlchd3 on 2009-12-20
Well thank you for all the help.  That looks exactly like the solution I'm looking for.

---


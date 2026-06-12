---
title: "Getting average image colour (RGB/Hex)"
date: 2010-11-20
forum: Programming Talk
---

### Post by Jimmey on 2010-11-20
I am currently writing a program in python to handle large numbers of image files (for my purposes, 2,000+).

I really need to get the "average image colour", with the same result as has been achieved using [this code]("http://pythonicprose.blogspot.com/2009/09/python-find-average-rgb-color-for-image.html").

*[The code retrieves and totals the R, G, B values for each pixel in the image, and divides the total for each by the number of pixels, resulting in an average.]*

The problem is, previously, the program would run for between 10-20 seconds through the images I have. Just by adding the code to open each of these images using the PIL alone, I over double that time. And when I use the above algorithm, the time multiplies even higher.

Is there any quicker way to get the average image colour that anybody is aware of? 

Would it be much quicker to re-write a similar algorithm in a language like C++?

Any help is appreciated.

Jimmey

---

### Post by DougB1958 on 2010-11-20
> **Jimmey said:**
> 

I really need to get the "average image colour", with the same result as has been achieved using [this code]("http://pythonicprose.blogspot.com/2009/09/python-find-average-rgb-color-for-image.html").

*[The code retrieves and totals the R, G, B values for each pixel in the image, and divides the total for each by the number of pixels, resulting in an average.]*

...

Is there any quicker way to get the average image colour that anybody is aware of?
Jimmey

I seriously doubt that you can get substantially quicker, since to average all the pixels, you need to read all the pixels, and that's really all the example code does.

I suppose if you didn't need an exact average you could compute an average of some random sample of the pixels in the image, but the results could get pretty weird (for starters, the same image would almost certainly have different "average" colors on different runs, and how different those averages could be would depend a lot on your random number generator, how you sample, etc etc etc. All things I don't understand as well as I wish I did.)

---


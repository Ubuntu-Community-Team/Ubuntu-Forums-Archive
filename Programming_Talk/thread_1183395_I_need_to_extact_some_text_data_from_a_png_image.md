---
title: "I need to extact some text data from a png image"
date: 2009-06-10
forum: Programming Talk
---

### Post by Alcareru on 2009-06-10
Anybody have any ideas? What language might suit best for the job. The task is not time critical, so the efficency of the languge should not be much of a problem. More important time factor is that how quickly I can get this application working.

My coding experiences are C/C++ and Java. I haven't done much scripting (I've used bash and javascript a bit).

The end product needs to run on windows machines, but I would personally apreciate if the thing could also be used with linux computers.

---

### Post by Tony Flury on 2009-06-10
Just to confirm what you mean - you have a png image (which is basically a set of pixels) and as part of the image (combined maybe with background elements) there is a some text. You want to get that text (presumably in a format that you can edit in a word processor or text editor).

As far as I know the png format is a bitmap format, which means that all you have in the file is data about the pixels that make up the image and what colours they are.

Effectively what you are asking about is developing an OCR (Optical Character Recognition) program. These applications look at the patterns of pixels and they use inbuilt knowledge of the shape of fonts, and word patterns and shapes to make semi-intelligent guesses as to what the letters and words are. Such applications are complex beasts and are very difficult to get to 100%. You will also find that if there is considerable background graphics then even commercial OCR applications will struggle, and the accuracy may fall considerably.

I would recommend against trying to write a OCR application, you will probably find you will spend far more time getting the application right than you would spend just typing out the text. 

You could try using an existing OCR program to read your text - and you might have to convert the image from png to another format.

---

### Post by Alcareru on 2009-06-10
> **Tony Flury said:**
> Just to confirm what you mean - you have a png image (which is basically a set of pixels) and as part of the image (combined maybe with background elements) there is a some text. You want to get that text (presumably in a format that you can edit in a word processor or text editor).
Yes. You are correct. The picture "should" be simple. It has some graphics, but the textual matters are black letters on white background.

> **Tony Flury said:**
> As far as I know the png format is a bitmap format, which means that all you have in the file is data about the pixels that make up the image and what colours they are.
Yes, pngs are raster pictures.

> **Tony Flury said:**
> Effectively what you are asking about is developing an OCR (Optical Character Recognition) program. These applications look at the patterns of pixels and they use inbuilt knowledge of the shape of fonts, and word patterns and shapes to make semi-intelligent guesses as to what the letters and words are. Such applications are complex beasts and are very difficult to get to 100%. You will also find that if there is considerable background graphics then even commercial OCR applications will struggle, and the accuracy may fall considerably.
I understan that the problem doesen't have a generic quaranteed to work solution. This application does not have to be able to read any png image, but just one sort of picture that has "always" same font, colors, size, etc...
> **Tony Flury said:**
> I would recommend against trying to write a OCR application, you will probably find you will spend far more time getting the application right than you would spend just typing out the text.
That is out of the question. The picture is such that the text in it changes over time and it should be polled every hour. I have no access to the data in any other means than through this png image.

> **Tony Flury said:**
> You could try using an existing OCR program to read your text - and you might have to convert the image from png to another format.
That is not out of the question, I will look into those when I have the time.

In any case. I do know that this can be done with python for instance. I actually have an application that's suppose to do it, but it doesn't work anymore (the layout of picture changed) and I do not have the source that I could modify to make it work again.

A simple way to do this would be to cut the characters (actually I only need the numbers, 'cos the words don't change) out of the picture and have a small program to look for these small pictures within the big picture.

P.S. So essentially what I want to do is something like this (pseudo-code):
```

PNGPicture picture;
picture.open("input.png");
ArrayOfPNGPictures numbers[10];
for (int i=0; i<10; ++i)
{
    numbers[i].open(""+i+".png");
    ListOfCoords coords = getCoordinatesOfIn(numbers[i], picture);
    for (each coords as coord)
        processCoord(coord, i);
    numbers[i].close();
}
picture.close();

```

---

### Post by Tony Flury on 2009-06-11
In my opinion I would still look to use a 3rd party OCR application or library.

I have been in software development for an age (or it feels like it) and reasonable quality OCR is not something I would attempt to develop.

---

### Post by froggyswamp on 2009-06-11
> 
The picture "should" be simple. It has some graphics, but the textual matters are black letters on white background.
looks like he's trying to create a bot that can handle pictures-check enabled submission websites.

---

### Post by Alcareru on 2009-06-12
> **Tony Flury said:**
> In my opinion I would still look to use a 3rd party OCR application or library.

I have been in software development for an age (or it feels like it) and reasonable quality OCR is not something I would attempt to develop.
Well in this case the word reasonable might not be a necessity. :) Anyways, as I said I will dig into the existing software and libraries, as soon as I have the time. If they don't cut it I will then make my own app for the job... Thanks for the help.
> **froggyswamp said:**
> looks like he's trying to create a bot that can handle pictures-check enabled submission websites.
lol :)

---

### Post by crazyfuturamanoob on 2009-06-12
OpenCV is a great library capable of recognizing shapes, colors, motion, human face and lots of stuff from pixel data. Maybe that will help?

---

### Post by Alcareru on 2009-06-12
> **crazyfuturamanoob said:**
> OpenCV is a great library capable of recognizing shapes, colors, motion, human face and lots of stuff from pixel data. Maybe that will help?
Sounds like a solution. I will dig into that OpenCV, thanks all for your replies.

---

### Post by soltanis on 2009-06-12
gocr looks good (its a standalone program)

[http://jocr.sourceforge.net/](http://jocr.sourceforge.net/)

Just a suggestion.

---

### Post by Alcareru on 2009-06-24
Hi and thanks all for your replies. You gave me good suggestions, but I think I'm going to go for Tesseract: [http://code.google.com/p/tesseract-ocr/](http://code.google.com/p/tesseract-ocr/)

I will be digging into the api tomorrow... if that wont do it then it's libgocr (or conjecture or what ever it's called now days). It just seems to be dead project, but I suppose, if it does the job, who cares if it's nearly decade old?

OpenCV seems to be more about shape recognition and stuff like that. For computer vision, not text recognitino. I suppose I could use it for this purpose, but I'm guessing one of the other choices will be less painfull routes... :)

---


---
title: "Graphic Programming Language"
date: 2011-05-11
forum: Programming Talk
---

### Post by Mathew Roy on 2011-05-11
Hai buddies,
I have made a program in C that can write in my handwriting. It was a difficult ask for me. I have used libpng and my program and so my program can handle only png files.

Currently it is difficult to install a new handwritten, what I do now is I manually cut out letters in my handwriting in PNG format and give to my program. But this is a daunting task..

So, I want to automate it. My idea is to make one write alphabets, numbers in a given template, and  after scanning that the program should create the cutouts of each  characters by itself. And save the different characters as different PNG  files.

But, many told me that it is much easier and flexible to program in some other language other language. And also it should be able to handle at least common image formats..

Please help me choose a right language. And if u can help me in coding please help.

Thanks in advance..

---

### Post by slavik on 2011-05-12
basically, what you want to do is to create a font. :) google can help you.

---

### Post by Mathew Roy on 2011-05-12
> **slavik said:**
> basically, what you want to do is to create a font. :) google can help you.
Yea, but not exactly. Fonts are generally in ttf formal or some other format. but rarely png!. But I want the cutouts of each letter/number and essential symbols in PNG format..

Thanks for the input buddy..

[This site]("http://www.yourfonts.com/") internally does what I need, but it does not seem to be open source. Is there any open source program that does the same?. If so i could study it, so that my programming becomes easier. Right now I think I should start from scratch!..

---

### Post by Mathew Roy on 2011-05-12
Please someone try to help me..

---

### Post by kirkkaf on 2011-05-12
If you evenly space the characters apart on the piece of paper e.g each character is 32x32 (I assume you are using A4 paper so this needs to be something that works with the size of the paper 210x297)

You will need a graphics library something like SDL then in your program load the image and use loops to run through the size of the image copying part of the image e.g 32x32, 64x32, 96x32 saving each image as it's own PNG. (obviously you will need to work out a image size that works well with the size of the paper and how many characters will be written on it. 32x32 was just an example and won't work well with A4)

EDITED: C is just fine to use you just need to pick a good lib to deal with images. SDL is perfect for this task.

Sorry if this doesn't help.

---

### Post by slavik on 2011-05-12
why do you need all these pngs?

---

### Post by Mathew Roy on 2011-05-13
> **kirkkaf said:**
> If you evenly space the characters apart on the piece of paper e.g each character is 32x32 (I assume you are using A4 paper so this needs to be something that works with the size of the paper 210x297)

You will need a graphics library something like SDL then in your program load the image and use loops to run through the size of the image copying part of the image e.g 32x32, 64x32, 96x32 saving each image as it's own PNG. (obviously you will need to work out a image size that works well with the size of the paper and how many characters will be written on it. 32x32 was just an example and won't work well with A4)

EDITED: C is just fine to use you just need to pick a good lib to deal with images. SDL is perfect for this task.

Sorry if this doesn't help.
Thank you kirkkaf. That is exactly what I want. But the problem is, is it easy to find the area in which the image of the alphabet/number/symbol lies in the scan of A4 size template? The template will be basically made of squares, and one is supposed to write the letter in that square. Then, its the task of the program to find out the 4 corners of the square, so that it can copy the contents inside it. And how can I program that?. any idea?

Well thank-you for letting me know about SDL. It seems to a bit elaborate library. So can someone point in the direction where I should start from?.

---

### Post by Mathew Roy on 2011-05-13
> **slavik said:**
> why do you need all these pngs?
Well, as I said before, I used libpng and nothing else for my main program. So that program can handle only PNG files. So, If I want to include other types of images, then I will have to edit the whole code, which is not so easy for me. I have no formal education in dealing with graphics. So I am just a beginner in that field..

Also, there are some reasons behind the choosing of PNG.
The white area around each letter should be made transparent. JPEG, ttif, bmp etc cannot do this job because it has no transparency. Also the compression in PNG is lossless, which is an added advantage..

Thanks for the input.

---

### Post by kirkkaf on 2011-05-13
> **Mathew Roy said:**
> Thank you kirkkaf. That is exactly what I want. But the problem is, is it easy to find the area in which the image of the alphabet/number/symbol lies in the scan of A4 size template? The template will be basically made of squares, and one is supposed to write the letter in that square. Then, its the task of the program to find out the 4 corners of the square, so that it can copy the contents inside it. And how can I program that?. any idea?

Well thank-you for letting me know about SDL. It seems to a bit elaborate library. So can someone point in the direction where I should start from?.

I think what your looking for is a similar method to what is used in a tile based game, which takes one big image and breaks it down into smaller images. I am not the best C programmer so I can't really write anything in that language to help you but I something written in SDL and Lua that might help you implement it to your program.

I fount a decent graphics lib called Allegro for C which could do the job.

You want something like this:

```
your_image = loadimage("your_image.png")  'load image into memory.
new_image={}  'array.
for y=0, 2 do 
 for x=0,6 do
    new_image[i] = copyimage(x*64,y*64,64,64,your_image)
    saveimage(new_image[i],filename)
    i=i+1
 end
end
```

This would break an image of 1280x1280 into 64x64 smaller images and save them where ever you want.

So all there is to it really is afew for loops and afew commands from a graphics lib to handle loading, copying and saving an image.

Hope this helps, sorry if i'm off track here and couldn't write something in C but it shouldn't be hard for your to implement.

---

### Post by Some Penguin on 2011-05-14
> **Mathew Roy said:**
> 
Well thank-you for letting me know about SDL. It seems to a bit elaborate library. So can someone point in the direction where I should start from?.

Complex problems tend to require elaborate solutions.

Start by reading up on OCR algorithms.  You're not looking to implement a full OCR stack, as far as I can tell, but alignment and segmentation are problems you share with them.

---

### Post by kirkkaf on 2011-05-14
Hi Mathew,

I could program this little application for you if you like unless you want the programming experience.

However if I do it, it won't be written in C.

I will also need to know how many squares are in a template. Also if possible the width and height of the squares.

Kirk.

---

### Post by Mathew Roy on 2011-05-15
> **kirkkaf said:**
> Hi Mathew,

I could program this little application for you if you like unless you want the programming experience.

However if I do it, it won't be written in C.

I will also need to know how many squares are in a template. Also if possible the width and height of the squares.

Kirk.
Thank you kirkkaf for your sincere help towards my problem. please [Click Here]("http://ubuntuone.com/p/tNf/") to see the template. Its not necessary that u stick to this template. You can have your own choice if you want.

The specifications of the given template is as follows:
A4 size paper (@300 ppi)
Number of Columns   = 10
Number of Rows        = 14
Number of rectangles = 140
Thickness of the lines = 2 pixels
Distance between 2 vertical lines     = 206 pixels
Distance between 2 horizontal lines = 205 pixels

Its not at all necessary that you write it in C. U are free to choose the language you are comfortable with. I hope I will be able to understand the logic by reading the program, so that I can develop it further (Like making the white area in the image transparent). I will keep you updated about any development I make in this direction.

It is really helpful if you can help me out.. I am really thankful to you. Thank you Kirk.

There are some of the outputs of my handwriting program. [Click Here]("https://picasaweb.google.com/mathewroy007/Paper?authkey=Gv1sRgCLv7jsuIlYzX0AE&feat=directlink"). These will become more realistic when I have different images of same character.

---

### Post by Mathew Roy on 2011-05-15
> **Some Penguin said:**
> Complex problems tend to require elaborate solutions.

Start by reading up on OCR algorithms.  You're not looking to implement a full OCR stack, as far as I can tell, but alignment and segmentation are problems you share with them.
U are right!. I shall do some research in that direction also.. In fact it is necessary. Thank u for the input.

---

### Post by kirkkaf on 2011-05-16
Hi Mathew,

I think your program is a great idea and will definatly speed up your writing time :).

I will get to work on this later on as soon as I am home from work.

Get back to you soon.

cheers.

---

### Post by Mathew Roy on 2011-05-16
> **kirkkaf said:**
> Hi Mathew,

I think your program is a great idea and will definatly speed up your writing time :).

I will get to work on this later on as soon as I am home from work.

Get back to you soon.

cheers.
Thank you so much kirkkaf.
I had to make this program because I could not find an alternative in Internet. All I could find in net is handwriting font.
Well my program is not really handwriting font, one can have different  images of same alphabet/number/symbol. The distance between words are  not equal. Even the distance between lines are different (the error in  distance can be adjusted according to the needs). And as a fun, I added a  feature to write on any digital photos in your handwriting. 
If you are interested in getting the source code and binary files, I can give it.

---

### Post by Mathew Roy on 2011-07-28
**kirkkaf, [B]finally **I made it... Everything in just plain C....
[/B]

---

### Post by cgroza on 2011-07-28
> **Mathew Roy said:**
> **kirkkaf, [B]finally **I made it... Everything in just plain C....
[/B]
Mind sharing the code with us? Many people could benefit to your efforts. :D :D :D

---

### Post by slavik on 2011-07-28
I still don't understand how this is different than creating your own font using something like fontforge.

---

### Post by nvteighen on 2011-07-29
> **slavik said:**
> I still don't understand how this is different than creating your own font using something like fontforge.

Me neither. But I guess it was a great learning experience for the OP.

Some code would help me to understand this.

---

### Post by Mathew Roy on 2011-07-29
slayik. 
When we write, an 'a' will seem to be slightly different from  next 'a'. same with case of other characters and symbols.. If we create a  font of 'a'. every 'a' will look exactly same and wont look like  handwritten anymore...
So I choose to have different pictures of same  letter. And each time an 'a' is encountered, the program choses a  random image of 'a' form the database...
So. it increases the reality of the output...
Thanks...

---

### Post by Mathew Roy on 2011-07-29
> **cgroza said:**
> Mind sharing the code with us? Many people could benefit to your efforts. :D :D :D

Hai, Here is the code...
If you come across any difficulties in compiling please let me know...I have also included compiled files.

My program is nowhere near perfect. It has a lot of space to improve.. I will be very happy if some one give me new suggestions or bugs or modify the source.... 
Thank u all for the support...

OOPS!.. I cannot upload the executable files as it is more than 1mb..So sharing via UbuntuOne...here is the link to the file...[click here]("http://ubuntuone.com/p/16zu/").

---

### Post by slavik on 2011-07-30
[http://www.scribd.com/doc/202362/Random-Fonts-for-the-Simulation-of-Handwriting](http://www.scribd.com/doc/202362/Random-Fonts-for-the-Simulation-of-Handwriting)
:)

---

### Post by Mathew Roy on 2011-07-30
Slavic, the link that you posted is really helpful in the future development of the program. For that i think i should learn vector graphics.
Well is there any chance of getting the code for the same??

---


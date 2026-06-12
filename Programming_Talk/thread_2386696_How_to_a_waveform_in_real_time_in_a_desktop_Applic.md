---
title: "How to a waveform in real time in a desktop Application"
date: 2018-03-09
forum: Programming Talk
---

### Post by min-anand on 2018-03-09
Hi All,

I new to ubuntu and not familiar with most of the GUI toolkit which helps me draw a waveform in screen and will keep change based on the update.
I have created a GTK Window with Drawing Area.
Now I Can't think a way to use this show a waveform which will keep updating based on the input. Am I going in a right direction?

I have looked into the following link : 
**[SIZE=3][Drawing single pixel (again...) ]("https://ubuntuforums.org/showthread.php?t=1903258")[/SIZE]**

But I am not able to access the source that is been shared in this link.
Any help will be great support. Thanks a lot.

--Minakshi

---

### Post by norobro on 2018-03-09
Here's a link to a GTK3 Line Graph widget: [https://github.com/skoona/glinegraph-cairo](https://github.com/skoona/glinegraph-cairo)
I have not used this widget except to help the developer solve a problem a couple of years ago. If you can't use the widget maybe the code will give you some idea how to proceed.

In lieu of building and installing the whole package, you can compile and run the example like this:[INDENT]download and extract the zip file[/INDENT]
[INDENT]cd to the src/ directory[/INDENT]
[INDENT]gcc $(pkg-config --libs --cflags gtk+-3.0) *.c -o executable[/INDENT]
[INDENT]./executable[/INDENT]


If you are interested in Qt, Qwt is a lib that I have used: [http://qwt.sourceforge.net/](http://qwt.sourceforge.net/)  There is an example of a moving plot.
Also, the lead dev answers questions here: [http://www.qtcentre.org/forums/23-Qwt](http://www.qtcentre.org/forums/23-Qwt)

---

### Post by min-anand on 2018-03-12
Hi,

Thanks for response on my query. Actually I don't need to draw a curve or something.
I want to have black surface which I can treat as a collection of pixels.
So when get a notification to update the pixel position, then I simply fetch and update the pixel.

My intention is to use a Application window in place of fb. Any pointer will be a great help.

--Minakshi

---


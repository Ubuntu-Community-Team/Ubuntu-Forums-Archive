---
title: "java event on image"
date: 2011-04-07
forum: Programming Talk
---

### Post by edan3250 on 2011-04-07
hello all :)

i am using java-gnome, and i need to catch an image click event.
umm this is not my only problem, i have to get idea of algorithm to smart clicking... i explain what i mean.

i have an image called "piece" and the shape of image is hexagonal.
the all pieces images all close to others and here my problem start.

first all, i don't know how to catch image clicked, if someone know, it's will be helpful.

well, lets imagine that problem behind me...
a picture is rectangle, but my shape of picture is a hexagonal, how do i can catch the right image when i click on the transparent area?

i give an image of my game to see what i mean exactly!
[http://dl.dropbox.com/u/15250331/hex.png](http://dl.dropbox.com/u/15250331/hex.png)

do you see the mouse right now on the picture?
how can he knows i mean i clicked on this piece, or the others left pieces?
because in fact is an rectangle and not hexagonal, so its should catch an other picture :X

thanks for help!
and sorry for my english...

---

### Post by PaulM1985 on 2011-04-07
I am not 100% sure how you would catch the click event because I am not familiar with Gnome, I only ever use Swing when programming Java UI.  I will assume that Gnome has the concept of a panel (a sort of container that you can put things in) and explain how I would complete this task.

I would:
1 - have the image in the panel and the image and panel would be the same size.
2 - Add an action listener to the panel so that I can get click events.
3 - Get the X and Y co-ordinates of the click event.
4 - Get the corresponding pixel from the image object using the co-ordinates of the click event.
5 - If the pixel for the X and Y co-ordinate is transparent (check this by looking at the alpha component of the image) then the click is on the image, otherwise the click not on the image.

As far as clicking is concerned, I am guessing that you are using an image widget.  Maybe look at the addEvents method?  Like I said, I don't know java-gnome and I only had a quick look at the API.

Paul

---

### Post by edan3250 on 2011-04-07
> **PaulM1985 said:**
> I am not 100% sure how you would catch the click event because I am not familiar with Gnome, I only ever use Swing when programming Java UI.  I will assume that Gnome has the concept of a panel (a sort of container that you can put things in) and explain how I would complete this task.

I would:
1 - have the image in the panel and the image and panel would be the same size.
2 - Add an action listener to the panel so that I can get click events.
3 - Get the X and Y co-ordinates of the click event.
4 - Get the corresponding pixel from the image object using the co-ordinates of the click event.
5 - If the pixel for the X and Y co-ordinate is transparent (check this by looking at the alpha component of the image) then the click is on the image, otherwise the click not on the image.

As far as clicking is concerned, I am guessing that you are using an image widget.  Maybe look at the addEvents method?  Like I said, I don't know java-gnome and I only had a quick look at the API.

Paul
thanks paul!

1 - all the image on the same panel, so its not possible.
2 - that means i need to make a formula to get x,y of piece.
3 - click event of what?
4 - i don't know how do that... can you give me an example for swing?
5 - same as 4, and what is the r,g,b indexes of transparent?

thanks!

---

### Post by PaulM1985 on 2011-04-07
Ok, so if all of the images are on the same panel, you could probably work out which image the click is on given the co-ordinates of the click.

The code on this page describes how to add a MouseListener for Swing. [http://download.oracle.com/javase/tutorial/uiswing/events/mouselistener.html](http://download.oracle.com/javase/tutorial/uiswing/events/mouselistener.html)

You would have a mouseClicked function which takes a MouseEvent as an argument.  You can get the co-ordinates of the click from the MouseEvent object.  The mouseClicked function gets called on the clicks.

For colours there is a separate index for transparency.  See the Color class [http://download.oracle.com/javase/1.5.0/docs/api/java/awt/Color.html](http://download.oracle.com/javase/1.5.0/docs/api/java/awt/Color.html)

If your images do not have a transparent layer you will have to choose a colour which you will class to be "outside" the image (maybe white).  Either than or do some complex coding to create a boundary for an image.

If you have any more questions just ask.

Paul

---

### Post by edan3250 on 2011-04-07
thanks!

the mouselistener is not help me, because im using gnome... (anyway i know that)

about the transparent color i will read it, thanks!
do you know if have a function build-in to get pixel of the screen?

thanks again for help!

---

### Post by PaulM1985 on 2011-04-07
> **edan3250 said:**
> 
do you know if have a function build-in to get pixel of the screen?


I would expect this information would be available but you will have to check the java-gnome api.

---

### Post by edan3250 on 2011-04-08
i still need help, i can't get it work :(

java-gnome api:
[http://java-gnome.sourceforge.net/4.0/doc/api/index.html?overview-summary.html](http://java-gnome.sourceforge.net/4.0/doc/api/index.html?overview-summary.html)

can someone help me to use the right event to catch click by mouse on image?

if you are a c++ programmer it's will help me if i see an example on c++, i can read it and understand to translate to java... (on gtk+)

---

### Post by PaulM1985 on 2011-04-08
Have you researched button press events on widgets?

---

### Post by edan3250 on 2011-04-08
> **PaulM1985 said:**
> Have you researched button press events on widgets?
on button its works for me...
i'm using implements to Button.Clicked and this create me new function called "onClicked" there i catch the button clicks...
but its not works on image =/

---


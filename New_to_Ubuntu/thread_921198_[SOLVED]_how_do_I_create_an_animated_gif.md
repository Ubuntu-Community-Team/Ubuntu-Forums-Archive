---
title: "[SOLVED] how do I create an animated gif?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by anewguy on 2008-09-16
Even though I come from a technical background, it never included working with images.  I did create an animated gif in Windows years ago, but now have need for an easy to use and follow tool to do so in Linux.

I need to take several pictures, put a fade between them, and make a single animated gif from them.  I saw mention of using gimp, but that darn thing is hard for me to follow.  I also have Inkscape but have no idea if I can do it in there either.  I need something _*simple*_ for an old guy to use! :)

Thanks in advance!
Dave :)

---

### Post by Pro-reason on 2008-09-16
You've got thirteen hundred posts on here and you still can't use the GIMP?  Come on, I'm sure you could if you just gave it a try.

---

### Post by anewguy on 2008-09-16
I've tried GIMP  MANY times, but find I have better luck for what I do using Inkscape.  GIMP is quite cryptic for just casual use.

Dave :)

EDIT:  To give you an idea what I'm looking for, in Windows I used a simple little program where you just put each image you wanted in the animated gif in holders on the screen, set a delay between images, and a fade, and bingo, instant animated gif.

---

### Post by Pro-reason on 2008-09-16
Inkscape is fine for SVG, but not yet the tool to use for animation.

Just send me the images and I'll do it in the GIMP.

---

### Post by scragar on 2008-09-16
make it with a few layers(1 image per layer), then just save it as a gif, you get asked.

---

### Post by Pro-reason on 2008-09-16
> **scragar said:**
> make it with a few layers(1 image per layer), then just save it as a gif, you get asked.
So... what?  The computer asked you a simple question.  Did you answer? :confused:

Edit: ah, sorry.  I thought you must be asking what to do, but you probably intended to explain how to do it.

---

### Post by scragar on 2008-09-16
yeah, but I sort of assumed it would be easy to work out what the next page asks.

Interlacing normally reduces file size, but it's not much, and it can cause flickering.

The comment for you to decide if you want one or not(and what it says).

Loop forever is obvious, do you want it to loop forever, yes or no

Delay is up to you, 1,000 millsecs = 1sec

frame disposal is does it leave each old frame as the background for the new one (so if you want a fade out you could achieve this with just the initial image and a few partially transparent images, each transparent image will show some of the old content through, but at those partially transparent ones build up in number the picture will fade out more and more).

then you get to decide if you want your options to be aplied to all frames or not(I'd say tick them if you don't know what your doing, odds are you've not willingly set them anywhere else).

---

### Post by anewguy on 2008-09-16
Here's the problem I've always had.  I create 2 layers to test - 1 image in each.  I can use filters/web/animations and play it, but if I save as a gf I never get the screen you showed - it just saves it as a single image, with the 2nd superimposed on the first - no animation, no nothing.

---

### Post by enlightenment now on 2008-09-16
> **anewguy said:**
> Here's the problem I've always had.  I create 2 layers to test - 1 image in each.  I can use filters/web/animations and play it, but if I save as a gf I never get the screen you showed - it just saves it as a single image, with the 2nd superimposed on the first - no animation, no nothing.you usually need more then 2 layers, try 12.

---

### Post by Pro-reason on 2008-09-16
[CENTER][SIZE="1"]*(Stolen from [http://xkcd.org/473](http://xkcd.org/473))*[/SIZE]
[[IMG]http://img229.imageshack.us/img229/4171/stillrawvz0.gif[/IMG]]("http://xkcd.org/473")[/CENTER]

I've never used the GIMP for this before, but it was easy.

The Animation option under Effects allows you to do stuff like the blend transition.  By putting &#8220;(1000ms)&#8221; in the name of a layer, you can make it hang on for a second.  You can do more complex stuff if you add the gimp-gap package.

---

### Post by billgoldberg on 2008-09-16
> **anewguy said:**
> Even though I come from a technical background, it never included working with images.  I did create an animated gif in Windows years ago, but now have need for an easy to use and follow tool to do so in Linux.

I need to take several pictures, put a fade between them, and make a single animated gif from them.  I saw mention of using gimp, but that darn thing is hard for me to follow.  I also have Inkscape but have no idea if I can do it in there either.  I need something _*simple*_ for an old guy to use! :)

Thanks in advance!
Dave :)


Just put every single frame you need into a layer in the gimp and safe it as a .gif

Then you will need to play with the speed of the animations a bit to get it right.

---

### Post by anewguy on 2008-09-16
I finally got it!!  I was trying to do layers through the dialog menu - I didn't know all I had to do was "open as layers".  Now everything works exactly as you have all described, and it works beautifully!!

Okay, I also apologize to GIMP - although nothing I found on the net or in the help text said to "open as layers" :):)

Thanks, everyone!!  :)

Dave

---

### Post by cmb12352 on 2008-09-16
[size=2][font=Times New Roman][size=3]hi,everyone,need guitar effects pedals? take a look at [guitar effects pedals shop](http://www.myguitarpedals.com/), may be u will find ur favorite...This is an excellent thread!**The good:** The optional Bowers and Wilkins audio system in the 2009 Jaguar XF offers exceptional separation and clarity for music playback. We like the interior materials in the XF, along with the tech touches. The engine offers a good amount of power for the car while delivering acceptable fuel economy.[runescape gold](http://www.runescapecoin.net/) **The bad:** The touch-screen interface for audio, navigation, and other car systems is too slow, and it is not well organized. The navigation system is unremarkable.[age of conan gold](http://www.buy-age-of-conan-gold.com/)**The bottom line:** The 2009 Jaguar XF offers a lot of luxury for the money, with many unique high-tech touches and an exceptional audio system. But it doesn't always deliver on its apparent promise, [color=#008000][age of conan money](http://www.ageofconanmoney.net/) [/color]with a run-of-the-mill suspension and navigation system.[runescape money](http://www.runescapemoney.ws/). [/size][/font][/size]

---


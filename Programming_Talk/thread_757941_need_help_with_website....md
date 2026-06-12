---
title: "need help with website..."
date: 2008-04-17
forum: Programming Talk
---

### Post by hockey97 on 2008-04-17
Hi I need some help I have a problem...

I am currently making a website I am half way done just need to make the finishing touches.

Today I felt lazy and decided to not work on it so I thought I would give it a test try to see how it looks and if it works on ohter computers.

I boot up 3 other computers and typed my domain name in and looked at the website it was ok on 2 of the computers but the laptop had different display size. 

This made the website look ulgy.

I used css to make fixed positions to display the images and links ect and I also had css applied to the body of the html page to make the backround image fixed  and when I looked on the laptop it shows the backround image being displayed with a repeat of the image at the bottom it starts to repeat the top of the background image.

How would you go abouts to have a website display on each computer the same way???

would I have to check the users web browser and the current display settings and then grab a version of that??

or is there a way where I can resize my images or changed how they are displayed base off the users current display settings??

---

### Post by CptPicard on 2008-04-17
Welcome to the realization of why you don't use fixed positioning but instead try to create a so called fluid layout that scales to all screen and browser window sizes.

---

### Post by LaRoza on 2008-04-17
You need to get yourself the web developer toolbar for Firefox.

It allows you to resize to preset dimensions so you can test during development. (It does a lot more than that as well)

Your design has to be redone to be fluid.

---

### Post by DrMega on 2008-04-17
Don't use a background image if it doesn't tile well. An large image will just slow down your page (there are still a remarkable number of people using slow connections).

If you can't avoid it, then just define a single layer, fixed at the size of your image, and set that layour to house your image rather than having it as the overall background of the page, then draw all your other layers over the top of that one.

---

### Post by timcredible on 2008-04-17
have you tried [joomla?]("http://joomla.org") for web creation?  it's open source, has tons of templates, plugins, allows for html coding if you want, etc.

---

### Post by hockey97 on 2008-04-17
Thanks for the replies.  The reason I used fixed is becuse if I don't use the fixed settings in css  then my images  and text when rezied would shift to the left causing overlapping on ohther images and texts.

I am going to play around with the display/position. I will see if it still shifts the images to the left when the window gets resized.

---

### Post by hockey97 on 2008-04-17
oops  my  mistake I mean I am using  position:absolute; 

that's what I am using. it resizes when you resize the window.
It dosen't resize my website when the user has different display settings.

so my the laptop I have the settings for the display were high.

So my website now looks small where my images and texts are. 

It looks like the website is small which is displayed at the top of the window and then all the areas far out of my website reach would repeat my background image.

my background image I made  is at the size of my display settings which is  1024 by 768 pixels. the laptop  is  1680 by 1050.

---

### Post by LaRoza on 2008-04-17
Links to the site would help.

---

### Post by hockey97 on 2008-04-17
sure no problem I am still working on the website it's not done yet.

could you also give me comments on what you think of it so far??

here is the link  and this will only be up for like 1 to 4 hours.

so if it dosen't work that's becuse my server will not be up I will have it up just to let you guys see the problem.

resize your display settings to see the problem I face.

here is the link: [Click Here]("http://67.149.150.40/cpro.html")

---

### Post by hockey97 on 2008-04-17
so what do you guy's think of it??

I know some of you already looked at it .

---

### Post by Can+~ on 2008-04-17
Okay, here goes my opinion about the website, mainly, in terms of graphic style:

-The background is a huge image, kinda unnecessary, adds weight. Try to use a tiny repeatable/tiled background. 
-I'm still wondering what this page is.
-The content is presented in 4 tiny boxes, is there a reason for such minimalistic style?
-There's no cohesion between the elements. There's a blue-gray background, there's an image placed over a wooden background for no reason.
-I don't get that effect like.. blur on the objects, it's supposed to look like ice?
-The font on the titles is ugly.
-Use a fluid design, as someone pointed above, but quite a lot more fluid, instead of solid boxes with fixed numbers (you know, like width:100px), use %, like (width:10%), float:left/right for fixed divs, etc.

Please read my comments above as in "trying to help you", not the "boo, it sucks!" tone..

For further information on how to improve design, try to read and watch good design, smashing magazine has a lot of good examples:
[http://www.smashingmagazine.com/2007/05/21/60-elegant-and-visually-appealling-designs/](http://www.smashingmagazine.com/2007/05/21/60-elegant-and-visually-appealling-designs/)

---

### Post by hockey97 on 2008-04-18
Post closed!!!!

---

### Post by era86 on 2008-04-18
I would like to give input, but the website is not coming up for me..

---

### Post by hockey97 on 2008-04-18
Closed post!!!!

---

### Post by Can+~ on 2008-04-18
Image backup:
[http://img.photobucket.com/albums/v517/CanXp/hokey97page.png](http://img.photobucket.com/albums/v517/CanXp/hokey97page.png)

---

### Post by hockey97 on 2008-04-18
Closed post!!!

---

### Post by Can+~ on 2008-04-18
When I make websites, I usually start with a mockup made on fireworks (my favorite graphic tool, at least for web stuff).

I break it down into segments, see where I need to repeat elements, slice them accordingly, breaking it down to single image files, trying to save space depending on the type:

-Small image, usually for repetition: .gif
-Big image, poor colors: 16-bit -> 32-bit png
-Photograph: 80 quality: jpg.

Image of my localhost (apache2). It's behind a router anyway.
[http://img.photobucket.com/albums/v517/CanXp/local.png](http://img.photobucket.com/albums/v517/CanXp/local.png)

My server is named "Asgard". My windows partition has another name "Utgard". Go figure.


Oh, and my desktop has:
-minimalist murrine theme, running on gtk2 cairo engine  [gnome look](http://www.gnome-look.org/content/show.php/Murrine+Compact?content=78182).
-gnome-elephant icons [again, gnome look](http://www.gnome-look.org/content/show.php/Gnome%2BHumanElephant+Savane%2BMarine+?content=75500)
and my KDE apps have qt-curve and kde3-curve respectively with oxygen icons.

---

### Post by hockey97 on 2008-04-19
Closed post!!!!

---

### Post by hockey97 on 2008-04-20
Closed post!!!!

---

### Post by mssever on 2008-04-20
If I remember correctly, the CSS properties for controlling background image repeats are repeat-x and repeat-y. But your decision to eliminate the image altogether is wise; it looks like it was quite a large download.

For most purposes, trying to get the window dimensions for page layout purposes will cause more problems than it will solve. As you gain experience, you'll find fluid designs to be easier. But the other way, you'll encounter a number of browser differences; plus, what will you do about people who disable Javascript or who are using a setup that doesn't support it (screen readers, some cell phones, etc.)?

---

### Post by Can+~ on 2008-04-20
One typical solution in web design is using a wrapper. Is a big div (or table) which contains all the elements that must be positioned. If you need it to be centered, use both center for the parent (for compatibility with IE) and margin: auto; for firefox.

Grab Web Developer extension for firefox, and go look other pages, enable "Outline Custom element: Div" and see.

---

### Post by soapytheclown on 2008-04-21
> **hockey97 said:**
> So is there no way I can make a script to figure out the users web browser and version and the display settings the userser uses. Then change the hight and width of each element value?

you can using javascript to work out the resolution using:

screen.width();
screen.height();

then selecting each element and altering its css on the fly.. 
but this way would be greatly inefficient a complete redesign is needed imo based on that screen shot :)

---

### Post by hockey97 on 2008-04-22
Closed post!!!!

---

### Post by mssever on 2008-04-23
> **hockey97 said:**
> I also got a question since someone brought it up, I don't know much about the cellphones.  I had saw board froums saying you have to know mhtl or some new markup lango for the cellphones to display your page on the cellphone browser is that true or html would be read on all cellphones that have internet capabilites is that true??

It depends on the phone. Some phones are very primitive. Some (smart phones, especially) have normal browsers. the iPhone includes Safari, and Since Opera has a cell phone browser, presumably it's on some phones.

There is a separate language for cell phones (I don't remember what it's called). It seems silly to me to have a separate language, though. Just teach the phone HTML. But the mistake I'm making is in assuming that all cell phone companies have intelligent employees.

---

### Post by hockey97 on 2008-04-23
Closed post!!!!

---

### Post by hockey97 on 2008-04-26
Closed post!!!!

---

### Post by mssever on 2008-04-26
> **hockey97 said:**
> If there is any other way to resize my website and the elenments inside it so that the layout dosen't change due to the users display settings please do tell...

Make a container with a fixed size. Although I tend to frown on fixed layouts. Unless you've seriously redesigned your page from what you posted earlier, JavaScript is overkill--and it slows your page down. You don't need to calculate the page width. CSS will take care of that for you.

---

### Post by hockey97 on 2008-04-29
Closed post!!!!

---


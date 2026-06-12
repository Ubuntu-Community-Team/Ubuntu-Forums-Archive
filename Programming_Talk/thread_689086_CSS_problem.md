---
title: "CSS problem"
date: 2008-02-06
forum: Programming Talk
---

### Post by DanielJackins on 2008-02-06
Hi

I am slowly but surely learning how to and am in the process of designing my website. I have a fairly good understanding of HTML and CSS, but can not, for the life of me, figure out one thing.

[http://www.danieljackins.com](http://www.danieljackins.com)

Here is the site in question; 
I have no problems whatsoever setting things to the edges of the screen, but my main body of the page (or "mainBodyClass, if you look at the source) won't do what I want it to. I would like the main body to automatically position itself beside the left panel (with the links), no matter the browser or computer viewing it.

How would I do this?

---

### Post by irrdev on 2008-02-06
This should do the trick:

In the "leftPanelClass" add:

*position:relative;*
*float:left;*

In the "mainBodyClass" add:

[I]position:relative;
float:right;[/I]

Hope that helps. ;)

EDIT: I looked over your stylesheet a bit more, and noticed that all of your css positioning is "absolute". If you want perfect cross-browser rendering, you're going to have to change this to "relative". Generally, "absolute" positioning should only be used within a layout container, such as placing an image within the mainBodyClass. The actual layout should be free to rescale and resize itself to fit the viewer's screen. This is especially an issue in today's world, as widescreen displays are drastically different to the older but still popular monitors.

---

### Post by DanielJackins on 2008-02-06
Thanks!

So I tried what you told me, and now the main body is just hugging the right side of the page. I would like it right beside the left panel.

---

### Post by DanielJackins on 2008-02-07
anyone?

---

### Post by shawnhcorey on 2008-02-07
Could you post a PNG mockup of what you want?

---

### Post by LaRoza on 2008-02-07
I am not sure what you want.

Look at my site, is it anything like that?

---

### Post by DanielJackins on 2008-02-07
Yes, it would be something like yours. If I was looking at it in your sites perspective, I would want the main body up against the links on the left, no matter the browser and such forth

---

### Post by LaRoza on 2008-02-07
That would be easy.

[http://laroza.freehostia.com/home/style](http://laroza.freehostia.com/home/style)

Just change the numbers.

Notes:

div#title
div#nav
div#body 

are the three parts of the page, the links themselves are an unordered list.

---

### Post by Dojan5 on 2008-02-08
Hmm, makeing them work on "no matter browser" and so on is VERY hard...
Im a programmer (obviously)
If looking at the site i made here [Eva's Trädgårdscoaching]("http://www.tradgardscoach.de")
The Pop out menu doesnt work correctly on FireFox, on IE it works beautifully.
And, [Ksearch]("http://ksearch.atspace.com") looks dispositioned on IE since it was created in Ubuntu....
There are smaller problems with such things depending on which platform you use.

You can try and use tables to get your columns (Like i did in KSearch)
Or use CSS which you already do. I for one find CSS more extensible while tabled are easier to use.

---

### Post by DanielJackins on 2008-02-08
Do you mean changing the amount of pixels its placed by? Because wouldn't that make it different on different monitors/browsers?

---

### Post by tosk on 2008-02-08
Try changing this for mainBodyClass:
```
position:relative;
float:right;
```

to:

```
position:relative;
float:left;
```

As a word of advice, Internet Explorer DOES NOT like tags that end like this:
```
<link rel="stylesheet" type-"text/css" href="http://www.danieljackins.com/stylesheets/stylesheet.css" />
```
...with the trailing slash before the end of the tag.

---

### Post by DanielJackins on 2008-02-08
That was exactly what I was looking for, thank you very much!

How would you suggest I end it?

---

### Post by tosk on 2008-02-08
```
<link rel="stylesheet" type-"text/css" href="http://www.danieljackins.com/stylesheets/stylesheet.css">
```

Just without the slash. If this is XHTML, it won't validate, but if this is HTML then it should validate fine.

---

### Post by DanielJackins on 2008-02-09
Another question (sorry if your getting sick of me by now :))

Is there any way to make my headClass section not change at all? Whenever I add text to it its size changes according to the texts size :confused:

Any way to stop this from happening?

---

### Post by cb951303 on 2008-02-09
> **DanielJackins said:**
> Another question (sorry if your getting sick of me by now :))

Is there any way to make my headClass section not change at all? Whenever I add text to it its size changes according to the texts size :confused:

Any way to stop this from happening?

try

width: 100%;
height: YYpx;

to your head class

---

### Post by DanielJackins on 2008-02-10
So I got everything nice, on my monitor at least. When I view it on other peoples, or even resize the browser window for that matter, things get messed up. Could anyone look at my Style sheet and tell me what I'm doing wrong?

---

### Post by tosk on 2008-02-10
You have post the style sheet before we can. :P

Remember to put it in CODE brackets so it's easy to read.

---

### Post by DanielJackins on 2008-02-10
Right, sorry about that :P

```
body {
background-color: rgb(200,200,200);
margin: 0px;
padding: 0px;
font: 75%/1.4 verdana,Helvetica,sans-serif;
}

div.headClass {
border-bottom: 2px;
margin-bottom: 0px;
margin-left: 0px;
border-style: solid;
border-color: rgb(0,0,0);
border-top: 0px;
border-left: 0px;
border-right: 0px;
padding-bottom: 0px;
font-size: 24px;
position: relative;
background-image: url(http://www.danieljackins.com/Banner.jpg);
background-repeat: no-repeat;
height: 100px;
&nbsp;
}

p.headClass {
padding: 0px;
margin: 0px;
text-align: right;
padding-top: 25px;
padding-right: 20px;
color: rgb(255,255,255);

}

div.leftPanelClass {
border-top: 0px;
border-left: 0px;
border-right: 2px;
border-bottom: 2px;
border-style: solid;
border-color: rgb(0,0,0);
position: relative;
float: left;
padding: 10px;
margin: 0px;
height: 90%;
width: 10%;

}

div.leftPanelClass ul {
margin: 0px;
padding: 0px;
list-style-type: none;
}

div.leftPanelClass a {
display: block;
color: #FFF;
background-color: #036;
width: 14em;
padding: .2em .8em;
text-decoration: none;

}

div.leftPanelClass a:hover {
background-color: #369;
color: #FFF;
}


div.rightPanelClass {
border-top: 0px;
border-left: 0px;
border-right: 0px;
border-bottom: 0px;
border-style: solid;
border-color: rgb(0,0,0);
position: relative;
float: right;
padding: 10px;
margin: 10px;
width: 5%;
height: 70%;
}

div.mainBodyClass {
border-top: 0px;
border-left: 0px;
border-right: 2px;
border-bottom: 2px;
border-style: solid;
border-color: rgb(0,0,0);
position: relative;
float: left;
margin: 0px;
height: 70%;
width: 80%;
padding: 10px;
}

div.footClass {
position: relative;
top: 90%;
left: 45%;
right: 45%;
}
```

---

### Post by cb951303 on 2008-02-11
I likte to use fixed width websites. cause it gives me the chance to use absolute positioning and believe me it's much more easy :)

check www-yudosk-org it's the website I'm currently working on, it's tableless and uses absolute positioning for all of its divs ;)

---

### Post by shawnhcorey on 2008-02-11
> **cb951303 said:**
> I likte to use fixed width websites. cause it gives me the chance to use absolute positioning and believe me it's much more easy :)

So what does it looked like when one of your viewers who can see very well turns the minimum font size to 48pt?

---

### Post by cb951303 on 2008-02-11
> **shawnhcorey said:**
> So what does it looked like when one of your viewers who can see very well turns the minimum font size to 48pt?

I've just tested ubuntuforums.org and sitepoint.com with 48pt minimum font size and they DON'T look better at all then my site.
this is kind of an engineering problem. do we really need to consider half-blind people who wants to view sites at 48pt or should we use our resources at optimum (meaning spending less time and resource on a almost equally good looking site with acceptable font sizes) I choose the latter.

---

### Post by shawnhcorey on 2008-02-11
> **cb951303 said:**
> I've just tested ubuntuforums.org and sitepoint.com with 48pt minimum font size and they DON'T look better at all then my site.
this is kind of an engineering problem. do we really need to consider half-blind people who wants to view sites at 48pt or should we use our resources at optimum (meaning spending less time and resource on a almost equally good looking site with acceptable font sizes) I choose the latter.

It's not how they look.  The question is, "Are they readable at large font sizes?"

The problem with fixed-size block elements is that large font sizes forces the text outside of the block, meaning it either gets chopped off or overwrites other text.  Neither is readable.

You can, of course, do whatever you please on your own website but to give advice that you don't have to consider anyone less gifted than you is not just rude, it would get you fire at every placed I worked.

The technique of creating variable blocks is called fluid design or liquid design and your favourite search engine can give you millions of references.

---

### Post by popch on 2008-02-11
> **cb951303 said:**
> I've just tested ubuntuforums.org and sitepoint.com with 48pt minimum font size and they DON'T look better at all then my site.
this is kind of an engineering problem. do we really need to consider half-blind people who wants to view sites at 48pt or should we use our resources at optimum (meaning spending less time and resource on a almost equally good looking site with acceptable font sizes) I choose the latter.

Not quite the point. 

Your site becomes very hard to use (and to read) after increasing font sizes by 1 (one) step in Firefox. Texts overlap each other, images overlap text and so on. 

Your page already starts with a rather small font size, so your interpretation of what constitutes an 'acceptable font size' might be a bit narrow.

As others have said, it is perfectly within your right to restrict the visibility and usability of your site to hawk-eyed youngster viewing the the site within optimal lighting and seating conditions. Others might feel that your money and skills are better employed by taking care that the greatest number of people can read and use what you publish.

And compliments, by the way, on the looks of the site. Under ideal viewing conditions, that is.

---

### Post by LaRoza on 2008-02-11
[http://www.useit.com/alertbox/20020819.html](http://www.useit.com/alertbox/20020819.html)

Good site, and that article in particular may be interesting.

---

### Post by cb951303 on 2008-02-11
> **shawnhcorey said:**
> It's not how they look.  The question is, "Are they readable at large font sizes?"

 you don't have to consider anyone less gifted than you is not just rude, it would get you fire at every placed I worked.


When exactly I did what you stated in above quote?  I really don't understand why people gets offended so easily by others' ideas. I never stated that my approach was the best and you were less gifted than me ... I found that sentence as a serious attitude problem

I see your point about the liquid design, it's definitely better than my approach but it wasn't my point at all. As I stated before, I found more difficult to mess with relative positions than messing with absolute positioning so the time I gain is more valuable for me than making a site that can handle 48pt fonts. (assuming that I'm not a pro web designer)

---

### Post by cb951303 on 2008-02-11
> **popch said:**
> Not quite the point. 

Your site becomes very hard to use (and to read) after increasing font sizes by 1 (one) step in Firefox. Texts overlap each other, images overlap text and so on. 

Your page already starts with a rather small font size, so your interpretation of what constitutes an 'acceptable font size' might be a bit narrow.

As others have said, it is perfectly within your right to restrict the visibility and usability of your site to hawk-eyed youngster viewing the the site within optimal lighting and seating conditions. Others might feel that your money and skills are better employed by taking care that the greatest number of people can read and use what you publish.

And compliments, by the way, on the looks of the site. Under ideal viewing conditions, that is.

thanks for the compliments on the look :)

do you really think that the greatest number of people can't read my site? I'm asking because I've just learned the concept of liquid design and I might consider adapting my sites to it ...

thanks

---

### Post by LaRoza on 2008-02-11
> **cb951303 said:**
> thanks for the compliments on the look :)

do you really think that the greatest number of people can't read my site? I'm asking because I've just learned the concept of liquid design and I might consider adapting my sites to it ...

thanks

I am a web developer, and my opinion on that site, [http://www.yudosk.org/](http://www.yudosk.org/), is that it is a good idea for a layout, but it is way too small. (There is also a text overflow on the lelf)

The best thing about it is it works at 800x600, the worst thing is that is looks like it is at that resolution all the time.

I am twenty, and have good eyesite, and it is too small. Try using 12 pt at the least.

---

### Post by popch on 2008-02-11
> **cb951303 said:**
> 
do you really think that the greatest number of people can't read my site? I'm asking because I've just learned the concept of liquid design and I might consider adapting my sites to it ...

Consider: the font size of the text part is quite small and it is in front of an area which is unevenly colored. 

There are a number of situations where that text can become hard to read:
[LIST]
[*]Using a small screen
[*]Having less than ideal eyesight
[*]Using the screen in sunlight
[*]Using the screen in a place where the sun shines into your face
[*]Using a poorly adjusted screen (including a poorly focused CRT)[/LIST]The list can go on and on. 

For practically every of those situations you have to increase the size of the text in order to read it. Try and see what happens. Not only will your page layout become very ugly, but your entire page will be rather difficult to use and understand.

By adapting a set of skills and techniques which minimizes those problems you will have a site which is usable by many more people, at no extra cost to you or your employer. It will also make look the web site more professional.

If you are really interested in the topic, have a look at [http://www.w3.org/WAI/](http://www.w3.org/WAI/)

---

### Post by cb951303 on 2008-02-11
LaRoza & popch: thanks for kind critics and links, it seems like relative positioning worths the extra(for me at least) work  ...

---

### Post by tosk on 2008-02-11
I could've sworn I replied to this thread earlier. :/

In div.leftPanelClass, change this:
```
width:10%;
```
to:
```
width:14em;
```

What else doesn't look right specifically?

---

### Post by DanielJackins on 2008-02-13
Okay, and what exactly does em stand for?

---

### Post by tosk on 2008-02-13
It's a unit of measure. See this in your code:
```
div.leftPanelClass a {
...
width: 14em;
...
}
```

That's why your links stick out so far past the edge of the parent object. The parent object has a variable width that is less than the absolute with of its child (in this case, the links). Setting the parent to an absolute width, or setting the child to a variable width of 100% will fix the problem.

---

### Post by LaRoza on 2008-02-13
> **DanielJackins said:**
> Okay, and what exactly does em stand for?

emphasis.

It is usually rendered by default as italic.

In CSS, 1em is the current font size.

---

### Post by popch on 2008-02-13
> **DanielJackins said:**
> Okay, and what exactly does em stand for?

The "em" is a unit of length and is used to express the size of a font. One em is the height of the upper case letter 'M' as measured from baseline to top. In the case of css, it refers to the letter 'M' in the font which applies to the place where the measure is applied.

A typical use would be the value 1.2em to state that an element B occurring within element A is to use a font which is 20% taller than the font of element A.

Caution: 1 em is still the ***height*** of the letter 'M' even when measuring horizontal or oblique distances. It does not magically or mysteriously become the width of that letter.

---

### Post by DanielJackins on 2008-02-13
How would I set it to a variable width of 100%?

---

### Post by shawnhcorey on 2008-02-13
> **DanielJackins said:**
> Okay, and what exactly does em stand for?

That depends on the context.

Sometimes it means the width of a lowercase 'm'.  This is the width of the HTML characters &emsp; and &mdash;  There is also an en, which is the width of a lowercase 'n', with the corresponding characters &ensp; and &ndash;

When you're talking about font-size, an em is the size of the em square [15.4.3 Coordinate units on the em square]("http://www.w3.org/TR/REC-CSS2/fonts.html#emsq") which in typography terms is the leading (pronounced "LED ing"), the distance between one baseline and the next.

And finally there is the HTML element <em> which stands for emphasis.

---

### Post by tosk on 2008-02-13
> **DanielJackins said:**
> How would I set it to a variable width of 100%?

```
width:100%;
```

---

### Post by DanielJackins on 2008-02-20
CSS is starting to confuse me so much :confused:

Can anyone look at my [stylesheet](http://www.danieljackins.com/stylesheets/stylesheet.css)
and tell me what I'm doing wrong with it?

My problem right now is that if I resize my browser to much it becomes very messed up

---

### Post by shawnhcorey on 2008-02-20
> **DanielJackins said:**
> CSS is starting to confuse me so much :confused:

Can anyone look at my [stylesheet](http://www.danieljackins.com/stylesheets/stylesheet.css)
and tell me what I'm doing wrong with it?

My problem right now is that if I resize my browser to much it becomes very messed up

Your problem is that you are not using fluid design (also called liquid design).

1.  You change the font size to something smaller than what the viewer wants.

2.  You change the font size to pixels, not percentage.  And all percentages must be greater than or equal to 100.

3.  You use relative position rather than let the browser decide the position.

4.  You dictate a height.  Text has no bottom, ever.

5.  You dictate a width that is not expressed in the font size.

HTML is not GUI.  You cannot control the font size, the window dimensions, or the viewers' preferences.  Adopting to these requirements takes effort but will give you a web site that can adjust to varying window sizes and font preferences.

---


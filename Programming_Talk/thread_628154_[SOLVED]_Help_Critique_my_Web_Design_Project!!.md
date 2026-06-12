---
title: "[SOLVED] Help Critique my Web Design Project!!"
date: 2007-11-30
forum: Programming Talk
---

### Post by brennydoogles on 2007-11-30
I am in an intro level Web Design class, and on Tuesday I am turning in my final project. In the mean time, I was wondering if anyone would be willing to take a look at it and  give me some suggestions and/or report bugs. A few details to help with suggestions:

My class has not covered Javascript, or any server languages, so the entire site is Xhtml and CSS. If there is a simple script that would make the site better, go ahead and post it, but also please explain what each part of the script does so that I can tweak it (if needed) and verify what it is for.

It is a cooperative project, and some of the pages may have dirty code produced by Dreamweaver (in Design mode) rest assured that those aren't my pages ;P 

The site is not done, and is only a prototype for my intro class. Not all thumbnails will eventually link to full pages for example. Thanks so much for your help, and without further ado, the site is [HERE]("http://innerworkingdesigns.fill-intheblank.com/thelook/intro.html")

---

### Post by Dark Hornet on 2007-12-01
Not bad...personally, I am not a fan of the scrolling anything on a website, but thats just me.  In addition, you might want to consider changing the font size on the home page of the signature, as usually this is smaller than the actual text, and tends to look a little more professional.

Good luck!

---

### Post by LaRoza on 2007-12-01
* get rid of the splash screen, or if you must have it, have the 'click to enter' actually a link

* get rid of the scrolling banner

* possibly add more navigation, right now the site is small, but having links on the side or bottom could be needed when it gets bigger

* get rid of the deprecated elements, and use more CSS

For the splash screen, if you must have it:

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>The Look</title>
<script type="text/ecmascript">
window.onload = function()
{
    //This is just for brevity, you should have all CSS and Script in external files
    setTimeOut('window.location="home.html"',3000);
}
</script>
</head>



<body>
<center>
<br />
<br/>
<br/>
<br />
<br />
<br />
<br/>
<br/>
<br />
<br />
<br />
<a href="home.html"><img border="0"  src="images/lookreflectedsmall.jpg" alt="Click to Enter" /></a>
<br/>
<br/>
<a href="home.html" title="Click to enter">Click to Enter</a>

</center>
</body>
</html>

```

---

### Post by brennydoogles on 2007-12-01
Thanks for the suggestions!! As for the scrolling images, I have to admit that it is actually an inside joke between our group and the professor. He hates scrolling marquee, and told us that we could find a way to use a marquee in a semi-useful way we could get extra credit. I normally would not use marquee at all.

If I understand correctly, is the javascript you mentioned LaRoza to redirect the visitor?? If so, that would be really cool. Thanks for the feedback!!

---

### Post by LaRoza on 2007-12-01
> **brennydoogles said:**
> 
If I understand correctly, is the javascript you mentioned LaRoza to redirect the visitor?? If so, that would be really cool. Thanks for the feedback!!

Yes. I didn't test it though.

---

### Post by smartbei on 2007-12-01
It should be 'onTimeout', not 'onTimeOut'. Other than that it should be fine.

@OP: I highly recommend installing the html tidy firefox extension (google is your friend). It makes it very easy to catch errors in the (x)html itself. For example, in home.html page your '&nbsp's should end in a semicolon, and in you contact.html page you use the same id - 'bold' - multiple times (use a class instead (you can have an element 'inherit' [what is the correct term?] from two classes using class="class1 class2")). :D (no, I don't do lisp (working on it though))

---

### Post by ThinkBuntu on 2007-12-01
Critique:

[LIST=1]
[*]Use color
[*]Never have a splash screen unless it's delivering useful information. That goes for any page, actually
[*]You're scrolling stuff at the bottom. Why? Visitors shouldn't have to wait for your content, and you have plenty of room to spare
[*]Footer links disappear when I hover them
[*]When I click a link (a:active) in the body, it also disappears
[*]You're re-using a visual element, your logo, and I'm not sure why.
[/LIST]

But all that being said, pretty decent for a beginner. Keep it up!

---

### Post by Mr.popo on 2007-12-01
*  Get rid of the spash screen
*  Needs more attractive colours.
*  Make the font smaller.
*  Make a better navigation.

other than that its looknig good :)

---

### Post by alphane on 2007-12-01
+ 1 for smaller font.

I'm on a limited resolution (1360x768) and once on your page I can't even see any of your sale items, just the huge intro text.

---

### Post by Kadrus on 2007-12-01
Euuh..the font is a bit big..just make it a little smaller...and the only think that I don't like is the menu{that displays the links}what I mean that i don't like this :
Home          Catalog          Jean LeHott          Our Legacy          Contact Us

And the scrolling items..don't like it..

---

### Post by pmasiar on 2007-12-01
> **LaRoza said:**
>  possibly add more navigation, right now the site is small, but having links on the side or bottom could be needed when it gets bigger


Agree with LaRoza 100%. But research says, navigation should be on top or left side:
People scan pages in F fashion.

For usability tips for websites, useit.com is THE ultimate source.

---

### Post by brennydoogles on 2007-12-01
> **Kadrus said:**
> Euuh..the font is a bit big..just make it a little smaller...and the only think that I don't like is the menu{that displays the links}what I mean that i don't like this :
Home          Catalog          Jean LeHott          Our Legacy          Contact Us

And the scrolling items..don't like it..

So what do you not like about the menu? Since the site is as large as it will ever be (since it will never be touched again after Tuesday), we were looking for a very minimalist nav system, and settled upon that. Any way to improve it, however, would be wonderful. As for the scrolling items, noone likes them, and we understand that. This is more of a friendly jab at our professor than an actual design decision.


Now speaking of the scrolling pictures, has anyone had problems loading the entire images the first time? I have noticed that sometimes only the top 1/4 of the images will load, but a page refresh will load the rest of the images. Any ideas on what might be causing this or how to fix it? Any help would be greatly appreciated!

---

### Post by smartbei on 2007-12-01
I have had the exact problem you just stated brennydoogles, but didn't mention it since it didn't 'reproduce' :D.

I am not exactly sure what the problem is. I guess you could try to use javascript to preload the images and only display them when the are done loading. Since your class does not cover javascript however...

---

### Post by Kadrus on 2007-12-01
> **brennydoogles said:**
> So what do you not like about the menu? Since the site is as large as it will ever be (since it will never be touched again after Tuesday), we were looking for a very minimalist nav system, and settled upon that. Any way to improve it, however, would be wonderful. As for the scrolling items, noone likes them, and we understand that. This is more of a friendly jab at our professor than an actual design decision.


Now speaking of the scrolling pictures, has anyone had problems loading the entire images the first time? I have noticed that sometimes only the top 1/4 of the images will load, but a page refresh will load the rest of the images. Any ideas on what might be causing this or how to fix it? Any help would be greatly appreciated!

Since the links are very few...there is no need to use a drop down menu..using Javascript..,and I can't see the images in the marquee..

---

### Post by Vadi on 2007-12-01
I got the 1/4 of images loaded too. It doesn't scroll smoothly either.

It would look much nicer like the scrolling thing YouTube embedded applets have - although that might be quite complex to make..

---

### Post by Kadrus on 2007-12-01
> **Vadi said:**
> I got the 1/4 of images loaded too. It doesn't scroll smoothly either.

It would look much nicer like the scrolling thing YouTube embedded applets have - although that might be quite complex to make..

It's made using Flash if I am not mistaken...and you can create a very attractive image slide show with Javascript..so I don't see the necessity of using a marquee ..

---

### Post by brennydoogles on 2007-12-01
> **smartbei said:**
> I have had the exact problem you just stated brennydoogles, but didn't mention it since it didn't 'reproduce' :D.

I am not exactly sure what the problem is. I guess you could try to use javascript to preload the images and only display them when the are done loading. Since your class does not cover javascript however...

If you have a suggestion for the Javascript, I would be more than happy to go outside of the scope of the class to make the images functional. I have to present to the professor and the class, and the last thing I need is for the images to not load correctly. Since I already added the redirect script, this would be fine as well. Also, just for simplicity sake, how do you link to an external javascript file? Thanks!!

---

### Post by Kadrus on 2007-12-01
> **brennydoogles said:**
> If you have a suggestion for the Javascript, I would be more than happy to go outside of the scope of the class to make the images functional. I have to present to the professor and the class, and the last thing I need is for the images to not load correctly. Since I already added the redirect script, this would be fine as well. Also, just for simplicity sake, how do you link to an external javascript file? Thanks!!
For linking to an external Javascrit file
```
<script src="example.js">
</script>
```
easy..

---

### Post by ThinkBuntu on 2007-12-01
Not to be smart, but you actually want to use:
```
<script src="example.js" type="text/javascript"></script>
```

---

### Post by brennydoogles on 2007-12-01
> **ThinkBuntu said:**
> Not to be smart, but you actually want to use:
```
<script src="example.js" type="text/javascript"></script>
```

ok, cool. Now inside the script file I do not need the script tags correct?? Also, I noticed that the redirect script was an ecmascript, does that have to have a different filetype as Javascript? Also do I reference it as Javascript in the src or as an ecmascript? Thanks so much for your help!

---

### Post by ThinkBuntu on 2007-12-01
> **brennydoogles said:**
> ok, cool. Now inside the script file I do not need the script tags correct?? Also, I noticed that the redirect script was an ecmascript, does that have to have a different filetype as Javascript? Also do I reference it as Javascript in the src or as an ecmascript? Thanks so much for your help!
This is basically a file include, and there's nothing more you need to do. For all practical purposes, JavaScript is ECMAScript so you should be OK.

---

### Post by smartbei on 2007-12-01
I am not exactly sure why LaRoza put ecmascript. I usually use text/javascript - perhaps he knows better. That is correct, you do not need script tags in the .js file.

---

### Post by LaRoza on 2007-12-01
> **smartbei said:**
> I am not exactly sure why LaRoza put ecmascript. I usually use text/javascript - perhaps he knows better. That is correct, you do not need script tags in the .js file.

Most usually do put text/javascript. One could also use text/jscript, but text/ecmascript is what I use.

I write in standards compliant ecmascript, and want the MIME type to reflect that. You can use text/javascript if you want, I don't think it will change anything.

---

### Post by brennydoogles on 2007-12-02
> **LaRoza said:**
> Most usually do put text/javascript. One could also use text/jscript, but text/ecmascript is what I use.

I write in standards compliant ecmascript, and want the MIME type to reflect that. You can use text/javascript if you want, I don't think it will change anything.

What are the differences between Javascript and ecmascript, and why would one choose one over the other? Where could I learn ecmascript?

---

### Post by LaRoza on 2007-12-02
> **brennydoogles said:**
> What are the differences between Javascript and ecmascript, and why would one choose one over the other? Where could I learn ecmascript?

Technically, ECMAScript is the standard that JavaScript and JScript follow. JavaScript and JScript are the propreitary languages. JavaScript is mostly used, and is even recommended by Microsoft as the MIME type, because it is the same as JScript.

There are a few things specific to JScript and JavaScript, however, if you follow the standards, like the Document Object Model, you are writing ECMAScript. You probably avoid the extensions of JScript and JavaScript anyway, as I doubt IE is your primary browser.

JavaScript and JScript are "branches" of ECMAScript.

---

### Post by brennydoogles on 2007-12-02
> **LaRoza said:**
> Technically, ECMAScript is the standard that JavaScript and JScript follow. JavaScript and JScript are the propreitary languages. JavaScript is mostly used, and is even recommended by Microsoft as the MIME type, because it is the same as JScript.

There are a few things specific to JScript and JavaScript, however, if you follow the standards, like the Document Object Model, you are writing ECMAScript. [COLOR="Red"]You probably avoid the extensions of JScript and JavaScript anyway, as I doubt IE is your primary browser.[/COLOR]

JavaScript and JScript are "branches" of ECMAScript.

Does this mean that ecmascript is not compatible with IE?? I don't really care about IE, but it is useful to know the limitations and specifications of each language. In an external ecmascript file, do I need to use a .js file extension? Thanks so much for your sugestions!!

Also, if anyone knows how to preload the images on the home page that would be great. Thanks!

---

### Post by LaRoza on 2007-12-02
> **brennydoogles said:**
> Does this mean that ecmascript is not compatible with IE?? I don't really care about IE, but it is useful to know the limitations and specifications of each language. In an external ecmascript file, do I need to use a .js file extension? Thanks so much for your sugestions!!


ECMAScript is compatible with IE.

See my page for a working example: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

It is the same code as JScript and JavaScript, just not with any browser specific code.
 
I use the .js file extension, but I don't know if it is needed. It just to has to be served with the correct MIME type.

---

### Post by brennydoogles on 2007-12-02
> **LaRoza said:**
> ECMAScript is compatible with IE.

See my page for a working example: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

It is the same code as JScript and JavaScript, just not with any browser specific code.
 
I use the .js file extension, but I don't know if it is needed. It just to has to be served with the correct MIME type.

Thanks. You're my Hero.

---

### Post by LaRoza on 2007-12-02
> **brennydoogles said:**
> Thanks. You're my Hero.

Any particular reason?

Glad it helped.

---

### Post by ThinkBuntu on 2007-12-02
I just know that O'Reilly's Rhino book says "JavaScript" and not "ECMAScript." I'm sure that the majority of my script is essentially ECMA, but I understand that such useful ditties as innerHTML aren't standards.

---

### Post by LaRoza on 2007-12-02
> **ThinkBuntu said:**
> I just know that O'Reilly's Rhino book says "JavaScript" and not "ECMAScript." I'm sure that the majority of my script is essentially ECMA, but I understand that such useful ditties as innerHTML aren't standards.

innerHTML is a MS thing.

I use the DOM for almost everything I do, to ensure compatibility.

---

### Post by brennydoogles on 2007-12-02
Ok, I updated the site, and linked to the redirect script and a script to preload the images on the home page. Hopefully, this will take care of the issue with images in the marquee not loading correctly before a page refresh. If anyone would be willing to test it for me it would be awesome. [HERE]("http://innerworkingdesigns.fill-intheblank.com/thelook/intro.html")  is the link again. Thanks so much for all of the help you guys have given me. You RAWK!!

---

### Post by ThinkBuntu on 2007-12-03
You really need to ditch the splash page. It serves no discernible purpose and is a waste of a click.

---

### Post by LaRoza on 2007-12-03
> **ThinkBuntu said:**
> You really need to ditch the splash page. It serves no discernible purpose and is a waste of a click.

+1

---

### Post by brennydoogles on 2007-12-08
Thank you all so much for your help!! My team and I made a 97% on the project! The site will only be up for a few more days, so I may see if admin will close the thread so no one gets confused in the future. Thanks again for the help!

---


---
title: "HTML help- adding a background image"
date: 2010-11-07
forum: Programming Talk
---

### Post by sudoer541 on 2010-11-07
I want to add a background image to my site, but whatever I do the image is repeated or it does not cover the whole page!

Here is one sample: ```

<html>
<body>
</body>
<head> 
<style type="text/css">
.imageBox {
  width:300;
  height:100;
  background-image:url("gradient.jpg");
}
</style>
<div class="imageBox">
</div>
```Is there something wrong with my code? 

more info: 
The image file is placed on the same folder as my html code. 
Is there a specific place to place the CSS code ?

---

### Post by sudoer541 on 2010-11-07
Here is a better version: 

```

<style type="text/css">
.imageBox {
  background-image:url("gradient.jpg");
}
```

Yet am still unable to cover the whole page with the selected background image
I would really appreciate your help!

---

### Post by s.fox on 2010-11-07
Thread moved to  [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by Joeb454 on 2010-11-07
Perhaps this will help?

[http://www.w3schools.com/css/pr_background-repeat.asp](http://www.w3schools.com/css/pr_background-repeat.asp)

---

### Post by sudoer541 on 2010-11-07
> **Joeb454 said:**
> Perhaps this will help?

[http://www.w3schools.com/css/pr_background-repeat.asp](http://www.w3schools.com/css/pr_background-repeat.asp)


hmm I tried that but nothing happens:(
Should I paste my HTML code here? (its not too long I promise!)

---

### Post by ~LoKe on 2010-11-07
Sure, post it.

---

### Post by sudoer541 on 2010-11-07
Here it is: 

```

<html>
<body>
body
{
background-image:url('gradient.jpg');
background-repeat:repeat-n;
}
</body>
<head> 
}
</style>

</head>
<title>
My first website 
</title>
</body>


<body> <font size=13>This is a sample.</body> 
<font size=13/>
 

<p>testing paragraphs:</p>
<p>
<a href= "www.google.ca">
<font> Google</font>
</a>
<a href="Google">
<img src= "Google logo.jpg" height="100" width="100"/>
</a>

</p>
<p>
<a href="http://www.google.com/chrome">
<font> Google Chrome</font>
</a>
<a href= "http://www.google.com/chrome">
<img src="chrome.jpg" height="100" width="100"/>
</a>
<p>
<a href=www.yahoo.ca>
<font> Yahoo </font>
</a>
<a href= "www.yahoo.ca">
<img src="yahoo logo.png" height="100" width="100"/>
</a>
</p>


<p>
<body>
This is a sample paragraph (again) 
</body>
</p>


<p>
<a href=info.html>
<H2 align="center">Help</H2>
</a>
</p>




</body>
</html>
```

---

### Post by ~LoKe on 2010-11-07
You better do some research on HTML and CSS and how they work together.  You've got CSS randomly pasted without the proper style tags, that thing's a mess.

Here you go:

```
<html>
<head>
<style type="text/css">
body
{
	background-image:url('gradient.jpg');
	background-repeat:repeat-y;
}
</style>
<title>My first website</title>
</head>

<body>
<p>This is a paragraph.  It's a proper paragraph tag.  You don't use the body tag for every paragraph, it's only used at the beginning and end of your content.</p>
<p>This is a link to <a href="http://google.com">Google</a>.  That's a proper link.</p>
<p><h2>This is a proper header</h2></p>
<img src="http://www.google.com/images/logos/ps_logo2a_cp.png" alt="" />

<p>The above the correct use of an image tag.</p>

<p><h1>Good luck.</h1></p>

</body>
</html>
```

---

### Post by sudoer541 on 2010-11-07
Update: I just corrected a small bug on the code. However the image still repeats itself even when I inserted N instead of Y
here is a sample again: 

```
<style type="text/css">
body
{
background-image:url('gradient.jpg');
background-repeat:repeat-N;
}
</style>
```

---

### Post by sudoer541 on 2010-11-07
> **~LoKe said:**
> You better do some research on HTML and CSS and how they work together.  You've got CSS randomly pasted without the proper style tags, that thing's a mess.

Ohh, so i cant mix HTML with CSS?
edit:  I know its very messy:D

---

### Post by Untitled_No4 on 2010-11-07
If I understand you correctly you want one image to stretch to cover the whole page but without repeating the image?
If so, check out this link and check the page source to see how he's done it: [http://www.cssplay.co.uk/layouts/background.html](http://www.cssplay.co.uk/layouts/background.html)

---

### Post by ~LoKe on 2010-11-07
You can most certainly mix HTML and CSS, you just have to do it with proper tags and the right structure.

AS for repeat-n, well, that's no an argument I'm aware of.  repeat, repeat-x, and repeat-y are.  I'm pretty certain there's no repeat-n.

And it's not just messy, it's just plain wrong.  Usually I'd just let people mess around with their code and do whatever, but you're going to get confused and pissed when you can't get the layout right, just because you screwed up a paragraph tag or something silly that throws off the entire layout.

---

### Post by Untitled_No4 on 2010-11-07
```
<style type="text/css">
body
{
background-image:url('gradient.jpg');
background-repeat:repeat-N;
}
</style>
```

There's no repeat-N value. repeat-y means the background will repeat vertically.
```
background-repeat: repeat-y /* repeat vertically */
background-repeat: repeat-x /* repeat horizontally
background-repeat: no-repeat /* image will not be repeated */

```

---

### Post by sudoer541 on 2010-11-07
> **Untitled_No4 said:**
> If I understand you correctly you want one image to stretch to cover the whole page but without repeating the image?
If so, check out this link and check the page source to see how he's done it: [http://www.cssplay.co.uk/layouts/background.html](http://www.cssplay.co.uk/layouts/background.html)


Thanks this kinda worked but I am looking for a code that is simple.
I am trying to learn HTML, but I dont want to copy from other people's work.

---

### Post by sudoer541 on 2010-11-07
Ok, I made some more corrections

```
<style type="text/css">
body
{
background-image:url('gradient.jpg');
background-repeat:no-repeat;
}
</style>
```edit: now the background stopped repeating but its too small and it does not strech to cover the page:(
I tried to adjust the size by adding

```
height: 100
width:100 
```

---

### Post by Untitled_No4 on 2010-11-07
> **sudoer541 said:**
> Thanks this kinda worked but I am looking for a code that is simple.
I am trying to learn HTML, but I dont want to copy from other people's work.

If you're trying to stretch an image over the whole page then this is probably the easiest way to do it. 

CSS Play is made for people to learn from his experience. He's happy for you to copy it (on certain things he asks to ask his permission) and to learn from what he does. Also, looking at other people's work and see how they achieved it is one of the best ways of learning. This is part of the reason about the open source movement, allowing people to learn from one's code.

---

### Post by Untitled_No4 on 2010-11-07
> **sudoer541 said:**
> Ok, I made some more corrections

```
<style type="text/css">
body
{
background-image:url('gradient.jpg');
background-repeat:no-repeat;
}
</style>
```but the background still repeats:(

You first need to clean your code:

basic structure is:
<html>
   <head>
   </head>
   <body>
      CONTENT
   </body>
</html>

---

### Post by Untitled_No4 on 2010-11-07
> **sudoer541 said:**
> Ok, I made some more corrections

edit: now the background stopped repeating but its too small!
I tried to adjust the size by adding

```
height: 100
width:100 
```

1. height/width 100 doesn't mean anything in CSS. it's either 100px or 100% (or em, etc.).
2. Background image is a background image, it doesn't have height properties. Setting height and width to 100% on body would mean that the body itself will have height and width of 100%, not the background image.
3. When you set a body height  + width of 100%, the question is: 100% of what?
4. CSS = Cascading Style Sheets, meaning the styling of the parent element are inherited to the children elements.
5. So, back to 3, by setting body height and width to 100% you tell it to take the full size of its parent, which is html, which has no size, so neither does body.
6. So, you have to tell what is the size of your the html element. 100% means the size of the viewport:
```

html {width: 100%; height: 100%;}
body {width: 100%; height: 100%;} 

```

or, shorter:
```
html, body {width: 100%; height: 100%;}
```

Now your body will take the whole size of the viewport and you can test it by adding "background: red;" or something to body. The image above will not, since background-image does not have a height/width properties (well, it has in CSS3, but we're not there yet). So it can't be done.

So how is it done? by not using background-image property. If you looked at the code in CSS play you would see that the body does not have a background image. What he does have this:
```
<img id="background" src="rabbit.jpg" alt="" title="" />
```
which is a simple image tag. To stretch it all over the page he then added the following to his CSS:
```
#background{position:absolute; z-index:1; width:100%; height:100%;}

```
This will stretch the image over the full size of the viewport.

If you do all that it still won't be perfect because there are other things in his code, but I'm not going to go line by line and explain it... Just read his code, when you see a property you don't know (z-index, perhaps?) read about it online, understand why he added it and learn from his example.

FINALLY:
Your image name is gradient. I think you're really trying to complicate things a bit. Can you post your background image here? I think the solution is easier than you realise.

---

### Post by sudoer541 on 2010-11-07
here is the image

---

### Post by Untitled_No4 on 2010-11-07
> **sudoer541 said:**
> here is the image

With that image CSS Play's method would work the best.

---

### Post by sudoer541 on 2010-11-07
Ok, for now I am using a basic background (no image) and once I learn more I will start with CSS.

---

### Post by Untitled_No4 on 2010-11-08
It's really not that difficult and since I think one can learn a lot from inspecting other people's code, here it is:

index.html
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
  <head>
    <title>My first website</title>
  <link type="text/css" rel="stylesheet" href="style.css" />
  </head>
  <body> 
    <div>
      <img src="gradient.jpg" alt="Background Image" class="background" />
    </div>
    <div id="Container">
      Your content goes here.
    </div>
  </body>
</html>
```

2. style.css (to be in the same folder as index.html and background image)
```
html, body {
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
} 
.background {
  height: 100%;
  width: 100%;
  position: absolute;
  left: 0;
  top: 0;
  z-index: 1:
}
#Container {
  position: absolute;
  font-size: 20px;
  left: 0;
  top: 0;
  z-index: 2;
}
```

A few things to notice:
1. The separation of style from content is the idea behind CSS. If you use CSS you don't want to use elements like <font> in your content.
2. The separation of files is not important if the website has only one page, but it's better for anything else and better getting used to it now.
3. The CSS has some unnecessary style definitions (like setting top and left position on the background element), but they are there for a reason.
4. An HTML document should have one <head> element and one <body> element (you had three <body> elements in your codes). They should both nest in the <html> element with <body> coming after <head>.
5. Writing standard-compliant code will save you a lot of headache later, especially when it comes to IE. If you use Firefox install the HTML Validator extension. It will teach you a lot and will save you time. ([http://users.skynet.be/mgueury/mozilla/](http://users.skynet.be/mgueury/mozilla/))
This will also work better if you ask for help since it means that your code will probably be easier for people to read, so the more likely they are to help you.

The most important thing here, I think, is for you to learn and not just copy/paste. View the index file without the style file and see how it looks. Read about the styling properties you don't know about, what available options they have, etc. It's not that difficult once you know it...

---


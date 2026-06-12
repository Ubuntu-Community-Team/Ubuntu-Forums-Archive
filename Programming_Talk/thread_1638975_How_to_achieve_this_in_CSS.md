---
title: "How to achieve this in CSS?"
date: 2010-12-06
forum: Programming Talk
---

### Post by rcayea on 2010-12-06
How do I achieve the "outline" style in CSS as seen in the screen shot I have attached?

I want my font to have the hollowness as if you were selecting "outline" font in Openoffice. 

thanks!

---

### Post by Tony Flury on 2010-12-06
not convinced you can - it is all to do with fonts and although you can do things like bold, italics etc - you can't do effects like that.

---

### Post by rcayea on 2010-12-06
OK, thanks. I guess I will have to find a font to do what I want.

---

### Post by laceration on 2010-12-06
Web fonts are pretty limited.  You could make an image of the the text created in oo.

---

### Post by yeleek on 2010-12-06
Yes you can achieve an outline effect, what you may struggle with is the font you outline.  If its a specific font you want, i'd make an image and then use CSS to place it where you want.

If its any font and you aren't fussy - look at this for guide (no 13 - tho may not work with IE):

[http://www.1stwebdesigner.com/css/advanced-css-text-effects-web-typography-tips/](http://www.1stwebdesigner.com/css/advanced-css-text-effects-web-typography-tips/)

---

### Post by rcayea on 2010-12-06
Excellent! Thanks-a-bunch!

---

### Post by roccivic on 2010-12-06
The effect that you are looking for is possible by using CSS3.

Bear in mind the requirement for a very modern browser: Firefox 3.5+, Chrome 4.0+, Safari 4.0+, Opera 9.6+.
And the piece of junk that is IE does not support this at all.

Here's an example:

[HTML]<!DOCTYPE html>
<head>
    <title>Outline</title>
    <style>
    .hollow {
      position: absolute;
      top: 20px;
      left: 20px;
      color: white;
      font-size: 56px;
      font-family: serif;
      font-weight: bold;
      text-shadow: 0px 0px 1px #000000;
      filter: dropshadow(color=#000000, offx=0, offy=0);
    }
    </style>
</head>
<body>
    <div class="hollow">
    I LOVE LINUX
    </div>
    <div class="hollow">
    I LOVE LINUX
    </div>
</body></html>[/HTML]

For a thinker outline you can increase the blur radius and overlay the text a few extra times.

That said, I don't recommend that you actually do this for a production site.

Peace

---

### Post by Krupski on 2010-12-06
> **rcayea said:**
> How do I achieve the "outline" style in CSS as seen in the screen shot I have attached?

I want my font to have the hollowness as if you were selecting "outline" font in Openoffice. 

thanks!

One way that's supported by all browsers (even that POS Internet Explorer) is to *send the browser* an outline font.

Do this in your CSS:

```

@font-face {
    font-family:'outline';
    src: url('fontpath/outlinefont.eot');
    src: local('&#9786;'), url('fontpath/outlinefont.ttf') format('truetype');
    font-weight:normal;
    font-style:normal;
}

```

(be sure to keep the smiley face character - and read why here: **[COLOR="RoyalBlue"][http://paulirish.com/2009/bulletproof-font-face-implementation-syntax](http://paulirish.com/2009/bulletproof-font-face-implementation-syntax)[/COLOR]** )

Then, any text you want to be outlined, simply set it's style to "font-family: outline;" like this:

<span style="font-family: outline;">I LOVE LINUX!</span>

You take any of your TTF fonts you wish to use and also convert them to .EOT format (for MSIE arghhhhh!). 

A free online font converter is here: **[COLOR="RoyalBlue"][http://www.fontsquirrel.com/fontface/generator](http://www.fontsquirrel.com/fontface/generator)[/COLOR]**

Hope this helps.

-- Roger

---

### Post by rcayea on 2010-12-06
Fantastic help! let me go give this a try.

thank you much!

---


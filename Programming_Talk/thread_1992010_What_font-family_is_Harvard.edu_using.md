---
title: "What font-family is Harvard.edu using?"
date: 2012-05-31
forum: Programming Talk
---

### Post by emoguitarist06 on 2012-05-31
I would like to implement their font that they're using on their homepage on my website

(see link and picture attached)

[http://www.harvard.edu]("http://www.harvard.edu")

I checked out the source and man it's super advanced css for me LOL I'm extremely noob and so I can't understand it :(

Thanks for the help!

---

### Post by Simian Man on 2012-05-31
From using the chrome inspect element tool, it looks like: "font-family: Helvetica, Arial, sans-serif;"

---

### Post by ofnuts on 2012-05-31
> **emoguitarist06 said:**
> I would like to implement their font that they're using on their homepage on my website

(see link and picture attached)

[http://www.harvard.edu](http://www.harvard.edu)

I checked out the source and man it's super advanced css for me LOL I'm extremely noob and so I can't understand it :(

Thanks for the help!
From the style sheet and depending on what you have on your system, it's "Georgia" or "Times New Roman".

---

### Post by emoguitarist06 on 2012-05-31
> **Simian Man said:**
> From using the chrome inspect element tool, it looks like: "font-family: Helvetica, Arial, sans-serif;"

Inspect Element! Why didn't I think of that! I'm getting Helvetica,Arial,sans-serif as well in firefox

Thanks

---

### Post by Enigmapond on 2012-05-31
> **ofnuts said:**
> From the style sheet and depending on what you have on your system, it's "Georgia" or "Times New Roman".

Right the header is Georgia but if you don't have that installed on your system. it will show Times New Roman.

---

### Post by Lars Noodén on 2012-05-31
You're probably looking at the wrong element.  I haven't waded through the CSS, but Ofnuts is probably right because it is clearly a typeface with serifs.

---

### Post by emoguitarist06 on 2012-05-31
Actually I don't think we're right

The Harvard Logo and the Navigation are images and not text defined by CSS

[http://www.harvard.edu/sites/all/themes/hedu2011hc/a/titles/logo.gif]("http://www.harvard.edu/sites/all/themes/hedu2011hc/a/titles/logo.gif")
[http://www.harvard.edu/sites/all/themes/hedu2011hc/a/screen/main-nav.gif]("http://www.harvard.edu/sites/all/themes/hedu2011hc/a/screen/main-nav.gif")

---

### Post by Simian Man on 2012-05-31
Yeah you guys are right.  I got confused looking at it as the HTML actually has the text in there for the menu with the fonts.  I didn't notice the image too.  I guess they do so the site works without images.  I tried the site in elinks and it works well with the text.

I tried giving the logo image to whatthefont and it gave me these results: [1]("http://www.myfonts.com/fonts/canadatype/roma/bold/"), [2]("http://www.myfonts.com/fonts/mti/at-schneidler-mediaeval/atschneidler-mediaeval/"), [3]("http://www.myfonts.com/fonts/adobe/chaparral/regular/"), [4]("http://www.myfonts.com/fonts/mti/pompei/light-small-caps/"), [5]("http://www.myfonts.com/fonts/efscangraphic/congress-sb/light/").  4 looks the closest to me personally.

---

### Post by emoguitarist06 on 2012-05-31
> **Simian Man said:**
> Yeah you guys are right.  I got confused looking at it as the HTML actually has the text in there for the menu with the fonts.  I didn't notice the image too.  I guess they do so the site works without images.  I tried the site in elinks and it works well with the text.

I tried giving the logo image to whatthefont and it gave me these results: [1]("http://www.myfonts.com/fonts/canadatype/roma/bold/"), [2]("http://www.myfonts.com/fonts/mti/at-schneidler-mediaeval/atschneidler-mediaeval/"), [3]("http://www.myfonts.com/fonts/adobe/chaparral/regular/"), [4]("http://www.myfonts.com/fonts/mti/pompei/light-small-caps/"), [5]("http://www.myfonts.com/fonts/efscangraphic/congress-sb/light/").  4 looks the closest to me personally.

What an awesome resource! I'm definitely bookmarking whatthefont 
I think it's more like #2 personally but I submitted my own image now and getting more close results

Marking as solved as this is the closest we're probably getting :)

---

### Post by Bachstelze on 2012-05-31
It's Adobe Caslon. [http://www.myfonts.com/fonts/adobe/caslon/](http://www.myfonts.com/fonts/adobe/caslon/)

---


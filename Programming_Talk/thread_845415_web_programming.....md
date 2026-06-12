---
title: "web programming...."
date: 2008-06-30
forum: Programming Talk
---

### Post by hockey97 on 2008-06-30
Hi, ok I am making a website, I want to have my website be viewed in any display settings.

I am confused on how to go about making the website display friendly.

like if I made a website in 800x600 and someone had the display settings higher than that it would make the website look small and ugly. I am using css making exact positions otherwise I lose the control of the layout.

so if I want the layout that I made in 800x600 what should I do to still make that layout adjust to higher display settings??

I been thinking I know I can make layouts for each display settings I want to accept but it's alot of work and also takes up alot of memory.

The next thing I started to think was to using programming to detect the clients display settings and base off that I could edit the size and position of my elements on the website using css to adjust to the user's display settings.

or I can make a case switch so with the clients display settings stored in a variable I could then run css code I put.

The css code I put for each acceptable display settings I would have to first see how the layout looks with those css settings for individual display settings  so those values would go in the code that's if the user uses that certain display settings.

My question is how do you guys go about this?? like how do you make your website to be viewable in other display settings?

---

### Post by CptPicard on 2008-06-30
> **hockey97 said:**
> 
My question is how do you guys go about this?? like how do you make your website to be viewable in other display settings?

I appreciate your perseverance in bringing this topic back up even after experiencing catastrophic data loss, but the answer *still* is that what you're doing is sort of weird and people just use fluid CSS design techniques to make the single design be viewable on most screens.

---

### Post by LaRoza on 2008-06-30
> **hockey97 said:**
> 
My question is how do you guys go about this?? like how do you make your website to be viewable in other display settings?

"in other display settings" has several meanings here. For different displays, see:
[http://www.w3.org/TR/REC-CSS2/media.html](http://www.w3.org/TR/REC-CSS2/media.html)

For differen size displays, you have two options. Fluid CSS or user chosen style sheet (make more than one style sheet and allow the user to chose) or have a script measure the screen then apply a sheet for it.

---

### Post by skeeterbug on 2008-06-30
> **hockey97 said:**
> Hi, ok I am making a website, I want to have my website be viewed in any display settings.

I am confused on how to go about making the website display friendly.

like if I made a website in 800x600 and someone had the display settings higher than that it would make the website look small and ugly. I am using css making exact positions otherwise I lose the control of the layout.

so if I want the layout that I made in 800x600 what should I do to still make that layout adjust to higher display settings??

I been thinking I know I can make layouts for each display settings I want to accept but it's alot of work and also takes up alot of memory.

The next thing I started to think was to using programming to detect the clients display settings and base off that I could edit the size and position of my elements on the website using css to adjust to the user's display settings.

or I can make a case switch so with the clients display settings stored in a variable I could then run css code I put.

The css code I put for each acceptable display settings I would have to first see how the layout looks with those css settings for individual display settings  so those values would go in the code that's if the user uses that certain display settings.

My question is how do you guys go about this?? like how do you make your website to be viewable in other display settings?

If you make a site close to 800px wide for the content, it will not look any different. I am working on a new look for my companies website currently. [http://test.mission3.com/]("http://test.mission3.com/")

I have the main content set to 792px wide, height auto adjusts to content. I develop this in a 24 inch wide screen monitor, so I know for a fact it looks fine on high, wide screen resolutions. I also test it on the Mac Mini, with a little 14 inch monitor (looks great there too).

---


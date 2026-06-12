---
title: "Building a Website"
date: 2009-08-20
forum: Programming Talk
---

### Post by ArmenianLeader4 on 2009-08-20
Im working on this website, and I need to make sure that it's good enough for even you guys here on ubuntu forums. Tell me whats wrong, give me some code to fix, do whatever you please, just tell me what to fix and why, and I'll get to work.

Here's the site:
[http://r9films.com]("http://r9films.com/")

Go and critique!

---

### Post by .Maleficus. on 2009-08-20
Upon first glance...

1.  On every page (except the homepage) the red bar at the bottom is off center.
2.  The Reviews and Downloads pages will occasionally 404 on me, and not display your "Under Construction" page.
3.  The homepage background is not the same as the other backgrounds (it has 2 vertical black bars on the edges and the others don't).
4.  I don't know if you did this purposely or not, but the "send an email" line at the bottom of your pages don't have a "mailto:" link.
5.  Speaking of those bottom lines, they aren't the same on the homepage as they are on the other pages.  Different font/size.

That should get you started at least :).

---

### Post by ArmenianLeader4 on 2009-08-20
Thanks, thats what I needed. I don't see the same issues, however, which is strange, but I'll get them fixed.

---

### Post by ArmenianLeader4 on 2009-08-21
I fixed the 404-ing and the different background images. I dont see the problem with the red bar yet, but that may be because it hasnt updated for everyone yet. I dont want people to click to be able to mailto, it causes spam, and unless they really have something to say, i dont want to hear it. Also, what do you think of the content on the pages? is everything well written? is the slider on the home page easy to navigate with? are the downloads good? need more info, please! (bump)

---

### Post by haemulon on 2009-08-21
Looks good, however I  don't like "dark" websites, but that's just  a personal preference.

The navigation tabs on the sides of your panel are not immediately obvious to function as "next" and "back" buttons.

The red bar at the page bottoms looks off center here also.

---

### Post by Drone022 on 2009-08-21
I can see all your css code at the top of the page.

Close the tag thingy on this line (you missed the closing '>').
```
<meta http-equiv="Content-Style-Type" content="text/css"
```

---

### Post by smartbei on 2009-08-21
What browsers are you testing with? Here is a screenshot of what I see when I view your homepage.
[[IMG]http://img23.imageshack.us/img23/9531/screenshot1jhh.th.png[/IMG]](http://img23.imageshack.us/i/screenshot1jhh.png/)
Notice the red underline under the 'Home', 'Gallery', etc.?

As someone has said above - the next/previous buttons could be more intuitively designed. (for example, have a < symbol on the left button).

---

### Post by hessiess on 2009-08-21
Nice, dark websites are good:) though get rid of the `minimise, maximise, close' buttons, they don't do anything and just look silly, and there are a few errors in the html [http://validator.w3.org/check?uri=http%3A%2F%2Fr9films.com%2Fcs.html&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fr9films.com%2Fcs.html&charset=%28detect+automatically%29&doctype=Inline&group=0).

---

### Post by ArmenianLeader4 on 2009-08-21
Most of the errors on that link you gave were from alts being unspecified. I fixed most of them, and I removed the red bar entirely from the bottom of the page. I'll also fix those graphics for the 'next' tabs, and attempt to get my "gallery sorting tool" up and running by this sunday. Thanks for the help, everyone. Keep posting!

Oh, and I checked those errors, and most of them are just spaces inside the tags. like </div > instead of </div>. I don't have the time to sit around and fix such minuscule details like that, but that site does help. Thanks!

---

### Post by ArmenianLeader4 on 2009-08-21
By the way, does anyone have the CSS code for putting a background image only on the bottom section of a website? or do i need to <div> it off and add it that way? I just want to put a transparent .png image over the current image, but only on the bottom portion.

---

### Post by ArmenianLeader4 on 2009-08-21
bump on the post right above! ^

---

### Post by JordyD on 2009-08-21
The bottom red bar on all the pages isn't centered (others mentioned this). If you maximize the web browser, you get a centered bar, but if you resize your browser it goes off-center.

---

### Post by ArmenianLeader4 on 2009-08-22
Thanks for finding the problem.. I would have never guessed that was it. BTW, anyone know that CSS code??

---

### Post by Hendrixski on 2009-08-22
Very awesome! I was going to say "too much flash" but then I realized that my CPU fan wasn't going crazy and though "oh, this is javascript, awesome".

It's a little dark. I'm not a fan of black backgrounds on websites, reminds me of the early days of web 1.0 where everybody did that in geocities ... hell they still do it on myspace.  But that's just me.

Keep up the good work.

---

### Post by ArmenianLeader4 on 2009-08-22
I can lighten it up a bit! thanks, btw. Still bumping on that CSS code!! :O

---

### Post by Can+~ on 2009-08-23
The initial page looks ok, it has the navigation set up right, not that visible, but forgivable. I would drop the iframe because of resizing issues.

I notice that images are lossy JPGs. If you're creating Logos and working with low quantities of colour, you can use either PNG or GIF, otherwise, it looks pixelated (look at the borders of "R9").

Now I head to the gallery, to find that everything has changed, for the worse:

Gallery section:
[LIST=1]
[*]Navigations has been transferred to the bottom of the page. If the page gets bigger, I'll have to scroll to get there.
[*]Find an awful "windows titlebar-esque" with apparently interactive button, that actually don't do a thing. Looks confusing and doesn't add up.
[*]That red-to-white separator on the bottom has nothing to do there.
[*]"The Gallery" section has some serious trouble deciding what it should look like. The first row looks really different, and when clicked it expands? Not intuitive at all.
[*]I would drop the *border:* to "none" on pretty much everything on this section.
[*]Icons go from "pixel drawn" (good) to wrongly-resized (bad). If you want icons, go download some or draw them yourself, don't try to resize images to fit it in sizes less than 32, otherwise, it will look wrong.
[*]Links are hard to distinguish from normal text, besides everything being grey over black.
[/LIST]

Downloads Section: This one gets it's own header, why the gallery doesn't have one?

Links & Reviews: Not there, but still have that awful titlebar.

In other words: Find a style and stick to it.

---

### Post by staf0048 on 2009-08-23
I'm no CSS expert, but couldn't you use whatever background you wanted at the bottom of the page listed within the <body> tag.  Such as:

<body>
background: url(yourbackground.jpg) bottom;
</body>

And then create seperate <div>'s for the other images?

I like the site, wondering why there are 3 different ways to navigate through the same fields though.  If they're going to be used for different purposes in the future I like it, but I don't see a need for the "next" or "previous" links with the "left" and "right" available as well as the individual links.

However, I could see a use for the "next" and "previous" links if they're used to navigate to the next posting within the same heading.

Just my thoughts . . .

---

### Post by ArmenianLeader4 on 2009-08-24
thanks to Can+~ and staf, both of you guys gave me what i was looking for.. I am considering changing the gallery to a CSS image rotator-type layout with 10 posts per page, similar to this:
[http://www.sohtanaka.com/web-design/examples/image-rotator/](http://www.sohtanaka.com/web-design/examples/image-rotator/)

Also, I will get rid of those "windows" bars that everyone seems to loathe so much. (although its ripped from one of my linux screenshots) 
And I just brightened up the background as a whole. Hope that's better.
:P

---

### Post by ArmenianLeader4 on 2009-09-04
Alright, everybody, I re-created the homepage. It's a LOT better looking. But if you do decide to check it out, be sure to note that only the homepage is complete. So, take this bump as an opportunity to check out the new beta theme for this website. R9Films.com

---

### Post by Reiger on 2009-09-04
The home page:

- It is segmented. I think that's bad.
- The rounded corners don't actually work out because there isn't enough margin on the left/right side (there isn't any).
- The links on the menubar are not consistent: positioning and font-width of the Links & Downloads respectively are not consistent with the others.
- The fonts used in the various images aren't sharp and some characters are hence illegible/indistinguishable.

The downloads page:

- The margin's are off, meaning that the total area occupied by the text exceeds or equals that of its background, especially noticeable on the y-axis.
- The font used for the menubar isn't sharp.

The links/reviews pages:

-The width of the picture that something is yet under construction exceeds that of what appears a window title bar...
-Mimicking window title bars leads to a segmented look. Such bars are only appropriate for (scripted) dialogs which ordinary websites need none of.
- The red-white-red divider isn't centered properly
- Using digits for numbers, especially "distorted" digits appears a bit silly to me. It also reduces the accessibility of your site: people must make much more effort in determining whether this is "all you have to offer" or whether there is something else going on.

The gallery page:

- Backgrounds of pop-ups/slide-in elements are solid which breaks the look of the menubar & background image
- Fonts are again not sharp
- Images do not load
- "Image" is not a valid alt text. Imagine a visually impaired person using a screen reader going to your site being greeted by "Image". "Image". "Image". ad nauseam?

---

### Post by socool274 on 2009-09-04
I'm not criticizing at all, and I couldn't possibly make a site as good as yours, but for me, it would be nice if all the pages had the same type of theme.

---

### Post by Mirge on 2009-09-04
Well he said only the home page was complete.

I think the quality of the graphics isn't high enough, and I see tiny whitespace gaps on the rounded-corners.

---

### Post by Kristofer Van Orton on 2009-09-04
from expirence its best to download popular web browsers
ex. opera firefox internet explorer safari ect.
and test them yourself
well that is if you have access to windows as a lot of them dont run on linux
anyway
i like the design
im not sure about the background i think it would look better a bit more solid
but thats just my opinion
good work :D

btw are you using photoshop?

---

### Post by Can+~ on 2009-09-04
Is a step forward, but there are many weird things about it.

First, start looking at good design:

[http://www.smashingmagazine.com/2006/12/19/50-beautiful-css-based-web-designs-in-2006/](http://www.smashingmagazine.com/2006/12/19/50-beautiful-css-based-web-designs-in-2006/)

Smashing magazine (don't want to sound like spam) has some nice collection of examples and material (free icons, fonts, CSS tricks, etc).

Here's one site I made:
[http://img.photobucket.com/albums/v517/CanXp/sample.png](http://img.photobucket.com/albums/v517/CanXp/sample.png)

And if you want a simple, repetitive border, have this thing I made:

---

### Post by -grubby on 2009-09-04
I've only checked out the home page, but here goes nothing:

[list=1]
[*] The background is too busy
[*] I'm using Chromium, and the "9" in "R9" overlaps parts of the page it shouldn't be (such as over the text)
[*] I don't think the navigation link hover has enough padding
[/list]

---

### Post by Gen2ly on 2009-09-04
Have to aggree with -grubby's #1.  The background grabs alot of attention.  When it first loaded it was just a white background which I thought fit better with the current theme.

---

### Post by ArmenianLeader4 on 2009-09-04
> **Reiger said:**
> The home page:

- It is segmented. I think that's bad.
- The rounded corners don't actually work out because there isn't enough margin on the left/right side (there isn't any).
- The links on the menubar are not consistent: positioning and font-width of the Links & Downloads respectively are not consistent with the others.
- The fonts used in the various images aren't sharp and some characters are hence illegible/indistinguishable.

The downloads page:

- The margin's are off, meaning that the total area occupied by the text exceeds or equals that of its background, especially noticeable on the y-axis.
- The font used for the menubar isn't sharp.

The links/reviews pages:

-The width of the picture that something is yet under construction exceeds that of what appears a window title bar...
-Mimicking window title bars leads to a segmented look. Such bars are only appropriate for (scripted) dialogs which ordinary websites need none of.
- The red-white-red divider isn't centered properly
- Using digits for numbers, especially "distorted" digits appears a bit silly to me. It also reduces the accessibility of your site: people must make much more effort in determining whether this is "all you have to offer" or whether there is something else going on.

The gallery page:

- Backgrounds of pop-ups/slide-in elements are solid which breaks the look of the menubar & background image
- Fonts are again not sharp
- Images do not load
- "Image" is not a valid alt text. Imagine a visually impaired person using a screen reader going to your site being greeted by "Image". "Image". "Image". ad nauseam?


As I had previously stated, I do NOT want criticism on any other page BESIDES the home page, because those pages are NOT complete.

---

### Post by ArmenianLeader4 on 2009-09-04
If anyone had cared to read the content posted on the page, I am hosting a "background image entry contest" because I know that the background is way too busy. That contest will be up by tonight, and hopefully so will the gallery, downloads, and submit pages.

And, no. I am not using photshop. I have used photoshop, and I prefer GIMP.

---

### Post by ArmenianLeader4 on 2009-09-07
Bump. The background image entry contest is up, and so is some of the gallery.

[http://r9films.com]("http://r9films.com/")

---

### Post by TheBuzzSaw on 2009-09-07
What was the site built in? The HTML underneath is incredibly archaic (HTML4, all caps tags, table-based layout, etc.).

---

### Post by TheBuzzSaw on 2009-09-07
(site lag)

---

### Post by TheBuzzSaw on 2009-09-07
(site lag)

---

### Post by ArmenianLeader4 on 2009-09-12
Bump. Updates are here!

---


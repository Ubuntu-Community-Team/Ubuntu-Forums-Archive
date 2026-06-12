---
title: "&quot;Great&quot; XHTML and CSS"
date: 2009-06-12
forum: Programming Talk
---

### Post by SuperMike on 2009-06-12
Although I have my own idea of this, but does anyone here have a picky opinion on what they think exemplifies "great" XHTML and CSS? Your help just might help me catch a lucrative project in this bad economy -- something has come up for me. Your help is greatly appreciated.

---

### Post by soltanis on 2009-06-13
I fail to understand. Do you want a website that uses "great" XHTML/CSS? Or do you want "great" XHTML/CSS design patterns? Or what?

---

### Post by hessiess on 2009-06-13
Just don't use tables for layout and make sure that the layout dousen't break if the user increases the text size.

---

### Post by noerrorsfound on 2009-06-14
Be sure to [separate content from presentation]("http://en.wikipedia.org/wiki/Separation%20of%20presentation%20and%20content").

---

### Post by SuperMike on 2009-06-14
> **soltanis said:**
> I fail to understand. Do you want a website that uses "great" XHTML/CSS? Or do you want "great" XHTML/CSS design patterns? Or what?

I've got a monstrously great project opp. The catch is that they want me only for front-end work because they already have a PHP dev., a Java dev, and a C# dev. (Their backend is nuts.)

They said they want to hire someone who can do great XHTML and CSS, and they are mostly interested in viewing the source of what I've done, not necessarily any designs, and they aren't interested in any PHP work I've done.

They also want to see my jQuery and AJAX work, but I've already got a sample ready on that.

I've already got some ideas on what XHTML and CSS things they might want to see to consider it the best that it could be. However, I'm interested in seeing what you all have to say so that I could ensure I don't miss anything.

---

### Post by tturrisi on 2009-06-14
> **SuperMike said:**
> I've already got some ideas on what XHTML and CSS things they might want to see to consider it the best that it could be. However, I'm interested in seeing what you all have to say so that I could ensure I don't miss anything.
Just show 'em what they want to see, examples of previous work.  Show 'em html, xhtmk & css.

There's no definitive answer to "what is great xhtml/css?"

But there are coding standards and coding styles that set one group of code from another.

For example, if use css ids & classes, use simple non-confusing names.  Use <div id="header">, <div id="footer"> don't use <div id="top-of-page"> & <div id="bottom-of-page">.

Don't name ids and classes with "illegal names". For example, don't do <span class="onload">, which will actually work as a style, but best to keep the name "onload" reserved for scripting.

Code in such a way that if any other coder reads it they will instantly understand your namings.

Get the idea that when holding such a job that your work represents a hat (a job title), not personal stuff.  Thus your replacement, senior, junior or others can view your code & instantly grok it, and/or easily integrate it with no changes to backend code.

---

### Post by markux^Hs on 2009-06-14
Standards                                       compliant.

---

### Post by SuperMike on 2009-06-14
Here's what I believe so far by guessing:

- As for a page theme, I don't think by this specification that they would really care much except to see use of 2 column and 3 column formats. They probably want a page that would look like the Wall Street Journal page, but far less "busy". When they are interested in looking at your XHTML and CSS, and don't look at your design skills, they want to really focus just on the XHTML and CSS.

- An understanding of advertising -- such as some selling point or major news item in the "foldspace" (the space above 600px) on the homepage, and space for ads in appropriate places like the sidebar or end of an article.

- Articles having buttons for text size, print view, social bookmarking, email/share with a friend, and perhaps comments. They don't necessarily have to work since this is XHTML/CSS, but shows an understanding of the need for this.

- They want to see XHTML Strict, right? Not XHTML Transitional? And then having that validate 100%.

- It's obvious they want to see mostly DIVs unless I'm displaying grid-type data where a TABLE tag would do.

- They want to see tidy indenting, such as run through some kind of tidy script, and using tabs instead of spaces.

- No inline styles.

- Use of :hover, :active, and :visited.

- Callouts on article text. Is that what you call them? That's where you put some quote in bold and in a separate section on the page with text wrapping around it.

- Good use of stylesheets. I start with a good reset.css. Then, my strategy is to use a default CSS that handles all browsers and is geared for FF 2 and 3. Then, I load a smaller override set of 3 for IE6, IE7, and IE8 to override the default CSS, and using conditional comments. And since Opera and Safari/Chrome do not support conditional comments, using CSS Hacks to delineate Opera and Safari/Chrome -- but used extremely sparingly, or perhaps not at all. (Often I find if a page validates in FF 2 and 3, it often works in Opera and Safari/Chrome -- but not 100%.) Now you may think you're cool and only use one CSS file and think all browsers will work great with that, but I disagree. Go take a look at many top news sites out there and you'll see they use multiple CSS files -- one master and then a handful of override CSS's depending on browser type.

- Good use of CSS selectors such that not everything needs an ID or class applied to it.

- Classes on similar DIVs unless I can apply an ID on the container DIV and use CSS selectors to reach the children.

- Using classes only where applicable because they put more processor and memory overhead than an ID tag would.

- Using the IE6 trick to make containers containing floats to expand to the size of the floated contents inside, and yet also work in other browsers too.

- Shows use of floats and relative positioning.

- Avoiding occasionally risky absolute positioning except where necessary, and using relative positioning if necessary at all.

- Using a centered 960px #body DIV and use the HTML {overflow-y:scroll;} technique for FF to remove "page wiggle" for that format.

- Uses a CSS tidy program.

- Optimizes the CSS down to the minimum necessary so that I don't have too many IDs and classes and use base classes and inheritance that overrides those classes.

- Uses font sizing with 'em' instead of pixels or points. (That one I think is controversial to me. I mean, I prefer points because then I don't have to do 1.5em, 2.7em, etc., and instead I do 12pt, 14pt, 18pt -- matching more what you might see with a word processor. But for some reason the rest of the web world likes em's? I still don't get it.)

- Doesn't include comments -- reduces page load speed.

- Of course, some people like to minify the CSS and the XHTML, but then that doesn't demonstrate how organized you are, and makes it a nightmare to debug. So, for busy environments, minifying CSS and XHTML is no longer the norm in my opinion.

- CSS in a separate file.

- Defines CSS for different media -- what a pain, but necessary. For instance, makes the screen CSS in one format, and the print in another format. And if you're really hip, you may even have a mobile CSS.

- Uses an XHTML/CSS that degrades nicely across browsers.

- Doesn't use blank GIFs for spacers.

- Was designed by hand in a product like Dreamweaver or other good tool. Doesn't use something like FrontPage or other WYSIWYG editor.

- Doesn't just get a template from the web and customize it -- understands completely how to make an XHTML page from scratch along with its various CSS files.

- Works across various browsers even if you increase or decrease the font size with CTRL+Plus and CTRL+Minus.


Now what I don't understand is why so many sites use UL/LI without using DIVs, and even when they are turning off bullets on those elements. Is it to save keystrokes and make the page load faster? Is it because it might stack better? I have like no clue. I mean, if bullets are not necessary, then to me it seems more logical to use DIVs.

---

### Post by tturrisi on 2009-06-14
> - Doesn't include comments -- reduces page load speed.
Has no bearing on page load, comments are ignored by the browser so it in essence sees the start of a comment & skips to the end.  Try it. Paste a 5 page word doc in between comment tags and see if you can tell the difference in page loading.

Commenst are important and should be used, especially if working with other developers.

---

### Post by SuperMike on 2009-06-14
The way the HTML protocol works, it loads the XHTML page, sees the separate CSS file link, and downloads it. Once downloaded into the browser cache, it processes it. The larger that file is, the slower it is before it can process it. Sure, it might skip it fast after downloading it, but that initial download is the problem. Most browsers might only show a fraction of a slowdown because of how efficient they are, but when you have a large page doing a lot of things, and several other CSS files, you need every fraction of a second that you can get. Fractions of seconds add up. They also increase your bandwidth bill for the website ever so slightly.

---

### Post by carstenbn on 2009-06-17
Always validate, keep content and presentation seperate and make sure to optimize. Do what you can to make the (X)HTML as human-readable as possible, and the CSS file as optimized and clean/small as possible.

---

### Post by Reiger on 2009-06-17
Great XHTML and CSS makes it entirely clear where a particular change goes without fear of mucking things up. Sure, your layout and styles and whatnot may be awesome; and [by awesome I mean totally sweet]("http://www.realultimatepower.net/index4.htm") - but that doesn't count a bit when you want to edit the page contents (nevermind now the idea to automatically generate content and insert it where needed) and get out of the XHTML/CSS as fast as you can without fear of breaking anything.

So the bits that are most likely to change should -in order to be changed easily- require the least amount of code and most importantly: the least complex code. Which means to me that something like:

```

<div id="someMagicCSSIdentifier">
<h1 class="articleheader">Bad code</h1><br />
<p class="example of bad code">This is an example of how not to do it</p>
<p class="example of bad code">Imagine the fun manually updating it</p>
<p class="example of bad code">Each time you want to type a paragraph</p>
<p class="example of bad code">You could figure out a Kafka book easily.</p>
</div>

```

Is pure horror.

---

### Post by Mirge on 2009-06-17
> **tturrisi said:**
> Has no bearing on page load, comments are ignored by the browser so it in essence sees the start of a comment & skips to the end.  Try it. Paste a 5 page word doc in between comment tags and see if you can tell the difference in page loading.

Commenst are important and should be used, especially if working with other developers.

As SuperMike mentioned, inserting a TON of comments *will* cause a slower page load, due to the fact that whether the browser ignores it or not, it's still having to download the document in the first place. Unfortunately, dial-up is still around :(.

---

### Post by Jekshadow on 2009-06-17
[LIST]
[*]Follow the specification to the character.
[*]Do not use tables for page layout!
[*]Test it in at least 3 browsers (Internet Explorer, Firefox, Opera).
[*]Make sure that it looks good in all the browsers.
[*]Do not use too many images, as too many images can lag up page load. (Not XHTML, but if you want happy visitors to your site, make it load quickly)
[/LIST]

---

### Post by Frak on 2009-06-17
1. Don't use Tables for layouts, only for tables, hence the name.
2. Make sure it is FULLY accessible and FULLY complies to the WCAG
3. Appended to 2, make sure that text can be changed in size and not hinder the interface
4. Works in all browsers, and contains the appropriate stylesheets for IE6
5. Remember to place ALL of your javascript at the BOTTOM of the page. Javascript is not (and according to #2, should not be) required, so it is the least important part of the page to load.
6. Don't use GIF, ever. Use JPEG for images with many colors, and PNG for images either low in color, or require transparency.
7. Stray away from dirty hacks to get things done (like Microsofts implementation of an engine for IE6 to display PNG's correctly. Instead, use something like [Unit PNG fix]("http://unitinteractive.com/labs/unitpngfix.php").)
8. While specifications are great, use them sparingly for bug checking. In the business world, I haven't come accross a client yet that cared about the W3C test results as long as the page displayed fine on all popular browsers, lived up to its accessibility needs, and was able to be modified for the users pleasure. What I'm saying here is: **Web Standards mean jack in the industry.**

---

### Post by SuperMike on 2009-06-17
> **Frak said:**
> 2. Make sure it is FULLY accessible and FULLY complies to the WCAG

5. Remember to place ALL of your javascript at the BOTTOM of the page. Javascript is not (and according to #2, should not be) required, so it is the least important part of the page to load.


2: Man, that's a hard thing to pull off, especially in this day and age with jQuery all over the websites. It's like you have to build a special page in your sitemap that duplicates the functionality in a clumsy but effective WCAG way for anything you are doing with jQuery. For instance, imagine using a jQuery Carousel image doodad. Those with handicaps may not be able to easily get around with it. You may have to create a link on the page to let the handicap person to see all the images in one big screen of thumbnails and then let them choose the one they want.


5: The bottom thing is nice, but I see a problem with it. For one, you end up with slow Javascript. For instance, let's say you have suckerfish menus on the page. Someone may load your page and try to hover over them before the Javascript has finished loading, and thus not be able to get around on your site until that's finished. So, for me, I disagree -- load jQuery from the page head section, [COLOR="Red"]load Javascript at the end of the page as a guideline, not the rule,[/COLOR] and load any Javascript early in the page (like in the page head section) for anything that needs to load super fast or the site becomes less functional, such as with menus.

---

### Post by Mirge on 2009-06-17
> **SuperMike said:**
> 2: Man, that's a hard thing to pull off, especially in this day and age with jQuery all over the websites. It's like you have to build a special page in your sitemap that duplicates the functionality in a clumsy but effective WCAG way for anything you are doing with jQuery. For instance, imagine using a jQuery Carousel image doodad. Those with handicaps may not be able to easily get around with it. You may have to create a link on the page to let the handicap person to see all the images in one big screen of thumbnails and then let them choose the one they want.


5: The bottom thing is nice, but I see a problem with it. For one, you end up with slow Javascript. For instance, let's say you have suckerfish menus on the page. Someone may load your page and try to hover over them before the Javascript has finished loading, and thus not be able to get around on your site until that's finished. So, for me, I disagree -- load jQuery from the page head section, [COLOR=Red]load Javascript at the end of the page as a guideline, not the rule,[/COLOR] and load any Javascript early in the page (like in the page head section) for anything that needs to load super fast or the site becomes less functional, such as with menus.

Glad to see another jQuery user! Long live jQuery!

---

### Post by Reiger on 2009-06-18
> **Frak said:**
> 
4. Works in all browsers, and contains the appropriate stylesheets for IE6


> 
8. While specifications are great, use them sparingly for bug checking. In the business world, I haven't come accross a client yet that cared about the W3C test results as long as the page displayed fine on all popular browsers, lived up to its accessibility needs, and was able to be modified for the users pleasure. What I'm saying here is: **Web Standards mean jack in the industry.**

I would be slightly more careful. Make sure your code conforms to the standards without so much as a warning from the validator and you will find that (#4) becomes a lot easier. There are other browsers on this world besides MSIE 6, 7 and 8; most (all?) of them try their best to implement *those very same standards you code towards*. So if you want to support Safari [Webkit], Chrome [Webkit], Arora [Webkit], Epiphany [Webkit], Iceweasel [Gecko], Firefox [Gecko], Opera [Presto], Flock [Gecko] etc. in one go: standards compliant code is your best bet. 

[SIZE="1"]And web standards (as are any standards) are important enough for companies like Google, Opera, SUN (now Oracle) etc. to spend money on by letting their employees spend time and effort on those. :p[/SIZE]

---

### Post by SuperMike on 2009-06-18
Here were some of the interview questions I recall for this project I was trying to join:

1. Do you know what the box model is in regards to browsers?

{I had heard this, but bombed it. I then asked if he could provide a hint and I would be able to explain. He then started talking about padding, margins, and borders, and I said, oh -- margins add space on the outside of a box, padding on the inside, and borders on the outside.}

2. What does quirks mode mean?

{I said I didn't know exactly, but thought it meant a state in IE where it defaults to HTML 4?}

3. Why might I use a DOCTYPE?

4. Describe some features of XSL.

{This hit me from left field because I didn't know the job required use of it. However, I used it back in 2001 only briefly, so I said that and said it might take me a couple days to relearn it. I said in general it's a template language to convert something from one data format like XML into another format like XHTML.}

5. What are some ways you know of to reduce page load speed?

6. Why might I use or not use sprites?

{I bombed this one because I told him I had only read this one 2 days ago and knew it had something to do with images, but had forgotten what else was interesting about it.}

7. What kinds of addons do you use to help debug a XHTML, CSS, or Javascript? (And after I mentioned my answer -- ) Any tools besides YSlow or Firebug?

8. How may I handle people with a disability with my website?

9. What kinds of reasons are there why I might put an image in my CSS versus in the XTHML?

10. When might I need to minify my CSS?

11. Describe some levels of minifying CSS.

12. Why might I use multiple CSS files as opposed to one or two?

13. Why might I use an ID versus a class on an XHTML element?

14. Describe some differences between HTML 4.01 Transitional and XHTML 1.0 Transitional.

15. Describe some differences between XHTML 1.0 Transitional and XHTML 1.0 Strict.

16. With jQuery, how might I handle like a click on an image if I wanted that?

17. Why might I use onclick versus, say, jQuery to handle it?

{I gave him a couple answers on this and said basically it depends on what you're trying to do. I don't know if he liked that answer or not.}

18. Name some WCAG 1.0 or 2.0 guidelines you know.

{Luckily I had studied this the night before based on your recommendations, guys. I also had the screen open on my page.}

19. In Javascript, what is a prototype?

{I told him that all I could think was that it was Javascript's way of making a kind of class, but admitted that with jQuery I am abstracted from having to deal with this and mostly I just deal with jQuery. I don't know if he liked that answer or not.}

20. Are you aware of how many connections a browser can open back to the web server at a time?

21. Do you know what a reset.css is? (And when I answered, he asked --) Why is it a good idea to use it?

22. How do you declare font sizes in your XHTML?

{I told him to take a reset.css and set font sizes to 62.5%, and then inside the page use ems, with 1em being roughly 10px, and then use a chart for every other point size I might want. He said that was an excellent answer -- that's what they use.}

23. Why use ems versus points or pixels?

{I told him about the IE problem with points and pixels, and why ems is better, although points is more developer friendly because then you don't have to use like decimal places on describing your sizes. So, 100%, I use ems now but when the day comes when we can use points, I plan to do so. The problem is IE.}

24. Do you know what I might mean when I say "table-less" XHTML? (And when I answered, he asked --) When might I use tables in XHTML?

25. What does eval() mean in Javascript?

26. Is it okay to use eval() in Javascript?

27. How do I access the nth character of a string in Javascript?

28. How do I see if a string contains another string in Javascript?

29. With CSS, how do you make a container of floats expand to the size of floats inside, and work cross-browser starting with any of the top 6 browsers since the launch of IE6?

30. With CSS, how might I use absolute positioning on an item inside something so that it goes by those inner bounds and not the bounds of the page?

---

### Post by Frak on 2009-06-18
> **SuperMike said:**
> 
1. Do you know what the box model is in regards to browsers?

Every element is a rectangular box. Remember your Geometry class when every square was a rectangle but not all rectangles are a square. It's just the relationship between Margins, Borders, Height, Width, and padding.

> **SuperMike said:**
> 
3. Why might I use a DOCTYPE?

For easier debugging and correct rendering across browsers. Browsers use the doctype to determine the correct method of laying out a page.

> **SuperMike said:**
> 
5. What are some ways you know of to reduce page load speed?

Use sprites, and tell the server admin to flip the file compression switch on (all modern browsers support gzip, and even if they don't, apache will accommodate them.)

> **SuperMike said:**
> 
6. Why might I use or not use sprites?

If you were to place one all the images in one file, you would then be able to make a single request from the server and cache the image on the clients end. You would then be able to call upon the coordinates of the images within the larger sprite. This way you could satisfy the needs of the entire site with one image, saving the user and the server valuable bandwidth. Ask and Google do this.


> **SuperMike said:**
> 7. What kinds of addons do you use to help debug a XHTML, CSS, or Javascript? (And after I mentioned my answer -- ) Any tools besides YSlow or Firebug?


I use the [Web Developer Toolbar]("https://addons.mozilla.org/en-US/firefox/addon/60").

> **SuperMike said:**
> 
8. How may I handle people with a disability with my website?


Make sure you append the correct noscript section to a page to make sure that people without JavaScript or those that use screenreaders are able to view the equivalent information between them.

> **SuperMike said:**
> 
9. What kinds of reasons are there why I might put an image in my CSS versus in the XTHML?


I honestly don't know other than it feels smoother. Besides that, images in XHTML are more equivalent to objects while in CSS are more like scenery providing a more fine tuned flow.

> **SuperMike said:**
> 
10. When might I need to minify my CSS?


You're using a single CSS script to supply your entire website. Using just one is NOT a bad thing. You can cache it via a single HTTP GET request.

> **SuperMike said:**
> 
12. Why might I use multiple CSS files as opposed to one or two?


Your visitors aren't guaranteed to visit every part of your site. You may want to separate some heavy parts away from each other to ensure bandwidth savings.


> **SuperMike said:**
> 
18. Name some WCAG 1.0 or 2.0 guidelines you know.

{Luckily I had studied this the night before based on your recommendations, guys. I also had the screen open on my page.}


*applauds*

> **SuperMike said:**
> 
20. Are you aware of how many connections a browser can open back to the web server at a time?


Around 2 on most browsers.

> **SuperMike said:**
> 
21. Do you know what a reset.css is? (And when I answered, he asked --) Why is it a good idea to use it?


To ensure consistent results cross-browser. Browsers can set their own css-defaults, but designs never always follow those trends. Therefore, it is your job to reset all of the CSS tags to mold them to your liking.

> **SuperMike said:**
> 
23. Why use ems versus points or pixels?


More than anything, it's accessibility. Disabled people will set a large font so they can see. If the font is set to pixels, it will override this for the user, but using an em, the page will set the font size according to the already default font size on the users computer. If their font size is 26px, then 1.5 ems will increase it to 39px.

> **SuperMike said:**
> 24. Do you know what I might mean when I say "table-less" XHTML? (And when I answered, he asked --) When might I use tables in XHTML?

Yes, and only when you need to display data in a table form, such as an order form with different choices of packages.

I just answered a random choice of questions, but I thought you may like my input on it. Maybe not, but it's my 2c anyhow.

---

### Post by tturrisi on 2009-06-18
> **Mirge said:**
> As SuperMike mentioned, inserting a TON of comments *will* cause a slower page load, due to the fact that whether the browser ignores it or not, it's still having to download the document in the first place. Unfortunately, dial-up is still around :(.

I beg to differ.  yes, dialup is still around, but the majority of the world now uses some type of broadband.  And even for dialup users, the initial css file download gets cached so that subsequent pages on the same site that call the same css files will now load extraordinarily faster. 

Even a "large" css file can be a only a few kilobytes in size. (20-50 kilobytes)

It is far better to offload the processing of css files and some scripting to the client system, which in most cases, will process the css or script faster than any server will process it.  Today's browsers and cpus can handle it.

If anyone can really honestly see a detectable difference in page load time by adding comments to a larger css file, and/or html comments, then that person needs to upgrade their system to at least a celeron 300!

I run various systems, from a 333 celeron Debian server to dual cores, and I can't see any difference in page load times due to large css files or code comments.

The common thing across all systems that causes page load delays is caused by streamed ads from other domains, esp if have 3rd party cookies blocked.  The other common slow is caused by database queries, such as at this ubuntu forums site sometimes.

---

### Post by PC-XT on 2009-06-18
> Now what I don't understand is why so many sites use UL/LI without using DIVs, and even when they are turning off bullets on those elements. Is it to save keystrokes and make the page load faster? Is it because it might stack better? I have like no clue. I mean, if bullets are not necessary, then to me it seems more logical to use DIVs.
I feel the same way about divs vs lists with menus and such, because it seems to work better for me in practice, but theroetically, since menus are basically lists, and presentation should be separate, list tags are generally used.

---

### Post by Mirge on 2009-06-18
> **tturrisi said:**
> I beg to differ.  yes, dialup is still around, but the majority of the world now uses some type of broadband.  And even for dialup users, the initial css file download gets cached so that subsequent pages on the same site that call the same css files will now load extraordinarily faster. 

Even a "large" css file can be a only a few kilobytes in size. (20-50 kilobytes)

It is far better to offload the processing of css files and some scripting to the client system, which in most cases, will process the css or script faster than any server will process it.  Today's browsers and cpus can handle it.

If anyone can really honestly see a detectable difference in page load time by adding comments to a larger css file, and/or html comments, then that person needs to upgrade their system to at least a celeron 300!

I run various systems, from a 333 celeron Debian server to dual cores, and I can't see any difference in page load times due to large css files or code comments.

The common thing across all systems that causes page load delays is caused by streamed ads from other domains, esp if have 3rd party cookies blocked.  The other common slow is caused by database queries, such as at this ubuntu forums site sometimes.

I agree @ CSS comments. I was referring to HTML comments. I never really had a need to insert HTML comments... I didn't really like "explaining" what I was trying to accomplish when it came to static HTML content. If I was generating content on the fly using something like PHP, I'd write my comments in PHP. Less to download for a user, and less bandwidth used up on my dedicated servers.

And while I wish I controlled what people used to view sites, I can't. I have to make sites as accessible and speedy as possible in most cases.

---

### Post by SuperMike on 2009-06-18
I agree, if PHP, then make the comments in PHP and not in your HTML. However, if you use a link technique to load a CSS, then comments obviously make sense occasionally in them, and they would get cached because the file is downloaded, but obviously if you have thousands of connections an hour, and all those are downloading that CSS file with added bytes for those comments, then yes, you'd be looking at a slightly larger bandwidth bill because of it.

---

### Post by Frak on 2009-06-18
> **SuperMike said:**
> Now what I don't understand is why so many sites use UL/LI without using DIVs, and even when they are turning off bullets on those elements. Is it to save keystrokes and make the page load faster? Is it because it might stack better? I have like no clue. I mean, if bullets are not necessary, then to me it seems more logical to use DIVs.

It's best practice to use as few DIVs as possible. In your first mockup, you will most likely have more DIVs than necessary. My design is not done until I have removed every possible DIV that can be replaced with either modifying an existing div, or styling the class itself. Loading DIVs increases loading time and can make the page feel slower on some computers. Always design for the oldest, slowest computer still operating with a modern Operating System. I don't want to hear the "Well, modern processors can, blah, blah, blah". It doesn't matter. There are computers out there that are being used to browse the web, and it is only right to make a website that can be viewed relatively easily by these people.

---

### Post by SuperMike on 2009-06-18
> It's best practice to use as few DIVs as possible.

Yeah, that's something that needs to be said. I mean, DIVs are necessary, but use the least of them as possible to make the XHTML or HTML lean and mean. One thing I learned bad about the Blueprint CSS system as that it added too many DIVs. Eventually I didn't need that framework anymore and could do far better on my own and with less DIVs.

---

### Post by tturrisi on 2009-06-19
> **Mirge said:**
> I agree @ CSS comments. I was referring to HTML comments. I never really had a need to insert HTML comments... I didn't really like "explaining" what I was trying to accomplish when it came to static HTML content. If I was generating content on the fly using something like PHP, I'd write my comments in PHP. Less to download for a user, and less bandwidth used up on my dedicated servers.

And while I wish I controlled what people used to view sites, I can't. I have to make sites as accessible and speedy as possible in most cases.
Agreed.
Comments should be in php for script generated html. I still comment html as needed though as I don't believe it slows page rendering in today's computers and browsers.

As for bandwidth, most hosting packages now give a generous amount of monthly bandwidth.  I have yet to exceed the allocation at any of the sites I've done and manage.  Of course, none of these sites get facebook quantities of traffic!

---

### Post by tturrisi on 2009-06-19
re Divs:

My standard practice is to use minimal divs.  I generally split the page into sections, such as header, left, middle, right, footer.  I use ids for each section and eliminate classes.  I now only use classes for speciialized stuff like <spans>.

example:

```

css:
#header {
width:100%;
height:160px;
margin:0px;
padding:0px;
text-align:center;
background-position:top left;
background-image:url('images/header_bg.gif');
background-repeat:repeat;
background-color:#404040;}

#header p {
margin:0px auto 0px auto;
padding:0px;
text-align:center;
background-color:transparent;}

html:
<div id="header">
<p>some text</p>
</div>

```

Using this type of css: #header p { xxxxx;}
eliminates the need to use class="" in the html
which in turn makes it faster and easier to code php generated html or other script generated html.  No more troubleshooting unescaped quotes, etc., and above all else, it's less typing!

---

### Post by Mirge on 2009-06-19
> **tturrisi said:**
> Agreed.
Comments should be in php for script generated html. I still comment html as needed though as I don't believe it slows page rendering in today's computers and browsers.

As for bandwidth, most hosting packages now give a generous amount of monthly bandwidth.  I have yet to exceed the allocation at any of the sites I've done and manage.  Of course, none of these sites get facebook quantities of traffic!

Going off-topic for just a second, WTF is up with Facebook lately? All kinds of "Still ironing out the kinks" or whatever pages. I'm trying to get my Mafia Wars fix dang it!!:lolflag:

---

### Post by mynameinc on 2009-06-19
Make sure your code is 
[haiku compliant]("http://xkcd.com/554/") before you
make any websites.

---

### Post by PC-XT on 2009-07-02
Also, mobile devices can usually navigate menus better if they are lists rather than divs. Numbered lists often have shortcut (access) keys. If someone may ever need to access the site via cellphone or other smallscreen, when away from a working computer, this is something to consider.

> **SuperMike said:**
> DIVs are necessary, but use the least of them as possible to make the XHTML or HTML lean and mean. One thing I learned bad about the Blueprint CSS system as that it added too many DIVs. Eventually I didn't need that framework anymore and could do far better on my own and with less DIVs.

I find that many HTML tools I have worked with use too many DIVs. However, I haven't worked with any for a while because of this and other reasons, so the newer ones are probably better (hopefully). I find text editors are almost as good and more portable. (The best editors for me are just code highlighting text editors.)

---


---
title: "Opera is NOT IE! (A Javascript question)"
date: 2006-06-22
forum: Programming Talk
---

### Post by DirtDawg on 2006-06-22
Sooooooo, I have spent a great deal of time redesigning my website with CSS because, well, CSS is awsome. But, of course, Internet Explorer (officially endorsed by The Devil) won't read the new design without brutally mangaling it. Having expected this, I wrote a harmless bit of Javascript code on the index page.
```

		<script language="javascript" type="text/javascript">
		<!--
			if (navigator.appName == "Microsoft Internet Explorer") 
				{ window.location = "Pages/home.html" }
		-->
		</script>

```
Essentially it redirects IE users to the old design, which plays nice with IE. So far so good.

But when I tested the new design in the Opera Broswer, I was dismayed to find that it identifies itself as Internet Explorer! #-o 

According to the [Opera FAQ page]("http://www.opera.com/press/faq/#tech11"):
> Opera needs to identify itself as Internet Explorer, as some sites simply will not let Opera in. This includes many Microsoft sites and others. Some sites also fail without warning if the user tries to identify the browser as Opera or as an unknown browser. This is particularly true for sites running Microsoft IIS server, since Microsoft introduced a method that makes all unknown browsers fail and decided not to include Opera on the list of known browsers.

Terrible, terrible news. Does anyone have any idea if there's a way to identify Opera as Opera? I have found a few links to hacks, but they all appear to be for the client side. 

I have a feeling my attempt to alienate IE users has backfired so *only* Firefox users can view the new design as intended. Ironic!

---

### Post by km0ti0n on 2006-06-22
Many people insult IE without fulling understandng it.  IE's many issues is it's age, many of it so called "propiarty" features have been consumed by all most every modern browser.   Take, for example, innerHTML which has become defacto standards and the w3c are concidering addign it to the standards it was first seen in IE.  Also   take XMLHttpRequest AKA AJAX again all other have followed in IE's foot steps  and added this functionality.  But yes IE's CSS does lack a few features, but by no means enough for any developers to create alturnate pages.

Like me you're page and I'll give you a proper solution.

---

### Post by x64Jimbo on 2006-06-22
There are other ways to ident the browser. For instance, there are certain javascript functions that only exist in IE. You can attempt to call one of them and if it works, you can have it execute your IE code. If not, well you know what to do.

---

### Post by KlausPaiva on 2006-06-22
```
if ( window.opera )
{
  // your code here
}
```

---

### Post by dabear on 2006-06-22
[QUOTE=KlausPaiva]```
if ( window.opera )
{
  // your code here
}
```[/QUOTE]
Plase, please, do not do this!

It is far better to go through your css and correct your errors than to use js to redirect. If you at all have to redirect, do it on the serverside.

The best thing would, as said, be to correct your code, and possibly adding a stylesheet only for IE afterwards if that doesn't work.

```

<!--[if IE]>
<link rel="style sheet" type="text/css" href="IEspesificStyleSheey.css" />
<![endif]-->

```

---

### Post by penguintutor on 2006-06-22
> 
But yes IE's CSS does lack a few features, but by no means enough for any developers to create alturnate pages.


It's not just features that are lacking, but they implemented CSS wrong. The best example is the [Broken Box Model](http://glish.com/css/hacks.asp)
where the IE developers just didn't read the W3C specifications correctly. IE puts both the padding and margin inside the specified width, not outside as per the W3C.

If you try and do accurate positioning with CSS then it just doesn't work in IE.

Generally if you spend enough time redesigning your site you can end up with a compromise so that the page looks acceptable in other browsers. This is one of the things I did with my website where the menu is aligned with the bottom of the banner image with Firefox, Opera and other browsers, but in IE, it overlaps the top of the banner image, and the hover doesn't work correctly as one of the borders has disappeared in IE. 

About 35% of my visitors use IE, and see the less asthetically pleasing (but still functional) page, the rest of my visitors see the menu flush with the banner image.

---

### Post by s|k on 2006-06-22
This may sound terrible, but I just avoid testing for Opera in JavaScript heavy DHTML sites, and just make sure the website degrades properly. Opera is lousy at rendering DHTML, at implementing DOM functionality with JavaScript, and it's not so good with JavaScript in general (for instance no stylesheet object).

---

### Post by LordHunter317 on 2006-06-22
The correct thing to do is never do browser detects at all.  At most, use an IE-specific stylesheet.

[QUOTE=penguintutor]It's not just features that are lacking, but they implemented CSS wrong.[/quote]No, they did not.

>  The best example is the [Broken Box Model](http://glish.com/css/hacks.asp)
where the IE developers just didn't read the W3C specifications correctly.No, they did not.  The CSS2 spec wasn't close to finished when IE6 was launched.  Hard to support something still be drafted, no?

>  IE puts both the padding and margin inside the specified width, not outside as per the W3C.Ignoring the fact this makes more sense, it does support the CSS box model correctly anyway in strict rendering mode.

---

### Post by DirtDawg on 2006-06-22
Wowee! Lots of responses, thank you all very much.

I weighed the pros and cons of creating a website where all browsers are treated equally before I even started the redesign. But the fact of the matter is, less than a third of the traffic to my site uses IE. Also, I want a fixed side-bar navigator *without* the use of frames. Period. Top that with the fact that I still have plenty of server room left and the IE compatible website is already built so it's no problem to just funnel IE users to the old site.

x64Jimbo gets an A+ for creativity. That's the kind of hack I like to see. But I'll likely go for the "if(window.opera)" option since that's exactly the sort of solution I was hoping for. 

Of course the best solution would be for Micrsoft to update their friggin' browser. But alas, I've no control over such things.

I really appreciate everybody taking the time to respond. This community is the best there is. :KS

---

### Post by DirtDawg on 2006-06-22
[QUOTE=dabear]
It is far better to go through your css and correct your errors than to use js to redirect. If you at all have to redirect, do it on the serverside.
[/QUOTE]

I just reread this and I'm intrigued by the server-side redirection. Do you mean with PHP or Perl or some such?

---

### Post by dabear on 2006-06-22
[QUOTE=DirtDawg]I just reread this and I'm intrigued by the server-side redirection. Do you mean with PHP or Perl or some such?[/QUOTE]
php can do that, so can python with django, and probably perl too.

However, I am not showing you how, as you can easily find relevant info about this @ google.

Please, do not use redirections for this, correct your coding and use ie-conditional statements (shown in my last post) if you have to.

If you code correctly, there should be no problems arising in firefox, opera and khtml-based browseres such as safari and konqueror. IE is an exception, but as mentioned,  link-elements inside conditional-statements which points to IE-only stylesheets solves the problem.

I would go as far to that **YOU ARE A BAD CODER / WEB DEVELOPER** _if_ you have to use redirects for this purpose.

---

### Post by DirtDawg on 2006-06-22
[QUOTE=dabear]
I would go as far to that **YOU ARE A BAD CODER / WEB DEVELOPER** _if_ you have to use redirects for this purpose.[/QUOTE]

:p  Well I can't really argue with that. But if I only did things I was good at, I'd never get anything done.

Mostly I don't really feel like rewriting the whole site just to accomodate a small group of users. However, the posts from this thread have convinced me it's probably a worthwhile thing to do. I suppose what I'll do is use the redirection method for now until I figure out a good way to reconcile the differences (which could take 3 hours or 3 months).

Either way, your help is invaluable so thank you.

By the way, that Flock browser looks pretty interesting.

---

### Post by dabear on 2006-06-22
[QUOTE=DirtDawg]
Mostly I don't really feel like rewriting the whole site just to accomodate a small group of users.[/QUOTE]
Statistics can and WILL lie, you know. There would be no problem for an excerpiences user to change his or her browser string, atleast in the firefox,opera,konqueror and flock browsers

Flock is my new favorite browser. Because it's based off of firefox, nearly all extensions are or could be 'flockified'

---

### Post by LordHunter317 on 2006-06-22
Given that the beauty of IE is that you write a stylesheet identical to your current one (i.e., same classes and ids) but that only IE will use, you shouldn't have a problem.

---

### Post by DirtDawg on 2006-06-22
[QUOTE=LordHunter317]Given that the beauty of IE is that you write a stylesheet identical to your current one (i.e., same classes and ids) but that only IE will use, you shouldn't have a problem.[/QUOTE]

Maybe. I was thinking about that. I have 2 big problems. The first is the "fixed" property, but that should be easy to work around. 

But my navigation bar is built very delicately. As it consists of stacked images, IE breaks it pretty bad. I *think* I have an idea how to fix it, but it may take some doing (especially for an ameature like myself). 

Wish me luck!

---

### Post by Engnome on 2006-06-22
As an Opera fan i have to enlighten you that Opera does identify itself as Opera, if you know were to look that is 8) 

I think (I'm not a professional web dev) that it identifies itself as IE for simple checks like yours (or atleast it did) but not sure how it is nowadays.

check [http://en.wikipedia.org/wiki/Opera_(web_browser)#Compatibility](http://en.wikipedia.org/wiki/Opera_(web_browser)#Compatibility)

I don't really have to bother since anything that works in ff IE or whatever works in Opera :mrgreen:

Edit: What version of Opera are you testing with? Had an old version once that identifed itself something like "MS internet explorer bla bla bla Opera" It was the same string as for IE but with Opera added at the end. Guess they want to be seen in statistic on serious sites that really know how to check.

---

### Post by DirtDawg on 2006-06-23
Well, I must say, I am amazed, ***amazed*** with Internet Explorer. I have managed to create a special set of IE CSS layouts that, although hidiously ugly, works well enough. But the number of bugs IE displays boggles the mind.

a) I feel like my control of background images in small spaces is, to say the least, limited. In fact, I gave up on my navigation bar background and used a flat color instead. I may fix this later (maybe not).

b) My custom "centered" image tag (you know, left and right: auto), which is sort of a hack to begin with, absolutely does not work.

c) Lack of support for ".png" transparency? Microsoft should be embarrassed.

So, even though everything "works" now, it's a mess. Nothing some tweaking can't fix, but what a pain. My apologies to everyone who's "defended" IE in this thread but face it, from a designer's P.O.V., IE is just B.A.D.

I just so happened to pick up a copy of O'Reilly's "CSS Cookbook" from my local library earlier today.  A good thing in the sense that it really helped me figure out some puzzles that would have stumped me without (at least for a little while). A bad thing in the sense that I now realize there was a much better way to design my site from the very beginning (columns anyone?). #-o

Again, DaBear, once I figured out how to use it (I think), your byte of code worked  beautifully, so thank you again.

Engnome, Opera is great. It displays my site better than Firefox, actually.

---

### Post by DirtDawg on 2006-06-23
Nevermind. Please igonore.

---

### Post by LordHunter317 on 2006-06-23
[QUOTE=DirtDawg]b) My custom "centered" image tag (you know, left and right: auto), which is sort of a hack to begin with, absolutely does not work.[/quote]Centering in IE is best accomplished by wrapping your whole site in a div with 'text-align:center'.  Then, 'text-align: left' the actual content.  IE6 misinterprets the meaning of text-align and doesn't understand 'margin:0 auto' correctly.

> My apologies to everyone who's "defended" IE in this thread but face it, from a designer's P.O.V., IE is just B.A.D.Not really.  People writing webpages *today* forget how *old* IE6 is and that's the problem.  IE hasn't had a rendering refresh in ages--more than 6 years.  

I assure you every other browser 6 years ago, if you didn't do web design back then, was just as screwed up.  Honestly.

So yes, IE is a PITA, compared to newer browsers.  But IE7 will be drastically better.

---

### Post by DirtDawg on 2006-06-23
[QUOTE=LordHunter317]
I assure you every other browser 6 years ago, if you didn't do web design back then, was just as screwed up.  Honestly.

So yes, IE is a PITA, compared to newer browsers.  But IE7 will be drastically better.[/QUOTE]

I only started web design with this site. I hope you're right about IE 7. Unfortunately, I've read enough to understand that even when IE 7 is phased in, designers will still likely have to compinsate for its shortcomings for years (see: Netscape 4).

---

### Post by wmcbrine on 2006-06-24
[QUOTE=penguintutor]About 35% of my visitors use IE[/QUOTE]I'm impressed by this figure. How did you get it so low?

---

### Post by Stromham on 2006-06-25
how a bout having your first page a browser select? like ea's countrie and language select people will most likely select it once then bookmark it if they like your website.

---

### Post by virtuelvis on 2006-06-25
[QUOTE=s|k]This may sound terrible, but I just avoid testing for Opera in JavaScript heavy DHTML sites, and just make sure the website degrades properly. Opera is lousy at rendering DHTML, at implementing DOM functionality with JavaScript, and it's not so good with JavaScript in general (for instance no stylesheet object).[/QUOTE]

FWIW: Opera 9 supports DOM2 Stylesheets. (And DOM/JS support is really much better than you think. See [Web Specifications Supported in Opera 9](http://www.opera.com/docs/specs/) (The same document for [Opera 8.x](http://www.opera.com/docs/specs/opera8/)))

---

### Post by s|k on 2006-06-26
[QUOTE=virtuelvis]FWIW: Opera 9 supports DOM2 Stylesheets. (And DOM/JS support is really much better than you think. See [Web Specifications Supported in Opera 9](http://www.opera.com/docs/specs/) (The same document for [Opera 8.x](http://www.opera.com/docs/specs/opera8/)))[/QUOTE]
Well that's great news. :) However, I am still experiencing pretty lously rendering of dynamic effects such as moving elements in Opera 9. In addition, I am not saying that Opera doesn't support stylesheets, I'm refererring to the stylesheet object, which I am not sure is even part of any standard. It is just a useful tool.

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=s|k] I am not saying that Opera doesn't support stylesheets, I'm refererring to the stylesheet object,[/quote]As in the document.styleSheets[] array?

[QuirksMode](http://www.quirksmode.org/dom/changess.html) seems to imply it's part of the DOM CSS Level 2 rules, but clearly rants about inconsistent (and unspecificed by the spec) behavior with it's children.  Meaning that consistent usage across browsers is a PITA.

My experience with JS libraries that deal with styles in this manner confirms this for me anyway.

---

### Post by DirtDawg on 2006-06-26
[QUOTE=wmcbrine]I'm impressed by this figure. How did you get it so low?[/QUOTE]
Only about 30% of my visitors use IE as well. Maybe the "worm is turning", as they say.

---

### Post by penguintutor on 2006-06-26
> 
Originally Posted by penguintutor
About 35% of my visitors use IE

I'm impressed by this figure. How did you get it so low?


Simple it's a site about Linux. Although the majority of users are still using Windows machines, they tend to favour Firefox. Even then my non-Linux sites users have been moving away from IE, about 20% of them have switched away from IE. 

> 
Not really. People writing webpages today forget how old IE6 is and that's the problem. IE hasn't had a rendering refresh in ages--more than 6 years.

I assure you every other browser 6 years ago, if you didn't do web design back then, was just as screwed up. Honestly.


Isn't that the problem. IE is so old, and Microsoft has been unable to update it. No doubt the biggest problem is that it's so tied into the Operating System that if they make a minor change they risk messing up the entire Operating System, or maybe with such a large market share they were just happy to have everyone tied into their browser.

IE6 may have been out before CSS2 was finalised, but that doesn't explain why they didn't update it when it was. After all you wouldn't be happy if you bought the latest pre-N wifi card to find it was completely useless once the standards are actually ratified, and it then didn't work with any of the new hardware.

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=penguintutor]IE is so old, and Microsoft has been unable to update it.[/quote]No, they've always been able.  I don't know if they simply didn't bother or canceled whatever development they were doing and started over, but there's little question of capability.

> No doubt the biggest problem is that it's so tied into the Operating System that if they make a minor change they risk messing up the entire Operating System,Utter nonsense.  Go count security patches, for starters.

> but that doesn't explain why they didn't update it when it was.No one else did either.  Remember Seamonkey was in active development all this time, so it got fixed by and large as the spec did.  So did KHTML.  I can't speak to Opera but I assume they just fixed it in the next released version (that's the behavior we see now, so it's hard to believe it's not).

---


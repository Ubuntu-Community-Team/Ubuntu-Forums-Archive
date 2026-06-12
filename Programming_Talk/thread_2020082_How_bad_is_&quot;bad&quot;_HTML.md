---
title: "How bad is &quot;bad&quot; HTML?"
date: 2012-07-07
forum: Programming Talk
---

### Post by PaulM1985 on 2012-07-07
On this forum there have been a couple of discussions relating to how "bad" some web-based resources are (intentionally not naming the resources) and how annoyed people are that others reference them.

What I would like to know is, what are the actual drawbacks of using them?  Web browsers seem to have been developed to be extremely tolerant and accept code where a developer has done something slightly wrong, but what is the alternative to allowing incorrect HTML?  If a browser only accepted 100% correct HTML, then surely there would be a large number of websites that would not be available to the user and as a result the browser would not be very popular.

I am usually the sort of person to scream "what are you doing?" when I see bad Java, C++ or generally bad logic, but in the case of HTML, there seem to be so many "bad" resources I can't tell the difference between what is acceptable and what isn't.

Paul

---

### Post by codingman on 2012-07-07
[COLOR="Red"]WARNING! WARNING! POSSIBLE OPINION ALERT![/COLOR]

"bad" HTML, is, like, where deprecated tags are used, or like, having all of your code in one line, or being an XHTML freak and closing tags where there doesn't need to be. Bad html could also mean using a bunch of client-side languages that could be done instead with only one.

Just a big fat opinion,
Codingman

---

### Post by pqwoerituytrueiwoq on 2012-07-07
> **codingman said:**
> [COLOR=Red][/COLOR]or being an XHTML freak and closing tags where there doesn't need to be
like a br tag i do that all the time

not intending code is almost as bad as one line

---

### Post by PaulM1985 on 2012-07-07
Ok, thanks for the contributions so far, but what I maybe should have asked is what are the consequences of "bad" code?

Bad indenting etc might be annoying for a developer to read, but it won't affect the user.

Paul

---

### Post by trent.josephsen on 2012-07-07
> **PaulM1985 said:**
> Web browsers seem to have been developed to be extremely tolerant and accept code where a developer has done something slightly wrong,
This attitude shifts the burden of correct rendering onto the browser developer, not the site developer. This is bad because the more corner cases and "slightly wrong" things a browser has to figure out how to handle, the bigger and slower it becomes. Not only that, but since different browsers use different layout engines, there's not a "default behavior" for rendering non-compliant HTML. Desktop browsers might work consistently; what about mobile browsers? Text-mode browsers? Screen readers? Devices with small screens or limited colors? The idea of "gracefully degraded" performance can't be meaningfully applied in the same way to all these browsers, and if your "slightly" non-compliant HTML depends on a method that makes sense only for desktops, you can't guarantee it will still degrade gracefully under poor conditions.

> but what is the alternative to allowing incorrect HTML?  If a browser only accepted 100% correct HTML, then surely there would be a large number of websites that would not be available to the user and as a result the browser would not be very popular.
"If a browser only accepted **its vendor's version of** HTML, then surely there would be a large number of websites that would not be available to the user and as a result the browser would not be very popular." That's why we had the Browser Wars. The problem you observe does exist, but the correct response to it is proper education, not to throw up your hands in defeat.

> I am usually the sort of person to scream "what are you doing?" when I see bad Java, C++ or generally bad logic, but in the case of HTML, there seem to be so many "bad" resources I can't tell the difference between what is acceptable and what isn't.

This *is* a really big problem. Perhaps one day browsers will refuse to render invalid markup, like compilers can refuse to compile invalid programs.[1] Until then, we can advise newbies of the drawbacks of *certain resources* and point them toward better ones -- which, I think, this forum tends to be pretty good at.

[1]: Honestly, I think that's what we should be pushing for, but as you observe, there are currently too many noncompliant Web pages out there for such a browser to gain significant market share. Making sure everyone who wants to learn HTML has complete and accurate information (within our ability to do so) is IMO the best path toward this goal.

---

### Post by lykwydchykyn on 2012-07-07
The fact that browsers are tolerant of bad code makes it difficult to debug.  This is OK if you're just putting together a personal blog or vanity page, but when you're doing serious application-in-the-browser work it becomes a real problem.  

For example, just last week I wasted about an hour trying to debug a non-functional javascript method, and it turned out it failed because I forgot a closing tag on a DIV.  

There's an old programming principle that bugs should cause a program to fail "loudly and as soon as possible".  The way browsers render HTML pretty much turns that notion on its ear.

EDIT: Ok, I've read a few other threads in the forum and I can guess what this thread is about now.  Let me say this...

I started working with HTML about 12 years ago.  Back then, "web pages" were mostly a different form of rich-text document, with a few "advanced" capabilities with javascript that were mostly used for cheeseball special effects and useless doodads; but mostly, people created web pages with a "document mindset".  We had inline styles, FONT tags, tables for layout, invisible 1-pixel gifs for forcing spacing, and of course a whole bunch of tricks that only worked on that ONE browser that ran on that ONE operating system that about 95% of our visitors were using.

Things have changed.  

The new movement in web development is one of standards compliance, separation of content from logic, separation of presentation from content, semantic markup, function over form, security, maintainable code, and a dozen other wonderfully mature, healthy ideas that have been a long time coming.  It is (thank heavens) no longer acceptable to have a website that only works in that ONE browser on that ONE OS.  

Now, there are resources that get this new paradigm, and there are resources that don't. 

As someone who learned a lot of bad habits in the "bad old days" of web development (and has spent some frustrating years un-learning them), I would prefer to steer neophytes in the direction of resources that will teach them good practices for the future.

---

### Post by Dimarchi on 2012-07-08
Some of these resources are products of an earlier era, and dealing with stuff that is no longer the accepted way to go about it.  The skeleton in the web development closet was/is Internet Explorer 6 and they may do things the IE6 way, that being the most used browser at the time, with its own way of doing things. Other browsers started to show what following the standards meant for both end users and coders alike. I see this "upheaval" still as coder based: doing stuff that takes care of the various ways the browsers differ in their implementation is a source of much headache. Why not follow the standards? Pointy haired boss or the end user may disagree - do what I tell you, not what makes sense...let me see the page working in *my* browser, I don't care about the rest. One of the reasons, perhaps, why browsers are so forgiving of errors - although I do seem to have some recollection of there being some browsers that forgive nothing (iCab?).

The currently accepted way of doing things is the standards based stuff. All major browser vendors follow this. In this scenario these resources are at the very least partially out of date, and possibly harmful or misleading. There are more up-to-date resources, as well. How can you tell which resource is harmful and which is not? Experience - especially the experience working in the commercial field where you must deal with these issues, experts whose opinion you tend to trust (Ars Technica had a nice article about this a while ago, title had something about morons, though, fwiw).

Another interesting thing nowadays is the rapid development of some browsers (I'm looking at you, Chrome and Firefox...or should I say Webkit and Gecko?). Standards take time. Some parts may be more or less done, but not declared as something that is ok to fully implement by the parties in the standards process. These browser engines already adopt these more or less done parts, leading them to be seen as the most progressive and perhaps desirable products to code for and use as an end user. This may give rise to another "IE6 only, thanks" kind of scenario, this time featuring the other shoe.

Another resource splintering ahead? Maybe. Ok, I'm rambling here already, but hopefully this offers another way to look at this. :p

---

### Post by PaulM1985 on 2012-07-08
There have been a few points I had been sort of expecting but it was nice to know that I was thinking along the right lines.

Obviously people should follow standards.  It would make cross-browser testing almost a thing of the past.  If you know it works on one browser and you have followed the standards correctly then it should work on all browsers, right?  (I am assuming all desktop browsers here, not mobile as I don't have any experience in that area)

I guess the only way forward is to do what some guys have done on this forum and try to point people in the direction of good resources.  Is anything like this stickied?  I can see links to good resources for stuff like C++, Java, etc but there doesn't appear to be anything for HTML.

Paul

---

### Post by Odexios on 2012-07-08
Is there any browser around which strictly adheres to the standard, and warns the user when there's something not standard compliant?

---

### Post by mcduck on 2012-07-08
> **Odexios said:**
> Is there any browser around which strictly adheres to the standard, and warns the user when there's something not standard compliant?

As far as I know, no (apart perhaps from some Firefox extensions of course).

But using XHTML instead of HTML helps a bit, it's more strict about things and browsers also tend to interpret it that way.

And it of course forces you to make better and cleaner web code that's easier to maintain... :)

---

### Post by CptPicard on 2012-07-08
First of all, for a website developer, taking the attitude that "the browser will tolerate it" is no excuse. Standards are standards for a reason.

For the browser developer, considering that it's a client application, tolerating incorrect input in a sane way can perhaps be a service for the user. However, as IE demonstrates, going too far in this just results in the browser itself being fragile in the actual implementation of the standards themselves. Hence, I'd consider bad HTML to be an evil unto itself for this reason...

---

### Post by lykwydchykyn on 2012-07-08
> **Odexios said:**
> Is there any browser around which strictly adheres to the standard, and warns the user when there's something not standard compliant?

Don't know of a browser, but I use the w3c validor pages to test my HTML and CSS.

[http://validator.w3c.org](http://validator.w3c.org)

---


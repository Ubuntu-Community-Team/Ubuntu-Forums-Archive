---
title: "Javascript for unreasonably busy computer science dropouts?"
date: 2019-11-22
forum: Programming Talk
---

### Post by jetsam on 2019-11-22
Anybody have a book recommendation for getting up to speed with web client side programming quickly?  I want to do some in-browser manipulation stuff, maybe a Firefox extension.  I'd explain more, but I'm not very sure of where I'm headed...

You all always want the problem to be specified.  Let's try a hypothetical assignment:
Say I wanted to program a web page that acted as a communal jukebox?  There would be user accounts, and users could log in, select a track, pay an internet point, and have their song request added to the queue.  Any user will then be able to listen to the jukebox play either by visiting the web page, or by listening through an audio feed that is set up separately...

...there is no cheating on this assignment, it is not for school, and I expect to make heavy use of the YouTube api, or possibly the Soundcloud one, or Pandora, or... you get the drift.

Basically a medium complex web app with back end offloaded on some big audio/media site somewhere...  

I'll find things on my own, but a hand up the first few rungs of the ladder would be appreciated...

Thanks for your input,
jetsam

---

### Post by SeijiSensei on 2019-11-22
Sites that handle user accounts, etc., usually involve server-side programming tools like PHP or Python. They also typically involve a back-end database program like PostgreSQL or MySQL. I don't know how you would do all that you want to accomplish with client-side programming in Javascript. I've written a number of sites with accounts and other features; they're all in PHP with a PostgreSQL back-end.

Have you coded in another language like C or Python or is this your first time out?

---

### Post by jetsam on 2019-11-22
I was just in a graphical chat room that had everything but the queue.  It's just a small window with a search button.  You search for a song, a menu comes up of several from YouTube matching your search terms.  You pick one, it plays. 

Everyone in the chat room hears the music, unless you turn the volume down on your personal player in the corner of the window.

Maybe I could forgo user accounts and make due with open sessions.  There's no real security concerns, I don't think.  Not during obscure development days, at any rate...

**Edit**:  I have C and Python experience and a now rusty approximate minor in computer science courses taken from MOOCs like edX and Coursera.  I can pick up a new language, but I seldom want to.  Javascript may just have made the cut.

**Edit 2:**: I also have more hardware experience than most CS majors.  I may have near the same level of casual education in Embeded design/ECE, plus a few courses in Communications Systems (Essentially the basics of modern communications, following the signal path through a simplified cell phone network.)  This may or may not have some relevance to Web App design. I know enough Matlab to dislike Matlab.

---

### Post by jetsam on 2019-11-22
This looks like a good place to start on a weekend just now beginning:
[Learn JavaScript - Full Course for Beginners]("https://www.youtube.com/watch?v=PkZNo7MFNFg")

I think javascript is probably worth learning because it's already installed literally everywhere there's a standard web browser installed.  It's sort of the one ubiquitous language out there now, and it's everywhere...

---

### Post by Skaperen on 2019-11-22
oh nice, now i can *really* learn JavaScript instead of doing little dinky things like [this]("http://ipal.net/vance/").

---

### Post by Skaperen on 2019-11-22
> **jetsam said:**
> This looks like a good place to start on a weekend just now beginning:
[Learn JavaScript - Full Course for Beginners]("https://www.youtube.com/watch?v=PkZNo7MFNFg")

I think javascript is probably worth learning because it's already installed literally everywhere there's a standard web browser installed.  It's sort of the one ubiquitous language out there now, and it's everywhere...

"[JavaScript in 3 hours]("https://www.youtube.com/watch?v=PkZNo7MFNFg")"

and YouTube just had to let me know about "[JavaScript in 1 hour]("https://www.youtube.com/watch?v=W6NZfCO5SIk")" (and even half an hour).

---

### Post by jetsam on 2019-11-22
What do you call someone who knows at least 7 languages? A developer.

I like the panorama page.  

I'm a little uncertain about the depth of the youTube course I linked above, but heck it's free to try...  

I'll probably pick up a reference book as well.  I like the O'Reilly In a Nutshell Series for both Python and C so I'll probably get Javascript in a Nutshell.  Here's the equivalent: [JavaScript: The Definitive Guide]("https://www.amazon.com/gp/product/0596805527/") (Amazon non-affiliate link.)

Yep.  Just found an $11.00 used copy including shipping.  It's been out long enough the used copies are inexpensive.

---

### Post by jetsam on 2019-11-22
Do web-devs mostly pick up the various frameworks and front ends and back ends and middle-wares piece by piece as they go along?

Is there like a web-dev architecture course that makes a super-framework of a sort that you can conceptualize the other frameworks under?  Bit of an abstract question...

How do you get your bearings in this landscape and not lose time learning platforms you'll never use?

---

### Post by sdsurfer on 2019-11-25
I don't know if you follow TechLead on YouTube, the guy is hilarious. "Hello, it's coffee time again with Ex-Google, Ex-Facebook TechLead (as a millionaire.) I an **THE** tech lead. Not your boss, not your team lead, **ME.** If you don't understand that, there's really no point in continuing." :-)

Anyway, he's been around the block a few times and in one of his videos he gives a piece of advice that hits home. All of your programming education, which language you learn, and how far, should be **project driven.** He says (paraphrased) he sees a lot of people digging in to learn a language just for the sake of learning the language, then maybe never using it or forgetting most of it. Or learning the obscure aspects of the language that have very little practical use. I've learned many languages over the years and once the project is done, they are long forgotten (VBscript, Flash, asp.net, to name a few.)

The point is you look at your project and then determine what to apply and whether you need to dig in to that language. You're correct, Javascript or some framework built on it is everywhere, digging in would definitely not be a waste of time,  but hold to the KISS rule and don't rebuild the wheel. Using the communal jukebox mentioned in the O.P., I could easily see "some Javascript framework" front end and "any server side language" back end. The same is true of your server-side coding, what language works best for you, and would be easiest to implement without rebuilding the wheel? Then ditto on the database you'd use.

By "some Javascript Framework" I mean it could be anything, which "kind of" answers as a yes, 
> Is there like a web-dev architecture course that makes a super-framework  of a sort that you can conceptualize the other frameworks under?

At the very least, jQuery is a well established framework, but there are many more built on top of it. jQuery UI, for example, is the user interface plugin for jQuery combined with bootstrap which is used by thousands of sites for a front end. There are others that build on those two for a framework API.

It really depends on your project, and that's how you dig in. Find something that looks like it's moving in the direction of your project, and start fiddling with it.

---


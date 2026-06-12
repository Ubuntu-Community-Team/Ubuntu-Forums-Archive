---
title: "Html 5??"
date: 2009-12-07
forum: Programming Talk
---

### Post by abhilashm86 on 2009-12-07
i hear it frequently, also saw some of its features, all richer tags, video, image and lots.....
will you think html 5 will replace ajax and some RIA like flex? also php gets stronger with html 5, what you people say?

---

### Post by nvteighen on 2009-12-08
IIRC, HTML 5 is just an update to HTML 4.01 Strict... I guess the W3 Consortium will keep updating HTML until all browser support XHTML 1.1 Strict decently. (Meanwhile, what about CSS 3 support!?)

---

### Post by bobince on 2009-12-08
HTML5 will not replace AJAX (XMLHttpRequest); many HTML5 apps will rely on it.

One of the proposals that has arisen from HTML5 (and, like the best bits, has subsequently been spun off into its own independent specification) is WebSocket, which can be used as a substitute for XMLHttpRequest in situations that require low-latency two-way network access. But extra complexity in writing the server-side to talk WebSocket (in comparison to XHR which leverages existing web server plumbing) means that most simpler apps, which do not need this, will stick to XHR.

HTML5 is very much a mixed bag. It's not really useful as a single specification, since it foolishly attempts to document pretty much everything a web browser should do, and has therefore become a sprawling mess that I doubt any browser will ever implement 100%. (Hell, you could argue that no browser quite supports HTML4 100% either, and that's a much simpler standalone spec that doesn't attempt to do a hundred things at once.) It disappoints me in its insanely prescriptive approach to parsing every last invalid byte sequence as HTML; why we need to worry about this when XML has already solved that problem is beyond me. I find it sad that it emphasises old-school tag soup methods over XHTML5.

But there are features that have emerged from the HTML5 process that have proven popular and are starting to see real-world use already. For example the querySelector interface (now spun off to W3 Selectors-API) and getElementsByClassName bring into the plain-JS world the simple binding JS-framework users are used to but with much better performance. These methods have been demanded by users for years (since they're not difficult for browsers to provide and they make authors' lives way easier), but until WHATWG started getting the browser vendors to wake the hell up there was just no traction.

The canvas, video and audio elements are really promising and I would love for them to start reducing the web's reliance on Flash. Unfortunately Apple has really dropped an interoperability-turd in the gears with its refusal to support the OGG formats. Microsoft may still kill mass adoption of these by refusing to implement them in IE9, and there is every chance they might do so, in order to avoid stepping on Silverlight's toes.

The new input elements are a nice convenience which sadly haven't seen a great deal of implementation love yet.

There are other features that are just HTML5 blessing existing IE-originated practice, such as innerHTML and friends (which are an unfortunate necessity), the designMode/contentEditable stuff (which personally I think is an ugly mess), and showModalDialog (the whole concept of which is vile and repellent and should have been burned years ago). But then as with the whole HTML 3.2 vs 3.0 debacle W3 are more likely to get somewhere by documenting existing practice than trying to push vendors to new, cleaner APIs.

So, yeah, HTML5 isn't one monolithic environment you'll learn and use to replace RIAs. It's a collection of small enhancements to the existing web environment which will chip away bit by bit at the areas Flash and Silverlight have previously owned. Some of them you can use already, some of them will gradually come into use as implementations arrive, some of them will never happen. Learn the useful bits piecemeal as they become available.

For me, the biggest factor in making JavaScript a challenger to Flash et al is not any one feature that HTML5 has proposed, but the huge improvement in the speed of JavaScript that has resulted from the New Browser War and its emphasis on scripting performance. Think back to how clunky scripts could be in IE5 or, even worse, the dreaded Netscape 4, and there's no way JS could have been a contender. The ongoing competition of &#8220;my engine's faster than your engine&#8221; has massively benefited JS authors and users.

---


---
title: "Trying to get CSS counter to span across two &lt;tr&gt;s and/or &lt;td&gt;s of a &lt;table&gt; (HTML5)"
date: 2017-03-30
forum: Programming Talk
---

### Post by s3a on 2017-03-30
Before anyone suggests to use the start attribute of <ol> tags ( [https://www.w3schools.com/tags/att_ol_start.asp](https://www.w3schools.com/tags/att_ol_start.asp) ), I am trying to not do it that way.

More specifically, I am trying to do it using the CSS counter mechanism (for learning purposes, plus it seems to be better practice, since HTML should not be used for styling, such as is the case with the start attribute of the <ol> tags).

_So, here is the HTML and CSS.:_
[http://codepen.io/anon/pen/xqQPew](http://codepen.io/anon/pen/xqQPew)

My problem is shown visually (in the codepen link above), where it says "[THIS SHOULD BE 'II', INSTEAD OF 'I'!!!]".

I've looked at so many links, and I'm still confused, so could someone please help me figure out how to solve my problem (by referring to my specific scenario)?

Any input would be GREATLY appreciated!

---

### Post by norobro on 2017-03-31
I've been trying to respond to your post for over a day. Didn't realize that you can't post html code even inside of code tags.

Looks like you have a scope problem. Give this a read: [https://www.w3.org/TR/CSS21/generate.html#scope](https://www.w3.org/TR/CSS21/generate.html#scope)

See example here: [http://codepen.io/anon/pen/PpXXJR](http://codepen.io/anon/pen/PpXXJR)

---

### Post by s3a on 2017-04-03
Firstly, thanks for your help so far. :)

I've been looking at this thread for a while, though, and I'm still stuck; sorry! :(

I made an improved version of the syntax you gave me, and it (also) *does* work.:
[http://codepen.io/anon/pen/wJOrWY](http://codepen.io/anon/pen/wJOrWY)

Having said that, though, when I try to modify the syntax from my initial post, I am still getting the same problem. :(

Could you please create another codepen that is a minimally-modified version of the initial syntax I posted and put (a) comment(s) wherever you made a change? I really feel like that would help a lot, because I would then be asking myself "Why does that work?", which I believe would help me along much better than trying to apply theory that I have been re-reading for a long time, where I'm probably reading past something, thinking that I've understood it, while actually not having understood, but I don't even know what it is I'm misunderstanding.

---

### Post by 1clue on 2017-04-03
Not much to add except this:

[LIST=1]
[*][www.w3.org](www.w3.org) is ***The**** authoritative source *for html. It is literally the organization in charge of defining html and many other web-based markup.
[*][www.w3schools.com](www.w3schools.com) is notorious for having outdated, incorrect or just plain terrible information.  [https://meta.stackoverflow.com/questions/280478/why-not-w3schools-com](https://meta.stackoverflow.com/questions/280478/why-not-w3schools-com)
[/LIST]

Supposedly they have gotten somewhat better over the years, but w3schools is responsible for some worst practices in web development. If you find a link from elsewhere, use that first. If you must use w3schools then do so knowing that they appear not to care whether they lead you astray.

---

### Post by norobro on 2017-04-04
It's really very simple. You have to have both lists in the scope of one "div" so the counter is not reset.

Here you go: [http://codepen.io/anon/pen/EWMomz](http://codepen.io/anon/pen/EWMomz)

Html file - added lines 14 & 79
Css file - removed line 58 and added lines 63-65

---

### Post by s3a on 2017-04-10
_@norobro:_
Actually, I figured it out, and I wanted to contribute my findings to you (and anyone else that might find this thread useful), it seems that the problem was that I had to replace the three counter-reset lines with one (counter-reset myCounter myCounter2, myCounter3; - here is the correctly-working codepen with only lines 58-60 modified: [http://codepen.io/anon/pen/RpXVYG](http://codepen.io/anon/pen/RpXVYG)), since, apparently, having three counter-reset lines makes only the last counter-reset line apply (and the first two are ignored).

Basically, according to this ( [https://developer.mozilla.org/en-US/docs/Web/CSS/counter-reset](https://developer.mozilla.org/en-US/docs/Web/CSS/counter-reset) ), the counter is reset on each occurrence of "the element", which is body in this case, and since body&#8217;s scope is a more "zoomed-out" scope than div.myCounter_class&#8217; and both lists seem to me to be in the scope of body (which is the criterion you mentioned for the counter not resetting), it was confusing me why the smaller scope was working (=div), but not the larger one (=body). It turns out my thinking was right all along and that the counter-reset simply wasn&#8217;t being processed/applied as I stated in the paragraph above this one.

Another flaw, which was in your syntax, that I recently learned about is that <div>s being inside <table>s are invalid syntax. If I&#8217;m correct, the <tbody> tags should be used as alternatives to <div>s within <table> tags, if such a thing is desired.

Having said that, I still appreciate your input very much (and it did technically help me move forward a little bit), so thanks. :)

_@1clue:_
I&#8217;ve been told that w3schools sucks before. ;) The thing is, a lot of the time (but not necessarily always), they tend to explain things better, so what I do is I generally use w3schools along with more reliable sources, like MDN.

---


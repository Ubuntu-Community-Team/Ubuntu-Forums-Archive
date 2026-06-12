---
title: "C# (C Sharp) concepts and doubts"
date: 2009-10-22
forum: Programming Talk
---

### Post by munishvit on 2009-10-22
Hello friends,

In this thread, anybody can [FONT="Arial Black"][COLOR="Black"]ask any doubt related to C# programming[/COLOR][/FONT]. 

In order to make this more readable, let's follow [COLOR="Red"][FONT="Arial Black"]some rules[/FONT][/COLOR]:
1. If you are posting a doubt, then start your post with "[COLOR="Blue"][FONT="Arial Black"]DOUBT NO. <n>[/FONT][/COLOR]", where 'n' will be next natural number as compared to last 'doubt' posted.
2. If you are posting a reply, then start your post with [COLOR="blue"]"[FONT="Arial Black"]---Reply to <n>---[/FONT][/COLOR]", where 'n' is 'doubt' no. to which you are replying.

---

### Post by munishvit on 2009-10-22
[FONT="Arial Black"]DOUBT NO. 1[/FONT]

Why don't we make all methods of a class to be 'static'. What can be the use of keeping a method non-static?

---

### Post by OpenGuard on 2009-10-22
[COLOR=RoyalBlue][B][COLOR=Blue]DOUBT NO.2[/COLOR]

[/B][/COLOR]Is it copyrighted by Microsoft and can they take it back whenever they want ( sue those who want to release commercial software without buying licenses ) ?

---

### Post by unknownPoster on 2009-10-22
> **OpenGuard said:**
> [COLOR=RoyalBlue][B][COLOR=Blue]DOUBT NO.2[/COLOR]

[/B][/COLOR]Is it copyrighted by Microsoft and can they take it back whenever they want ( sue those who want to release commercial software without buying licenses ) ?

That has been discussed so many times here that every mention of it is put in Recurring discussions...

Regardless, the entire concept of this thread confuses me.

---

### Post by OpenGuard on 2009-10-22
> **unknownPoster said:**
> That has been discussed so many times here that every mention of it is put in Recurring discussions...

Regardless, the entire concept of this thread confuses me.

And that's why you shouldn't answer ( or at least point to the place where this have been already answered ) ?

---

### Post by unknownPoster on 2009-10-22
> **OpenGuard said:**
> And that's why you shouldn't answer ( or at least point to the place where this have been already answered ) ?

Honestly, yes. I believe that self-sufficiency and motivation are keys to a good life. It's also a sticky, and if you can't find that kind of thing...well, I'm not sure what to say.

[http://ubuntuforums.org/showthread.php?t=1200946](http://ubuntuforums.org/showthread.php?t=1200946)

---

### Post by OpenGuard on 2009-10-22
> **unknownPoster said:**
> Honestly, yes. I believe that self-sufficiency and motivation are keys to a good life. It's also a sticky, and if you can't find that kind of thing...well, I'm not sure what to say.

[http://ubuntuforums.org/showthread.php?t=1200946](http://ubuntuforums.org/showthread.php?t=1200946)

If only that would be so simple. Sticky doesn't explain anything - Ubuntu and Mono is not what the question was about.

---

### Post by unknownPoster on 2009-10-22
Considering that mono is the Linux implementation of C#, I'd say it's very pertinent to the topic.

Regardless, Microsoft owns C# just as much as Sun owns Java.

---

### Post by OpenGuard on 2009-10-22
> **unknownPoster said:**
> 
Regardless, Microsoft owns C# just as much as Sun owns Java.

What makes you think so ( I don't disagree .. just want to see something black-on-white ) ? I was reading something about it's Community Promise and patents, but honestly .. explanations were too geeky for me.

---

### Post by unknownPoster on 2009-10-22
Essentially, a programming language is just Intellectual Property(IP) and IP ownership rights are tricky and complicated to determine. Although Sun has released much of the Java platform under the GPL, an open-source license. Sun Microsystems is still the major decision maker in the development of the Java Platform. Java is copyrighted, and it's probably patented as well. Here's an article by RMS on the topic, although it's three years old:

[http://www.groklaw.net/article.php?story=20060524112209579](http://www.groklaw.net/article.php?story=20060524112209579)

From a purely objective point of view, I see C# and Java being two fairly similar tools with the same goals in mind.

In my subjective opinion, I don't care enough to get caught up in the Microsoft ownership debate.

---

### Post by munishvit on 2009-10-22
> **munishvit said:**
> [FONT="Arial Black"]DOUBT NO. 1[/FONT]

Why don't we make all methods of a class to be 'static'. What can be the use of keeping a method non-static?

Can anybody clarify my doubt?

---

### Post by directhex on 2009-10-22
> **munishvit said:**
> Can anybody clarify my doubt?

Um....... because it's not exactly OO if you're going to remove the ability to instantiate objects (or use methods & properties on instantiated objects, anyway)?

Instances are *useful*

---

### Post by cszikszoy on 2009-10-22
> **OpenGuard said:**
> What makes you think so ( I don't disagree .. just want to see something black-on-white ) ?

This is about as clear of an explanation as you'll get: [http://tirania.org/blog/archive/2009/Jul-06.html](http://tirania.org/blog/archive/2009/Jul-06.html)

> **unknownPoster said:**
> Essentially, a programming language is just Intellectual Property(IP) and IP ownership rights are tricky and complicated to determine.
....
 the Microsoft ownership debate.

Microsoft does not "own" the language.  C# is actually an EMCA standard ([reference]("http://www.ecma-international.org/publications/standards/Ecma-334.htm")), not Microsoft IP.  .NET is Microsoft IP.  If you read the community promise (and the .pdf lined to at the bottom of the reference link, you'll see that Microsoft has agreed to license "on a non-discriminatory basis, to any party requesting" the implementation of this standard.  That's why you can even use Mono on Windows.

---

### Post by CptPicard on 2009-10-22
This is such a wrong way to attempt to use the forum... all discussion topics ("doubts"... :) ) should really go under their own threads so that they are easily viewable, and the quote tags are there for a reason for referral to what has been said previously...

---


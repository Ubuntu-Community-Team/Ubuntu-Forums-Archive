---
title: "A little note on Thanks (or the lack thereof..) and common courtesy"
date: 2009-01-21
forum: Programming Talk
---

### Post by stevescripts on 2009-01-21
Hi folks.

Well, I don't know why the powers that be have chosen to remove the thanks and thank yous... 

That said, I have always tried (and will continue to try) to take the time to thank anyone who helps me with a problem, and hope that others will do the same.

(just my $0.02 on the topic)

Steve
(mods feel free to chastise me in any way you might deem appropriate ;) )

---

### Post by Wybiral on 2009-01-21
> **stevescripts said:**
> hi folks.

Well, i don't know why the powers that be have chosen to remove the thanks and thank yous... 

That said, i have always tried (and will continue to try) to take the time to thank anyone who helps me with a problem, and hope that others will do the same.

(just my $0.02 on the topic)

steve
(mods feel free to chastise me in any way you might deem appropriate ;) )

+1

---

### Post by CptPicard on 2009-01-21
> **stevescripts said:**
> 
Well, I don't know why the powers that be have chosen to remove the thanks and thank yous... 

The optimist in me thinks that it was because it probably was a heavy feature to run on a large forum like this.

The cynic in me thinks that they wanted people not to know who actually posts anything of substance ;)

---

### Post by lukjad on 2009-01-21
Well, I have it on good authority that it is because of the server load, and that there have been over 20,000 leagues of threads on this. ;)

---

### Post by howefield on 2009-01-21
> **stevescripts said:**
> Hi folks.

Well, I don't know why the powers that be have chosen to remove the thanks and thank yous... 

Read this and you will

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

### Post by Felixworks on 2009-01-21
The solved feature was removed too??  That didn't seem very intensive...

---

### Post by lykwydchykyn on 2009-01-21
Forum sure has been stable since its removal.  I'm thankful for that!  Still, it's a bummer...

---

### Post by stevescripts on 2009-01-21
howefield - I didn't see that, Thank You very much for the pointer!

Steve

---

### Post by howefield on 2009-01-21
> **Felixworks said:**
> The solved feature was removed too??  That didn't seem very intensive...

It probably wasn't that intensive in and of itself, but multiplied by the number of queries on the database, it places extra load on the resources. 

Each search would have to read that line on the database ect, ect.

---

### Post by Reiger on 2009-01-21
Well by definition it is an expensive feature:
(1) You must per post track the "thanks" gathered
(2) You must per account track the number of "thanks" given
(3) You must per account track the number of "thanks" received as well as the number of posts which gathered these "thanks".
(4) You have cascading update triggers:
    - When someone revokes his "thanks" (ugh!)
    - When someone adds his "thanks"

And a very, very often used one too:
(a) You must display this info for every single post someone makes
(b) You must display this info for every single user page.

Very, very often times expensive might cost you stability and performance. ;)

---

### Post by mike_g on 2009-01-21
An anonymous thanks system wouldent be intensive. Just add a thanky count to posts and users. Wouldent be quite as nice tho and would mean digging around in the Vbullitin source, which could get mangled by updates. Guess it would also need a last thanks time in the user profile to stop thank spamming.

---

### Post by CptPicard on 2009-01-21
Considering that it is the display of posts that is probably the most intensive part of all of it, all you would need to have would be a per-user field that has a trigger attached. Then again I suppose that this runs om MySQL which is not a real database in this regard ;)

---

### Post by slavik on 2009-01-21
> **CptPicard said:**
> Considering that it is the display of posts that is probably the most intensive part of all of it, all you would need to have would be a per-user field that has a trigger attached. Then again I suppose that this runs om MySQL which is not a real database in this regard ;)
MySQL 5.x has triggers ...

---

### Post by myrtle1908 on 2009-01-21
Personally I don't see any point in the "Thanks" system.

After I help people out here at work (or wherever) I don't expect them to update a running "Thanks" tally glued to my forehead so that everyone knows how "helpful" I am.

Could someone please explain why there is such a fuss.

---

### Post by ajackson on 2009-01-22
> **myrtle1908 said:**
> Could someone please explain why there is such a fuss.
It was a way of showing your appreciation to the people who have helped you out or posted very useful information.

If you didn't want to use it you didn't have to but it helped remind people there were people at the other end of forum names. most (if not all) don't have to help out in any way but do. It let you show some basic manners, something lacking on most internet fora.

---

### Post by scourge on 2009-01-22
> **ajackson said:**
> It was a way of showing your appreciation to the people who have helped you out or posted very useful information.

At least that's what it was supposed to be at first. In reality the thanks feature meant "this person is my friend and agrees with me on everything, so I'm going to thank him for every post he makes".

---

### Post by nvteighen on 2009-01-22
> **ajackson said:**
> (...) It let you show some basic manners, something lacking on most internet **fora**.

Yeah! Someone using the proper plural of "forum" :D Where's the "Thanks" button? :(

Ok, on topic. It was a bit annoying, because sometimes people ended up giving their thanks with the button and also with a post... And the button was meant to eliminate "Thanks" posts that could mess the thread.

Possibly an anomymous or, at least, a static (i.e. no "revoking") thanking system wouldn't be that expensive, I guess...

---

### Post by ajackson on 2009-01-22
> **scourge said:**
> At least that's what it was supposed to be at first. In reality the thanks feature meant "this person is my friend and agrees with me on everything, so I'm going to thank him for every post he makes".
For some people that might be what happened but for others it was a genuine thank you for your help system. I doubt you'd ever get a system that some people wouldn't try to abuse.

---

### Post by scourge on 2009-01-22
> **nvteighen said:**
> Yeah! Someone using the proper plural of "forum" :D

"fora" is the correct Latin plural, but in English "forums" is correct as well. I like "forums" more because it sounds more like English, and because I want to distance myself from people who invent their own stupid pseudo-latin plurals like "virii" and "boxen".

---

### Post by scourge on 2009-01-22
> **ajackson said:**
> For some people that might be what happened but for others it was a genuine thank you for your help system. I doubt you'd ever get a system that some people wouldn't try to abuse.

We still have a pretty good system for thanking someone. Just type "Thank you" in the message box, and hit "Submit Reply" ;) That's how we did it in the good ol' days, and it worked.

---

### Post by mister_pink on 2009-01-22
I don't think it had anything to do with forum load - the thanks and solved features are not a core part of the board but 3rd party add ons. The board kept crashing, and the logical thing to do to try and find a problem is the strip things back. Turns out they were an issue, its possible a bug. 

Either way, it makes sense for them to use the standard software if they're having problems as the company that sells the software is unlikely to offer technical help if you're running any addons.

---

### Post by stevescripts on 2009-01-22
> **scourge said:**
> We still have a pretty good system for thanking someone. Just type "Thank you" in the message box, and hit "Submit Reply" ;) That's how we did it in the good ol' days, and it worked.

Indeed, and that was the *implied* messages of this thread ...

Steve

---

### Post by fiddler616 on 2009-01-22
I don't know...I really liked the *feature* of thanking (as opposed to always just posting). It was a bit more subtle, it gave you something tangible to appreciate ("I've helped someone out __ times!") and it also let you recognize if someone was genuinely helpful most-if-not-all of the time (LaRoza), or just had a lot of posts (this happens. Case in point: me).
But some forum is better than no forum at all, so I fully agree with the management's decision.
---
Marking things as solved just saved time--both for helpers, and those seeking help. Is there really much to be said?
---
+1 to whoever encouraged common courtesy.

---

### Post by MockY on 2009-01-22
One good thing that I think the Thank You system increased was enticement. Yes, people here in the forum are very helpful and friendly and really don't need a carrot of any kind in order to help out, but I think some people went an extra mile to solve someones problem. I have nothing to base this on, but isn't that human behavior after all?
Overall, the system served no real purpose, but was a nice touch.

The SOLVED thread capability however served a purpose. It makes it easier for people to find an answer to a particular issue. But I much rather have a stable forum than that feature back.

---

### Post by Wybiral on 2009-01-22
I mostly just liked it because it reduced noise. Having 15 thanks on a post vs 15 "+1"s or "nice post"s is much more pleasing to the eye.

---

### Post by fiddler616 on 2009-01-22
> **Wybiral said:**
> I mostly just liked it because it reduced noise. Having 15 thanks on a post vs 15 "+1"s or "nice post"s is much more pleasing to the eye.
+1

---
Case in point.

---

### Post by Wybiral on 2009-01-22
> **fiddler616 said:**
> +1

---
Case in point.

I agree

---

### Post by CptPicard on 2009-01-22
+1

---

### Post by fiddler616 on 2009-01-22
+1 for satire.

---


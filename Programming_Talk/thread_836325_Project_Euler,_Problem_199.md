---
title: "Project Euler, Problem 199"
date: 2008-06-21
forum: Programming Talk
---

### Post by Lster on 2008-06-21
Hi!

As the title suggests, I'm stuck on Project Euler Problem 199. Geometry is one of my weak areas and this one is fully of it!

[http://projecteuler.net/index.php?section=problems&id=199](http://projecteuler.net/index.php?section=problems&id=199)

Let me explain what I've done so far. If we say that the container has a diameter of 2 units, the first three circles that we start with (colored pink in the diagram) have a diameter of 2/(1+2(&#8730;3)/3)*.

This simplifies to: ???. So we can easily work out where the first circles are as vectors or something.

The other thing that I that I found was that, if we know where three circles are, we can work out the position of the center of the new circle by putting a kind of triangle round it (as my diagram shows). It would be quite easy to do some sort of intersection to find the new circle's radius.

The bit I'm especially having difficulties with is how we could find the radius or center of a new circle when it is bound by two circles and the container circle. How would I do such a thing?

I've also considered whether each circles iteration's radius can be computed by the two of three circle's radius that made it (and maybe the iteration number). That way summation would be trivial as the number of circle increases four times, each iteration.

I think this might be quite easy, when looked at in the right way, but my brain just can't get around the problem!

Thanks,
Lster

*According to the second table on [http://mathworld.wolfram.com/CirclePacking.html](http://mathworld.wolfram.com/CirclePacking.html) and a little algebra!

---

### Post by nvteighen on 2008-06-21
Have you looked on [http://mathworld.wolfram.com/TangentCircles.html?](http://mathworld.wolfram.com/TangentCircles.html?)

Good luck! (I'm very bad a Geometry... and one math teacher told me: "Only those who know Geometry, really know Maths")

---

### Post by Lster on 2008-06-21
Thanks for the link but I've seen it already.

I'm really stumped on this one. Nothing I try seems useful!

---

### Post by Lster on 2008-06-22
Well, I've got a bit further with the geometry and have now derived three equations in terms of some already known quantities.

In the equations that follow:

(x,y) is the center of the new circle.
r is the new circle's radius.

(a,b) is the center of on of the boundary circles.
o is the radius of that circle.

(c,d) is the center of the other boundary circle.
p is its radius.

The attached PNG shows what I mean better.

But from that I managed to derive these equations:

(x-a)² + (y-b)² = (o+r)²
(x-c)² + (y-d)² = (p+r)²
x² + y² = (1-r)²

So I have three distinct equations and three unknowns (x, y and r). I'll try to solve it if I can, but it looks quite hard!

I'm still interested to know if there is another method for finding this - it seems I'm taking an awfully long winded way.

---

### Post by Noitues on 2008-06-23
Try this link.  
[http://mathworld.wolfram.com/DescartesCircleTheorem.html]("http://mathworld.wolfram.com/DescartesCircleTheorem.html")
This Descartes Circle Theorem seems as if it may be helpful.  Curvature?  Don't remember that in trig class.

---

### Post by Lster on 2008-06-24
Nice find - I'm not quite sure how to use it though. I'm only just getting onto more "advanced" calculus.

???

[QUOTE=Wikipedia, Curvature]The primordial example of extrinsic curvature is that of a circle, which has curvature equal to the inverse of its radius everywhere.[/QUOTE]

So does that mean r = 1/C? That would be my guess.

I think we're close! :)

---

### Post by Noitues on 2008-06-24
Yeah, so I have been working on it a bit, and I think the curvature idea can replace the need to find the location of the center of the circle.  Since the problem only requires us to determine the area of the circles, all we need are the Radii.

EDIT:  So I forgot to say... Yes curvature is just 1/(radius).  So as such with descartes theorem we can determine the Radius of the new circle given the surrounding circles.

---

### Post by Lster on 2008-06-24
So far, no avail! :(

---

### Post by Noitues on 2008-06-24
Not sure how you coded it but let me run through how I did it.

I did it by types of Spaces created.  Try to determine what types of spaces will be created with the creation of each new circle.

By the way, I got the answer using Matlab in 0.8 sec.  I will be following this thread, so ask more questions.

---

### Post by Lster on 2008-06-25
I've done it myself now. I had an error in the formula I was using (I miscopied it from Wikipedia!). :)

---

### Post by ed_r on 2008-06-25
For the sake of keeping PE solutions secret, could you try not to post big hints (*e.g.* Descartes theorem) or your solution methods in public?

It would be best if you could use the PE discussion forum ([http://forum.projecteuler.net](http://forum.projecteuler.net)) for this sort of thing: lots of people willing to help, but always careful not to give spoilers away!  Or if you prefer to stay on a forum that feels more like home, please try to follow the PE discussion forum's (unwritten) rule of non-disclosure.

Finally, if you must give away big spoilers, it would be much better to do that by private message than by public posting.

Thanks! :cool:

---

### Post by Lster on 2008-06-25
I see nothing wrong with what is shown here. I don't want to encourage cheating but effectively anyone who just wants a copy/ paste answer is only cheating themselves. Spoilers, to some degree, are obviously likely to appear in a thread named similarly to this, so I can't see it ruining anyone's satisfaction by giving it away early unless they chose to look.

Essentially, I see no reason this would be objectionable in anyway unless Project Euler was viewed as a competition in which case it would indeed be cheating. However, I don't do Project Euler for that reason.

And specifically, the only real help that has been offered here was the link posted by Noitues, the relation of a circle's radius to it's curvature and a little working in my initial post (rationalizing the reciprocal of the inner three circle's radii). Except possibly for the last point, the rest is just reference - which unless you know about it, might not be found. That would surely be worse than finding a couple of pointers on what to look at... :)

I'm interested in your why you seem to see this as detrimental to Project Euler.

All the best,
Lster

---

### Post by ed_r on 2008-06-25
There's a difference between Googling (say) "tangent circles", *versus* searching for "project euler" + "problem 199".  IMHO, the former is research; the latter is cheating.  As you wish not to encourage cheating, I can only ask that you cease supplying pages that are cheaters will latch on to.

You're correct that it's not a competition, but PE does have a high-scores table and people do take pride in solving problems honestly to claw their way up the rankings (however high or low).

If you think that I'm being overly protective then by all means raise the question of disclosure on the PE discussion forum.

---

### Post by Lster on 2008-06-25
I don't think that properly addresses my point. I didn't have any knowledge of the problem posted Descartes' Circle Theorem and spent ages unsuccessfully researching for the problem. None of that time was well spent - I didn't learn throughout that. I can see nothing but benefit to providing small pointers like these (in fact, sometimes I think a quick reference to relevant information would be a great improvement to Project Euler - something like the Roman Numerals FAQ).

I think I'll remove a little of the first post so it isn't quite so obvious - I hope that goes as a kind of compromise.

You said earlier about posting in the forums at Project Euler, which I may do. But to be honest the help I have received here was excellent.

[QUOTE=ed_r]If you think that I'm being overly protective then by all means raise the question of disclosure on the PE discussion forum.[/QUOTE]

I know that all the contributers, and I believe you are one of them, work really hard to make Project Euler what it is. So I suppose it is natural to be quite protective of it. However, I don't agree with imposing one's opinion on others and it does *feel* like well-mannered coercion to me. ;)

My ideological views seem not too dissimilar to your own; however I believe that if people want to cheat - let them (it's not beneficial to them except in an extremely superficial way).

---

### Post by ed_r on 2008-06-26
Kind of you to remove your partial answer but, as you pointed out, it is Noitues' first and third responses that are the most revealing.  Those really do count as "disclosure" in my view and are what I'd prefer were pm'd rather than posted.

We seem to disagree that this thread (as it stands) is a potential resource for cheaters.  If I can't convince you* of that then I suppose I'll have no further luck seeking your cooperation.

*[SIZE="1"]*: all "you" reading this, not Lster in particular.[/SIZE]*

---

### Post by Lster on 2008-06-26
[QUOTE=ed_r]We seem to disagree that this thread (as it stands) is a potential resource for cheaters.[/QUOTE]

I do think it a potential resource for cheaters - but if anyone wants to cheat, why stop them? It affects no one else and, although it's a shame, I would guess they are unlikely to benefit from Project Euler anyway.

---

### Post by ed_r on 2008-06-26
We can't *stop* cheaters, but we can stop *helping* them.  Can, but won't, it seems.  I'm disappointed.

---

### Post by Lster on 2008-06-26
What would you like to happen? I will try to accommodate your requests.

If you things are still inappropriate in your opinion, maybe you should contact a moderator requesting your desired action.

---

### Post by Noitues on 2008-06-26
I apologize I have not been following this till now.  What would you like me to do?  I understand your point in that you do not want to assist cheaters, but at what point do we detriment those truly trying to collaborate on these difficult and fulfilling problems?  There is a fine line and if it has been crossed in some of my posts I will attempt to edit them.  

I would like to thank Project Euler for this problem.  Very Fun.

EDIT:  I have removed some of the more in-depth explanations that could have been saved for PM's.  I did however leave my first post, as the link was really only one of the goto links at the bottom of one of the previously linked links, so hardly the in-depth search.  If you feel different please let me know.

---

### Post by ed_r on 2008-06-26
OK, thanks both of you for bearing with me.

You asked what to change.  For this thread, nothing.  I mean, ideally I'd want to remove all references to Descartes Theorem but I don't want to p*** you off any more with edits.  But for the future, by all means ask for clarifications, hints or outright spoilers, but please don't *respond publicly* with any give-aways.

I don't think that anything more that I say here will help, so please check out the PE discussion forum if you want to see examples of the level of (non-)disclosure that I'm after.

Thanks again, and happy solving!

---

### Post by Lster on 2008-06-26
It's fine. Don't worry, I'm not irritated that easily! ;)

[QUOTE=ed_r]Thanks again, and happy solving![/QUOTE]

I will enjoy Saturday's problem 200. It seems like we have a treat in store? :)

---

### Post by ed_r on 2008-06-26
Yeah, number 200 should be interesting.  I'm quite excited about it because, AFAIK, it's not a problem that the development subteam has been involved in (we normally see all problems but don't know their release schedule).  I think that the core admins have been hatching secret plans behind our backs!

---

### Post by Lster on 2008-06-26
How many of you (developers and admins) are there?

I'm nearly finished on problem 184. The spatial patterns were killing my brain but I've simplified it nicely now. Geometry and stuff like that has always been a weakness of mine. :)

---

### Post by hklein on 2008-06-26
Hi guys,
 I am the one known as hk on Project Euler, but this forum insists on user names with more characters.

It seems that you guys like to cooperate at solving PE problems.
The only problem is that you do that viewable for the entire world for ever after and easily Googable too.

Aren't there other ways to  cooperate in a less public way?
A few suggestions:
-You could  use the forum [http://forum.projecteuler.net](http://forum.projecteuler.net) to send each other PM's
-You could send each other emails using the main project euler website.

Perhaps other means can be invented to make easier communications through PE. If I can help I will gladly do:
I have full rights for the forum at [http://forum.projecteuler.net](http://forum.projecteuler.net).

One word though: show perhaps some more perseverance at solving:
Indeed the Mathworld page first mentioned in this thread contained links to other Mathworld pages that give all needed to solve this problem...

Happy solving
hk

---


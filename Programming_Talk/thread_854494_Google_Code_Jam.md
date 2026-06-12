---
title: "Google Code Jam?"
date: 2008-07-09
forum: Programming Talk
---

### Post by AOZ on 2008-07-09
Lets see how many ubuntu junkies are going to participate this year...

---

### Post by jingo811 on 2008-07-09
What do you guys usually do when you code jam?

---

### Post by AOZ on 2008-07-09
Go [here]("http://code.google.com/codejam/contest/") for more info.

---

### Post by pmasiar on 2008-07-09
Rapid problem solving - perfectly suited for Python.

Seems to me that Google cannot hire enough Python hackers, so they try to identify potential recruits.

---

### Post by jim_24601 on 2008-07-10
> **jingo811 said:**
> What do you guys usually do when you code jam?

Well, you start with your code and about 6 pounds of sugar in a saucepan...

---

### Post by jingo811 on 2008-07-11
That's what I suspected. :)  But I thought bread and [wafers]("http://www.answers.com/topic/wafer") would be involved somehow, I don't see any mention of bread and wafers anywhere?

---

### Post by kknd on 2008-07-15
Since performance isn't such a big issue as usual programming contests (ACM contests), and you can "do what you want", if you can output the correct awnser, scripting languages will help alot (alone or healping outher implementations)! I'm using Lua to the training here.

---

### Post by Wybiral on 2008-07-17
Yay, I passed the qualification round! Did anyone else from around here qualify?

---

### Post by samjh on 2008-07-17
Gonna try it as soon as my Ubuntu installation is fully updated (just reinstalled). :)

---

### Post by Sinkingships7 on 2008-07-17
What?! This is sweet :D

I'm not quite up to task now, but I hope to participate for sure next year!

---

### Post by kknd on 2008-07-17
> **Wybiral said:**
> Yay, I passed the qualification round! Did anyone else from around here qualify?

Hi, I passed too (50 points). I didn't tried the 3º problem (too lazy :)).

Did you or anyone else here solved the last one?

---

### Post by Wybiral on 2008-07-17
> **kknd said:**
> Hi, I passed too (50 points). I didn't tried the 3º problem (too lazy :)).

Did you or anyone else here solved the last one?

lol, nope, we're in the same boat. The first two weren't too bad (well, the second one was until I realized the trick to it) but I'm terrible with geometry problems like that and with little time left to freshen up, none of my ideas worked out too well (I eventually just tried simulating it with a geometry module, but the results weren't accurate enough by about 0.01 or so).

---

### Post by samjh on 2008-07-18
Ah, registration closed 7 hours ago.  Bugger. :(

I'll keep it in mind for next time though.

Good luck Wybiral, kknd, and AOZ. :)

---

### Post by themusicwave on 2008-07-18
Doh!

I totally forgot about code jam.  I was registered, but I was supposed to do 2 days ago.

I guess I won't be qualifying...0 points for me!

---

### Post by azredwing on 2008-07-25
I'm in, totally stoked and totally not gonna do so well. I qualified on the timetable problem, that's it. I attempted the fly swatter but it continues to elude me (on the other hand, I'm now a PRO at finding Perl modules to do stuff!). Haven't really looked at the other qualifier problem.

I did try the other practice problems up (albeit I didn't spend a whole lot of time on them). So far, I have gotten ONE.

I figure I won't do so well right now, but that's okay -- I'm not even a programmer by nature (aerospace engineering is my forte). It'll be fun to waste time on brain teasers later, though.

My round's in just under 2 hours. Here we go!

---

### Post by vexorian on 2008-07-25
> **pmasiar said:**
> Rapid problem solving - perfectly suited for Python.

Seems to me that Google cannot hire enough Python hackers, so they try to identify potential recruits.
It backfired then, since like most of these contests the top is full of C/++ coders :)

I got 75. Let's see how I do tonight...

---

### Post by azredwing on 2008-07-26
I'm in! Rank 487 and the top 840 advanced! (ssi.ide27 if you want to look me up)

Who did subround 1A?.. I got the dot product problem within 10 minutes; The one with the nth-power was pretty easy, but since I'm using Perl I had to get Math::BigFloat to deal with it. In retrospect, I should have probably used a divide-and-conquer technique; brute forcing with BigFloat was fine when the power was limited to 30, but got nowhere at power = 2,000,000... I didn't even attempt the milkshake problem.

---

### Post by dogbox on 2008-07-30
anyone else here doing round 2?

and on the topic, can someone explain how to do problem B for round 1C? some solutions use a memoized recursive call which i can't really understand

---

### Post by vexorian on 2008-07-30
> The one with the nth-power was pretty easyUnless you wanted to also get points for the large input...

> anyone else here doing round 2?I'd say azredwing will, me too.

> can someone explain how to do problem B for round 1C

Edit: sorry, I put a large explanation, but for another problem, so, maybe later I'll try 1C-B, I am busy with the one I thought you were talking about...


Edit: Ah, ok. If we took an easy subcase it would be (string portion,the current sum). However, the current sum can get pretty large (or negatively large) so we can't easily do memoization on the 40 digits case (notice it is possible in the 13 digits one to just have the sum and some map/hash) 

But we don't need the sum, we only need the sum%210 (because 2*3*5*7=210) then it is all set.



 You don't need the whole previous sum, you just need the previous sum%210 (2*3*5*7=210).

---

### Post by dogbox on 2008-07-31
of course for the large :) all of the small ones could pretty much be solved by bruteforce (which is what i did)

yeah, i figured it out (looked at someone else's code). it's pretty tricky

btw, i recognize your handle from topcoder :)

---

### Post by vexorian on 2008-08-02
So, how many ubuntuforums users made into round 3? I almost didn't, I wasted about half of the time thinking I could solve problem D with a [2^16][16][16] dp, but it seems I underestimated the effect of the length of the string.

Edit: Just advanced to the semifinals!

---


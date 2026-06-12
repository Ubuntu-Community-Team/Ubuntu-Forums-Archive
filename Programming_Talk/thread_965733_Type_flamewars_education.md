---
title: "Type flamewars: education"
date: 2008-10-31
forum: Programming Talk
---

### Post by ZylGadis on 2008-10-31
I just read through eight pages of the most recent so-called discussion about types, testing, Python is leet, Java is the devil, etc. All the usual suspects plus a few new people participated. In addition, almost every single participant made at least one horrible factual or terminological mistake that typically swept the discussion away.

I said "almost" in the above paragraph because I did not actually bother enumerating everyone and his/her mistakes, but I am pretty sure the "almost" is unnecessary.

Please, please educate yourselves. Otherwise you are just wasting time.

I've been meaning to write something on the topic for a while now, but I have not had the time (and, frankly, I did not see the point) to do so. Fortunately, someone saved me the trouble: [http://www.pphsg.org/cdsmith/types.html]("http://www.pphsg.org/cdsmith/types.html") . I have never heard of the guy, which probably means he is not an "expert," but his explanations of basic terminology are correct. Which is all that matters.

Go and read the thing. NOW.

P.S. One thing he does not make really clear is the difference between static and dynamic typing systems. In short, they are orthogonal. The opposite of a "static typing system" is not a "dynamic typing system," but rather "lack of a static typing system." The world is full of languages that feature both. Java is one (yes, pmasiar, Java is a dynamically typed language -- look up "method dispatch").

---

### Post by Delever on 2008-10-31
Here we go again :popcorn:

Yeah, I don't know everything, I agree. I bookmarked your link.

---

### Post by CptPicard on 2008-10-31
> **ZylGadis said:**
> 
I have never heard of the guy, which probably means he is not an "expert," but his explanations of basic terminology are correct. Which is all that matters.

Bah, you're just arguing from authority!

You need to type up everything yourself and it better be all 100% factual and even then it's just your opinion because you're not backing it up with anything! And if you did, you'd again be arguing from authority!

;)

---

### Post by pmasiar on 2008-10-31
> **ZylGadis said:**
> difference between static and dynamic typing systems. In short, they are orthogonal.

Thanks for the link.

Covers important fallacies: 
- Dynamically typed languages are weakly typed
- Dynamically typed languages provide no way to find bugs

That was exactly the point I argued for in [http://ubuntuforums.org/showthread.php?t=962611](http://ubuntuforums.org/showthread.php?t=962611) . Obviously I am not expert enough to write such articles (and if I would, I would not waste time hanging on this forum ;-) ), but I am not sure if I deserve to be beaten up to pulp for post true in 70% when people attacking me did not post anything better against the wrong opinion. Seems a lot of ego going around, people want to "stick it to me" instead of uncovering the "truth".

---

### Post by samjh on 2008-10-31
It doesn't matter whether or not you're a [published] "expert".  If you know the subject, you know the subject. :)  A lot of book authors aren't really more expert than the average programmer; same for a lot of the "hackers" who are semi-worshipped in the FOSS community.  Truly outstanding experts are few and far between, and most of them stay quiet.

The problem is when a person who knows the subject matter, but has only an opinion, tries to push that opinion as a fact.  This is typically for opinions that have no proven facts, such as the superiority of dynamic over static typing and vice versa, or whether C or Python are better for teaching beginners.

I think everyone should be mindful of the fact (that word again) that opinions are just opinions, and they can differ even amongst experts in topics that have been plentifully studied.  Scientists can reach two different conclusions even when looking at one set of results from a study.  How much more when there are no studies and evidence is only anecdotal?!

@ OP: Nice link!

---

### Post by CptPicard on 2008-10-31
One of the big problems is the insistence on "facts" that are just somehow handed to us from some source, that should then supposedly be authoritative enough (and it seems to never be).

If we did have hard "facts" that could be used, then there probably would just be a website somewhere saying that "RMS/Linus Torvalds says that language X > Y" and that would be it.

However I do not think that the lack of these sorts of facts renders the discussion meaningless, as seems to be often suggested. Sharing of viewpoints and persuasive argumentation can be just as valuable, and it is even more useful when backed up by material from outside that contributes more viewpoints. This of course means that the material needs to be read and understood, and all these "argument from authority" -complaints are cop-outs, no matter how high-brow they sound.

It really is not some strict logic-game that you try to win on procedural arguments, or if you can't, claim that there is no information there whatsoever...

---

### Post by Alasdair on 2008-10-31
I have linked to that article several times in the past, but I think it mostly just got ignored... :)

---

### Post by LaRoza on 2008-10-31
I'm an expert. Next time there are disputes, ask me and I'll settle it. 

Why I'm I the expert? Not because of knowledge, but because of power :evil:

Seriously, what sort of authority would have the opinion that people listen to? People don't accept ESR, PG, or others because that is just "Argument from Authority" (not really, but they say it is).

So it seems we need someone with an Iron Fist. Ask me, the not-all-knowing Oracle (or, MySQL).

---

### Post by ZylGadis on 2008-10-31
An "expert" saying something does not necessarily make it true (for any value of "true") and, by transitivity, worth processing.

Humans tend to look up at those they perceive as succesful, with the unconscious hope of emulating them one day. This simple human behavior is fallacious at so many levels I won't spend time on them. People must learn to judge by themselves, as opposed to relying on someone else's judgement.

So forgive me if I do not immediately accept e.g., Paul Graham's **opinions** as universally true. I have my own, thank you. Sometimes they may coincide with his, sometimes they may be opposite, sometimes I won't care for the topic enough to form an opinion at all. The same stands for Joe Sixpack's opinions. To me, attaching an expert's name on something is not an incentive to process the something, not to mention accepting it.

Or, in short: opinions must stand on their own merit, not on their author's; and merit is only estimated by the processor (reader/viewer/etc).

This is the root cause against authoritative links. Compare:

Paul Graham says Blub programmers are idiots, go read him to enlighten yourself!

with:

Here is an interesting opinion (link) that might provide another point of view to our discussion.

It is not about winning a game. It is about respect. These are my first two posts here since June (I think) for exactly that reason.

---

### Post by LaRoza on 2008-10-31
> **ZylGadis said:**
> 
So forgive me if I do not immediately accept e.g., Paul Graham's **opinions** as universally true.
No, but reading his reasoning for the opinion is worth reading instead of decrying any suggestion to read it as "Arguing from Authority". Not saying you did this, but many do.

> 
Paul Graham says Blub programmers are idiots, go read him to enlighten yourself!

with:

Here is an interesting opinion (link) that might provide another point of view to our discussion.

Programmers are almost universally not people to play word games.

---

### Post by CptPicard on 2008-10-31
> **ZylGadis said:**
> To me, attaching an expert's name on something is not an incentive to process the something, not to mention accepting it.

The other day I was just looking for a good explanation of a certain algorithm, and I knew that a certain professor writes stuff about that field, so I went to check out his bibliography and behold, he has written a book on the topic... off to Amazon.

Yes, his name is very much incentive for me to process his views on this, and I also believe that what I learn will not reduce to "he says this so.." but ... actual understanding of what he writes about in his book.

I also have enough respect for professors that I don't go suggest that they are wilfully lying at my face with their "opinions" and that they don't matter, even in cases where the opinion may actually consist of some sort of hand-waving and not a formal proof :)

---

### Post by HotCupOfJava on 2008-10-31
"Expert" - a has-been drip under pressure...........

---

### Post by nvteighen on 2008-11-01
Arguments from Authority are those that try to give reason of something just because someone used the same argument you do.

But, if you quote some authority's thought (neutral term for argument, opinion, etc.) and then you give your own arguments (no matter whether correct or not) backing that opinion, that's not the Argument from Authority (*Fallatia ad Auctoritatem*). Or, when you quote the authority's thought along with his/her arguments.

Remember that a fallacy ocurrs when there's a "bug" on the logical reasonale of a certain thesis. Plainly wrong, but logical arguments are not fallacies... just bad or insufficent arguments.

---


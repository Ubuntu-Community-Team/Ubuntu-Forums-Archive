---
title: "Interesting in helping create a MUD client?"
date: 2007-09-16
forum: Programming Talk
---

### Post by Vadi on 2007-09-16
The issue at hand is simple enough; native linux mud clients are lacking. For us people who like nice maps, easy to use syntax, and fancy looking gui's that go well with our desktop effects.

I was on a 'mission' since switching completely to Linux for a good MUD client, and here are my findings:

1) I play Achaea, which has their own custom client. It's written in Java, so it works on all platforms. It, as I would think, has the nicest looking GUI - they had a professional artist do it ([screenshot]("http://www.ironrealms.com/nexus/help.html#N10064")). However it has a limited scripting language of it's own, doesn't support any others, and has no mapping ability at all.

2) zMUD. It pretty much by itself holds half of the share of mud clients used on Windows. Out of the box, it installs and runs fine with Wine, but it's poor scripting performance suffers even more in Wine.

3) MUSHclient. Even though it's labelled as wine-friendly, I find that it's performance dips the same as zmud. The main problem is the way it handles outout display - if there is a lot of text coming, it'll display the last displayed line (usually your prompt) x times, and then substitute it all with the text that came at an undreadable speed. This problem is especially shown when running in Wine, where even single lines seem to lag.

4) No other windows clients offer necessary features, so I won't be analyzing them (yes, I'm aware of tf, tintin, al client, etc.). Onto linux clients then. Searching 'mud' in add/remove, I get two mud clients - gmud and kildclient. Let's start with gmud first. It has a mapping ability, albeit I don't know how good is it, didn't test much. The two flaws that let it down is that a) you can't copy from the output window, and b) if you're trying to create aliases in gmud, they're highlight limited - there's a limit even on their size.

5) Kildclient - it even lags on displaying text the first time you start it up, without any triggers to match. I haven't used it after that point too much.

6) xpertmud - not avialable as a .deb file nowhere that I found. Has a powerful scripting interface, but again, you can't copy from the output window, and no mapper.

7) kmud - not developed for a while, no .deb either. :(

8) there are -tons- of little clients, and none that I found fill the job of a client that "has it all". While one certainly wouldn't hurt, and here's what I'm thinking:

Would anyone be interested in working on a MUD client, that has all features that a modern mud client needs?

I'm thinking of:

-- scripting language support for popular languages (perl, python, lua, etc.), plus, it's own, non-tech user friendly language - and the scripting part definitely must be efficient.

-- highly user-customizable GUI, because the days of playing in telnet should be over. Buttons, labels, panels so that creative users can make nice-looking interfaces.

-- mapper. Could be a purely text-based one or one like the zMapper, but a good mapper is a must.

-- have a usable UI. One of the pitfalls of MUSHclient is that it's really not user friendly. It doesn't even support Ctrl+A, you get the idea.

That's about it that's needed for a good, in my opinion mud client. Unfortunately, no linux clients currently have *all* of these features. So why not make our own?

There are of course tons of itty-bitty details that'll make the client stand out, but those only should be discussed is there's interest.

If anyone is interested in helping out, please post. :)

---

### Post by Visti on 2007-10-04
Hi Vadi! I don't know if you've seen [my post]("http://ubuntuforums.org/showthread.php?t=532786&highlight=mudding"), but I'm basically looking for exactly the same thing. I'm not even too big on the mapping functions or anything like that, but I still think Zmud (Or Cmud now) is way superior to any native Linux client and it's all down to an appealing interface. Now, it's not like Zmud is amazing to look at by any means, so I just can't believe that there aren't anybody that can pull this off.

Oh, and for me the biggest feature in Cmud is integrated mudlist.. New fun instantly available at your fingertips.

Edit: Yikes! That Achaea client looks like a dream..

---

### Post by Vadi on 2007-10-04
Oh, no, no I didn't.

Guess what though! I found *the* best native linux mud client, who's author is aiming to have the best. It's really good! Very nice interfate, supports a ton of scripting languages plus has it's own, which is easy to use, and has gauges, buttons, and mapper... it's like the best of zmud and mush.

It's called KMuddy - the website is kmuddy.com, and you can get the .deb package for it from getdeb.net.

As for the intergrated mudlist - it doesn't have that feature yet, *but*, I asked mudconnector.com to send me one, as soon as I get it, I'll implement it in. It's definitely a great feature :)

Oh, and kmuddy has a decision assistant. That's a killer feature.

So, get kmuddy - I sent you a pm with my contact info so we can get in touch. Or, just register on kmuddy's forums.

---

### Post by nothingxs on 2007-10-28
I would suggest branching off of Kildclient and changing the way it renders text. The text renderer is pathetically slow (for comparison, use Mud Master 2000 on Windows, available at mmgui.com, to see what I mean by rendering speed), and there's no mapping functionality -- but that seems like it could be developed as a standalone plugin.

Kildclient really seems pretty powerful and has a lot of good features, but I think what kills it is how slow the text renders.

A good idea may be to just port MMGUI to Linux...

---

### Post by Vadi on 2007-10-28
No, like I said, I've settled on helping develop kmuddy - I compared the features of both, and kmuddy by several factors went ahead :).

I don't believe that porting mmgui either would be such a grand idea. What would be much better is porting kmuddy to windows, which is in plans ;)

Give it a try - I think you'll really like it. There are .debs on getdeb.net.

---

### Post by Vadi on 2008-09-26
Yeah, so, nearly a year later a serious effort has begun: [http://ubuntuforums.org/showthread.php?p=5861253#post5861253](http://ubuntuforums.org/showthread.php?p=5861253#post5861253)

---


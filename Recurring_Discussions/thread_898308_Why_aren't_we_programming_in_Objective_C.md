---
title: "Why aren't we programming in Objective C  ?"
date: 2008-08-23
forum: Recurring Discussions
---

### Post by stream303 on 2008-08-23
In a recent interview with Mark Shuttleworth, my eyes bugged out when I caught him wondering why Objective C wasn't used more in the open-source world:

[http://matthewhelmke.net/wordpress/2008/07/13/an-interview-with-the-sabdfl/](http://matthewhelmke.net/wordpress/2008/07/13/an-interview-with-the-sabdfl/)

In the recent past, things like NextBuntu were proposed and got a little bit of traction, but I think that we got caught up in GnuStep and Apple, and not striving to seek our own path with Objective C.  Surely these two could provide guidlines, but I'm wondering with the amount of talent I've seen here, instead of just trying to duplicate what has already been done, perhaps Rick 1 was on the right path:

[http://ubuntuforums.org/showthread.php?t=214470](http://ubuntuforums.org/showthread.php?t=214470)

Since I am not a programmer, I am wondering why Objective C seems to have been abandoned.  Is it just because that NeXT / OpenStep / Apple ultimately failed to sustain a commercial product (I don't count the current OSX to be following the ideals of programming and interface as OpenStep).

Can a discussion of the pros and cons of Objective C be found from programmers where the discussion of Objective C don't revolve solely around Apple and GnuStep?

So maybe my real question is why aren't we using it today?  Is it really that bad, or is it just not *fashionable?*

---

### Post by scourge on 2008-08-23
> **stream303 said:**
> So maybe my real question is why aren't we using it today?  Is it really that bad, or is it just not *fashionable?*

I'm not using ObjC because it lacks the cross-platform libraries and toolkits that I need. I think the language itself is great, and I'd definitely use it if it had wxWidgets and/or Qt bindings.

---

### Post by nrs on 2008-08-23
Because it's as ugly as sin. No. It just isn't that great a language, it's not bad, but it's not great, so it just got crushed by the momentum of others, some of which aren't particularly that great either, but at least were entrenched.

Re-writing the X server, and making its successor a standard is probably about 100 times more feasible than persuading everyone to switch Objective-C considering the state of non-OS X libraries.

---

### Post by NovaAesa on 2008-08-23
Dynamic weak typing system... what can I say. Also, I don't know anyone else that uses it, so it would be a bit hard to work on a colaborative project with it.

---

### Post by samjh on 2008-08-23
> **stream303 said:**
> Since I am not a programmer, I am wondering why Objective C seems to have been abandoned.  Is it just because that NeXT / OpenStep / Apple ultimately failed to sustain a commercial product (I don't count the current OSX to be following the ideals of programming and interface as OpenStep).

Can a discussion of the pros and cons of Objective C be found from programmers where the discussion of Objective C don't revolve solely around Apple and GnuStep?

So maybe my real question is why aren't we using it today?  Is it really that bad, or is it just not *fashionable?*

I have never used Objective-C.

But in the mid and late 1980s, C++ was gaining a lot of traction.  C was very popular and C++ was very similar to it.  C++ was designed with UNIX systems in mind, and so it was particularly attractive for existing C and UNIX programmers who wanted more features.  Furthermore, compilers and development tools were relatively low-cost, especially when Borland released their "Turbo" family of developer tools.

Basically, C++ got lucky.  It was - and still is - a good language for what it is designed be.  However there were several other languages that could have challenged it but didn't achieve the same success despite being technically worthy of success:
- Ada (successful in its field, but could have had more),
- Modula-2 and 3 (perhaps always doomed),
- Object-Pascal (had success at Apple but discarded after the fall of Motorola 68k processors),
- and Objective-C.

---

### Post by pmasiar on 2008-08-23
Exactly. Too many languages competing for the honor to be next OO system programming language. And too many platforms too, both hardware (Intel was not the only CPU architecture back then) and software (dozen of Unix clones fighting each other). And Apple's desktop share was steadily decreasing, why would anyone placed bet on language for that platform?

And of course obsession with static typing - it is **still** not over yet, 20 years later. :-)

---

### Post by LaRoza on 2008-08-23
Objective C is also a strict super set of C, meaning valid C code is valid Objective C code. So technically, all C programs are Objective C.

---

### Post by stream303 on 2008-08-23
> **LaRoza said:**
> Objective C is also a strict super set of C, meaning valid C code is valid Objective C code. So technically, all C programs are Objective C.

Wow - that gives me hope, as I read casually as a user that many programmers prefer C to C++.  (I'll leave that hot potato for another thread. )

It makes me wonder if many programmers mistakenly view Objective C as just a derivative or close relative to C++, and this confirms that it is NOT.

So now one reason for the lack of activity with it appears to just be lack of momentum, although there are a few additional annoyances that show that no language is perfect.

Hmm... if there were cross-platform libraries available, perhaps more would be likely to use it?

Or like VHS vs Betamax, (going out on a BIG limb here..) pure C is just so entrenched that Objective C would just be too much trouble?

Seems like the classic chicken-n-egg syndrome.  NeXT could bring it about due to corporate backing, but in the open-source world, we are just waiting for someone/group to have the drive to bring it to the plate again.

Edit: it just seems to me that this is the way to go considering the furious pace that hardware is changing.  Then again, this is coming from my limited experience that thinks that subroutines are cool. :)

Anyway, thanks for all the comments - it helps answer some questions I had about the stagnation over something that seemed great.

---

### Post by jinksys on 2008-08-23
> **nrs said:**
> Because it's as ugly as sin.

R'Amen.

---

### Post by stream303 on 2008-08-23
Can we change that ugliness, or is there some fundamental law inside that can't be broken?

In other words, does everyone like the concepts, but not the implementation?  Maybe we can change the implementation?  Or would that mean a fork of Objective C?

---

### Post by LaRoza on 2008-08-23
> **stream303 said:**
> Wow - that gives me hope, as I read casually as a user that many programmers prefer C to C++.  (I'll leave that hot potato for another thread. )

There are many reasons to like C over C++. C++ has some fatal flaws. [http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/)

> 
It makes me wonder if many programmers mistakenly view Objective C as just a derivative or close relative to C++, and this confirms that it is NOT.

It is popular on Macs I hear.

---

### Post by Rick 1 on 2008-08-23
I really don't have time to educate the world (and the more wayward) so let's keep this brief. Save for a few terse phrases and punctuation marks - and the original post by stream303 - this thread has some of the worst most uneducated and gratuitously obnoxious statements I've seen in a long time. It doesn't take a master shrink to understand none of you are professional programmers - much less professional students of programming languages, OO, and the rest. Should anyone be looking into this thread for any type of clue whatsoever on languages and especially OO - LOOK THE OTHER WAY. FAST.

Frankly I'm shocked. And ashamed. And perhaps not coincidentally feel a bit of pity for you.

Let me leave you with the words of Mark Shuttleworth which I believe will put things into their proper perspective.
> My least favourite app... probably GCC, just because **I don't have the clarity of engineering to work in C**! I think it's a great pity that Objective C hasn't taken root more deeply in the free software world. My ideal development environment would have elements of Python syntax all the way from the shell, through the script (Python) and down to the fastest-compiled language.
As I've stated before: Shuttleworth might be filthy rich and still a nice guy but selling software to VeriSign does not a systems programmer make or imply.

And should any of you self-appointed nuisances have something cogent to add to the discussion started years ago by Douglas Engelbart and Alan Kay; should you understand the true nature of languages such as C++; should you understand the latter's etymological derivation (Simula et al) and should you understand how Brad Cox put Objective-C together - then yes by all means let's hear your words of wisdom. But we all know they won't be forthcoming because they cannot by definition exist.

And should any of you punters claim you can do better than Jean-Marie Hullot, Avie Tevanian, and the rest - then by all means again: come forward and let us look at the code you cite. But don't bother pointing to either GNOME or KDE because we will only laugh at you.

If you're not professional - which you ostensibly and painfully are not - what are you doing in this thread anyway?

---

### Post by babyhuey on 2008-08-23
Is objective-c advantageous enough to warrant the change? I don't think so.

---

### Post by nrs on 2008-08-23
> **stream303 said:**
> Wow - that gives me hope, as I read casually as a user that many programmers prefer C to C++.  (I'll leave that hot potato for another thread. )

Goes both ways. I find it amusing how a lot of the C-is-superior crowd make pitiful attempts at emulating features found in C++, but never come close. GNOME/GTK+ && associates are probably the biggest examples of this in the free software world. iD is also a particularly egregious offender. Though I think with >= Doom III they just went with C++.

I'm a C programmer so I'm allowed to say these things. :-)

---

### Post by nrs on 2008-08-23
> **Rick 1 said:**
> I really don't have time to educate the world (and the more wayward) so let's keep this brief. Save for a few terse phrases and punctuation marks - and the original post by stream303 - this thread has some of the worst most uneducated and gratuitously obnoxious statements I've seen in a long time. It doesn't take a master shrink to understand none of you are professional programmers - much less professional students of programming languages, OO, and the rest. Should anyone be looking into this thread for any type of clue whatsoever on languages and especially OO - LOOK THE OTHER WAY. FAST.

Frankly I'm shocked. And ashamed. And perhaps not coincidentally feel a bit of pity for you.

Let me leave you with the words of Mark Shuttleworth which I believe will put things into their proper perspective.

As I've stated before: Shuttleworth might be filthy rich and still a nice guy but selling software to VeriSign does not a systems programmer make or imply.

And should any of you self-appointed nuisances have something cogent to add to the discussion started years ago by Douglas Engelbart and Alan Kay; should you understand the true nature of languages such as C++; should you understand the latter's etymological derivation (Simula et al) and should you understand how Brad Cox put Objective-C together - then yes by all means let's hear your words of wisdom. But we all know they won't be forthcoming because they cannot by definition exist.

And should any of you punters claim you can do better than Jean-Marie Hullot, Avie Tevanian, and the rest - then by all means again: come forward and let us look at the code you cite. But don't bother pointing to either GNOME or KDE because we will only laugh at you.

If you're not professional - which you ostensibly and painfully are not - what are you doing in this thread anyway?

:rolleyes:

---

### Post by samjh on 2008-08-23
> **nrs said:**
> iD is also a particularly egregious offender. Though I think with >= Doom III they just went with C++.

They did indeed.

---

### Post by jinksys on 2008-08-23
> **Rick 1 said:**
> I really don't have time to educate the world (and the more wayward) so let's keep this brief. 

Please, enlighten us... :popcorn:

> 
If you're not professional - which you ostensibly and painfully are not - what are you doing in this thread anyway?

And you are? 

[img]http://www.trendmicro.com/vinfo/images/WORM_MUGLY_F.gif[/img]

---

### Post by dribeas on 2008-08-24
> **LaRoza said:**
> There are many reasons to like C over C++. C++ has some fatal flaws. [http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/)


That FQA page is completely biases and written by someone that understood the syntax but not the language, someone that did not know the idioms, who might have browsed through STL docs but did not fully understand it... Someone that started to program C++ but never really learned. [*]

I read through the first items and that was my conclusions, I could try to argue point by point but I don't have the time for it. 

Now, just point to me one of the 'fatal' flaws as seen by a C programmer and we'll have a common ground of discussion.

[*] C++ is harder to learn than C/Java/.NET/Python I won't discuss it, and that is it's weakest point. I come across a lot of C++ programmers that just do C with some class syntax.

---

### Post by stream303 on 2008-08-24
> **babyhuey said:**
> Is objective-c advantageous enough to warrant the change? I don't think so.

I do, but then again I'm not a programmer.  

Strangely enough, even though Mark wants us to be more mac-like, I think that we are already there - but somewhat roughly analogous to the original Macintosh Mac-OS fashion that has a limited lifespan, unless we decide to learn from history, and avoid that dead end with objective-C.  Much like Jobs learned when he started NeXT after the Macintosh.

Now I will be the first to say thank you to all the devs that made Ubuntu possible on my G5 iMac.  However:

Where will we be in ten years?  Will it just be another addition to desktop environments - having been through Motif, CDE, Gnome, KDE and the like, if something new comes along it isn't going to ring my bell.

Aside from the desktop, I wonder about the underlying system programming itself.  Will we paint ourselves into a corner in 10 years unless we adopt OO in a major way?

Well, food for thought from someone who really doesn't know programming, that's for sure.

---

### Post by mujambee on 2008-08-24
Is there anyone who can give a brief explanation of what can Objective C do that C++ can't?

I've no previous knowledge of Objective C, have just browsed trough a tutorial on it, and save what looks like better support for polymorphism and a garbage collector, I can find no other advantage.

In exchage of that you have to carry that big runtime that does all that messaging, wich will eat cycles as mad. And loose inline expansion, function overload, new/delete operators and some other C++ extensions that are so useful.

Besides, I couldn't agree more with nrs, is ugly as sin.

---

### Post by nvteighen on 2008-08-24
> **nrs said:**
> Goes both ways. I find it amusing how a lot of the C-is-superior crowd make pitiful attempts at emulating features found in C++, but never come close. GNOME/GTK+ && associates are probably the biggest examples of this in the free software world. iD is also a particularly egregious offender. Though I think with >= Doom III they just went with C++.

I'm a C programmer so I'm allowed to say these things. :-)

I really don't consider GLib's object system to be a "pitiful emulation attempt". It's quite a great system for OOP in C, and it quite logically constructed and comes quite close to C++ built-in features; maybe inheritance is their weak point, done through type casting.

My C code, of course, is a constant OOP-ish approach that should be considered **painful** "attempts of emulating features found etc." :) (If you don't believe me, search for some code by me posted in these forums).

---

### Post by nrs on 2008-08-24
> **nvteighen said:**
> I really don't consider GLib's object system to be a "pitiful emulation attempt". It's quite a great system for OOP ***_[SIZE="4"]in C[/SIZE]_***
I agree, it's probably the best your best option for pseudo-OOP, ** in C**. Just like a cardboard box is your best option for housing, if you're homeless. ;-) 

I think they deserve a bit of a break though,  their model is extremely conductive to the creation of things like bindings, and my personal favourite GTKmm (though I still prefer Qt). I doubt it could be accomplished -- at least as easily -- if they had chosen a different model & language

---

### Post by babyhuey on 2008-08-24
> **stream303 said:**
> I do, but then again I'm not a programmer.  

Strangely enough, even though Mark wants us to be more mac-like, I think that we are already there - but somewhat roughly analogous to the original Macintosh Mac-OS fashion that has a limited lifespan, unless we decide to learn from history, and avoid that dead end with objective-C.  Much like Jobs learned when he started NeXT after the Macintosh.

Now I will be the first to say thank you to all the devs that made Ubuntu possible on my G5 iMac.  However:

Where will we be in ten years?  Will it just be another addition to desktop environments - having been through Motif, CDE, Gnome, KDE and the like, if something new comes along it isn't going to ring my bell.

Aside from the desktop, I wonder about the underlying system programming itself.  Will we paint ourselves into a corner in 10 years unless we adopt OO in a major way?

Well, food for thought from someone who really doesn't know programming, that's for sure.


The effort it would take to transition to Objective-C (Libraries, documentation..etc) outweighs its benefits compared to the well established C/C++.
It will take a language more revolutionary than Objective-C to get people put out that kind of effort.

I think people around here are pretty happy with C/C++ and Python combo. 

This is opinion of course. I don't expect it represents everyone but I have a feeling I'm not alone.

---

### Post by mssever on 2008-08-24
> **Rick 1 said:**
> this thread has some of the worst most uneducated and gratuitously obnoxious statements I've seen in a long time. It doesn't take a master shrink to understand none of you are professional programmers - much less professional students of programming languages, OO, and the rest. Should anyone be looking into this thread for any type of clue whatsoever on languages and especially OO - LOOK THE OTHER WAY. FAST.

Frankly I'm shocked. And ashamed. And perhaps not coincidentally feel a bit of pity for you.
<snip>
If you're not professional - which you ostensibly and painfully are not - what are you doing in this thread anyway?
Thanks for a good laugh. Why should I believe that you know any more about this subjects than the people you deride? You didn't provide any technical arguments, nor did you tell us why you're qualified to make such statements. If what you're saying is true, then it's important. But you haven't given us any reason to believe you.

There are some professionals who posted in this thread. But, this is open source, where most work is done by volunteers and what those volunteers do for money is unimportant. What matters is whether they're competent.

---

### Post by CptPicard on 2008-08-24
> **Rick 1 said:**
> 
Frankly I'm shocked. And ashamed. And perhaps not coincidentally feel a bit of pity for you.

Yes, your superiority is so glaringly apparent from your post that I agree that you would probably be better off buying out Novell already so your time would be better spent creating your legacy there. Posting here is a waste of time.

> **dribeas said:**
> 
I read through the first items and that was my conclusions, I could try to argue point by point but I don't have the time for it. 

Yea verily, we are blessed to have amongst us those who don't even need to read any arguments to be able to counter them. :) It's a long text, and makes it very obvious that indeed, there are a lot of so-called "idioms" (work-arounds) in C++ to master...

---

### Post by stream303 on 2008-08-25
> **babyhuey said:**
> The effort it would take to transition to Objective-C (Libraries, documentation..etc) outweighs its benefits compared to the well established C/C++.
It will take a language more revolutionary than Objective-C to get people put out that kind of effort.

I think people around here are pretty happy with C/C++ and Python combo.

I'm pretty happy with it too from a user standpoint.  I dig Linux / BSD, but I'm just wondering if we aren't just as satisfied as original Macintosh users were back in 1985 and headed for stagnation.

(Or to use an aircraft analogy - are we just perfecting the turbo-prop, and ignoring the jet-engine?  By the time we bring a perfected Linux to the world, will it be relevant?  Sure it will work, much like turbo-props do today, but to ignore the jet would be a mistake and force us to play catch-up for a looong time.)

If Job's history shows anything, he freely admits that early on he was so blown away by one of the *three* things that he was shown during his visit to Parc (the gui interface), that he forgot about one of the other major influences shown to him, that of OO programming.  So look at where the early macs are now which concentrated almost solely on the gui interface, and not so much on the system programming underneath.

That was rectified when he started NeXT and later OpenStep using OO with objective-C.  Of course that grew into OSX today, although it seems evident that marketing issues may have skewed the original vision.

And becoming comfortable is what worries me.  Apple was pretty comfortable with the early Mac designs and programming, and it nearly bankrupted them.  Jobs was out doing his OO thing with Next, and ultimately called back to Apple and blew their whole product line away.  It was a lot more than just a translucent case - it was OO underneath.

Ok, so perhaps the commercial pressure is off with open-source.  But the question of becoming stagnant with our "current product line" worries me. :)

Allright, everyone hit the rec-room for 2 hours, and come back so we can give the white-board a workout.  The hot-tubs are broken, so we've brought in a few extra bean-bag chairs to chill out with. :)

---

### Post by samjh on 2008-08-25
I don't think the Linux community is being stagnant with our "product line" as far as programming languages and tools are concerned.

There was a time when everything was programmed in C, C++, or Perl.

Now, we're moving slowly but steadily toward C#/Mono and Python.  C is still the heart of the Linux kernel, and that probably won't change for the forseeable future (nor is there any convincing reason to change).  C++ is the lurking behemoth behind some of our biggest projects (KDE and Qt to mention one of many).

Objective-C wasn't the only language that Apple toyed with.  Much of the API in System 7 series OS and earlier, were written in Object-Pascal, although the core (particularly networking) was written predominantly in C.  Apple played with many left-of-field technologies, but as with all experimental efforts, few of these technologies became big successes.

However, some things which aren't successful on their own, influence the success of future technologies.

---

### Post by Wybiral on 2008-08-25
Do we really need another C dialect? Are we gaining anything new or interesting from them?

C, C++, Java, C#, D, Obj-C... You learn one, you learn them all.

My question is: why aren't we using more Lisp[?]("http://mitpress.mit.edu/sicp/")-[?]("http://www.paulgraham.com/avg.html")-[?]("http://www.catb.org/~esr/faqs/hacker-howto.html")

---

### Post by dribeas on 2008-08-25
> **Wybiral said:**
> C, C++, Java, C#, D, Obj-C... You learn one, you learn them all.

<sarcasm>Yes, they are exactly the same.</sarcasm>

---

### Post by Wybiral on 2008-08-25
> **dribeas said:**
> <sarcasm>Yes, they are exactly the same.</sarcasm>

This doesn't make sense. I never said they were the same, I was saying that it's trivial to move between them and that you gain very little by adding a new one to your palette. We don't need any more. If you think that there's more than trivial differences between them, or that it's difficult to learn one after learning another, chances are you haven't effectively learned any languages outside of that family and would benefit from learning something like Lisp.

The main things you gain by moving between them (in a few cases) are platform or library (which is distinctly different from the language itself).

---

### Post by nvteighen on 2008-08-25
C, C++, C# and friends' base is all the same: Imperative procedural static typed languages. That's essentially represented by C. Extras are added afterwards in C++, C#, but built upon the same common typing discipline, the same common syntax and the same common semantics (Hey, I don't try to state those languages are all supersets of C).

It's like Romance languages: if you learn Spanish, you can easily get into Italian, Portuguese, French, etc.

That's what Wybiral is trying to say, not that C == C++ == C# == D == etc.

---

### Post by CptPicard on 2008-08-25
> **nvteighen said:**
> 
That's what Wybiral is trying to say, not that C == C++ == C# == D == etc.

It's all in vain of course, because the guys who don't know Lisp obviously know better than Wybiral that he's just being delusional and that the differences within that group trump anything else outside that group.

---

### Post by Kadrus on 2008-08-25
> **Wybiral said:**
> 
My question is: why aren't we using more Lisp[?]("http://mitpress.mit.edu/sicp/")-[?]("http://www.paulgraham.com/avg.html")-[?]("http://www.catb.org/~esr/faqs/hacker-howto.html")
Who says ***we*** aren't ;)..You just need to look in different places ^,^

---

### Post by dribeas on 2008-08-25
> **CptPicard said:**
> It's all in vain of course, because the guys who don't know Lisp obviously know better than Wybiral that he's just being delusional and that the differences within that group trump anything else outside that group.

Well, from Wybiral post I understood, my bad, that he was quoting all them as dialects, and that shocked me as quite stupid. Now, if what the post meant is that lisp (common lisp, scheme...) adds more to the developer than changing from C/C++/... to another from the same set I do agree, regardless of others prejudices. 

   David

---

### Post by LaRoza on 2008-08-25
> **nvteighen said:**
> 
It's like Romance languages: if you learn Spanish, you can easily get into Italian, Portuguese, French, etc.

What about Latin?

> 
That's what Wybiral is trying to say, not that C == C++ == C# == D == etc.

Forgot Java.

---

### Post by nvteighen on 2008-08-25
> **LaRoza said:**
> What about Latin?

Linguam Latinam non capisces Hispanicam aut Italianam aut similem aliam tantum sciens!

> Forgot Java.

Iavam non oblivisci: "etc" (et cetera) ad finem scripsi!

---

### Post by LaRoza on 2008-08-25
> **nvteighen said:**
> Linguam Latinam non capisces Hispanicam aut Italianam aut similem aliam tantum sciens!

Iavam non oblivisci: "etc" (et cetera) ad finem scripsi!

Etley otney etgey into a ightfey.

(There is a language called Java (Indonesia) do you know any of that?)

---

### Post by nvteighen on 2008-08-25
> **LaRoza said:**
> Etley otney etgey into a ightfey.

(There is a language called Java (Indonesia) do you know any of that?)

:D ("Let not get into a fight"?)

I knew about Java (the natural language)... I had to read an article that mentioned it, but I don't remember what was the author's point.

OK, the problem with Latin is that if you know it, you understand the Romance languages easily. But, knowing Romance languages doesn't make you understand Latin... at least easily.

But knowing a Romance language can help you to easily understand almost any other Romance language. There might be some harder combinations, of course, like stepping from Spanish to Romanian (which I don't know... don't be scared :))

---

### Post by CptPicard on 2008-08-25
> **nvteighen said:**
> 
But knowing a Romance language can help you to easily understand almost any other Romance language.

So it's like Lisp... understanding Lisp causes you to master any other language and paradigm more easily, while being a super-geek in C doesn't make you any better a Lisper... :p

---

### Post by LaRoza on 2008-08-25
> **nvteighen said:**
> :D ("Let not get into a fight"?)


You speak Latin!

See if you can get away with using pig-latin in your studies. Try to be all serious about it and see how long it takes...

---

### Post by nvteighen on 2008-08-25
> **CptPicard said:**
> So it's like Lisp... understanding Lisp causes you to master any other language and paradigm more easily, while being a super-geek in C doesn't make you any better a Lisper... :p

I'd rather say Lisp = Ancient Greek. Knowing Greek opens your (philological/linguistic) mind... Latin not. :D Greek's article can be applied to a whole sentence, the past simple could be used for some future actions (because of the "unreal" aspect both past and future share), the links between structures are precise and economical... I love it; sadly, I don't find the time I want to read Greek and have to deal with the hyper-strict, boring, unflexible Latin.

(OK, Latin vs. Greek is the classical flamewar in Classical Philology, since the Roman conquest of Greece! I'm sure you all notice in which side I am...)

> **LaRoza said:**
> You speak Latin!

See if you can get away with using pig-latin in your studies. Try to be all serious about it and see how long it takes...

:)

---

### Post by SeanHodges on 2008-08-25
> **Rick 1 said:**
> I really don't have time to educate the world (and the more wayward) so let's keep this brief. Save for a few terse phrases and punctuation marks - and the original post by stream303 - this thread has some of the worst most uneducated and gratuitously obnoxious statements I've seen in a long time. It doesn't take a master shrink to understand none of you are professional programmers - much less professional students of programming languages, OO, and the rest. Should anyone be looking into this thread for any type of clue whatsoever on languages and especially OO - LOOK THE OTHER WAY. FAST.

Frankly I'm shocked. And ashamed. And perhaps not coincidentally feel a bit of pity for you.

Let me leave you with the words of Mark Shuttleworth which I believe will put things into their proper perspective.

As I've stated before: Shuttleworth might be filthy rich and still a nice guy but selling software to VeriSign does not a systems programmer make or imply.

And should any of you self-appointed nuisances have something cogent to add to the discussion started years ago by Douglas Engelbart and Alan Kay; should you understand the true nature of languages such as C++; should you understand the latter's etymological derivation (Simula et al) and should you understand how Brad Cox put Objective-C together - then yes by all means let's hear your words of wisdom. But we all know they won't be forthcoming because they cannot by definition exist.

And should any of you punters claim you can do better than Jean-Marie Hullot, Avie Tevanian, and the rest - then by all means again: come forward and let us look at the code you cite. But don't bother pointing to either GNOME or KDE because we will only laugh at you.

If you're not professional - which you ostensibly and painfully are not - what are you doing in this thread anyway?

I'm sure you have some really deep and meaningful point to make, but I'm afraid not a single sentence in your post explained it.

---

### Post by CptPicard on 2008-08-25
> **nvteighen said:**
> I'd rather say Lisp = Ancient Greek. Knowing Greek opens your (philological/linguistic) mind... Latin not. :D

Interesting stuff.

> I love it; sadly, I don't find the time I want to read Greek and have to deal with the hyper-strict, boring, unflexible Latin.

Oh, but you know, all that pain is good for you! Latin forces you to be strict so that a language noob won't make that many mistakes in the future!

Think of the hyper-strictness as kind of static typing -- the compiler (teacher) catches your errors early and gives you a good crack on the knuckles with that ruler of his when you mess up the cases so that you learn to avoid bugs in an almost Pavlovian manner and don't sound like an idiot at runtime!

Greek sounds like some language for people who aren't just willing to sweat it but just want the easy way out, the lazy bums!

All languages are human-complete anyway so you can express in Latin anything you want in Greek and I think this all just sounds like an Argument from Authority, as if actually *knowing Greek* gave you some kind of an edge in this discussion and let you assume your opinion counts more! 

You really need to learn to prove your statements in a more rigorous fashion. And no, I will not listen to any counter-arguments, you're just imagining things because you're not smart enough to do it all in Latin.

</parody>

> 
(OK, Latin vs. Greek is the classical flamewar in Classical Philology, since the Roman conquest of Greece! I'm sure you all notice in which side I am...)

Hehe... ok, I'll take it from you, you're the Authority. ;)

---

### Post by nvteighen on 2008-08-25
> **CptPicard said:**
> 
Oh, but you know, all that pain is good for you! Latin forces you to be strict so that a language noob won't make that many mistakes in the future!

Think of the hyper-strictness as kind of static typing -- the compiler (teacher) catches your errors early and gives you a good crack on the knuckles with that ruler of his when you mess up the cases so that you learn to avoid bugs in an almost Pavlovian manner and don't sound like an idiot at runtime!

Greek sounds like some language for people who aren't just willing to sweat it but just want the easy way out, the lazy bums!

All languages are human-complete anyway so you can express in Latin anything you want in Greek and I think this all just sounds like an Argument from Authority, as if actually *knowing Greek* gave you some kind of an edge in this discussion and let you assume your opinion counts more! 

:D That was great!

---

### Post by stream303 on 2008-08-25
> **Wybiral said:**
> Do we really need another C dialect? Are we gaining anything new or interesting from them?

How about most of Apple's product line?

I'm not about to push their hardware or marketing - I'm just amazed that in the face of open-source is a model of something that works, and works well, based upon solid *nix principles and OO with objective-c.  In fact, I'm replying with that system now.

I think it would be foolish to adopt an NIH attitude.  Had we done so in the past, we would all be running closed-source ATT licensed code and hardware today.

Sure, we could all run Greenblatt and Knight's LISP machine, but I don't see any recent examples on my desktop.  What I do see 12 inches in front of me is something that has 23 years of advancing technology behind it.

(The history of the Lisp machines is fascinating stuff, and will take you right into RMS territory.  Next time I have lunch with Jobs, I'll have to ask him what he thought of lisp. :)

So in the end, we can try to *look* like something we're definitely not with a pretty face, or we can take the OO example to task, and make it even better from within.

In other words, it isn't anything new.  We just aren't using the tools available, and our current vision may be limited by familiarity.

---

### Post by LaRoza on 2008-08-25
> **stream303 said:**
> How about most of Apple's product line?

I'm not about to push their hardware or marketing - I'm just amazed that in the face of open-source is a model of something that works, and works well, based upon solid *nix principles and OO with objective-c.  In fact, I'm replying with that system now.

In other words, it isn't anything new.  We just aren't using the tools available, and our current vision may be limited by familiarity.

The thing is C and C++ are widely used. D is up coming, and dynamic typed languages (Python and Ruby) are get very popular and widespread. What does Objective-C offer that makes it worth learning or using over those languages? Variety for the sake of it is sloppy.

---

### Post by stream303 on 2008-08-25
From my limited understanding, it isn't that big of a jump from C, so the environment won't be totally alien.  There is also objective C++ from what I understand.

I think the big thing is not so much the language but the concepts behind it - that of objects.  When I want to write a note with a pencil, I pick up an object to write with and my mind doesn't have to reverse-engineer it every time I want to put it to use.  Does that make sense?  I think I'm losing myself here. :)

So I guess we could talk about the pros and cons of various languages while others pass us by and actually pick one, and do something with it.  To me, objective-c seems the natural choice for those already familiar with C, but hey if we can do it all in python, go for it. :)

---

### Post by mssever on 2008-08-25
> **stream303 said:**
> I'm not about to push their hardware or marketing - I'm just amazed that in the face of open-source is a model of something that works, and works well, based upon solid *nix principles and OO with objective-c.  In fact, I'm replying with that system now.

<snip>

So in the end, we can try to *look* like something we're definitely not with a pretty face, or we can take the OO example to task, and make it even better from within.

In other words, it isn't anything new.  We just aren't using the tools available, and our current vision may be limited by familiarity.
What you see when you look at an Apple product is their user interface. There's nothing in Apple products that couldn't be done effectively with the languages in common use in the open source world. Furthermore, most large open source products use OO concepts already. Finally, since when is OO the best way to approach every problem?

I fail to see how doing more OO will make open source more Mac-like.

Besides, MacOS is clunky and difficult to use, IMHO. Why copy such a system? The old Macs were ahead of their time UI-wise (System 7 was vastly superior to DOS with Windows 3.11), but they haven't kept up. And adding more carbon to the UI hasn't improved things. I'd rather use Vista over MacOS as far as the UI goes. Of course, Gnome with Compiz beats both. These are, of course, my opinions, and I'm not trying to start a flamewar. I'm simply stating that MacOS isn't objectively better. Some people might think it is. Fine. Let them waste money on Macs.

EDIT: I'm focusing on the UI, because that's the distinctive feature of MacOS. I don't think that there's too much under the hood that really makes it stand out.

---

### Post by stream303 on 2008-08-25
No flamewar here - I understand and appreciate ALL of the opinions put forth.

I'm saying that since we are free from commercial pressures, (theoretically) we can do it better!

Even though I'm not a programmer, if I was in charge of a team of objective-c programmers, I'd have to insist that they actually enjoy what they are doing.  If they disliked the programming environment, or it didn't make sense to them, I wouldn't want to force it.

I'll continue to enjoy the fruits of the current programming environment as a user that's for sure, and want to endlessly thank the devs for their devotion and hard work.

I'll adapt if the world doesn't convert to objective-c. :)

---

### Post by mssever on 2008-08-25
> **stream303 said:**
> Even though I'm not a programmer
If you aren't a programmer, then you really aren't qualified to discuss the technical merits of programming languages, are you? And a non-programmer lecturing programmers on OOP is hilarious.

---

### Post by Wybiral on 2008-08-25
> **stream303 said:**
> Sure, we could all run Greenblatt and Knight's LISP machine, but I don't see any recent examples on my desktop.  What I do see 12 inches in front of me is something that has 23 years of advancing technology behind it.

(The history of the Lisp machines is fascinating stuff, and will take you right into RMS territory.  Next time I have lunch with Jobs, I'll have to ask him what he thought of lisp. :)

So in the end, we can try to *look* like something we're definitely not with a pretty face, or we can take the OO example to task, and make it even better from within.

In other words, it isn't anything new.  We just aren't using the tools available, and our current vision may be limited by familiarity.

What does anything have to do with Lisp machines and why do you think ObjC is what makes apple who they are?

---

### Post by CptPicard on 2008-08-25
> **mssever said:**
> If you aren't a programmer, then you really aren't qualified to discuss the technical merits of programming languages, are you? And a non-programmer lecturing programmers on OOP is hilarious.

This is surprising how? :) Non-Xers offering opinions on technical merits of X to Xers is the norm here ;)

---

### Post by xmasterg on 2008-08-25
As someone who programs in C, C++, and Objective-C regularly (and LISP, Prolog, C#, and Java somewhat less frequently), I do not think that there would be any significant advantage in widespread use of Objective-C over any of the currently-common languages.

Objective-C does have a few features that make it convenient (dynamic typing and automatic memory management come to mind), and it is by no means a bad language (though its messaging syntax is like a cluttered form of LISP, which I imagine is the basis for those "ugly as sin" comments), but it quite simply is not revolutionary. Objective-C's dynamic typing is actually just the widespread use of a smart (void*) type, called *id*, that handles basic memory management for you. This is done better in some languages (Java and C# spring to mind), and not at all in others (C++, although smart pointer libs are all over the place, notably in Boost). Its lack of templating and default arguments is unfortunate, IMHO, and many of the standard container classes lack support for primitives, meaning that if you want to put an *int* into an *NSArray*, you'll need to wrap it in an *NSNumber* object, or simply use a C-style array without memory management. But these are not insurmountable issues, and essentially anything that you can do in C/C++/C# can be done in Objective-C in a manner that is not too radically different. The issue is, the converse of that statement is true, meaning that there isn't any major benefit to using Objective-C in most cases.

At the end of the day, anything you can do in Objective-C you can do in C++ and friends (or even C, though lacking native OO support makes many tasks somewhat harder), though each language will have particular cases where it makes your life easier than other languages would. If you wanted to write some performance-critical code, I would not recommend Objective-C (although it is by no means impossible to write efficient code!), but dynamic typing makes many tasks a little simpler. It's just a matter of choosing the right tool for the job.

In summary: Objective-C is *not* a silver bullet, and the Mac does not, in my opinion, derive its strength from its use of Objective-C as the basis for Cocoa, but rather from its Unix heritage, and the Mac dev team's success in making Unix user-friendly for the masses (it's pretty impressive that most of my Mac-using friends are not even aware of the Terminal app). The same thing could have been accomplished in C++, or C#, or Java (if you hate performance), and I doubt that any of those languages would have been noticeably superior to the others.

stream303, I can respect your curiousity w.r.t. Objective-C as a common language, and I realize that you are just trying to open a dialogue in an effort to ensure that developers don't overlook a potentially useful tool, but I am not sure that you are fully cognizant of its actual features vs. those of its competitors. Objective-C is not necessarily "worse" than its common counterparts, but it is not "better" either; there isn't a particularly strong reason not to use it, but there isn't a strong reason *to* use it. And, ultimately, the cost of changing gears to use another language takes effort (new syntax, rules, and libraries are not insurmountable challenges to developers, but they are not trivial), and in the case of Objective-C there simply isn't a strong reason to make that effort.

---

### Post by LaRoza on 2008-08-25
> **mssever said:**
> 
Besides, MacOS is clunky and difficult to use, IMHO. Why copy such a system? 
+1

I find it hard to use and messy. That is entirely due to my having other WM/DE preferences, but OS X is nothing special UI wise.

> **stream303 said:**
> 
Even though I'm not a programmer, if I was in charge of a team of objective-c programmers, I'd have to insist that they actually enjoy what they are doing.  If they disliked the programming environment, or it didn't make sense to them, I wouldn't want to force it.
"If I **were** in charge...", Subjunctive mood isn't dead!

I think the conversation is ended...

Without being a programmer, you have no way of knowing anything about the matter that really has any weight with us.

---

### Post by bilijoe on 2008-08-25
> **Rick 1 said:**
> I really don't have time to educate the world (and the more wayward) so let's keep this brief. Save for a few terse phrases and punctuation marks - and the original post by stream303 - this thread has some of the worst most uneducated and gratuitously obnoxious statements I've seen in a long time. It doesn't take a master shrink to understand none of you are professional programmers - much less professional students of programming languages, OO, and the rest. Should anyone be looking into this thread for any type of clue whatsoever on languages and especially OO - LOOK THE OTHER WAY. FAST.
 
Frankly I'm shocked. And ashamed. And perhaps not coincidentally feel a bit of pity for you.
 
Let me leave you with the words of Mark Shuttleworth which I believe will put things into their proper perspective.
 
As I've stated before: Shuttleworth might be filthy rich and still a nice guy but selling software to VeriSign does not a systems programmer make or imply.
 
And should any of you self-appointed nuisances have something cogent to add to the discussion started years ago by Douglas Engelbart and Alan Kay; should you understand the true nature of languages such as C++; should you understand the latter's etymological derivation (Simula et al) and should you understand how Brad Cox put Objective-C together - then yes by all means let's hear your words of wisdom. But we all know they won't be forthcoming because they cannot by definition exist.
 
And should any of you punters claim you can do better than Jean-Marie Hullot, Avie Tevanian, and the rest - then by all means again: come forward and let us look at the code you cite. But don't bother pointing to either GNOME or KDE because we will only laugh at you.
 
If you're not professional - which you ostensibly and painfully are not - what are you doing in this thread anyway? WOW! That was harsh.:shock:

---

### Post by TreeFinger on 2008-08-25
> **samjh said:**
> ..

Basically, C++ got lucky.  It was - and still is - a good language for what it is designed be... 


What is it designed to be used for?

---

### Post by LaRoza on 2008-08-26
> **TreeFinger said:**
> What is it designed to be used for?

To make jobs for programmers.

---

### Post by stream303 on 2008-08-26
> **xmasterg said:**
> stream303, I can respect your curiousity w.r.t. Objective-C as a common language, and I realize that you are just trying to open a dialogue in an effort to ensure that developers don't overlook a potentially useful tool, but I am not sure that you are fully cognizant of its actual features vs. those of its competitors.

Thank you!  That's all I was after, and your response makes absolute sense to me.

Anyway, even though I brought the issue up in the first place, honestly admitted my inability to program, praised the Ubuntu and Linux devs for what I have now, I'll bow out as it looks like my questions have been answered.

And I'm sorry about the bad grammar.  I won't be doing any live demo's or appearances, that's for sure. :)

---

### Post by stream303 on 2008-08-26
[QUOTE=LaRoza]Without being a programmer, you have no way of knowing anything about the matter that really has any weight with us.[/QUOTE]

Ok, so let us ask Mark Shuttleworth, who is a programmer, and who is the one who brought up the issue in the first place.  (See msg #1 in the thread for the interview link)

What made him make that statement about Objective-C?  Maybe he can read this thread and provide some sort of followup, since my opinion means nothing.

---

### Post by samjh on 2008-08-26
> **TreeFinger said:**
> What is it designed to be used for?Not "used for", but "to be", was what I said.

According to Stroustrup, C++ is designed to be:
- "A better C"
- Better at data abstraction than C.
- Able to provide OOP to programmers.
- Better at type checking than C.
- Enable programs to be written that are both efficient but also elegant.

You can find many answers to popular C++ questions at Stroustrup's official FAQ: [http://www.research.att.com/~bs/bs_faq.html](http://www.research.att.com/~bs/bs_faq.html)
There are lots of C++ related material at his C++ site: [http://www.research.att.com/~bs/C++.html](http://www.research.att.com/~bs/C++.html)

In my subjective opinion, I think C++ has achieved its aims reasonably well.  Certainly, I find well-written C++ code more comprehensible and safer than equally well-written C code.  On the flip side, unskilled C++ code seems to be worse than equally unskilled C code.

I liken C++ to F1 cars.  Lots of racing drivers can drive an F1 car.  Very few can drive an F1 car to its maximum.  And unskilled drivers mess it up bigtime and cost big $$$.
C is more like kart.  Lots of racing drivers can drive a kart.  Many of them can drive a kart to its maximum.  Unskilled drivers mess up but don't cause much damage.

---

### Post by TreeFinger on 2008-08-26
> **samjh said:**
> Not "used for", but "to be", was what I said.

According to Stroustrup, C++ is designed to be:
- "A better C"
- Better at data abstraction than C.
- Able to provide OOP to programmers.
- Better at type checking than C.
- Enable programs to be written that are both efficient but also elegant.

You can find many answers to popular C++ questions at Stroustrup's official FAQ: [http://www.research.att.com/~bs/bs_faq.html](http://www.research.att.com/~bs/bs_faq.html)
There are lots of C++ related material at his C++ site: [http://www.research.att.com/~bs/C++.html](http://www.research.att.com/~bs/C++.html)

In my subjective opinion, I think C++ has achieved its aims reasonably well.  Certainly, I find well-written C++ code more comprehensible and safer than equally well-written C code.  On the flip side, unskilled C++ code seems to be worse than equally unskilled C code.

I liken C++ to F1 cars.  Lots of racing drivers can drive an F1 car.  Very few can drive an F1 car to its maximum.  And unskilled drivers mess it up bigtime and cost big $$$.
C is more like kart.  Lots of racing drivers can drive a kart.  Many of them can drive a kart to its maximum.  Unskilled drivers mess up but don't cause much damage.

What is C designed to be?

---

### Post by LaRoza on 2008-08-26
> **TreeFinger said:**
> What is C designed to be?

To program Operating Systems (specifically, Unix)

---

### Post by samjh on 2008-08-27
> **TreeFinger said:**
> What is C designed to be?

This question has an answer only Dennis Ritchie and Brian Kernighan can truly answer.

Originally, C was written so that UNIX (which was written in Assembly up to that time) could be ported to different platforms more easily.  So one could say that C is like portable Assembly.  However that sort of answer wouldn't do C - or the efforts of Kernighan and Ritchie - enough justice.

The closest answer I can find is from the famous book, [i]The C Programming Language[i] by K&R:
> C is a general-purpose programming language which features economy of expression, modern control flow and data structures, and a rich set of operators.  C is not a "very high level" language, nor a "big" one, and is not specialized to any particular area of application.- Brian Kernighan and Dennis Ritchie, *The C Programming Language* (2nd ed, 1988[noparse])[/noparse] xi.

Keep in mind that objectives and descriptions of programming languages should be viewed in context of the era in which it was created.

For example, "modern... data structures" of the 1970s are not really modern by today's standards.

---

### Post by rplantz on 2008-08-27
The programming language is probably one of the least important factors in creating a good program. I define "good" here to mean a program that solves the problem accurately within the required time frame and presents an intuitive user interface. The intuitive user interface is important because it helps prevent user errors, which are probably the biggest cause of incorrect output.

In most designs, I believe that the most important, and often the most difficult, factor is learning how the user actually solves the problem "by hand." Most people are not aware of the algorithms they use in their jobs. Once the solution is specified in an algorithmic manner, writing the code is usually straightforward, no matter what the local language is.

In my several decades of working in industry and teaching programming, I have seen several excellent solutions to the wrong problem.

---

### Post by nvteighen on 2008-08-28
> **rplantz said:**
> The programming language is probably one of the least important factors in creating a good program. I define "good" here to mean a program that solves the problem accurately within the required time frame and presents an intuitive user interface. The intuitive user interface is important because it helps prevent user errors, which are probably the biggest cause of incorrect output.

In most designs, I believe that the most important, and often the most difficult, factor is learning how the user actually solves the problem "by hand." Most people are not aware of the algorithms they use in their jobs. Once the solution is specified in an algorithmic manner, writing the code is usually straightforward, no matter what the local language is.

In my several decades of working in industry and teaching programming, I have seen several excellent solutions to the wrong problem.
Let me disagree. OK, yes: in principle, you could code anything in any language that's Turing-complete. But, when programming there is also a human factor, so while the machine actually doesn't care if the algorith is written in language <x>, a human migth find writing the algorithm in language <x> is more suitable because of some reason. And there are several reasons: development speed, runtime speed, cross-platform support, etc. 

But there's a reason that seems to be ignored, expressiveness (which reveals I'm a Lisp-convert). Even if a language is Turing-complete, it may have less expressive power than the other because of the primitive data, combination means (glueing) and abstraction means (naming glued stuff) it offers (yes, [SICP]("http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-1.html#titlepage") is my source). The better those three aspects are, the more powerful the language is. "Better" doesn't mean "more", of course, but that using them can easily establish abstraction layers with the less lost of abstraction power while climbing up (in other words, "running out of air"). Lisp's power comes from the closure proprierty, which allows to infinitely climb up without ever losing any abstraction power (if you respect closure in your design, of course).

Well, this doesn't mean we all have to code in Lisp. But I believe expressiveness is a factor that subconsciously defines preference over a language for a certain kind of work, even when in theory any is capable of doing the job. Yes, in theory we are able to code a webpage in Assembly... but who does that?

---

### Post by CptPicard on 2008-08-28
+1 nvteighen, *excellent* post, I was just going to start typing when I read yours.

@rplantz, if you search the forums a little you will see that we've had sometimes rather heated discussions about this matter and whether this expressiveness has any meaning and intellectual merit vs. Turing-completeness and resultant equality of languages in terms of algorithmic computational power.

Of course, if this expressiveness did not exist at all, there would be no need for higher-level programming languages, so essentially people who argue against them are arguing against a lot of development, and those who can't see the benefits are frankly just losing much voluntarily (and as it seems, as a result of some contrived principle based on ignorance and masochism).

I of course fully agree with you that algorithmic solutions are always at the core. However, in real life they are not usually in pure form, and most of the time you do not have real "theory" to draw on. You need to be aware of algorithms and their implications, but real problems genuinely require powerful modelling tools for you to really be able to apply your mind to the pressure points where you can crack the problem the best.

As I like to say, programming languages provide a descriptive mapping of computational structure over the problem structure, allowing you to exploit problem structure according to algorithmic (mathematical) principles. The more flexible and malleable your mapping tool, the easier it becomes to fit your mind around the problem, and in best cases you will even be able to expose interesting structures merely by manipulating your code.

Some people will argue that they're so superior that they can just solve everything directly and then code everything in assembly (and that as a corollary others are just using mental crutches), but that's usually either a severe case of hubris and/or inexperience.... my *own experience* says that expressive languages really do grow on you, and do not deduct from your algorithmic understanding, but support it.

> Lisp's power comes from the closure proprierty, which allows to infinitely climb up without ever losing any abstraction power (if you respect closure in your design, of course).

Just to make this a bit exact, he means the homoiconic closure property of Lisp lists (ability to nest them)... not the lexical closure, which is a nice feature to have too though :)

---

### Post by nvteighen on 2008-08-28
> **CptPicard said:**
> 
Just to make this a bit exact, he means the homoiconic closure property of Lisp lists (ability to nest them)... not the lexical closure, which is a nice feature to have too though :)

Thanks for the correction!

---

### Post by CptPicard on 2008-08-28
> **nvteighen said:**
> Thanks for the correction!

No, there is nothing wrong with what you're saying. It's just that I want to point out the distinction to the audience :)

---

### Post by cb951303 on 2008-08-28
> **stream303 said:**
> 
So maybe my real question is why aren't we using it today?  Is it really that bad, or is it just not *fashionable?*

I'm not sure but maybe because open source world has GObject for C and C is more popular than objective-c?

---

### Post by techmarks on 2008-08-29
....and then there's the language ALL the programmers know

profanity
;-)

---

### Post by LaRoza on 2008-08-29
> **techmarks said:**
> ....and then there's the language ALL the programmers know

profanity
;-)
-1 I never use it.

---

### Post by CptPicard on 2008-08-29
> **LaRoza said:**
> -1 I never use it.

A good, heart-felt *perkele *really lets out the steam at times.

---

### Post by LaRoza on 2008-08-29
> **CptPicard said:**
> A good, heart-felt *perkele *really lets out the steam at times.

I don't use profanity in Finnish either ;)

---

### Post by CptPicard on 2008-08-29
> **LaRoza said:**
> I don't use profanity in Finnish either ;)

It's your loss...

---

### Post by mssever on 2008-08-29
> **LaRoza said:**
> -1 I never use it.

> **LaRoza said:**
> I don't use profanity in Finnish either ;)
Wow. It isn't very often that I meet someone else who doesn't use profanity. Good for you!

---

### Post by CptPicard on 2008-08-29
People who *absolutely *have no vices are just scary :) Hitler was one...

---

### Post by mssever on 2008-08-29
> **CptPicard said:**
> People who *absolutely *have no vices are just scary :) Hitler was one...
Godwin's Law...

---

### Post by LaRoza on 2008-08-29
> **mssever said:**
> Wow. It isn't very often that I meet someone else who doesn't use profanity. Good for you!

Never have. People think it is strange, but I don't see them as words I can use. I am not bothered by other people using them (in that it makes me uncomfortable, like it does to people who are rather sheltered) though.

> **CptPicard said:**
> People who *absolutely *have no vices are just scary :) Hitler was one...
Hitler was a vegatarian also (for health reasons). 

I do have vices (and a Vice-Grip), but they are known of your business :-)

> **mssever said:**
> Godwin's Law...

First time I was compared to Hitler :-)

---

### Post by mssever on 2008-08-29
> **LaRoza said:**
> Never have.
Same here. I was raised to not use profanity, and now that I'm on my own, I see no reason to start.

---

### Post by CptPicard on 2008-08-29
I was almost 30 before I actually smoked a cigarette, and then I did. Didn't see a reason to start the habit though. *Occasional well-placed* profanity is safer and more satisfying :)

"Always try everything except your sister and folk dancing". Old Finnish saying.

---

### Post by Senesence on 2008-08-29
> **mssever said:**
> Same here. I was raised to not use profanity, and now that I'm on my own, I see no reason to start.

Well, there is some entertainment value in observing how the "sheltered", as LaRoza refers to them, react when various profanities are uttered in their presence. If there was no "shock value" returned, I probably wouldn't bother to preface "I'll just rewrite the whole thing from scratch" with the phrase "f*ck it". :)

On another note (but still quite off topic); What's up with the Lambda symbols I see in the avatars of some users that posted here?

So far I count 3: **Wybiral**, **CptPicard**, **nvteighen**.

Is this a group effort to promote Scheme (dialect of Lisp), or are you guys just really into Half-Life....or is it both?

---

### Post by LaRoza on 2008-08-29
> **Senesence said:**
> Well, there is some entertainment value in observing how the "sheltered", as LaRoza refers to them, react when various profanities are uttered in their presence. If there was no "shock value" returned, I probably wouldn't bother to preface "I'll just rewrite the whole thing from scratch" with the phrase "f*ck it". :)

I am quite used to being around profane people. Interestingly, any sensible person will not use such words when they are talking to me even without me expressing any dislike for it. I guess they truly realise the idiocy of such words when talking to me.

---

### Post by Alasdair on 2008-08-29
> On another note (but still quite off topic); What's up with the Lambda symbols I see in the avatars of some users that posted here?

So far I count 3: Wybiral, CptPicard, nvteighen.


My avatar is the Haskell logo, hence the lambda - but I'm pretty sure the others are using it as a [gay pride symbol]("http://www.lambda.org/symbols.htm"). ;)

---

### Post by mssever on 2008-08-29
> **CptPicard said:**
> I was almost 30 before I actually smoked a cigarette, and then I did. Didn't see a reason to start the habit though.
I never saw a reason to try smoking, either. I'd probably end up addicted to nicotine...

---

### Post by dmitrijledkov on 2008-08-29
I would like to defend a little bit about Objective C on Mac platform.

Objective C in my opinion is very clean language. Strict super set of C (low entry level), good object model and messaging.

What is great about Objective C on Mac OS X is Cocoa. Cocoa is rich Objective C library which gives you ultimate power, flexibility and ease of use of anything apple has made.

From Cocoa you can access high performance modules such as Core Graphics (High performance rendering), Core Animation (OpenGL), Core Audio (?), Core Data (SQL databases). Core Animation is an easy to use wrapper around amazing OpenGL.

Cocoa also has eveything else like UI widget for taking webcam pictures.

From programmers point of view there is a central place to find almost anything your app needs. You will be able to use it quickly cause all of it is in the same language and style (Apple Objective C).

From users point of view there is unity in the resulting applications both from apple apps and third party apps.

When Mark was referring to ObjectiveC I do think he was referring to the design model. One OO language, Rich Libraries, similar conceptual design.

Answer to the question why aren't we programming in Objective C is very simple there are is no Cocoa. Gnustep does provide rich libraries but they are miles behind Cocoa.

On linux side there is slightly different way of developing: scratching an itch. There is a great library but it's in C++ and a C developer doesn't want to use it. There is a great library but it's licensed under peanut butter license, and app with chocolate license has to develop same library again. (reference zfs pics ;-) )

I do believe that Vala and Gtk+ together could in the future provide what ObjectiveC and Cocoa give on Mac.

But you will never be able to make everyone code in Vala (or even at least provide Vala bindings) and Gtk+ has large history which will be hard to change. And there is still KDE with Qt and other desktop environments which do their own thing.

Nextstep was experiment what if we can make a closely knit infrastructure and work from there. This experiment was indeed complete rewrite of previous efforts. It was hard and Jobs pulled it off.

Can linux distro pull it off? No! Therefore we have to find our own way of written success story. (Unless it is Emacs on a Kernel. Lol I just love emacs.)

ps. Heck, Cocoa app can be easily be GUI programmed using Applescript. Not incredibly fast but 100% PLEASURE writing test suites, plus your app automagicly has scripting language which guess what the same for all applications.

pss. Some one once told me this dialema is similar to C# + .Net, from their experience ObjC + Cocoa was way better.

Questions? :popcorn:

---

### Post by LaRoza on 2008-08-29
> **CptPicard said:**
> I was almost 30 before I actually smoked a cigarette, and then I did. Didn't see a reason to start the habit though. *Occasional well-placed* profanity is safer and more satisfying :)

Er, aren't you almost 30 now? 

I prefer more intellectual insults (the best are the ones where they can't tell what to think)

> 
"Always try everything except your sister and folk dancing". Old Finnish saying.

Old Finnish is a lot like English...

---

### Post by bruce89 on 2008-08-29
> **dmitrijledkov said:**
> I do believe that Vala and Gtk+ together could in the future provide what ObjectiveC and Cocoa give on Mac.

But you will never be able to make everyone code in Vala (or even at least provide Vala bindings) and Gtk+ has large history which will be hard to change. And there is still KDE with Qt and other desktop environments which do their own thing.

GTK+ may be written in GObject-using C, but Vala is also GObject-using C in disguise. AFAIK, Vala might be used in GTK 3.x for a few classes. Seahorse is C and Vala for instance.

Thanks for actually talking about Objective-C.

---

### Post by CptPicard on 2008-08-29
> **mssever said:**
> I never saw a reason to try smoking, either. I'd probably end up addicted to nicotine...

IMO the "I'd get hooked and be destroyed" excuse always makes me think the person is for some odd reason completely on edge already and needs to be kept far away from anything and everything for his own good ;)

Of course, even for me, that is not a reason to try something like hard drugs that objectively have a low treshold for causing addiction...

> **LaRoza said:**
> Er, aren't you almost 30 now?

Yes. I tried in Bulgaria a month ago. :)

Apparently, cigarettes do give you a very transient "kick" and then the nicotine makes you want more. It really is way too short-lived for me to actually consider doing it in comparison to alcohol.

> I prefer more intellectual insults

They are not used as insults. They are used as means of expression... you know the debates we've had about expressiveness of language. There really is no way to express the things I actually express with the profanity I do use, when I do happen use it. It's very qualified, and very powerful :)

---

### Post by LaRoza on 2008-08-29
> **CptPicard said:**
> 
Yes. I tried in Bulgaria a month ago. :)

Go to foreign countries, do drugs, get kicked out of monasteries... Is their no end to your madness?

---

### Post by dmitrijledkov on 2008-08-29
> **CptPicard said:**
> I was almost 30 before I actually smoked a cigarette, and then I did. Didn't see a reason to start the habit though. *Occasional well-placed* profanity is safer and more satisfying :)


Well I have interesting story about cigarettes. I believe I am truly second-hand smoker. My mom smoked, later I choose only heavy smoking friends. And when ban on smoking hit in country I was in, I was craving for a cigarette in 2 days time.

As a backup I said I will start smoking to find out how to quit. After smoking for a year on and off I have quit.

Profanity is not safe, it is not satisfying. Anything you believe in is satisfying.

---

### Post by dmitrijledkov on 2008-08-29
> **LaRoza said:**
> Go to foreign countries, do drugs, get kicked out of monasteries... Is their no end to your madness?

Agree!!!! I hate _some_ tourists from _some_ country who come to my country and piss on The Monument of Freedom.

---

### Post by CptPicard on 2008-08-29
> **LaRoza said:**
> do drugs,

... get taught to do them by a chain-smoking local 16-year old, no less... ;)

---

### Post by Senesence on 2008-08-29
> **Alasdair said:**
> My avatar is the Haskell logo, hence the lambda - but I'm pretty sure the others are using it as a [gay pride symbol]("http://www.lambda.org/symbols.htm"). ;)

:popcorn:

:)

---

### Post by LaRoza on 2008-08-29
> **CptPicard said:**
> ... get taught to do them by a chain-smoking local 16-year old, no less... ;)

Wow...

---

### Post by mssever on 2008-08-29
> **CptPicard said:**
> IMO the "I'd get hooked and be destroyed" excuse always makes me think the person is for some odd reason completely on edge already and needs to be kept far away from anything and everything for his own good ;)
Maybe so. :) Seriously, though, I avoid addictive and/or mind-altering substances (including illegal drugs, alcohol and caffeine) because the potential payoff isn't worth the risk to me. Maybe I'd become addicted, maybe I wouldn't. But I'm doing well without those substances, and I haven't heard any logical arguments about what of value I'm missing.

---

### Post by pmasiar on 2008-08-30
> **mssever said:**
> I avoid addictive and/or mind-altering substances (including illegal drugs, alcohol and caffeine) because the potential payoff isn't worth the risk to me. Maybe I'd become addicted, maybe I wouldn't.

Smart thing to do - just say no. Neuronal network is really tricky: sometimes dopamine overload in receptor can cause chemical change in receptors, or long-term potentiation of a synapse, and other neurons to compensate will turn that one synapse off. And I think you can imagine what might happen to your brain if normal dose of dopamine would be not enough for your receptors, or if due to LTP synapse will be ignored, right? Brain out of whack - and brain is your tool, don't mess with it, you are not plumber. :-)

You would need to make detailed genetic map of your gene alleles, and exact variants of protein receptors (and folding) to know if you are safe or susceptible. And as they say, better safe than sorry. :-) There are situation when you don't have much choice (ie you are in chemotherapy) and you may want to take that risk, but why take risk for fun? If, better do bungee jumping :-)

---

### Post by techmarks on 2008-08-30
> **techmarks said:**
> ....and then there's the language ALL the programmers know

profanity
;-)


> **LaRoza said:**
> -1 I never use it.

> **LaRoza said:**
> Not sure what "funnest" means, but I take it to mean a language that is fun to use, if not practicle.

Brainfuck. Nothing beats it.

Wow a little profanity there oops....

I was just having a little fun, actually I rarely use profanity or try not to. 
I still find the name of the "programming language" known as "Brainf***" offensive!

However at the time I was having a devilish time with a program and that's when it happens to me](*,)]
One gets all frustrated and next thing you know...oops

---

### Post by LaRoza on 2008-08-30
> **techmarks said:**
> Wow a little profanity there oops....

I was just having a little fun, actually I rarely use profanity or try not to. 
I still find the name of the "programming language" known as "Brainf***" offensive!


I never say it outloud like that, but it is one word. (In speech, I say "BF")

Do you find "assimilate" to be as offensive as the first three letters alone (when not used to refer to a mammal)?

---

### Post by ankursethi on 2008-08-30
Wow. Objective-C sure looks fun, what with all the pot and profanity. Quick, where do I get mine?

(You can probably guess I never read the first 9 pages of this discussion.)

---

### Post by jinksys on 2008-08-30
> **pmasiar said:**
>  but why take risk for fun?

Because that's what makes it fun, the risk involved.

---

### Post by nvteighen on 2008-08-30
> **jinksys said:**
> Because that's what makes it fun, the risk involved.

**kalòn tò kýndynon**, said Plato. ("Beautiful [is] the risk")

EDIT: Horrible performance... it's **kalòn ti ho kíndynos** (Plato, Laws 969a???)

---

### Post by CptPicard on 2008-08-30
> **nvteighen said:**
> **kalòn tò kýndynon**, said Plato. ("Beautiful [is] the risk")

I must quote this somewhere both in my betting and derivatives/stock market business... both revolve around quantifying and managing risk using best information I can get through computation :)

> **jinksys said:**
> Because that's what makes it fun, the risk involved.

Quite the contrary -- I am *very *averse doing things *because I'd enjoy risk* (this is why I do sports betting profitably). Because it's pleasurable makes it fun, and the risk is minimal if managed by a responsible adult. Besides, you can die crossing the street, so no reason becoming paranoid.

"Booze is the drink of the wise" -- another Finnish saying.

---

### Post by jinksys on 2008-08-30
> **CptPicard said:**
> 
Quite the contrary -- I am *very *averse doing things *because I'd enjoy risk* (this is why I do sports betting profitably). Because it's pleasurable makes it fun, and the risk is minimal if managed by a responsible adult. Besides, you can die crossing the street, so no reason becoming paranoid.


I'm not saying all risky actions are fun, or a fun activity has to involve risk to be enjoyable.  I'm saying that there are some activities that if you removed the risk then the appeal would be gone.  

There is also a personal factor too.  Some people find bungie jumping very thrilling, I personally find it stupid to tease gravity.  Each to his own I guess.

Wait, wasn't this thread about Obj-C at one point?

---

### Post by Wybiral on 2008-08-30
> **jinksys said:**
> Wait, wasn't this thread about Obj-C at one point?

Yeah, but we came to a group agreement that not using ObjC was not the thing holding us back from being mac.

---

### Post by nvteighen on 2008-08-30
> **CptPicard said:**
> I must quote this somewhere both in my betting and derivatives/stock market business... both revolve around quantifying and managing risk using best information I can get through computation :)

Haha... If you want I could search the exact quote, but it can take me some little time. Now, I have some doubts whether it was Plato who said that or it was Socrates in a Plato's writing... but certainly Plato **wrote** that.

Put it hidden in the source code or an easter egg (e.g. when stock prices/bets fulfill some conditions).

---

### Post by jinksys on 2008-08-30
> **Wybiral said:**
> Yeah, but we came to a group agreement that not using ObjC was not the thing holding us back from being mac.

Oh, you mean the holier-than-thou culture that surrounds the product line?

---

### Post by Wybiral on 2008-08-30
> **jinksys said:**
> Oh, you mean the holier-than-though culture that surrounds the product line?

Holier-than-though?

No, the point is that Obj-C is not whats keeping Ubuntu from being the next mac (and it's not whats making apple who they are).

---

### Post by mssever on 2008-08-31
> **CptPicard said:**
> "Booze is the drink of the wise" -- another Finnish saying.So that's why I'm not wise. Perhaps I should imbibe in order to gain wisdom. :) Or perhaps not. Alcohol has the wonderful quality of making fools out of people.

---

### Post by LaRoza on 2008-08-31
> **mssever said:**
> So that's why I'm not wise. Perhaps I should imbibe in order to gain wisdom. :) Or perhaps not. Alcohol has the wonderful quality of making fools out of people.

Yes, it makes fools for themselves, entertainment for others.

---

### Post by UBForty on 2009-04-29
I realise this is an old thread (well, not *that* old) but I found it worthwhile reviving ...

In particular, there have been a couple of falsehoods and misperceptions, or falsehoods based on misperceptions and vice versa, which I would like to respond to, if only "for the record" ...

> Dynamic weak typing system... what can I say.

This is one of the most common misperceptions about Objective-C but it is false! One might as well say that GCC is not typed at all simply because it allows inline assembly. Objective-C is a hybrid language of three different languages, each of which have a different typing system. There is the core language, ANSI-C, which uses a static weak typing system,  there is the original Smalltalk derived language extension by Brad Cox which uses dynamic weak typing and there is the evolution of those extensions which uses static strong typing.

In other words, Objective-C has three different typing systems to choose from, and it is up to the programmer to select one or you can mix them if you like. In practise, Objective-C programs use static strong typing most of the time, dynamic weak typing is only used in a few situations where one would use generics in other languages, or templates in C++ lingo. Thus from the viewpoint of common coding practise, it would be _more appropriate_ to characterise Objective-C as a "static strong typing" language, even if that, too, doesn't tell the whole story.

> Apple's desktop share was steadily decreasing, why would anyone placed bet on language for that platform?

This implies that Objective-C came out of Apple, which is false. Objective-C was created by Brad Cox for his company Stepstone when Apple was still selling the Apple II and using Pascal. Years later NeXT Inc. chose Objective-C for its NeXTstep operating system and its APIs. Eventually, NeXT acquired the rights to the Stepstone Objective-C compiler and sponsored the inclusion of Objective-C into the GNU compiler collection, aka GCC. NeXT's hardware business wasn't doing well, but its software business based on the Objective-C libraries and IDE was doing rather well.

For this reason, NeXT abandoned the hardware business and became a software company proper, after which they teamed up with Sun Microsystems to create an open standard specification for the NeXT API, which would be called OpenStep and did very well in rapid prototyping, and especially in the financial industry. Also, they had probably the first web application development environment in WebObjects, which was doing very well. DELL's ordering system was entirely built on top of WebObjects and in Objective-C. Michael Dell ditched in with sorrow when Apple acquired NeXT, simply because he didn't want his ordering system to be dependent on a competitor, not for technical reasons, Dell was very happy with WebObjects otherwise and would probably still use it if Apple hadn't acquired it.

Also, GNUstep was started and created in response to NeXT and Sun's cooperation on OpenStep, not as a response to Mac OS X and Cocoa. By the time Apple acquired NeXT, GNUstep was already a complete implementation of OpenStep.

In other words, Apple came very late to the Objective-C party, far too late to spoil that party. The reasons why Objective-C isn't as widespread as C++ or Java have absolutely nothing to do with the fact that Apple is using it.

Moreover, ever since Apple started using Objective-C, they have made an impressive comeback from a near-death experience and their market share has been steadily increasing. This doesn't mean that Objective-C is the sole reason for their come back, but if Apple's use of Objective-C has had any impact on the use of the language as suggested, then it would have to be quite the opposite, that more people are using it now, not less, which is quite possibly true.

In any event, Apple's decline in the 1990s has absolutely nothing to do with Objective-C and Objective-C has never been influenced in any way by Apple's decline in the 1990s, simply because Apple didn't do any Objective-C while they were in decline.

> It makes me wonder if many programmers mistakenly view Objective C as just a derivative or close relative to C++, and this confirms that it is NOT.

Precisely! C++ is a slightly modified version of ANSI-C augmented with the Simula object system and many other influences. Objective-C is a true superset of ANSI-C augmented with the Smalltalk object system and nothing else. In fact, the name Objective-C is a bit of a misnomer. There are nine letters in Objective-C which say "Smalltalk", there is only one letter which says "C", which reflects the true nature of the language. A more appropriate name might have been "Smalltalkish-C", that's what Objective-C really is.

> Can we change that ugliness, or is there some fundamental law inside that can't be broken?

In other words, does everyone like the concepts, but not the implementation? Maybe we can change the implementation? Or would that mean a fork of Objective C?

There is an interesting thought, although there is a hint of another misperception.

In my opinion, the single most important reason why Objective-C has troubles finding new friends lies in the fact that it is a marriage of two diametrically opposed paradigms and programming styles. To make this even worse, the people who embrace and like the one style are usually "at war" with the people who embrace and like the other style. The folks who like C are usually not the folks who like the concepts introduced by the Smalltalk layer on top. On the other hand, the folks who like the Smalltalk side of the language are usually not the folks who like C. Objective-C is a marriage between two very unlikely partners and their clans don't like each other much either.

Before this background it is quite amazing that the language has made it as far as it did. I believe that this speaks very strongly in favour of the language, there must be something about it that makes people use it against all those incredible odds. So what is it?

Again, due to the diametrically opposed marriage partners, the reasons why users of Objective-C like the language are mostly split into two camps. The one camp likes the fact that they can mostly stay with C and simply use the Smalltalk side of it as an easy to comprehend and use OO wrapper. The other camp likes Objective-C mostly for the Smalltalk concepts, but they couldn't care less for C.

Brad Cox once told me that he created the language as an anti-language, that it wasn't supposed to be a new language, but that it was just meant to be a tool bolted on to C. To me it seems that Objective-C still remains exactly that, a practical tool which can be used along with C. What people who use it like is mostly the practicality of it, even though for some this practicality stems from the fact that they can use existing C code and wrap OO around it, to others the practicality stems from the fact that they can do Smalltalk style OO within the more familiar framework of an imperative language.

So, if we ask the question how can you improve on it, how can you benefit from whatever it is good at without inheriting that which is undesirable, then you are almost certainly going to have to disappoint one of the two camps of Objective-C users. If you take away the C, the folks who like the C side of it will not be pleased, if you dumb down the Smalltalk side by making it look more like Simula, then the folks who like the Smalltalk side of it will not be pleased.

However, there is quite a lot of development going on following either of these two approaches. Developers who don't like the Smalltalkish ways of Objective-C but feel they need to provide an interface to Objective-C class libraries generally prefer the approach of getting rid of the Smalltalk nature in their target language by building a bridge that translates between their target language's native objects and Objective-C objects.

But strange as it may seem to those who don't like the Smalltalkish side of Objective-C, there are more and more languages which copy the exact same Smalltalkish language extensions in Objective-C and add them to their own languages. Those are the ones who like Objective-C for its Smallalkish side but couldn't care less about C, or in some cases they may not like C at all.

Some examples of existing languages which use this approach are Objective-J, a hybrid of Smalltalk and Javascript and Objective Modula-2, a hybrid of Smalltalk and Modula-2, both these languages use Objective-C as a blueprint. Essentially, they removed the C part in Objective-C and replaced it with a different language.

[http://www.sunrisetel.net/software/devtools/objective-modula-2.shtml]("http://www.sunrisetel.net/software/devtools/objective-modula-2.shtml")

[http://cappuccino.org/learn/tutorials/objective-j-tutorial.php]("http://cappuccino.org/learn/tutorials/objective-j-tutorial.php")

Some examples of entirely new languages which use Smalltalk or the Smalltalk side of Objective-C as a base are [F-Script]("http://www.fscript.org") and [Nu]("http://programming.nu"), also Ruby.

One thing is clear, if Objective-C's Smalltalk side was nothing but "ugly" or "weird" or "proprietary", if it did not have any merits on its own, then there wouldn't be all these new languages picking just that particular part of Objective-C and use it. There's got to be something more about it than just being a different syntax or a necessary evil for OO wrapping of legacy C code.

Of course there is always a component of personal taste when it comes to programming styles and paradigms. No style is suitable for everybody. That's why we need choices. Languages have been borrowing the OO model and syntax from Simula for ages, where is the choice in making another one that does? It was about time that new languages borrow the OO model and syntax of Smalltalk again, this gives us the choices we have been lacking all this time, the only choice having been Objective-C, now it seems that is changing.

This might lead to the question "Why arent' we programming in Objective <foobar>?", whichever foobar, but I will leave that up to others to explore. The concept certainly seems worth exploring to me.

---

### Post by Kilon on 2009-04-29
> Moreover, ever since Apple started using Objective-C, they have made an impressive comeback from a near-death experience and their market share has been steadily increasing. This doesn't mean that Objective-C is the sole reason for their come back, but if Apple's use of Objective-C has had any impact on the use of the language as suggested, then it would have to be quite the opposite, that more people are using it now, not less, which is quite possibly true.

Actually I do not think that the impressive come back of Apple has anything to do with Objective C at all. It a simple story really , the board of directors of Apple decided to send mr Jobs away, Mr Jobs then went to a company and made it to waht today people all around the world know as PIXAR, the board of directors almost sent Apple down the toilet, begged Jobs to return , Jobs returned and made sure he had full control this time. And from there on Apple is going straight up even with economical crisis , where many companies go down. 

The truth is that MACOS has not been the happy place of developer. 

Some may call me the fanboy of Apple as I really admire the company and its OS which I believe that is light years ahead of its time. 

But when it comes to supporting developers apple still fails miserly. Java was the biggest thorn, and still is. Apple seems not able or willing to support the most popular language in the world which is a really bad move, updates are slow and in some cases require an upgrade to the latest os, which both expensive and too much of a fuzz . 

But I will have to agree, if it was not for Apple and the huge success that the company has the last 3 years, then we would not be talking about objective c in the first place . 

I really enjoyed the rest of your post , you made some interesting points.  

I would like for someone to compare D to Objective C.

---

### Post by UBForty on 2009-04-29
> **Kilon said:**
> Actually I do not think that the impressive come back of Apple has anything to do with Objective C at all.

I didn't say that it did. Somebody had suggested that the reason why few people would choose to use Objective-C had something to do with the fact that Apple was in decline. I merely illustrated that this could not possibly have been a reason because when Apple was in decline they did not use Objective-C; and when they did use Objective-C they were no longer in decline. I didn't suggest that there was any causality. I only debunked the suggestion of causality of Objective-C's use and Apple's decline which, coincidentally or not, happens to have occurred before they acquired NeXT.

> Some may call me the fanboy of Apple as I really admire the company and its OS which I believe that is light years ahead of its time.

Having used Objective-C myself (including projects entirely unrelated to GUI programming) I do believe that the Smalltalk influences and the integration into a RAD style development environment are one factor in Apple's success, quite possibly an important factor.

But, of course that doesn't mean that you'll be successful as soon as you turn to Objective-C. It's not that simple. Few if any things are that simple.

> But when it comes to supporting developers apple still fails miserly. Java was the biggest thorn, and still is. Apple seems not able or willing to support the most popular language in the world which is a really bad move, updates are slow and in some cases require an upgrade to the latest os, which both expensive and too much of a fuzz.

I never used Java, other than fooling around with it a little when it became all the rage in the mid 1990s, so I haven't followed it that closely. However, I do seem to remember than Mr. Jobs himself announced that Apple would make OS X the best platform for Java programming when OS X was first released, some time in 2000 or so maybe?!

I wonder what happened there along the way, perhaps between Apple and Sun?, that changed this enthusiasm for Java. Without wanting to appear as an Apple fanboy, I have heard from various places unrelated to Apple and unrelated to Microsoft, that Sun was mismanaging Java, whatever that means. As I said, I don't follow Java close enough to form an opinion whether or not there is any truth to that, but when I read comments like yours, I am reminded of this and it makes me wonder if Sun's management of the languages, or its APIs or whatever has something to do with it all. Of course, people also say that Mr. Jobs has a temper, so it is within the realm of possibility that he just had a change of heart for no apparent reason, or for some silly reason. Either way, I wouldn't know.

> I really enjoyed the rest of your post , you made some interesting points.

thanks.

> I would like for someone to compare D to Objective C.

Interesting you should mention D. I personally think it is a much better evolution of C than is C++. However, it is interesting in this context because I remember some discussion within the D developer community which debated whether to follow Objective Modula-2 and add the Objective-C Smalltalk bits to D to create Objective-D in order to support Cocoa and GNUstep, or whether to develop a bridge. They seem to have settled for the bridged approach. I personally would have liked to see something like Objective-D, that could have been a really nice language, I think, quite probably with a potential to become more popular than is Objective-C if somebody like Apple (or one of the major Linux distros) would throw their weight behind it.

---

### Post by Kilon on 2009-04-29
> I didn't say that it did. Somebody had suggested that the reason why few people would choose to use Objective-C had something to do with the fact that Apple was in decline. I merely illustrated that this could not possibly have been a reason because when Apple was in decline they did not use Objective-C; and when they did use Objective-C they were no longer in decline. I didn't suggest that there was any causality. I only debunked the suggestion of causality of Objective-C's use and Apple's decline which, coincidentally or not, happens to have occurred before they acquired NeXT.

I see, my mistake, should have read your post more carefully.


> Having used Objective-C myself (including projects entirely unrelated to GUI programming) I do believe that the Smalltalk influences and the integration into a RAD style development environment are one factor in Apple's success, quite possibly an important factor.


The only thing close to smalltalk I used was Delphi, I loved it. So my guess would be that I would prefer objective c to c++ or c. 


> But, of course that doesn't mean that you'll be successful as soon as you turn to Objective-C. It's not that simple. Few if any things are that simple.

It would depend on how demanding you are . Personally I usually make simple programms With the least amount of code.

So I would guess that the experience will differ from programmer to programmer. 


> I never used Java, other than fooling around with it a little when it became all the rage in the mid 1990s, so I haven't followed it that closely. However, I do seem to remember than Mr. Jobs himself announced that Apple would make OS X the best platform for Java programming when OS X was first released, some time in 2000 or so maybe?!

He never made that promise a reality.

> I wonder what happened there along the way, perhaps between Apple and Sun?, that changed this enthusiasm for Java. Without wanting to appear as an Apple fanboy, I have heard from various places unrelated to Apple and unrelated to Microsoft, that Sun was mismanaging Java, whatever that means. 

Personally I believe that Apple has not Java in its high priority list. Sun has nothing to do with it as Apple is the one who can bring java to MACOS efficiently. MACOS GUI is quite tricky to develop in and Apple s very secretive about its technology. 


Apple are not interested in developers as much as it is to promoting its own products. And personally I do not blame them, much. Of course it is very bad to ignore java but making an OS popular is a tricky business. Bottom line is that unlikely UBUNTU and Windows both python and java are not well supported , of course that does not mean that a Java developer is not welcomed.  

But even with objective c , there has been a array of complains by developers that it was not as easy to develop as it was with windows. Lately things have improved alot in this area. Mainly because of the introduction of the intel cpu chips which brought the development on mac os close to the development on windows. So now you loads more apps that are cross platform.  


> Interesting you should mention D. I personally think it is a much better evolution of C than is C++. However, it is interesting in this context because I remember some discussion within the D developer community which debated whether to follow Objective Modula-2 and add the Objective-C Smalltalk bits to D to create Objective-D in order to support Cocoa and GNUstep, or whether to develop a bridge. They seem to have settled for the bridged approach. I personally would have liked to see something like Objective-D, that could have been a really nice language, I think, quite probably with a potential to become more popular than is Objective-C if somebody like Apple (or one of the major Linux distros) would throw their weight behind it.
[/QUOTE]


obviously the bridge solution would required less code to be written or it was less complex to materialise. 

However I think what makes a langauge popular is more its libraries than the language itself. Being able to avoid wrapping C++ or C code would make objective c very popular. However if i remember correctly this is not the case.

---

### Post by UBForty on 2009-04-29
> **Kilon said:**
> 
But even with objective c , there has been a array of complains by developers that it was not as easy to develop as it was with windows. Lately things have improved alot in this area. Mainly because of the introduction of the intel cpu chips which brought the development on mac os close to the development on windows. So now you loads more apps that are cross platform.

The whole *step application framework is far more platform independent than Windows APIs, OpenStep had been available on all the major Unixes in the 90s. Change of the underlying architecture shouldn't matter much if at all, certainly not for how easy it is to use. The only thing which has changed as a result of switching CPU architectures is that there is more interest, but that's about it.

The main reason why people say that something is difficult to use in the beginning is that when they are first working with a new tool then it is unfamiliar and unfamiliarity makes it seem less easy than whatever tool is more familiar. But more familiar doesn't mean it is a better tool. You have to bite the bullet and stick to a new tool for long enough to become familiar with it before you can pass any judgement on how it really stacks up against other things you have used.

It seems to me that due to Objective-C using the Smalltalk flavour of OO and most people being familiar with the Simula flavour of OO, they find it more unfamiliar than other languages they have tried before and the confuse that unfamiliarity with "not easy to use". Most don't stick around for long enough to get familiar enough to actually understand what the benefits of the Smalltalk model are, and so a myth is spread that it is "ugly" or "weird" or whatever other negative adjective people might use. What does "ugly" vs "beautiful", "weird" vs. "normal" etc etc mean anyway? What they really mean to say is "This language is unfamiliar and I am too lazy and too disinterested to get familiar enough to be able to make an intelligent comment, so I don't, I make a silly comment instead".

> obviously the bridge solution would required less code to be written or it was less complex to materialise.

That is a misperception, too. Building and maintaining a bridge is a tough business. It's not as straightforward as it would seem. Most bridges do not support the whole API. If it was straightforward, then you'd build the bridge and it would support every API written in Objective-C, but I have yet to see a bridge that does that, they are always work in progress and there is always something that doesn't work and something that is still missing.

If you support the Objective-C calling conventions natively in your language, then you add the required extensions once to your compiler and you're done. It's only when you try to translate between incompatible object systems that you have to look at each and every API individually and see whether your translation scheme works for it or whether it requires some work around.

A bridge gives you the illusion that the foreign Objective-C libraries are native libraries. The bridge makes them look native. But the Bridge isn't a library that can just be dropped in. It requires integration into the interpreter or compiler. So, if you are fiddling around inside the interpreter or compiler anyway, then you might as well add native support for Objective-C runtime calls. No, the only reason why people bother with bridges is that they want to make the Objective-C library look like a native library of their language. Fair enough, if you are a language purist, but from the viewpoint of efficiency and practicality this is not the best choice.

> However I think what makes a langauge popular is more its libraries than the language itself.

That is precisely what makes the Cocoa and GNUstep frameworks popular with those who have stuck around long enough to become familiar with them and be able to judge.

The ability to wrap legacy C code is often just icing on the cake. Especially for those folks who add Objective-C style OO to existing languages and those who create their own new languages borrowing the Objective-C object model and syntax. They don't care much for the C compatibility aspect. They care more about the Objective-C libraries (frameworks in ObjC lingo).

There is also the IDE and the way how Objective-C and its frameworks are integrated with it. For GUI developers that is certainly an important part of the attraction. Of course this is also the most important source of innertia. If you have learned to work with an IDE environment and associated application framework, you are unlikely to want to use another, simply because it probably took you a long time to become familiar with what your are using.

---

### Post by Kilon on 2009-04-29
Well I disagree with you in some areas

1) first when I was still developing in delphi , libraries where a big deal and thus the lack of them. Pascal was a beautiful language but there time people wished that wrapping C++ was easier and more direct. That would made the language far more useful. Now that Delphi .NET was released that can as any .net language access .net libraries directly with no wrapping required , guess what ?  From being almost dead , now it still in the scene with rapidly rising popularity.  

2) IDEs do not take so much time to learn , especially if you are not too demanding. I learned Delphi and jumping to Visual Studio and now Eclipse has been a breeze. I had to learn some new thing but overall the diffirences are not so great. 

But I have to emphasize my first point. I might have been arguing against C++ and C cyntax language for a very long time , in the past with delphi and now with python but there is this fact that cannot be escaped.

C++  and C libraries were in the most cases there first. And that made the difference. 

See for example Java. Sun did the clever thing to provide a whole FRAMEWORK and not just language. The same happed with .NET , Delphi and probably Objective C. But Sun provided more and thus made the life of developers easier.

Python for example migh be great (forces you to write less code, easier to learn adn understand etc.) but if it does not have the libraries that you need and C++ has them , then you will be coding in C++.

I do not think that importing C++ code or C code is small deal at all , especially for Objective C. 

D for example makes importing C++ code a breeze .

And becuase we are talking ubuntu here and linux in general , bottom line is that most objective c libraries are mac orientated and that makes a big difference.

---

### Post by UBForty on 2009-04-29
> **Kilon said:**
> IDEs do not take so much time to learn

I didnt' say they did. I said learning the application framework takes time, that using one which is well integrated with a good IDE is a factor for GUI developers, but not that the IDE takes time to learn. The APIs however, do take time to learn and that causes innertia.

> I might have been arguing against C++ and C cyntax language for a very long time , in the past with delphi and now with python but there is this fact that cannot be escaped.

You don't have to use C or C++, nor do you need to adopt C or C++ syntax to make use of C/C++ libraries. A good language has a foreign function interface for C. Most Pascal and Modula-2 compilers for example have one. Some can even read C header files directly and you don't have to supply an equivalent in Pascal or Modula-2. Maybe Python doesn't have that. I haven't done enough with Python to remember whether there is such an interface.

In any event, there is no need to switch to C just because you want to call C libraries. At the very least not with any language that is supported by GCC, its all interchangeable.



> See for example Java. Sun did the clever thing to provide a whole FRAMEWORK and not just language. The same happed with .NET , Delphi and probably Objective C. But Sun provided more and thus made the life of developers easier.

Yes, that's what NeXT did with NeXTstep and together with Sun, later with OpenStep, it wasn't just a language and compiler, it wasn;t just the IDE, it was a complete application framework. Where do you think Sun got all its ideas for Java from? Java is Sun's "OpenStep for the Web" clone.

> I do not think that importing C++ code or C code is small deal at all , especially for Objective C.

In Objective-C you may use some C stuff when you need things like an MD5 checksum or some such thing. Most of the time however, you use C only for things such as for (), while (), if() else and to declare pointers to class instances. Anything you need to write an application is in the framework. From collection classes such as associative arrays and sets, strings, enumerations, socket programming, web stuff all the way to GUI controls, you name it, its all there, you only need C libraries for really uncommon tasks.

D for example makes importing C++ code a breeze .

> And becuase we are talking ubuntu here and linux in general , bottom line is that most objective c libraries are mac orientated and that makes a big difference.

That is simply not true. Just because the libraries ship with every Mac doesn't mean they are mac centric. Most of it was developed at NeXT long before Apple had any interest. In fact the OpenStep standard was made for Sun predominantly and OpenStep got quite a few changes compared to when it was only for NeXT machines (NeXTstep). Apple's Cocoa is an impelemtation of OpenStep, not NeXTstep, they added a bunch of things, true, but the bulk of it was made for Sun, so you might as well say it is Sun centric. It isn't, but it isn't Mac centric either. It was redesigned to be platform independent when it was changed from NeXTstep to OpenStep.

If people claim it is Mac centric, that's just repeating hearsay based on nothing but assumption. Check your facts and you will see, it aint so.

---

### Post by Kilon on 2009-04-29
This is what you said 

> If you have learned to work with an IDE environment and associated application framework, you are unlikely to want to use another, simply because it probably took you a long time to become familiar with what your are using.

So it was reasonable of me to assume that you were talking about IDE as well. My telepathy skill is not very good you know. 

> You don't have to use C or C++, nor do you need to adopt C or C++ syntax to make use of C/C++ libraries.

no but it helps to know the language you are porting from. 

> In any event, there is no need to switch to C just because you want to call C libraries. 

I did not say that you need to. 
> 
That is simply not true. Just because the libraries ship with every Mac doesn't mean they are mac centric. 

I am not going to advertise that I am an objective c programmer because I am not. But I have never heard of objective c outside mac development and that casts serious doubts how well integrates with other os , like windows and linux. 

Also makes me wonder if objective c is all that nice and switch why don't the developers pick objective c for windows when the same app has been already developed in macos. Most windows ports from mac , are using c/c++ why is that?

---

### Post by gtr32 on 2009-04-29
> **CptPicard said:**
> A good, heart-felt *perkele *really lets out the steam at times.

LOL, that seems to be the one word everyone who isn't a Finn knows. I prefer to use other words than perkele myself. My wife doesn't speak the language but she does amazing job in pronouncing the words correctly since she's a native Spanish speaker. Pronounced as it is written, great language feature... ;)

---

### Post by UBForty on 2009-04-29
> I am not going to advertise that I am an objective c programmer because I am not. But I have never heard of objective c outside mac development and that casts serious doubts how well integrates with other os , like windows and linux.

on Windows ...

[http://www.cocotron.org/]("http://www.cocotron.org/")

[http://www.cocotron.org/Code/Examples/TextEditor/]("http://www.cocotron.org/Code/Examples/TextEditor/")

note that the examples presented in the screenshots compile and run without any modification whatsoever on both OSX and Windows, and if somebody bothered to, they'd probably compile and run the same under Linux using GNUstep.

[http://www.gnustep.org/]("http://www.gnustep.org/")

The whole point of OpenStep was platform independence, the API hasn't changed in that respect, what has been added since has been added at the top, not at the bottom where the hardware is.

> Also makes me wonder if objective c is all that nice and switch why don't the developers pick objective c for windows when the same app has been already developed in macos. Most windows ports from mac , are using c/c++ why is that?

The folks at Cocotron are doing just that, build their apps on Windows, using Objective-C and Cocotron, which is the Windows implementation of OpenStep.

However, your logic is flawed because by the same logic, .NET sucks because it is not used that commonly on platforms other than Windows. It ships with Windows, so it is bound to be most commonly used on Windows. Cocoa ships with OS X, so that is where it will be most commonly used. X.11, KDE and Gnome ship with the various Linux distros, that;s where they are most commonly used. Any of these can be used on any of the platforms though.

It's called innertia.

---

### Post by Kilon on 2009-04-29
Very interesting , thanks for the link , worth investigating further.

---

### Post by soltanis on 2009-04-29
I cry that we do not use Objective-C. Personally, it is my favorite Object Oriented successor to C, not the least because of dynamic message dispatch (most people downplay this feature until they've used it themselves; actually, its pretty damn useful).

Why don't we use it?

I. Apple dominates the ObjC market, unfortunately, most resources towards teaching you the language are also oriented towards teaching you the OS X/iPhone/etc API.

II. The syntax is ugly as hell, seriously. The square brackets are okay, but really, what is with the whole function declarations and the colons after their names?

III. It is simple. In fact, it is almost so simple, any C programmer who has the faintest idea of what OO is could learn it in about a day. It almost doesn't merit a book to be written about it in the first place (which explains why the introduction to ObjC itself covers about 1-2 chapters in most Cocoa books). Unfortunately simplicity is often frowned upon (for reasons I really can't understand, personally, I like having a language which I can keep all in my head without crowding other things out).

IV. Dude, what is with the file extension? .m? Seriously? If C is .c and C++ is .cc, where did .m come from? Why not .oc or .co or something like that?

---

### Post by ZuLuuuuuu on 2009-04-29
> **soltanis said:**
> II. The syntax is ugly as hell, seriously. The square brackets are okay, but really, what is with the whole function declarations and the colons after their names?

Are you serious? If you take out the "keyword: argument" thing from Objective-C then what will differentiate Objective-C from C++ or any other 431435285 programming language out there which are based on C++ syntax? Just dynamic message dispatching?

Maybe the syntax is ugly but saying "Obj-C is nice except its syntax" is like saying "Ice cream is nice except the cold melting thing on it".

---

### Post by soltanis on 2009-04-29
Call it what you will, but without that syntax ObjC would still be a far cry from C++. A superior far cry, by the way.

---

### Post by jimi_hendrix on 2009-04-29
maybe the fact that iphone apps are written in ObjC will give it some traction...

---

### Post by jimi_hendrix on 2009-04-29
> **soltanis said:**
> 
IV. Dude, what is with the file extension? .m? Seriously? If C is .c and C++ is .cc, where did .m come from? Why not .oc or .co or something like that?

.m == module || mac

take your pic

---

### Post by eye208 on 2009-04-30
> **jimi_hendrix said:**
> .m == module || mac

take your pic
.m == methods

@topic: Why is Objective-C not popular on Linux?

I guess it's because those who like the language only talk about it, but hardly use it. If you want to see your favorite language take off, write some code in it.

Of course that applies to all the other "superior" languages as well. C/C++ is popular because its fans are always busy producing new stuff. If you can't do that in <insert favorite language here>, maybe the language isn't that good after all.

---

### Post by UBForty on 2009-04-30
> **soltanis said:**
> I. Apple dominates the ObjC market, unfortunately, most resources towards teaching you the language are also oriented towards teaching you the OS X/iPhone/etc API.

By that same logic there should not be any Mono project, because .NET is dominated by Microsoft. Yet, there have been some folks who looked at .NET for its own merits, liked what they saw, apparently, and went about implementing their own and use it without being bothered where the original design/concept/implementation came from.

If a major linux distro, such as Ubuntu, was to embrace Objective-C and GNUstep, it would soon create enough momentum to make the whole thing less of an Apple dominated affair. Even if GNUstep was considered less desirable, one could always develop a new framework. If the naming was considered undesirable, one could build a new brand around the technology, say the language (or dialect if so desired) could be called Objuntu and the framework could be called Ustep, or something to do with coffee, Macchiato, whatever.

> II. The syntax is ugly as hell, seriously. The square brackets are okay, but really, what is with the whole function declarations and the colons after their names?

With all due respect but this is utter nonsense? What do you mean "ugly"? Do you have any _real_ argument? anything _tangible_? Someone might as well say "I would like Ubuntu, but I don't because it is brunette and I prefer blond." There is nothing that makes any sense in such a statement. It is not verifiable. Where is the standard, the definition for how to apply words such as "brunette" and "blond" to an operating system? There isn't any such thing. So it ends up being "It's brunette because I say so". Either, we have to take your word for it and conclude "Objective-C is ugly because you say so" or we can just make up our own, equally unverifiable definition and state, "Objective-C is beautiful, because I say so". Neither makes any sense. It's gobbledeegook. Postulating that colons within a method signature are a definition for "ugly" doesn't make any more sense either.

As for the syntax itself, it is simply a different notation, just like RPN (on many HP calculators) is a different notation from that found in calculators by most other vendors. Lisp is another example of a different notation, the function name is *inside* the parentheses along with its arguments. If you look around, you will find more examples. Different notation will mean _unfamiliar_ when you first look at it, sure, but that doesn't say anything about its qualities.

When Indo-Arabic numerals where introduced in Europe, it was a weird, unfamiliar notation. Roman numerals were considered normal, Indo-Arabic numerals were the "ugly" new kid on the block. It took a long time to phase out the Roman numerals, in some places we still use them today. Meanwhile, we don't think of Indo-Arabic numerals as weird looking anymore, to the contrary, Roman numerals are more unusual than Indo-Arabic ones. Now, it is Indo-Arabic numerals which are more familiar, and thus "normal" to us.

Roman numerals were good for the tasks which they were created for: writing down who has paid how much taxes, how owes whom how many silver coins or donkeys etc etc etc. Roman numerals are much less practical for more advanced mathematics though. With more advanced mathematics came a new notation which was more practical.

The common "function( arg1, arg2, ... argN)" style of notation has its roots in functional mathematics, it has originally been developed in the 17th century for notating and solving algebraic problems. For that type of problem it is a good notation indeed. The characteristics of these types of problems are such that there are a rather limited number of arguments and it is generally obvious what the arguments mean, they don't have to be explained.

In formulas such as a quadratic function, f(x) = a x^2 + b x + c, we know what x, a, b, and c mean because it is one function of a kind that we have memorised. In mathematics in general, and in algebra in particular, you have to memorise a great number of formulas, its the tool of the trade to know them, consequently, the parameters do not need much explaining, they are considered self-evident, even if they are not, we just memorise them and it becomes second nature to us (but most kids struggle at school to do so, not that natural after all). Also, the order of arguments is generally the same, for polynomials, it is an obvious convention to order the components by order of exponents from highest to lowest ... x^n + x^(n-1) ... x^0. All these characteristics of the problem domain lead to the characteristics of the notation.

However, in software development, today, the algebraic problems are only a small fraction of the entire problem space that is being handled. For most of the non-algebraic problems, the characteristics are different, in particular, it is no longer obvious what parameters mean and there is no logic or natural order how to order parameters. All this means that the notation alone is no longer sufficient to express the problem, that's why programs need comments that explain what the parameters of a function call are for. It would be obvious if the function is some algebraic function, but if the function is not algebraic, the more parameters there are, the more the need will arise to explain them.

Consider two examples ...

An algebraic function:

add(x, y)

Note how it is obvious what this does without any further documentation

A non algebraic function:

make_violin_top(3, 14, 26, 0, 2, 9 ...)

Note how ambiguous this is, no comments and we're are totally clueless


Now, consider the same examples in  Smalltalk style notation ...

the algebraic function:

a add: b

It is still fairly obvious what this does, but since the familiar notation does its job well, there isn't any obvious reason why we might want to use this new unfamiliar one.

the non algebraic one:

makeViolinTopFromWood: bearclawSpruce usingTemplate: GuarneriusDelGesu usingScraper: 3 usingCutter: 5 doublePurfling: No ...

This is the way humans communicate tasks to each other, you can translate the above Smalltalkish notation directly into instructions a violin master might use to talk to his apprentice when telling him to make a violin top

For non-algebraic real world tasks, the Smalltalk style notation is clearly more expressive than the algebraic notation. More expressive means there is less ambiguity, and less ambiguity leads to better understanding of the instructions, which ultimately means the instructions are going to be carried out properly. In a program it means better readability, this better maintainability and fewer bugs, thus overall more reliable software. In my experience, almost all of the bugs in Objective-C code come down to vanilla C bugs, unrelated to the message passing syntax. This also explains why Objective-C has a productivity advantage, interfaces are more easily understood without spending too much time trying to figure out what a function call does.

The downside (for some) is that you have to type more into your editor and many programmers, especially C programmers have grown into a culture where there appears to be a contest "He who can write the most tersely obfuscated code is the biggest gorilla on the block and gets all the bananas". However, there are syntax aware editors available today which do a great job at completion of partially typed in text and other such aids. So this downside is at best superfluous, at worst it is dishonest.

After decades of simply borrowing from Simula, we are now seeing more and more new languages which borrow from Smalltalk, including the "weird" syntax in question. It is too early to tell if that is going to be a major trend and it would be even more speculative to claim that this is going to be the mainstream notational style in the future, but the possibility for that certainly exists. It is certainly within the realm of possibility that the Smalltalk style of notation may one day be the mainstream and today's mainstream would then be considered "ugly" or "weird", simply because it wouldn't be taught to everybody at university anymore, simply because it would then be _unfamiliar_. Or, pehaps something yet again different comes along and replaces both the Simula and the Smalltalk style. In any event, unfamiliarity should not be confused for "bad" or whatever other negative adjective one might hastily attach to the unfamiliar.

> III. It is simple. In fact, it is almost so simple, any C programmer who has the faintest idea of what OO is could learn it in about a day. It almost doesn't merit a book to be written about it in the first place (which explains why the introduction to ObjC itself covers about 1-2 chapters in most Cocoa books). Unfortunately simplicity is often frowned upon (for reasons I really can't understand, personally, I like having a language which I can keep all in my head without crowding other things out).

The reason is the same reason why some people claim that some language is "ugly": unfamiliarity combined with innertia.

> IV. Dude, what is with the file extension? .m? Seriously? If C is .c and C++ is .cc, where did .m come from? Why not .oc or .co or something like that?

.m stands for iMplementation. They could have used .i but that would have been ambiguous because interface also starts with an "i". So they ended up with .h for the interface, out of convention, and .m for the implementation. I personally don't think that the file ending has any impact on the popularity of the language though.

> I you want to see your favorite language take off, write some code in it.

Amen to that! :-)

---

### Post by ZuLuuuuuu on 2009-04-30
> **UBForty said:**
> With all due respect but this is utter nonsense? What do you mean "ugly"? Do you have any _real_ argument? anything _tangible_?

I don't agree with this. Finding a syntax ugly is so natural (and it does not mean that it is ugly for all people). The real nonsense thing would be to demand a tangible thing about beauty. When you see a woman/man you can decide whether she is beautiful but you cannot list -at least, all- the arguments why she is beautiful.

[QUOTE=eye208]Of course that applies to all the other "superior" languages as well. C/C++ is popular because its fans are always busy producing new stuff. If you can't do that in <insert favorite language here>, maybe the language isn't that good after all.[/QUOTE]

The main reason I stop using ObjC was that I couldn't find the bindings for libraries I wanted. There is even no GTK+ binding (please don't count the 1-person, incomplete and not-maintained bindings). And I'm just an ordinary programmer who does not have technical knowledge to write bindings...

---

### Post by ajackson on 2009-04-30
> **eye208 said:**
> @topic: Why is Objective-C not popular on Linux?

I guess it's because those who like the language only talk about it, but hardly use it. If you want to see your favorite language take off, write some code in it.

Of course that applies to all the other "superior" languages as well. C/C++ is popular because its fans are always busy producing new stuff. If you can't do that in <insert favorite language here>, maybe the language isn't that good after all.

C/C++ **are** still popular, there is also a lot of development that is carried out in them because of legacy reasons. Not that legacy reasons are unique to C/C++ after all there was a huge demand for COBOL when the Y2K issue was around because a lot of firms had systems written in COBOL and it's hard to fix a COBOL program using <insert non-COBOL language here> but back in the late 90s you probably wouldn't class COBOL as a popular language.

As to why Obj-C isn't used more with Linux, it could just be that it didn't offer anything that couldn't already be done with tools that were in use at the start and that the developers were familiar with. Times change, requirements change but some languages still remain in use for a variety of reasons (legacy, popularity, "because I like it", "because I know how to use it", etc) and new languages enter the mix. If you can't handle change get out of computing as a lot of computing is about change.

At the end of the day there is no single killer language that suits all needs, some languages suit certain tasks but can be used for tasks they are not suited for (though a kernel written in Modula-2 would be funny to look at the source for). In some cases the choice of language to be used is limited (most IT departments probably don't have a free choice in language to use).

---

### Post by jinksys on 2009-04-30
> **ZuLuuuuuu said:**
> 
The main reason I stop using ObjC was that I couldn't find the bindings for libraries I wanted. There is even no GTK+ binding (please don't count the 1-person, incomplete and not-maintained bindings). And I'm just an ordinary programmer who does not have technical knowledge to write bindings...

Bindings? You can use any C/C++ library.  In fact, you can have C, C++ and ObjC in the same source file.

---

### Post by ZuLuuuuuu on 2009-04-30
> **jinksys said:**
> Bindings? You can use any C/C++ library.  In fact, you can have C, C++ and ObjC in the same source file.

I was expecting this answer :)

What is the point of using ObjC if you will write your code in C style? I will use ObjC because I want to do it like

```
[myWindow setHeight: 400 andWidth: 200]
```

not

```
gtk_widget_set_size_request (GTK_WIDGET (my_window), 400, 200);
```

And because there are so few bindings for ObjC you will end up using C or C++ in half of your ObjC source file.

---

### Post by UBForty on 2009-04-30
> **ZuLuuuuuu said:**
> I don't agree with this. Finding a syntax ugly is so natural (and it does not mean that it is ugly for all people). The real nonsense thing would be to demand a tangible thing about beauty. When you see a woman/man you can decide whether she is beautiful but you cannot list -at least, all- the arguments why she is beautiful.

Maybe you are confused, the adjective beautiful makes sense when used to describe a woman, or a picture and even the design of a GUI, but it doesn't make sense when used with things such as a notation, just as it doesn't make sense to call an operating system "salty" or "brunette" or "romantic" etc etc etc.

In any event the question was "Why is it not used" and the asnwer offered was "ugly" which you suggest to be translated into "because I personally don't like it" which is rubbish because the subjective emotional response of a single poster on a thread like this has absolutely nothing to do with the popularity and usage of a tool.

The real reason the poster was aiming at when he said "ugly" was however: unfamiliarity and innertia, that's what it will always come down to, no matter how you twist it.

---

### Post by UBForty on 2009-04-30
> **ajackson said:**
> C/C++ **are**some languages suit certain tasks but can be used for tasks they are not suited for (though a kernel written in Modula-2 would be funny to look at the source for).

You are misinformed. Modula-2 was created for one single purpose only: to build an operating system for an Alto like workstation.

[http://www.ethistory.ethz.ch/rueckblicke/departemente/dinfk/weitere_seiten/lilith/index_EN](http://www.ethistory.ethz.ch/rueckblicke/departemente/dinfk/weitere_seiten/lilith/index_EN)

You would be mistaken to believe that system programming languages have to be modeled after PDP-11 Assembly or that they can't be strongly typed. Nor was Modula-2 the first such system programming language either. Many people know that it is a descendent of Pascal, but few people know its other ancestor: Mesa, the system implementation language of the Alto at Xerox Parc.

---

### Post by UBForty on 2009-04-30
Anyway, I meant to ask

Whatever happened to this NextBuntu thing?

---

### Post by ZuLuuuuuu on 2009-04-30
> **UBForty said:**
> Maybe you are confused, the adjective beautiful makes sense when used to describe a woman, or a picture and even the design of a GUI, but it doesn't make sense when used with things such as a notation, just as it doesn't make sense to call an operating system "salty" or "brunette" or "romantic" etc etc etc.

Which kind of things may be called as beautiful is very subjective. You can claim that the adjective "beautiful" cannot be applied to a notation. It is your thought. But I think it can be applied. Typography deals directly with the beauty of a text in a composition and you can adopt the teachings of typography to the look of a code piece in your monitor to improve the readability of the language.

A person can think that being emotional is nonsense, which I think is very similar of your thought about a syntax being beautiful is nonsense :)

---

### Post by UBForty on 2009-04-30
> **ZuLuuuuuu said:**
> Which kind of things may be called as beautiful is very subjective.

Precisely my point. Unverifiable.

---

### Post by Kilon on 2009-04-30
> **UBForty said:**
> Precisely my point. Unverifiable.

People misunderstand subjectiveness and personal preference. They do not mean uniqueness as a matter of fact ugliness any way is perceived is more objective than it is subjective. 

So ugliness per se , may be an emotional response, but behind every motion there is reason and logic. Afterall  emotion and thought are closely interlinked. 

So when a person describes a language as ugly , it describes a set of criteria and priorities that exist many other people as well. Obviously not all of us have the same priorities. 

So dismissing personal preference as no proof , well it is plain wrong. Especially if that preference or dislike is expressed by many people.

---

### Post by UBForty on 2009-04-30
> **Kilon said:**
> So dismissing personal preference as no proof , well it is plain wrong.

Oh really? Well I loathe X11, I think it is the biggest pile of dog poo ever created, so my personal preference is not to program for it, and since dismissing such personal preference would be plain wrong, it should serve as proof that X11 is unpopular. Terrific spin worthy of an Iraqi Information Minister. But thanks for the laugh.

---

### Post by jimi_hendrix on 2009-04-30
> **ZuLuuuuuu said:**
> I was expecting this answer :)

What is the point of using ObjC if you will write your code in C style? I will use ObjC because I want to do it like

```
[myWindow setHeight: 400 andWidth: 200]
```

not

```
gtk_widget_set_size_request (GTK_WIDGET (my_window), 400, 200);
```

And because there are so few bindings for ObjC you will end up using C or C++ in half of your ObjC source file.

theres a gtk objc wrapper on LP that you could use

---

### Post by ajackson on 2009-04-30
> **UBForty said:**
> You are misinformed. Modula-2 was created for one single purpose only: to build an operating system for an Alto like workstation.
That'll teach me to pluck a language out of the air to use in an example :lolflag:. Thanks for the correction.

---

### Post by Kilon on 2009-04-30
> **UBForty said:**
> Oh really? Well I loathe X11, I think it is the biggest pile of dog poo ever created, so my personal preference is not to program for it, and since dismissing such personal preference would be plain wrong, it should serve as proof that X11 is unpopular. Terrific spin worthy of an Iraqi Information Minister. But thanks for the laugh.

explore the emotion , understand the logic behind it and you will see how complex our brain and our thought patterns are. Nothing is random. 

It is not rare to see people here being confuse of what goal should they set. Many people do not understand the logic behind their emotions and are quick to dismiss them as random events . But that is not true , emotions follow a special process and required a set of criteria. Understanding emotions , will help you understand your priorities and who you really are.  

Why do not you like this programming language ? What is it that frustrates you more ? Which is the cause of this frustration ? What this frustration says about yourself ?

These are the questions I asked myself many times and now I can understand why some programming languages do not fit me and what tools are more appropriate to my line of thinking.

---

### Post by ajackson on 2009-04-30
> **UBForty said:**
> Oh really? Well I loathe X11, I think it is the biggest pile of dog poo ever created, so my personal preference is not to program for it, and since dismissing such personal preference would be plain wrong, it should serve as proof that X11 is unpopular. Terrific spin worthy of an Iraqi Information Minister. But thanks for the laugh.
Personal preference is highly subjective but there comes a point when a lot of people sharing that preference make it a popular preference. Where that line is and what <random thing> needs to do to reach that point is one for the philosophers to debate for years on.

---

### Post by Kilon on 2009-04-30
> **ajackson said:**
> Personal preference is highly subjective but there comes a point when a lot of people sharing that preference make it a popular preference.

then it is not subjective. Or at least it is far from "highly subjective". 

There is reason why people have common preferences. And this reason is EXTREMELY IMPORTANT to understand.

---

### Post by ZuLuuuuuu on 2009-04-30
> **jimi_hendrix said:**
> theres a gtk objc wrapper on LP that you could use

[QUOTE=ZuLuuuuuu](please don't count the 1-person, incomplete and not-maintained bindings).[/QUOTE]

I guess ([https://launchpad.net/libobgtk](https://launchpad.net/libobgtk)) can be safely classified as incomplete and unmaintained (looking that it is last updated over one year ago). But I appreciate the work, hope that the team will get active again and it will be a usable binding one day.

---

### Post by ibuclaw on 2009-04-30
> **Kilon said:**
> People misunderstand subjectiveness and personal preference. They do not mean uniqueness as a matter of fact ugliness any way is perceived is more objective than it is subjective. 

So ugliness per se , may be an emotional response, but behind every motion there is reason and logic. Afterall  emotion and thought are closely interlinked. 

So when a person describes a language as ugly , it describes a set of criteria and priorities that exist many other people as well. Obviously not all of us have the same priorities. 

So dismissing personal preference as no proof , well it is plain wrong. Especially if that preference or dislike is expressed by many people.

I see ugliness as a "per program" basis, rather than a language thing. Since all the languages I work/deal with are procedural/imperative, I can read and follow them to a reasonable degree, even without prior knowledge of a particular language.

What makes a program look ugly in a certain programming language depends on the standard of that language, but the one that never fails to make me cringe are programs that make abusive use of system() calls or fsync().

I actually came across/read one such Pascal program once. Filed about 10 bugs on the google project page, and debated with the author as to why using a shell script is better idea in this case.

Don't use a screwdriver to hammer nails into a wall, or something along those lines is how the saying goes. ;)

Regards
Iain

---

### Post by ajackson on 2009-04-30
> **Kilon said:**
> then it is not subjective. Or at least it is far from "highly subjective".
I know but I was struggling to word it right.

> **Kilon said:**
> There is reason why people have common preferences. And this reason is EXTREMELY IMPORTANT to understand.
Of course you can't discount that people hold common preferences because they are told to (i.e. it is drilled into them that such and such is good, such and such is bad then in the end they don't form their own opinion but take up the mantra as the absolute truth, which it might well be but without evaluating or questioning it how would anyone know?)

Emotions, peer pressure, society - all these will have an impact on what we end up prefering.

---

### Post by Kilon on 2009-04-30
> **ajackson said:**
> 
Of course you can't discount that people hold common preferences because they are told to (i.e. it is drilled into them that such and such is good, such and such is bad then in the end they don't form their own opinion but take up the mantra as the absolute truth, which it might well be but without evaluating or questioning it how would anyone know?)



Of course. It is not brainwash actually , it is an instict of our brain to copy the behavior of others, if the beahviour is popular then the instinct become hard to resist. That is why popular choices are so easily followed. 

It is not wrong per so to behave likes this , afterall it is a hundrend million years evolution that got us here in the first place (counting from the first form of intelligent life on earth) . But it is not flexible and fitting to a creature of equal intelligence as we have.

I see this instinct as a fail safe device, I am not feeling bound to it but I am not dismissing it either.    

Thus mean that if you reallywant to use objective c , the instict might force you to a more popular choice , but as an intelligent being you can always ignore your instincts and prefer to choose something that better fits your personal needs.

---

### Post by eye208 on 2009-04-30
> **ZuLuuuuuu said:**
> The main reason I stop using ObjC was that I couldn't find the bindings for libraries I wanted. There is even no GTK+ binding (please don't count the 1-person, incomplete and not-maintained bindings). And I'm just an ordinary programmer who does not have technical knowledge to write bindings...
That is exactly what I was talking about. GTK+ has C bindings because Objective-C programmers *did not develop* GTK+. The only way to make a language popular is by writing code in it. Promoting it in forums and evangelizing people is not enough.

---

### Post by ajackson on 2009-04-30
> **eye208 said:**
> The only way to make a language popular is by writing code in it. Promoting it in forums and evangelizing people is not enough.
But then forums are for promoting discussions, talking about problems, pros, cons, etc. I'm fairly certain the forum isn't a compiler/interpreter, so posted everything you write in language *X* is pretty pointless.

Likewise how do you know what people write? Is every bit of source code ever written by a forum member magically available to others when they enter this forum? If so a warning notice should be displayed because some firms might not want there source code becoming freely available when an employee enters this forum.

In short just because people don't post their code in Modula-2, Obj-C, COBOL, Python, C, Ada, Fortran, etc; it doesn't mean they don't use the language.

---

### Post by bapoumba on 2009-04-30
Welcome to the Recurring discussions..

---

### Post by Kilon on 2009-04-30
> **eye208 said:**
> Promoting it in forums and evangelizing people is not enough.

Actually I disagree, making a buzz is always important. That is what Sun made with Java for instance.  

Of course coding for a language is what makes it more useful, obviously. But promotion is also very important if it motivates people to work for it. 

Afterall marketing nowdays is a big deal for companies. Forums might not be the best place to promote a language but is certainly a start. 

And as I am not the type of person who likes popular choices , I really like to hear about languages I have not explored, It keeps me open minded .

---

### Post by ZuLuuuuuu on 2009-04-30
> **bapoumba said:**
> Welcome to the Recurring discussions..

Why Objective-C is not a popular language is a recurring discussion?

---

### Post by jimi_hendrix on 2009-04-30
> **ZuLuuuuuu said:**
> Why Objective-C is not a popular language is a recurring discussion?

they see this is degrading to a flamewar...but thats not fun to move it :(

btw, does anyone have an objc plugin for eclipse?

---

### Post by UBForty on 2009-05-01
> **Kilon said:**
> Thus mean that if you reallywant to use objective c , the instict might force you to a more popular choice , but as an intelligent being you can always ignore your instincts and prefer to choose something that better fits your personal needs.

What is mainstream and what is not is entirely random and artificial, it has to do with luck and backing by a major player who is willing to push it down our throats for as long as it takes to break our resistance to change. It is a variation of the old Goebbels paradigm to repeat a lie often enough and people will believe it. Perl is quite possibly the only exception to this.

The only difference between accepting a shoved-down-your-throat language and an also-run language is that your motivation to overcome the unfamiliarity is externally imposed in the first and has to come from within yourself in the latter case.

Note that the sides can easily be reversed depending on environment. For example, at Apple, Pascal used to be the language for everything and not everybody liked it initially, so Pascal was a shoved-down-your-throat language within that eco-system. Objective-C has since replaced Pascal in that capacity in that eco-system. On the other hand, within that eco-system C# and Java are playing the role that Pascal and Objective-C have in the Windows and Linux eco-systems.

In the Windows and Linux eco-systems it is the opposite, C# and Java are shoved-down-your-throat languages and Pascal (now Delphi) and Objective-C are also-rans for which you have to find motivation by yourself, without external imposition.

Murphy's law "You have taken yourself too seriously" applies here more than anything else. Just because you are in agreement with most of your peers within your reference group doesn't mean that you have made "the right choice". The choice was made for you and you have been coaxed into believing that it was yours. This applies to C# programmers in the Windows eco-system as much as it does to Objective-C programmers in the OS X eco-system.

This is the root course of why there is innertia. Goup think may have something to do with it, too, but first and foremost it is resistance to change, resistance to investing time and effort.

An argument that X is unpopular because it is "ugly" where ugly has been defined by the majority opinion on this thread as "not conforming to majority preference" can be logically reduced to "X is unpopular because it is unpopular", which is just very ineloquent way of saying, "X is unpopular because of innertia".

---


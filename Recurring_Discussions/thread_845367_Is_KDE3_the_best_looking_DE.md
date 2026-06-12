---
title: "Is KDE3 the best looking DE?"
date: 2008-06-30
forum: Recurring Discussions
---

### Post by sink on 2008-06-30
I think it looks gorguous

---

### Post by Greyed on 2008-06-30
It's all subjective, really, esp. given the prevalence of themes.  However, my personal opinion is:

KDE3 is the best looking and feeling DE.
Heron Gnome's background is the best default background I have seen in decades.
XFCE4 is only slight less than KDE3 but that's because of the insistence of having the frakin' bar at the top of the window.

---

### Post by sink on 2008-06-30
xfce is the only de whose desktop effect works without turning compiz on in my machine.

but kde has very good icons set.

---

### Post by dexter.deepak on 2008-06-30
have you all tried kde4 ? i guess you'll like it much more...and seems pretty stable too:
```
sudo apt-get install kde4-core
```

---

### Post by Greyed on 2008-06-30
> **dexter.deepak said:**
> have you all tried kde4 ? i guess you'll like it much more...and seems pretty stable too:
```
sudo apt-get install kde4-core
```

Yes.  Complete and utter rubbish.  I lament the fact that after 3.5.9 ages I'll have to move off to Gnome or switch full time to XFCE.

---

### Post by doorknob60 on 2008-06-30
Or wait till the KDE developers think it's ready. Kubuntu gives KDE 4 a terrible reputation, try Opensuse KDE 4 and you'll change you're mind. KDE 4 will be ready by Ibex, and hopefully the Kubuntu team does a good job of implementing it.

---

### Post by tubasoldier on 2008-06-30
Its interesting when threads like this start. Objective opinions.

As far as KDE4 goes, 4.0.83 is pretty decent. However, there are still a lot of bugs. It is still considered beta. KDE 3.2 had loads of issues as well. Now that its on to 3.5.9 KDE 3 is rather stable. It may take a few dot releases for KDE to reach the same level of usability and stability. You have to keep in mind that it was a complete rewrite of the desktop. There were lots of reasons behind rewriting a lot of it.

KDE 3.5.9 will be available in repos for quite some time. If not available in the official repos it will be available in third party repos like medibuntu. Give KDE4 the benefit of the doubt. wait for 4.1 see how it is. If it isn't quite up to par wait for 4.2. KDE 3 will still be available.

As far as looks go I think with a little work it isn't hard to make Gnome or KDE look very similar.

---

### Post by Greyed on 2008-06-30
See, that's why I'm a tad miffed about KDE4.  It is 4.0.  Released.  There is an official release notice on the KDE site.  I may be wrong but I don't recall FOSS pushing out known unfinished software with all the markers of being finished.  If it's not finished they why did it get out of the 3.9 or 4.0alpha, 4.0beta stage?

Sorry, they pushed it out as finished and I'm judging it as such.  If it isn't then either way you look at it that is on them.

---

### Post by tubasoldier on 2008-06-30
> **Greyed said:**
> See, that's why I'm a tad miffed about KDE4.  It is 4.0.  Released.  There is an official release notice on the KDE site.  I may be wrong but I don't recall FOSS pushing out known unfinished software with all the markers of being finished.  If it's not finished they why did it get out of the 3.9 or 4.0alpha, 4.0beta stage?

Sorry, they pushed it out as finished and I'm judging it as such.  If it isn't then either way you look at it that is on them.

KDE has always been this way. KDE 3 was the same when it was first released. KDE developers are known for saying things before they are actually done. when KDE 3.5.1 was released we were told that they were going to stop working on KDE 3 all together. Now its at 3.5.9. Calling 4.0 a release and not beta was pretty bad marketing wise. However, it got a lot of people trying it and filing bug reports.

I'm a tad miffed that KDE is being touted as "dead" because of the poor release timing of KDE 4. I'm surprised at all the "I'm done with KDE all together" threats. Steven J. Vaughn-Nichols even suggested a fork. While he himself was against forking KDE 3 two years ago in what was called "KDE classic".

The open source ideals are to "release early and release often". Thats what the KDE devs have done. Personally I'm not much of a coder, but I know how to file bug reports.

All I'm saying is to give it time. Have you tried the new 4.1 RC2? A MAJOR improvement over 4.0.4. If you think its terrible now, then give it a year. KDE 3.3 was the release that I stopped noticing major bugs. It may take KDE4 that long as well.

---

### Post by sink on 2008-06-30
I have tried open suse 11

sorry, kde 4 is ugly, the plasma is ugly(at least for now).

---

### Post by GeneralZod on 2008-07-01
> **Greyed said:**
> I may be wrong but I don't recall FOSS pushing out known unfinished software with all the markers of being finished.

Perhaps you're too young to remember, then ;) It results from two things.

1) Release Early, Release Often - the open source mantra.  Free Software projects can rarely afford QA teams, so they are forced to rely on community testing.  One of the perversities of human nature is that the point at which software most needs testing - the alpha and beta stage - is precisely the point at which people don't bother to test - they wait for the full release, and *then* complain that things don't work as expected :).  So what can you do? The only move that makes sense is to do a proper release. 

2) Big Changes Mean Big Breakage.  I'm not sure people fully appreciate just how much work the port from Qt3 to Qt4 was: to put it in perspective, *half* of the total number of commits to KDE's svn - with records dating back to 1998, right near the beginning of the project - have occurred since work on the KDE4 branch began, some time around June 2005.  The creaky desktop shell has been replaced and re-written from scratch.  Millions of lines of code have been ported to a version of a toolkit which is very, very different to the one before it.  You don't do this level of breakage and expect to Get It Right(TM), or anywhere close to right, on the first release.  It will likely take a few extra releases for the dust to settle.

The reasons we don't see very many such breakages in the Free Software world is that, bluntly, very few have been of equivalent scope - GNOME 2.0 is perhaps the only example that is close.  And what do we see when we examine the reaction to this? Erunno has a nice post on the subject, here; I advise people to go check it out.  And this isn't a case of "Well, the GNOME guys are just as bad!" - it's a case of "This is what the first release(s) of a major departure from an existing codebase is supposed (destined ... ?) to look like".

[http://www.osnews.com/thread?304220](http://www.osnews.com/thread?304220)

But look where it is today: perhaps the most popular desktop environment, and very slick and complete.  Linux 2.6.0, Apache 2.0 etc are apparently other major, full releases of software that were similarly lambasted upon release, and on the proprietary side, people were severely unimpressed with OS X 10.0 

Personally, I see two aspects where the KDE guys dropped the ball:

1) The Release Candidates were not Release Candidates.  Aaron Seigo has argued the point extensively, but as much as I like the guy, this is is one area where I've never been convinced by him.  A Release Candidate, as the term is generally used, is a release which will be the final release as long as no showstoppers are found - in particular, no new features are supposed  to be added in a release candidate.  KDE continued to have very major work performed on it through the RC cycle, which annoyed a lot of people - including a lot of core devs - due to what appears to be a rather cynical abuse of the term.

2) As someone who anticipated how rough the KDE4.0.0 release would be a year in advance - partly due to the reasoning above which made it more or less an inevitability, and partly due to the fact that I started doing daily builds for myself back in Jan '07 - and started warning people not to get their hopes up, I was rather dismayed by the lack of warnings coming from the developers - particularly on the main release announcement:

[http://www.kde.org/announcements/4.0/](http://www.kde.org/announcements/4.0/)

Sure, developer blogs were full of warnings, but the places where an end-user will look are almost devoid of them.

---

### Post by Greyed on 2008-07-01
> **tubasoldier said:**
> The open source ideals are to "release early and release often". Thats what the KDE devs have done. Personally I'm not much of a coder, but I know how to file bug reports.

Yes, it is.  Release early and release often does not include "release unfinished software and call it a milestone release."  Which is why I said if 4.0 was not done and they knew it then it should still be 3.9.x or 4.0alpha or 4.0beta or whatever their particular marker for "we're close but not done yet" is.

Let me further clarify that I am not talking about without bugs.  I'm not so naive to believe software is ever bug free.  Even "hello world" probably has bugs introduce by the compiler.  ;)  I'm talking about lacking fundamental features.  Like, for example, being able to move widgets on the bottom bar.

That's not a "whoops, how'd that get there, let's push out a hot fix for that."  That was a, "It's not done yet but we need to shove this out the door to get into several distros long-term releases."

One I can, and do, find acceptable.  The other I do not.

---

### Post by Greyed on 2008-07-01
> **GeneralZod said:**
> Perhaps you're too young to remember, then ;) It results from two things.

I would not presume such things.  

Date: Fri, 18 Sep 1998 13:13:34 -0700

Timestamp of my first message to debian-users.  ;)


> 1) Release Early, Release Often - the open source mantra.

As my previous message says, that does not extend to "release known unfinished versions as finished".  Release early means works in progress are released.  And if they are known as works in progress they tend to get the appropriate response which is, "Oh, this is missing, cool, I'll check back later."  Release it as finished and you get "WTH, this is missing, what were they thinking!?"

> One of the perversities of human nature is that the point at which software most needs testing - the alpha and beta stage - is precisely the point at which people don't bother to test - they wait for the full release, and *then* complain that things don't work as expected :).

Which is exacerbated by the fact that distributions were one can reach a large audience of testers-but-not-compilers don't compile until late in the testing game.  I'm more than willing to test packaged versions.  I'm an early adopter.  Just not roll-your-own early as I have other projects I'd much rather work on that compiling something as large as KDE.  :)

> So what can you do? The only move that makes sense is to do a proper release.

Nope, doesn't make sense to me hence my comments.  Though with my above paragraph I will say that maybe the distros could help in the process by starting the packaging a tad earlier?  

> 2) Big Changes Mean Big Breakage.

I can't think of a bigger change with less breakage than that from libc5 to libc6 aka glib2.  Nothing like breaking binary compatibility at the most basic of level and upgrading through it.  :P

> I'm not sure people fully appreciate just how much work the port from Qt3 to Qt4 was:

I don't care how much work it was.  I care that it was unfinished and declared finished.  Unfinished to anyone who twiddled with it for more than 3 minutes unfinished.  That's barely alpha level software.  At least from my understanding:

**alpha** - feature incomplete, put out to test the features that are there, get feedback on them to guide development of features that are not yet complete.
**beta** - feature complete but needs testing; lots of bugs to squish.
**gamma**, whoops, these days they're called "**release candidates**" or simply RCs - feature complete, been through testing, no showstoppers are known to exist but still holding out for x days/weeks to see if some crop up.
Release - feature complete, no known showstoppers, maybe some minor annoyances are known, probably some lurking unknown bugs.

Now, given the above understanding let me tell you what happened on my KDE4 install.

Fired it up.  Cringed at the huge ball-o-crap in the upper left corner.  Cringed again at the drancing, prancing, **pay attention to meeeeeee** icons.  Held down my bile at the horrible XP-esque, completely useless K menu.  Found out I could change it to something more akin to KDE3's quite useful K menu.  Deleted the worthless one, add "applet" for the other K Menu.  It adds on the far right.  Ok, no problem, let's drag that to the left.  Nope, no draging.  Ok, right click to select "move" and move it that way.  Nope, no move in the right click menu.  Check in configure, no way to tell it was position to occupy.  RClick on the menu bar to see if there's a way there to tell it how to order it.  Nope.  We have now hit the 3 minute mark in KDE and this is what I consider feature incomplete since this is the most basic of operations for the bar across the bottom of the screen.

OOOk, get grumpy and grouse about it to K-U in case someone knows what to do.  0 response in 2 weeks; figured someone didn't know.  So in an unrelated discussion in K-U where I defended someone else being just as annoyed as I was at KDE I described the above and was told "Drag it from the add-an-applet dialog to the bar."  Tried that, won't drag.  Ok, try it again, won't drag.  Sneak-up-on-it, won't drag.  No, I didn't try grabbing some of my wife's clothes and dress in drag to see if that would convince it to drag but the idea did cross my mind.  I finally tried dragging the *icon* instead of the text and it worked.  Nevermind that dragging from the text has worked in every version of KDE, XFCE and Gnome I have tried in the past few years.  So again, in about 3 minutes I hit something that I considered feature incomplete for one of the most basic operations of a DE...  ***DRAG* & drop**.

So, armed with that knowledge look at the scale above and where do you see me fitting this particular piece of software?

**alpha** - feature incomplete, put out to test the features that are there, get feedback on them to guide development of features that are not yet complete.

Is it feature incomplete?  Obviously.  Are they still looking for feedback to guide future features and refine the current ones?  Yes.  It's ok they released it, really, it is.  It is not ok they called it a finished release when they knew and it is obvious they were far from.

> Linux 2.6.0, Apache 2.0 etc are apparently other major, full releases of software that were similarly lambasted upon release

No, not as bad as this.  Not nearly as bad as this.  2.6.0 was controversial because of some features not being included that people thought should have and vice versa.  It also had issues with the memory management but, and this is key, it was better than 2.4 in certain situations, worse in a few rare situations and *nothing better was in the wings until months later*.  Apache 2.0 was a major departure from Apache 1.x in that it uses threads instead of processes but having been on the business end of a 1.x to 2.0 conversion it was feature complete.  Some things changed but they were needed changes that were good.  

Both of those, and many others, don't apply at all to KDE4.

> and on the proprietary side, people were severely unimpressed with OS X 10.0

Well, those people are clueless.  10.0 was far better than some *cough*Vista*cough*ME*cough*NT 3.51*cough* OS releases prior to it.  The problem was that it broke compatibility with 9.x applications which was a good thing.  I'm betting if you asked the complainers then if they think it was a good thing now they'd either agree with you or continue banging their head into the padded wall.  Heck, I can sum up in 2-words.  Preemptive multitasking.

> 1) The Release Candidates were not Release Candidates.

On this we agree although I considered the release 2 steps back from RC.  ;)

> 2) As someone who anticipated how rough the KDE4.0.0 release would be a year in advance


(snippage)

> I was rather dismayed by the lack of warnings coming from the developers - particularly on the main release announcement:

[http://www.kde.org/announcements/4.0/](http://www.kde.org/announcements/4.0/)

And this is my main beef.  I can forgive a lot in alpha/beta level software.  Even RCs.  But this was billed as a fully functional release.  That is why I say I judge it as such.  There's no do-over for that as much as they might want.  That announcement doesn't say it's bare-bones, feature incomplete, bordering on possible-beta status.  It says this is the next release, full stop, no qualifiers.

Either they didn't know and released it or they did know and released it.  The latter is the most likely case and that is the worst of the two because if they knew then they knew they shouldn't have released it.  So now they have a feature incomplete DE being judged on its horrible merits **and** trying to backpedal out of the release announcement.  Bad, bad devs.

---

### Post by joninkrakow on 2008-07-01
> **Greyed said:**
> 


Well, those people are clueless.  10.0 was far better than some *cough*Vista*cough*ME*cough*NT 3.51*cough* OS releases prior to it.  The problem was that it broke compatibility with 9.x applications which was a good thing.  I'm betting if you asked the complainers then if they think it was a good thing now they'd either agree with you or continue banging their head into the padded wall.  Heck, I can sum up in 2-words.  Preemptive multitasking.

Actually, I personally consider OS X.0 to be a perfect analogy to KDE4. OS 10.0 was _not_ feature complete. It was a dog--and a very sick one at that. OS X.0 raised the ire of many a user for these reasons, and I hear the same sort of complaints regarding KDE4 as I heard from X.0 users. In fact, I didn't upgrade from OS 9 until 10.2 was well under way. 10.1 was only slightly less of a sick dog than 10.0 was, and it wasn't until 10.2 that we could say that we had a proper operating system, and X has only gotten better since. 

In fact, when I was reading about KDE 4, earlier in the process, I remember reading how some features were "planned" for later releases, and thinking how much it sounded like 10.0. That said, the changes sounded good to me, though I knew that KDE4 would not be complete. I made the "mistake" of installing KDE4 right off the bat, and lost my panel--a bug--a genuine bug--fixed rather quickly, but otherwise, while it's lacking what could be called functionality, it also offers stuff the old KDE didn't. I think that KDE is truly pushing the boundaries, and the fact that some things still work is a small surprise (coming from Classic MacOS to OSX) ;-) 

My take is that simply complaining--griping--never helped anyone, including the griper. Your bile probably doesn't need to be that active--causes indigestion. ;-)

-Jon

---

### Post by Greyed on 2008-07-01
I play enough TF2 to relieve any stress.  ;P

---

### Post by T2manner on 2008-07-01
KDE3 is okay.
I much prefer Gnome or Xfce.

I had a lot of problems with the themes on KDE3 and haven't tried it since then.  Besides the default theme, the others look like they're still in alpha stages!

---

### Post by sub2007 on 2008-07-01
> **Greyed said:**
> It's all subjective, really, esp. given the prevalence of themes.  However, my personal opinion is:

KDE3 is the best looking and feeling DE.
Heron Gnome's background is the best default background I have seen in decades.
XFCE4 is only slight less than KDE3 but that's because of the insistence of having the frakin' bar at the top of the window.

In XFCE you can put the bar wherever you want, it's very flexible. Just right click on the bar > Customize Panel > Then "Fixed Position" and click what position you want the bar in. You can add the task list to the "top" bar so all your running programs will stack onto that easily and then you can put that to the bottom and it will be a spitting image of the KDE "bottom" bar. I personally like having it set to the top centre with "Normal Width" so it sits nicely in the middle of the top of the screen with no wasted space.

I'm not sure what's the best looking, I think probably XFCE for it's elegance. I always found KDE too flashy looking for my liking.

---

### Post by cardinals_fan on 2008-07-01
I love KDE 3.5.  Not as much as Xmonad, but I still love it.

---

### Post by sink on 2008-07-02
> **sub2007 said:**
> In XFCE you can put the bar wherever you want, it's very flexible. Just right click on the bar > Customize Panel > Then "Fixed Position" and click what position you want the bar in. You can add the task list to the "top" bar so all your running programs will stack onto that easily and then you can put that to the bottom and it will be a spitting image of the KDE "bottom" bar. I personally like having it set to the top centre with "Normal Width" so it sits nicely in the middle of the top of the screen with no wasted space.

I'm not sure what's the best looking, I think probably XFCE for it's elegance. I always found KDE too flashy looking for my liking.

I like xfce too but it lacks a decent menu editor or I will like it very much.

---

### Post by cardinals_fan on 2008-07-02
> **Greyed said:**
> Yes, it is.  Release early and release often does not include "release unfinished software and call it a milestone release."  Which is why I said if 4.0 was not done and they knew it then it should still be 3.9.x or 4.0alpha or 4.0beta or whatever their particular marker for "we're close but not done yet" is.

Let me further clarify that I am not talking about without bugs.  I'm not so naive to believe software is ever bug free.  Even "hello world" probably has bugs introduce by the compiler.  ;)  I'm talking about lacking fundamental features.  Like, for example, being able to move widgets on the bottom bar.

That's not a "whoops, how'd that get there, let's push out a hot fix for that."  That was a, "It's not done yet but we need to shove this out the door to get into several distros long-term releases."

One I can, and do, find acceptable.  The other I do not.
Took the words out of my mouth ;)
> **sink said:**
> I like xfce too but it lacks a decent menu editor or I will like it very much.
Xfce **does** have a decent menu editor, it's just implemented poorly.  Read [the wiki section]("http://wiki.xfce.org/faq#menu").

---


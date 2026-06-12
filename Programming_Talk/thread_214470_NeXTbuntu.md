---
title: "NeXTbuntu?"
date: 2006-07-12
forum: Programming Talk
---

### Post by Rick 1 on 2006-07-12
I'd be interested to find good developers who'd contribute to getting an OpenStep spec running on a Ubuntu distro. Given my current situation I can devote considerable time to such a project.

I know there are bits and pieces strewn around the Internet, but there's nothing cohesive there. Having worked in systems development with both hard-wired 'C' systems and NS/OS X, I know why the one is so much better than the other.

And these are benefits that can accrue to users too.

Drop a line - send a mail message - if you're interested.

Thank you.

---

### Post by Daverz on 2006-07-12
An up-to-date set of debs might be a good start.  I don't really want to install another distro just to get a working GnuSTEP environment.

Frankly I don't think there will be many GnuSTEP apps written until the tools are better documented.  I spent several hours trying to figure out how to add a field to a NSFORM in Gorm, and I eventually just had to guess (Right ALT + left mouse button drag on an existing field.)

Well, sorry to use this thread to do a bit of whining...

Anyway, here are [all the debian GnuStep packages.](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=gnustep&searchon=all&subword=1&version=all&release=all&page=1&number=50)

---

### Post by Max Luebbe on 2006-07-12
I love doing NextStep, Objective-C work.
I'd be interested in helping out if something gets going.

---

### Post by Note360 on 2006-07-12
Sounds good coming from OS X. Good luck I may join in at a latter date.

---

### Post by henrikmk on 2006-07-14
I'd be interested too, if it gives a chance to make a real and proper GNUstep desktop. I'm never sure on how to get the dev-tools working properly.

Also I think that GNUstep gets way too little attention.

---

### Post by Rick 1 on 2006-07-15
Oh very good. I think our tally is now up to about ten. Now to figure out the NeXT move... :grin:

---

### Post by Note360 on 2006-07-15
Ok cool I will make a page up for use how does
[http://zephyrwood.org/Ustep](http://zephyrwood.org/Ustep) sound? I'll install drupal or should I just put up a normal XHTML page?

---

### Post by gmclachl on 2006-07-15
Coming from OSX to Ubuntu this interests me. I would love to get involved as well.

---

### Post by Note360 on 2006-07-15
So should I make up the temporay page for our litte project. Sorry if I can't help much cause I don't know Obj-C just some Perl and Ruby and C.

---

### Post by Daverz on 2006-07-15
> **Note360 said:**
> So should I make up the temporay page for our litte project. Sorry if I can't help much cause I don't know Obj-C just some Perl and Ruby and C.

There's a Ruby bridge for Obj-C called Rigs:

[http://www.gnustep.org/experience/RIGS.html](http://www.gnustep.org/experience/RIGS.html)

---

### Post by Note360 on 2006-07-15
Wow so most of it has been done for us all we have to do is fill in the pieces. Implement Rigs and Jigs get a slightly better GUI than the classic NeXT GUI and we should be good. Though after that comes the hard part replacing apps and bringing the dead ones back into movement. We may be able to get some OS X programmers to help us out. Personally I think we should try to get some sort of Mono thing where all the NeXTSTeP implemented languages can speak to eachother.

---

### Post by Rick 1 on 2006-07-16
I think what's next is a wish list, a declaration of intent, to see where people stand. I think there is code that can be yanked from a number of places. Some of the things I'd like to see and/or make clear are as follows.

- Use the 'NS' prefix for all classes. None of this 'search and destroy' for 'GObject' replacing it with 'NSObject' and so forth. Jobs might have a hissy fit but I don't think he can patent a bloody prefix. Idea is to make code as portable as possible.

- This is for Linux so there's no Carbon/toolbox/beige box cruft in there. This means that there are no toll free bridged classes such as NSCFString and so forth - there is only NSString.

- Get as close to the current Apple OS X spec without going OTT. I think this means stopping short of 10.3 as that one started to really lose it.

- Don't lock the GUI in to only one look approved by Jobs. Make sure people can use skins without reverting to 'unsane' approaches as used by Unsanity. We don't want system hooks running in a root account context. That's just nuts.

- Offer a menu bar as one of (at least) two ways of doing the same thing and offer the NeXT cascading menus out of the left side of the screen as the other way.

- Get the graphics out of the 1980s and into 2006. Again, don't go OTT, but make it look as much like Apple as Apple themselves have done.

- Try to keep as much compatibility as possible. Don't go redesigning things. Apple can be very good at times in terms of UI design (and then they can be bad). Settle on just doing what everyone agrees is good with what they do and disregard the rest.

- No more blithering .DS_Store or anything like that. The default file manager (FileViewer?) has to be fast and practical. I think the NS file manager was one of the weak points of the platform.

- As you don't have to cater to Carbon freaks, you can implement all the things Apple deprecated to placate them. Such as detachable menus and the like.

Any or all of this might already exist in GNUstep. I don't know. I haven't got that far. We've got a tonne of CDs here and are waiting for the opportunity to begin. But I think those points could be the start of a much longer and more cohesive list so everyone knows up front what we all want and so we're in agreement before we begin.

Cheers.

---

### Post by Rick 1 on 2006-07-16
> **Note360 said:**
> Wow so most of it has been done for us all we have to do is fill in the pieces. Implement Rigs and Jigs get a slightly better GUI than the classic NeXT GUI and we should be good. Though after that comes the hard part replacing apps and bringing the dead ones back into movement. We may be able to get some OS X programmers to help us out. Personally I think we should try to get some sort of Mono thing where all the NeXTSTeP implemented languages can speak to eachother.
I think the real bitch is to get an IB working. If you can make that almost totally cross-platform compatible, then you can import NIBs. I think this would be a huge jump forward. Of course making an IB that good isn't going to be easy. It's a cornerstone of what they got.

If you can 'basically' port code directly and it at least compiles (without telling you blah-blah header file or library can't be found) then you have an incredible hurdle behind you.

Yes, I think there is a lot of code out there that can be used. But now it's going to have to be gone over with a fine toothed comb. What are the current specs and how well does the available code measure up to it? What has to be added? And so forth.

I think GNUstep might very well be the place to start, but I'd be for more cross-platform compatibility. Re-christen everything so OS X developers can directly use their code as much as possible in the new environment.

If Jobs wants to cling to his 2% market share, let him. A project like this will steal his baby out from his clutches and give everyone the opportunity to use the technology.

Maybe we need someone to take a look at what GNUstep has today and report in broad strokes what's needed to get to tomorrow.

As for Mono stuff and all that, I think that's something to wait with. One bridge, one objective, at a time. Objective-C is the in-house language - don't get anxious about others just yet. My 0.02.

---

### Post by Note360 on 2006-07-16
Well I know that any Mono like thing will come much much latter after we get something working. SO whats the name I think we need to keep step get rid of NeXT cause NeXT is what will get us into trouble. One last thing we have Ruby and Java built in from GnuStep (JIGS and RIGS).

---

### Post by Max Luebbe on 2006-07-18
I'm getting excited about this.
Anybody make a project page yet?
A wiki or something would be useful to start organizing thoughts.

I also agree that we should stick to ObjC before going overboard and trying to write in a bunch of languages

If anybody knows any graphic design folks, that would be a huge help, as I agree that getting a modern look to NStep that doesnt scream NEXTCUBE would be a major step forward.

---

### Post by Daverz on 2006-07-18
> **Max Luebbe said:**
> I'm getting excited about this.
Anybody make a project page yet?
A wiki or something would be useful to start organizing thoughts.

I also agree that we should stick to ObjC before going overboard and trying to write in a bunch of languages


However, making sure that RIGS and JIGS work out of the box will make GnuSTEP accessible to that many more programmers.

If PyObjC worked with GnuSTEP I'd definitely use it, but that will take a lot more work from an experienced GnuSTEP programmer as the PyObjC developers are just not interested enough to make it work right now.

---

### Post by Note360 on 2006-07-18
OK I set up the drupal blog at zephyrwood.org/ustep I am working on putting a wiki up in it.

---

### Post by Note360 on 2006-07-18
Sorry having some trouble

---

### Post by Note360 on 2006-07-18
OK, Finally the drupal page is up at [http://www.zephyrwood.org/ustep](http://www.zephyrwood.org/ustep) I have a nice forum set up for us to use. [http://www.zephyrwood.org/forums](http://www.zephyrwood.org/forums) lets move over their for now for discussion (our main page will be the drupal one). Let me tell you this is one strung out forum it does live chatting (every time some one posts it auto updates), RSS feeds on the posts, ect.

---

### Post by cbv on 2006-07-19
Replying to Rick1's comments:

- The OPENSTEP API is, well, open. So, yes, you can prefix classes with NS without Jobs having a *hissy fit*. Cocoa on the other hand is not. So you will have a hard time implementing those classes without makeing a copy which will have Apple Legal knocking at your front door...

- CoreFoundation is open-sourced and can be compiled on Linux. No problem implementing NSCFString here. Thing is, no one has bothered to do so, because there's no real need to.

- Cocoa classes are well documented and available online. Read the documentation, then start hacking, but see above.

- GNUstep already is themable.

- GNUstep already offers several different ways of implementing application menus. One is the original vertical menu as seen on NeXTSTEP and OpenStep, another is a vertical menu as seen on OS X.

- See above, GNUstep is already themable. And 'system images' can be replaced by simply copying over more 'appropriate' images.

- Compatibility as in? GNUstep works on everything but your toaster. Then again, since NetBSD can run your toaster and GNUstep works on NetBSD...

- GNUstep is an API, not a program, application or Desktop Environment. If you feel you need a decent 'file explorer' go ahead and write one. The power of GNUstep's API is Objective-C which is object-oriented. Overwrite the methods you think are implemented in a 'wrong' way.

- GNUstep already offers detachable menus.

Instead of re-inventing the wheel and write your own implementation, go ahead, take a look at GNUstep and get involved.

GNUstep's development tools are using a very different approach to what you may be used to. To get an idea how they actually work, head over to Linux Journal and read the excellent article by Ludovic Marcotte, the author of GNUMail: [http://www.linuxjournal.com/article/6418](http://www.linuxjournal.com/article/6418)

Oh, and before I forget: GNUstep can read and use NIBs already. Support for writing NIBs will be implemented within the next few days.


*A project like this will steal his baby out from his clutches and give everyone the opportunity to use the technology.*

Actually, GNUstep has been around since about 1992. Public interest has been low ever since. Mostly because of *that weird C dialect*. And it doesn't look, feel and crash like Windows, GNOME or KDE. So people rather stay away...

---

### Post by Note360 on 2006-07-19
Ok, sorry well we will try our hand at it for a bit you GNUsteppers are fully inclined to come and help as well as come and take everything is open.

---

### Post by mk_schmidt on 2006-07-20
That sounds really great!

I posted a link to his thread on the last two active NeXT forums ([www.nextcomputers.org](www.nextcomputers.org) and [www.nextarchive.net)](www.nextarchive.net)).

---


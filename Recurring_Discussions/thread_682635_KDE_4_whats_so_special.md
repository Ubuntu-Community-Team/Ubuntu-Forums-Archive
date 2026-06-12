---
title: "KDE 4 whats so special"
date: 2008-01-30
forum: Recurring Discussions
---

### Post by timboellis on 2008-01-30
With the release of KDE4 the one I was looking at was Shift Linux I have used KDE about 6 months ago but now like Gnome but what so great about the new one?

---

### Post by sumguy231 on 2008-01-30
In my experience, nothing with KDE 4.0. There were a few new features like plasma widgets, compositing, and a new menu, but from what I saw they were all incomplete or broken on my system. KDE 4.1 should fix them and restore some of the features that KDE 3.5 has that 4.0 doesn't. But for end users, KDE 4.0 is complete garbage*

*Insert KDE fanboy reminding me that KDE 4.0 is about the applications, not the desktop. Okay, first of all I would say that the desktop is probably the most important part of a **desktop** environment. Second of all, the applications I used weren't in much better of a state themselves.

---

### Post by wieman01 on 2008-01-30
It just looks great, that's all. I like the color theme, the new gadgets and the menu. Plus performance is allegedly much better (30% gain over KDE3 as I have heard)... That's all.

---

### Post by samwyse on 2008-01-30
Framework stuff that currently don't mean much to the end user.

---

### Post by BDNiner on 2008-01-30
It seems like a beta release to me. There is a lot of functionality missing.

---

### Post by timboellis on 2008-01-30
Well I downloaded Shift linux but turns out to be Kubuntu with KDE 4 Wrong mirror or somthing but anyhow I booted up the live cd looks good, so trying to install KDE4 on Ubuntu just now just to see, or crash my machine one or the two

---

### Post by SunnyRabbiera on 2008-01-30
right now there is nothing real special about KDE4, its still early so nothing much is open for it.
I am staying with KDE3 until KDE 4.1, thats where the fun will begin I will imagine

---

### Post by Quillz on 2008-01-30
What is special about KDE 4 at the moment is that it's been finally released. However, it's far from usable. Of course this will improve, with 4.0.1 soon and 4.1 later on, but until then, just stick with KDE 3 or another window manager.

---

### Post by SunnyRabbiera on 2008-01-31
I am hoping that 4.0.1 will come soon though to get some more of the rough spots out.
We may see some decent progress by 4.0.5, thats when I may give KDE 4 its second shot as by then most of the features would be worked out.
This all hinges on the development team though.

---

### Post by bufsabre666 on 2008-01-31
honestly i like the new look and think it is mildly faster but i thought the betas and the rc's were more stable than the final

---

### Post by Xbehave on 2008-01-31
> There were a few new features like plasma widgets, compositing,
these are pretty huge features,
plasma alows programs to be build to integrate better intll o the DE (i think not 100% on this)
puts KDE on the level of compiz (well not quite but
 quite close)
also phonon is very important for programs to be closer integrated
> **wieman01 said:**
> Plus performance is allegedly much better (30% gain over KDE3 as I have heard)... That's all.
sorry that was a dud its turned out that they were pretty much wrong there is infact slightly more ram usage

---

### Post by wieman01 on 2008-02-01
> **Xbehave said:**
> sorry that was a dud its turned out that they were pretty much wrong there is infact slightly more ram usage
Too bad... good to know.

---

### Post by maniacmusician on 2008-02-02
> **Xbehave said:**
> these are pretty huge features,
plasma alows programs to be build to integrate better intll o the DE (i think not 100% on this)
puts KDE on the level of compiz (well not quite but
 quite close)
also phonon is very important for programs to be closer integrated

sorry that was a dud its turned out that they were pretty much wrong there is infact slightly more ram usage
do you have a source for that last statement? I haven't read anything conclusive like that, and I've been keeping an eye on the Planet and the Dot.

---

### Post by GeneralZod on 2008-02-02
> **maniacmusician said:**
> do you have a source for that last statement? I haven't read anything conclusive like that, and I've been keeping an eye on the Planet and the Dot.

The original claim of "39% less memory" is debunked here:

[http://www.kdedevelopers.org/node/3138](http://www.kdedevelopers.org/node/3138)

The guy who made the claim retracts it here, and shows that it uses quite significantly more (with compositing on):

[http://www.jarzebski.pl/read/kde-3-5-vs-4-0-round-two.so](http://www.jarzebski.pl/read/kde-3-5-vs-4-0-round-two.so)

Most of it comes from pixmap usage due to the fact that Qt4 double-buffers all widgets by default, which is ginormously wasteful and redundant if a compositing window manager is used.  Hopefully they'll optimise this aspect at some point - the "Alien" flicker-reducing stuff coming with Qt4.4 may or may not make double-buffering superfluous and I believe the double-buffering won't  be used for an app if a certain environment variable is set when it is launched.  Still, even now it seems to run decently on old-ish hardware:

[http://www.kdedevelopers.org/node/3137](http://www.kdedevelopers.org/node/3137)

---

### Post by maniacmusician on 2008-02-02
> **GeneralZod said:**
> The original claim of "39% less memory" is debunked here:

[http://www.kdedevelopers.org/node/3138](http://www.kdedevelopers.org/node/3138)

The guy who made the claim retracts it here, and shows that it uses quite significantly more (with compositing on):

[http://www.jarzebski.pl/read/kde-3-5-vs-4-0-round-two.so](http://www.jarzebski.pl/read/kde-3-5-vs-4-0-round-two.so)

Most of it comes from pixmap usage due to the fact that Qt4 double-buffers all widgets by default, which is ginormously wasteful and redundant if a compositing window manager is used.  Hopefully they'll optimise this aspect at some point - the "Alien" flicker-reducing stuff coming with Qt4.4 may or may not make double-buffering superfluous and I believe the double-buffering won't  be used for an app if a certain environment variable is set when it is launched.  Still, even now it seems to run decently on old-ish hardware:

[http://www.kdedevelopers.org/node/3137](http://www.kdedevelopers.org/node/3137)
cool, thanks. While you're here, I wanted to ask you; do you know what's happening to Kaffeine for KDE4? I couldn't find any details on its active development. Seeing as how it's one of the most versatile players I've ever used, I would hate for it to fade away and be replaced by Dragon Player.

---

### Post by GeneralZod on 2008-02-02
> **maniacmusician said:**
> cool, thanks. While you're here, I wanted to ask you; do you know what's happening to Kaffeine for KDE4? I couldn't find any details on its active development. Seeing as how it's one of the most versatile players I've ever used, I would hate for it to fade away and be replaced by Dragon Player.

No idea, I'm afraid :) If it's popular enough - as it seems to be - I imagine someone will start to port it once KDE4 starts to become more popular.

---

### Post by bruce89 on 2008-02-02
They ought not to have released 4.0 until it was useful. For instance what's called 4.0 now should have been 3.9, otherwise people may think KDE 4.x is useless.

---

### Post by Xbehave on 2008-02-02
4.0 is pretty standard .0 software, not good for users but a stable framework for developers
3.9 would have caused far too much confusiong 
4.-1 would have looked silly

thx GeneralZod as i didnt have a source just heard it somehere

---

### Post by tikal26 on 2008-02-02
WEll KDE 4.0.0 is useful you have a panel amenu and a desktop shell so its 'useful' it doe snot have a bunch of fancy feature, but I tihnk they needed to make a release to 'force' aplication developers to port and work on KDe 4 apps. Most of the improvements are going to be lelt once apps come out like koffice. (Krita is going to be awesome), Amarok, etc,etc. KDE 4.1 will have the imroved plasma that everyone had heard of and will have most apps finished.

---

### Post by sunexplodes on 2008-02-04
> **Xbehave said:**
> 4.0 is pretty standard .0 software, not good for users but a stable framework for developers


Can you give me an example of another large-scale or widely used piece of software where the .0 release has been as unusable and as incomplete as KDE 4? 

I'm not trying to start a flamewar, but I've yet to hear a convincing argument for why 4.0 is anything other than a rushed Alpha.

---

### Post by GeneralZod on 2008-02-04
> **sunexplodes said:**
> Can you give me an example of another large-scale or widely used piece of software where the .0 release has been as unusable and as incomplete as KDE 4? 

I'm not trying to start a flamewar, but I've yet to hear a convincing argument for why 4.0 is anything other than a rushed Alpha.

Someone pointed this out the other day.  It's amazing how often you can s/GNOME 2.0.0/KDE 4.0.0/ in the article and still have it ring true:

[http://osnews.com/story/1280/A_Users_First_Look_at_GNOME_2.0](http://osnews.com/story/1280/A_Users_First_Look_at_GNOME_2.0)

Linux 2.6.0 is another commonly-cited example.  The larger and more complex the code base and the bigger the departure from the old, well-tested code-base, the rougher the .0.0 release will be.  Very few pieces of software are as large or as tightly coupled to their own APIs as desktop environments and their application suites, so the examples of .0.0 releases being as rushed as KDE4.0.0 are naturally limited.

---


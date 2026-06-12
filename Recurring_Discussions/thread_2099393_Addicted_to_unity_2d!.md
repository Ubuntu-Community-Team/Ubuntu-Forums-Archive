---
title: "Addicted to unity 2d!"
date: 2012-12-29
forum: Recurring Discussions
---

### Post by swoll1980 on 2012-12-29
I hated Unity do to its instability, and sluggishness. I heard that if you enable the 2d version it is 100 times more stable, and responsive. So I give it a try, and it's running smooth as silk. It is old school Ubuntu speed mixed with the efficiency of the new interface. "How cool is that?" I thought to myself. 

I was thinking of upgrading to 12.10, then I found out there wasn't any 2d option for Unity. The first thing I ask myself is "Why?!"

Now I'm no genius or anything, but why drop the fast stable version, instead of the slow buggy version? Is it so that we might watch the cool effect of a window shrinking into it's icon when we minimize it?

What are the benefits, if any, of running 3d desktops, over 2d, which would make it worth the performance drop off?
am I missing somthing here?

---

### Post by kaldor on 2012-12-29
> **swoll1980 said:**
> I hated Unity do to its instability, and sluggishness. I heard that if you enable the 2d version it is 100 times more stable, and responsive. So I give it a try, and it's running smooth as silk. It is old school Ubuntu speed mixed with the efficiency of the new interface. "How cool is that?" I thought to myself. 

I was thinking of upgrading to 12.10, then I found out there wasn't any 2d option for Unity. The first thing I ask myself is "Why?!"

Now I'm no genius or anything, but why drop the fast stable version, instead of the slow buggy version? Is it so that we might watch the cool effect of a window shrinking into it's icon when we minimize it?

What are the benefits, if any, of running 3d desktops, over 2d, which would make it worth the performance drop off?
am I missing somthing here?

The issue isn't a matter of "eye candy vs stable/fast". The issue is that Unity 2d and Unity are both different projects with different codebases. This is why there's a feature difference between the two.

There was too much repetitive work being done. Unity 2d was dropped in favour of putting the effort into Unity (3d), and getting Unity 3d to work on older/slower hardware. This avoids the issues related to having to reimplement features, incompatibilities, etc.

Unity is a Compiz plugin. Unity 2d is a non-compositing GNOME desktop shell written in Qt. While I agree that Unity 2d is much more efficient on some machines, I agree with the decision to drop it. It's present in the current LTS, at least!

---

### Post by KiwiNZ on 2012-12-29
Use 12.04 until 3d is sorted. I am not using or recommending 12.10.

---

### Post by swoll1980 on 2012-12-29
> **KiwiNZ said:**
> Use 12.04 until 3d is sorted. I am not using or recommending 12.10.

Yeah that's what I'm going to do. Hopefully they'll figure out a way to make everyone happy. I just can't see the 3d version ever being as fast for some reason.

Is it me, or does creating a desktop environment out of a compiz plugin seem pretty ambitious?

---

### Post by KiwiNZ on 2012-12-29
> **swoll1980 said:**
> Yeah that's what I'm going to do. Hopefully they'll figure out a way to make everyone happy. I just can't see the 3d version ever being as fast for some reason.

Is it me, or does creating a desktop environment out of a compiz plugin seem pretty ambitious?

My opinion only, the two main issues with 12.10 is releasing in Beta quality and very poor driver support and implementation, both of which are unacceptable in a modern OS.

It is my belief that delaying a release is less damaging than releasing on time but broken. The religious adherence to the six monthly release cycle needs to be reviewed.

---

### Post by swoll1980 on 2012-12-29
> **KiwiNZ said:**
> My opinion only, the two main issues with 12.10 is releasing in Beta quality and very poor driver support and implementation, both of which are unacceptable in a modern OS.

It is my belief that delaying a release is less damaging than releasing on time but broken. The religious adherence to the six monthly release cycle needs to be reviewed.

Yeah I agree. Ironically, the first Linux distro  I ever used was Ubuntu 7.04, it was delayed a couple of months. It seemed to work out fine that time.

---

### Post by Old_Grey_Wolf on 2012-12-29
> **swoll1980 said:**
> Yeah I agree. Ironically, the first Linux distro  I ever used was Ubuntu 7.04, it was delayed a couple of months. It seemed to work out fine that time.

It think you are referring to 6.06 LTS that was delayed.

---

### Post by swoll1980 on 2012-12-29
> **Old_Grey_Wolf said:**
> It think you are referring to 6.06 LTS that was delayed.

Yeah it was 6.06. I had it on there then edited to 7.04. Should have trusted my gut on that one. The name implies it's late arrival. :p

---

### Post by monkeybrain2012 on 2012-12-29
Don't know about your hardware, but on my laptop Unity 3d (12.04)is actually a lot faster and smoother than Unity 2d, everything just flows while Unity 2d is kind of sluggish. I can see that if you have very old hardware it may be the opposite(my laptop is almost 4 years old and it is a mid range laptop I bought on discount so not the greatest and newest either)


BTW, I see no compelling reason to upgrade to 12.10. Why the rush?

---

### Post by swoll1980 on 2012-12-29
My hardware isn't really old, it's budget. I think people including Canonical forget that it's not just old hardware that has lower specs. My laptop has better specs than say a tablet computer. If Canonical is planning on targeting that market they better figure something out.

---

### Post by swoll1980 on 2012-12-29
> **monkeybrain2012 said:**
> 


BTW, I see no compelling reason to upgrade to 12.10. Why the rush?

No rush. I tried it before, and it was horrible. I found out about the 2d option, how good it worked, and figured I would try it again in 2d, but found out that It was removed from the new version. It's just annoying because I found my perfect DE only to find out an hour later that it's being abandoned.

---

### Post by KiwiNZ on 2012-12-29
> **monkeybrain2012 said:**
> Don't know about your hardware, but on my laptop Unity 3d (12.04)is actually a lot faster and smoother than Unity 2d, everything just flows while Unity 2d is kind of sluggish. I can see that if you have very old hardware it may be the opposite(my laptop is almost 4 years old and it is a mid range laptop I bought on discount so not the greatest and newest either)


BTW, I see no compelling reason to upgrade to 12.10. Why the rush?

I have high spec hardware, eg latest i7, 16gb Ram etc and 12.10 3d runs, correction crawls very poorly.

---

### Post by jerome1232 on 2012-12-29
> **KiwiNZ said:**
> I have high spec hardware, eg latest i7, 16gb Ram etc and 12.10 3d runs, correction crawls very poorly.

There's gotta be something funny going on there, I'm on a 4 Gb ram, Intel Core 2 Quad cpu, Nvidia GTS 450 and it runs 12.04.1 fine. I briefly ran 12.10 and it was faster if anything.

Out of curiosity what video card and driver are you using?


[SIZE="2"]Perhaps you have the expectation that if you press a button the context menu should have appeared before your mouse arrived on the button? (I'm joking)[/SIZE]

---

### Post by monkeybrain2012 on 2012-12-29
12.10 is a bit slower than 12.04 on my laptop, but still quite fast. I have used Unity 3d with 12.04 on several machines and they are all very fast. The only thing that is visibly slower is actually kubuntu with kde.

---

### Post by swoll1980 on 2012-12-29
> **monkeybrain2012 said:**
> 12.10 is a bit slower than 12.04 on my laptop, but still quite fast. I have used Unity 3d with 12.04 on several machines and they are all very fast. The only thing that is visibly slower is actually kubuntu with kde.

My video card isn't supported anymore, which would explain bad 3d performance on my machine. That will bring me to my next point though. Why do these distros feel the need to upgrade the xserver package every 6 months. Did anyone on here get any new functionality out of all these xserver updates? I didn't. Seems like all the stuff that didn't work in last version, still doesn't, and some of the stuff that did work doesn't anymore. Seems kind of backwards.

---

### Post by rrich1974 on 2012-12-30
pretty strange, i use unity 3D on a almost 5 years old computer. 
amd turion 1.9 ghz and ati mobility radeon x1270. i am using gallium video.

if i remember, i have red somewhere that the unity 3D has something to do with improving the gaming experience in ubuntu.

---

### Post by 3rdalbum on 2012-12-30
The workspace selector on Unity 2D was a bit slow and clunky, but smooth as silk on Unity 3D.

Unity 3D also had a few more features than 2D. Quite often we'd give instructions to people about how to (for instance) arrange their icons in Unity, and the person would say "It doesn't work" and we'd realize they were using Unity 2D.

Unity 3D drops back to "no transparency" mode when there's no OpenGL support on the computer, but if your graphics driver has 3D support - however poor - you'll get the full fat transparency and animations. Try running that on an ATi Radeon Xpress 200, that is unsupported by official AMD drivers. Unity 3D needs to better judge when to turn off transparency for the sake of performance.

---

### Post by OluszDes on 2012-12-30
> **kaldor said:**
> The issue isn't a matter of "eye candy vs stable/fast". The issue is that Unity 2d and Unity are both different projects with different codebases. This is why there's a feature difference between the two.

Are you really sure that there were two different code bases?

> There was too much repetitive work being done. Unity 2d was dropped in favour of putting the effort into Unity (3d), and getting Unity 3d to work on older/slower hardware. This avoids the issues related to having to reimplement features, incompatibilities, etc.

There is something else the matter, I believe. Compiz is buggy as their own devs say, but it worked in the older hardware for few years. I don't know whether you'd consider P3 as old hardware, but Compiz is happily working there. 

> Unity is a Compiz plugin. Unity 2d is a non-compositing GNOME desktop shell written in Qt. While I agree that Unity 2d is much more efficient on some machines, I agree with the decision to drop it. It's present in the current LTS, at least!

Unity 2D is **not** a non-compositing Gnome desktop shell. If anything is written in Qt, then it can handle compositing. Quite interesting to hear your words that Unity (3D) is a Compiz plugin. Can you tell us more about that?

---

### Post by Frogs Hair on 2012-12-30
Unity 2D is in the 12.10 repository although I have had no reason to install it. I did use 2D on 12.04 and enjoyed it though I didn't notice a performance difference.

12.10 is the best release on my hardware since 10.10 I can only hope 13.04 works as well.With everything Ubuntu/Linux I wait and see.

---

### Post by vanadium on 2012-12-30
> **OluszDes said:**
> Are you really sure that there were two different code bases?
Quite interesting to hear your words that Unity (3D) is a Compiz plugin. Can you tell us more about that?
I would second the explanation of kaldor. It is a good, brief explanation about the fundamental differences between Unity and unity-2D, and why unity-2D was discontinued.

---

### Post by OluszDes on 2012-12-30
> **Frogs Hair said:**
> Unity 2D is in the 12.10 repository although I have had no reason to install it. I did use 2D on 12.04 and enjoyed it though I didn't notice a performance difference.

12.10 is the best release on my hardware since 10.10 I can only hope 13.04 works as well.With everything Ubuntu/Linux I wait and see.

There is no Unity 2D in 12.10 repos, but dummy packeges, that is useless packages.

---

### Post by OluszDes on 2012-12-30
> **vanadium said:**
> I would second the explanation of kaldor. It is a good, brief explanation about the fundamental differences between Unity and unity-2D, and why unity-2D was discontinued.

I am sorry, but I'd have to tell you that the fundamental difference of Unity 3D and Unity 2D is not that as kaldor had explained. There is more to it than the eye can see. In my country, people say that it darker under the lamppost.  Unity 2D works very well in a 3D environment and *not* dependent on Compiz. It works with KDE too, in which Kwin is the composite manager and with all the eye candy.

Check and see for yourself. I am not going to get into an argument with anyone, please. The new year's coming, so let's be happy!:)

---

### Post by vanadium on 2012-12-30
Please reread Kaldor's post. It is a good summary of the essential differences. Nothing you say is contradicting his post.

Of course, you can run unity-2D in a 3D environment. You can run it on metacity, but also on compiz.

In contrast, Unity-3D is implemented as a compiz plugin, and thus can only run on compiz.

Reread Kaldor's post carefully.

---

### Post by kurt18947 on 2012-12-30
> **KiwiNZ said:**
> My opinion only, the two main issues with 12.10 is releasing in Beta quality and very poor driver support and implementation, both of which are unacceptable in a modern OS.

It is my belief that delaying a release is less damaging than releasing on time but broken. The religious adherence to the six monthly release cycle needs to be reviewed.

No worries, just treat it as a beta :p i.e. don't use it for important stuff.  I have 12.04 and 12.10 gnome remix installed.  The 12.10 was a horror when I first installed it, largely due to Nvidia issues I believe.  It's pretty stable now especially with Nouveau video.  I keep at least two installs.  One for 'real work', another for ditzing around the web/visiting crapware infested sites/ etc. etc.

---

### Post by OluszDes on 2012-12-30
> **vanadium said:**
> Please reread Kaldor's post. It is a good summary of the essential differences. Nothing you say is contradicting his post.

Of course, you can run unity-2D in a 3D environment. You can run it on metacity, but also on compiz.

In contrast, Unity-3D is implemented as a compiz plugin, and thus can only run on compiz.

Reread Kaldor's post carefully.

I read Kaldor's post again and installed Unity again.

 					> Originally Posted by **kaldor** 					[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12427732#post12427732") 				
 				*The issue isn't a matter of "eye  candy vs stable/fast". The issue is that Unity 2d and Unity are both  different projects with different codebases. This is why there's a  feature difference between the two.*

And, I found that I was right. This is *not *a case of two different code bases. I looked in to all those files connected to Compiz and disabled some that I decided not needed for Unity(3D) to work and ran Unity 3D. What did I get? Unity 2D desktop! 

Unity 3D could not appear as I had disabled few files, but it pulled in Unity 2D desktop in full. Unity 2D *shouldn't* appear too as I had disabled some files also in Unity 2D. So, they can't be from 2 different code bases. There aren't any feature differences at all.

In a way, *I thank you* for contradicting me, which led to a careful scrutiny.:popcorn: Anyway, I copied few files to my Documents and uninstalled Unity (3D). 


[I]

[/I]

---

### Post by vanadium on 2012-12-30
There may be common elements in use by the two systems. Here is some reading that may confirm or not confirm your view on the matter:
[http://en.wikipedia.org/wiki/Unity_%28user_interface%29](http://en.wikipedia.org/wiki/Unity_%28user_interface%29), scroll down to "Unity vs. Unity 2D"

---

### Post by OluszDes on 2012-12-30
> **vanadium said:**
> There may be common elements in use by the two systems. Here is some reading that may confirm or not confirm your view on the matter:
[http://en.wikipedia.org/wiki/Unity_%28user_interface%29](http://en.wikipedia.org/wiki/Unity_%28user_interface%29), scroll down to "Unity vs. Unity 2D"

I *know* about the alleged difference of Unity 2D and 3D. Everyone was trying to tell us that Unity 2D was made for haedware that won't work with 3D acceleration*, but *it works with that hardware, so, whether it was named 2D or not it is a very good UI for any new computer, or in other words, this 3D is not that needed, to have the launcher, dash and the global panel in the 3D environment. I believe, the gnome-wm would live for some time and that is a 3D environment. I am not talking about Metacity at all.

Please read my post carefully; I wrote that *neither *Unity 3D *nor* 2D was supposed to appear as I had disabled certain files in both 2D and 3D, but when I ran Unity (3D), out jumped this so-called Unity 2D. When, I uninstalled Unity (3D) all came backto normal and Unity 2D vanished leaving something useful for me to work on.

This 2D is a misnomer. It is not 2 dimensional, neither Unity is 3 dimensional. As the OP wrote in his heading "Addicted to 2D!", I agree with him. That was all that's needed. 

The Compiz devs ask us to note something. It is in  [http://wiki.compiz.org/Distributions](http://wiki.compiz.org/Distributions)
If something is a plugin to an unstable something, how can I trust the plugin to work flawlessly? If the plugin, which is important to us users, and without which we can't work with Ubuntu, is so dependent on the unstable base, aren't we in trouble?

So, should we or shouldn't we be addicted to 2D?

---

### Post by MG&amp;TL on 2012-12-30
> Everyone was trying to tell us that Unity 2D was made for haedware that won't work with 3D acceleration*, but *it works with that hardware, so, whether it was named 2D or not it is a very good UI for any new computer, or in other words, this 3D is not that needed, to have the launcher, dash and the global panel in the 3D environment.

The idea being that 3D acceleration provides for effects that enhance the experience. Whether that is a good thing or not is a matter for you to decide.

> I believe, the gnome-wm would live for some time and that is a 3D environment. I am not talking about Metacity at all.

...what? If you mean gnome-shell (which uses libmutter as a window-manager backend AFAIK), then yes, it is a 3D environment.

> Please read my post carefully; I wrote that *neither *Unity 3D *nor* 2D was supposed to appear as I had disabled certain files in both 2D and 3D,

How is 'disabling' (here I read "removed"-disabling files?) a logical way to test for anything other than whether or not a desktop environment can survive having its files removed?

> but when I ran Unity (3D), out jumped this so-called Unity 2D. When, I uninstalled Unity (3D) all came backto normal and Unity 2D vanished leaving something useful for me to work on.

If I recall, if Unity failed, it was engineered (for end-user purposes) to start unity2D as a fallback.

> This 2D is a misnomer. It is not 2 dimensional, neither Unity is 3 dimensional. As the OP wrote in his heading "Addicted to 2D!", I agree with him. That was all that's needed. 

So, if unity2d is not 2-dimensonal, what is it? AFAIK Qt uses 2D hardware acceleration or software rendering to perform whatever it's doing at the time. If you can provide code examples showing it is using 3D acceleration (OpenGL?), I'll be happy to be proved wrong.

> The Compiz devs ask us to note something. It is in  [http://wiki.compiz.org/Distributions](http://wiki.compiz.org/Distributions)
If something is a plugin to an unstable something, how can I trust the plugin to work flawlessly?

We can't. We just have to trust that Canonical knows what it's doing. And, so far, it does. I've never had a horrible crash while using Unity, and they perform extensive testing to ensure that the version of Compiz they ship is stable enough.

> If the plugin, which is important to us users, and without which we can't work with Ubuntu, is so dependent on the unstable base, aren't we in trouble?

We have been since 11.04. 2 years later, I haven't seen any evidence that we're in trouble.

> So, should we or shouldn't we be addicted to 2D?

Being addicted to something is generally bad. It's either expensive, bad for you, or just gets removed on the next release cycle. :P

Sorry if you think this is overly negative, I'm just intrigued as to what you are saying.

---

### Post by Frogs Hair on 2012-12-30
> **OluszDes said:**
> There is no Unity 2D in 12.10 repos, but dummy packeges, that is useless packages.

You are correct , I saw the packages in synaptic but did not check the description. ;)

---

### Post by OluszDes on 2012-12-30
> **MG&TL said:**
> The idea being that 3D acceleration provides for effects that enhance the experience. Whether that is a good thing or not is a matter for you to decide. 
...what? If you mean gnome-shell (which uses libmutter as a window-manager backend AFAIK), then yes, it is a 3D environment.

I didn't mean gnome-shell or libmutter. Unity is the launcher, the global menu and the dash, the rest is Compiz. It is Compiz that gives the 3D effect. We have been using Compiz for so long, we have sort of forgotten that it is the only thing that gives 3D effects/environment in Gnome, Xfce and Lxde. As a plugin, Unity uses Compiz. It could use Metacity and Gnome-wm, as both happily work in 3D. Take a old distro, say Lucid and add Compiz to it, you get your 3D. Take the same Lucid and add Unity and you get your Unity 2D or 3D. The thing is Unity 3D is made to work only with Compiz and cannot also live without Gnome 3, but the so-called Unity 2D can live without both of them and work with pure KDE, LXDE or XFCE.* A problem? *

> How is 'disabling' (here I read "removed"-disabling files?) a logical way to test for anything other than whether or not a desktop environment can survive having its files removed?Disabling means disabling, nothing else. The file is there, but is not allowed to work.  

> If I recall, if Unity failed, it was engineered (for end-user purposes) to start unity2D as a fallback.Well, yes and no.

> So, if unity2d is not 2-dimensonal, what is it? AFAIK Qt uses 2D hardware acceleration or software rendering to perform whatever it's doing at the time. If you can provide code examples showing it is using 3D acceleration (OpenGL?), I'll be happy to be proved wrong.No, not at this stage. I can, but I won't at this stage. I have no Unity 3D in my laptop, but Unity 2D is there, at least the parts I need. My window manager is gnome-wm and Compiz doing all kinds of effects.  I have the Compiz cylinder moving away from the screen, when I change workplaces. In Quantal and Raring with their "3D accelerations" that doesn't work.

> We can't. We just have to trust that Canonical knows what it's doing. And, so far, it does. I've never had a horrible crash while using Unity, and they perform extensive testing to ensure that the version of Compiz they ship is stable enough.If Compiz crashes everything would crash. Unity is a plugin of Compiz, but when you install CCSM and try to make effects work, what happens? Unity goes haywire. You have to manually restart your computer, after enabling some of them. Nothing responds.

Now tell me, why this Unity 3D, which is based on Compiz, crashes when you enable few of Compiz's own effects?  Why you have to restart all the time, if you enable/disable some of those effects? Why it doesn't crash, when you are using the so-called Unity 2D?

> We have been since 11.04. 2 years later, I haven't seen any evidence that we're in trouble.The answer to this is written above.

> Being addicted to something is generally bad. It's either expensive, bad for you, or just gets removed on the next release cycle. :PHow true! Are you addicted to Unity 3D? The OP meant that he liked it and found it better than the so-called Unity 3D, not exactly addicted. Personally, I don't want Unity 3D, but I like parts of Unity 2D and I use them. Its an application, which is useful to me for everyday work, so I use it. No addiction whatsoever.:)

> Sorry if you think this is overly negative, I'm just intrigued as to what you are saying.Absolutely not! This is Recurring Discussions, so no one should feel bad, if the other has a different idea. Its good to discuss, not argue, but discuss and that way we become knowledgeable.

---

### Post by cariboo on 2012-12-31
@[s]Chdslv[/s] OluszDes You may find [this]("http://askubuntu.com/questions/21697/why-was-qt-chosen-for-unity-2d-and-nux-for-3d") will help you understand the difference between Unity 3D and Unity 2D.

---

### Post by zombifier25 on 2012-12-31
> **OluszDes said:**
> Now tell me, why this Unity 3D, which is based on Compiz, crashes when you enable few of Compiz's own effects?  Why you have to restart all the time, if you enable/disable some of those effects? Why it doesn't crash, when you are using the so-called Unity 2D?

You said that it only crashes when you enable effects on it (and for me, it doesn't realy crash, it simply flickers a little bit), which AFAIK has been this way since Compiz's introduction (I use Compiz since 10.04, which some says as the MOST STABLE Compiz ever, and it flickers when enabling effects). Compiz is very stable for me when I do other stuffs.

When you start ccsm for the first time, do you see that little error advising you to use it with care? Why do you think they put it there in the first place? During Precise's beta test, someone even lobbied to have the abomination known as ccsm be **removed from the repo completely**, but others decided against it and put a warning in ccsm instead.

---

### Post by OluszDes on 2012-12-31
> **zombifier25 said:**
> You said that it only crashes when you  enable effects on it (and for me, it doesn't realy crash, it simply  flickers a little bit), which AFAIK has been this way since Compiz's  introduction (I use Compiz since 10.04, which some says as the MOST  STABLE Compiz ever, and it flickers when enabling effects). Compiz is  very stable for me when I do other stuffs.

Flickering is  something else, but crashing means, you just cannot get the desktop  working and you have to reboot it with the power off button. If you have  used Knoppix, you'd know that Compiz doesn't "flicker" in it. If you  check the OZ Unity Remixes of Ubuntu, Onyx64, BlackOpal64 and 32, you'd *never* find Compiz flickering.

> When you start ccsm for the first time, do you see that little  error advising you to use it with care? Why do you think they put it  there in the first place? During Precise's beta test, someone even  lobbied to have the abomination known as ccsm be **removed from the repo completely**, but others decided against it and put a warning in ccsm instead.

When you say that's "a little error." Its a warning!  Compiz is too powerful, it can eat into your distro. Compiz is *that* powerful, Ubuntu decided to use it as the base of their Unity 3D, *even *though  the Compiz devs say it is buggy. How did you use Compiz in your 10.04,  if CCSM is "an abomination?" How come it works in Debian in full blast?  How come it works in Lxde Knoppix? Install a Debian distro with CCSM  already installed in it and see, whether that "little error" appears  there.Or even a Arch, Gentoo based distro.

Its time for New Year!

*Najlepsze*[COLOR=#222222][FONT=arial] &#380;yczenia z okazji nadchodz&#261;cego [/FONT][/COLOR]*Nowego Roku*[COLOR=#222222][FONT=arial], spe&#322;nienia marze&#324; oraz wspania&#322;ej sylwestrowej zabawy! [/FONT][/COLOR]Happy new Year and may your wishes com true! Have a nice time at the New Year Ball!

---

### Post by MG&amp;TL on 2012-12-31
> Unity is the launcher, the global menu and the dash, the rest is Compiz. It is Compiz that gives the 3D effect. We have been using Compiz for so long, we have sort of forgotten that it is the only thing that gives 3D effects/environment in Gnome, Xfce and Lxde. 

Compiz itself just provides a helpful API for 3D effects. Compiz plugins on the other hand...

> As a plugin, Unity uses Compiz. It could use Metacity and Gnome-wm, as both happily work in 3D.

It could (I'm referring to metacity here-not sure on gnome-wm), but as metacity uses no hardware acceleration to my knowledge, Unity would be horribly slow. See the LLVM fallback mode introduced with 12.10...

> The thing is Unity 3D is made to work only with Compiz and cannot also live without Gnome 3, but the so-called Unity 2D can live without both of them and work with pure KDE, LXDE or XFCE.* A problem? *


Not a problem, no, a good thing, but it doesn't necessarily mean that the 3D version is worse.

> Disabling means disabling, nothing else. The file is there, but is not allowed to work.  

Ehh...you removed the "read" file permission? You can't "disable" a file AFAIK.

> No, not at this stage. I can, but I won't at this stage.

I'll look forward to it then. :)

> My window manager is gnome-wm and Compiz doing all kinds of effects.

You have two window managers running? :shock:

> If Compiz crashes everything would crash. Unity is a plugin of Compiz, but when you install CCSM and try to make effects work, what happens? Unity goes haywire. You have to manually restart your computer, after enabling some of them. Nothing responds.

Have you used Unity recently? Never had any of these problems since 11.10.

> Now tell me, why this Unity 3D, which is based on Compiz, crashes when you enable few of Compiz's own effects?  Why you have to restart all the time, if you enable/disable some of those effects? Why it doesn't crash, when you are using the so-called Unity 2D?

It doesn't. But if it did, that would be because Compiz is a less stable platform than Qt, by its own admission.

> How true! Are you addicted to Unity 3D? 

Nope! I'm on DWM currently. Now THAT is addictive window management.[http://dwm.suckless.org/]("http://dwm.suckless.org/")

> The OP meant that he liked it and found it better than the so-called Unity 3D, not exactly addicted. Personally, I don't want Unity 3D, but I like parts of Unity 2D and I use them. Its an application, which is useful to me for everyday work, so I use it. No addiction whatsoever.:)

Great! Use whatever works for you. I don't particularly like/dislike any window manager or desktop, but I do like minimalism, and most desktops do this nicely.

---

### Post by OluszDes on 2012-12-31
> **MG&TL said:**
> Compiz itself just provides a helpful API for 3D effects. Compiz plugins on the other hand... I haven't come across any other application that gives 3D effects in Lxde, Gnome, Xfce. I don't know, whether Kwin works with Lxde, Gnome, Xfce. 

I agree with you on your comment "Compiz plugins on the other hand..."

> It could (I'm referring to metacity here-not sure on gnome-wm), but as metacity uses no hardware acceleration to my knowledge, Unity would be horribly slow. See the LLVM fallback mode introduced with 12.10...

I am referring to gnome-wm, not metacity. I read that metacity doesn't need hardware acceleration. [http://readm3.org/os/ubuntu/extended-compiz-config](http://readm3.org/os/ubuntu/extended-compiz-config) Everything works very well with gnome-wm.. 

> Not a problem, no, a good thing, but it doesn't necessarily mean that the 3D version is worse.
You are correct. It doesn't necessarily mean that the 3D version is worse. It also doesn't mean that the so-called 2D version is bad and malfunction in 3D environment.

> Ehh...you removed the "read" file permission? You can't "disable" a file AFAIK. No, I didn't do that. I disabled them. The file is there, but is disabled. 

> You have two window managers running? :shock:
I don't know, whether two window managers could work simultaneously. Only gnome-wm is working.

> Have you used Unity recently? Never had any of these problems since 11.10. Oh, yes. I have used it in Quantal and Raring too. Actually, I have a quantal and raring in 2 partitions with Unity on board. 

> It doesn't. But if it did, that would be because Compiz is a less stable platform than Qt, by its own admission. You are right!

> Nope! I'm on DWM currently. Now THAT is addictive window management.[http://dwm.suckless.org/](http://dwm.suckless.org/) I was looking at it just yesterday. You are experienced in it, could you make a write up about i1?

> Great! Use whatever works for you. I don't particularly like/dislike any window manager or desktop, but I do like minimalism, and most desktops do this nicely.
I too! Lately, I had become a tinkerer.  

Nice speaking to you! Wish you are very happy new year!

---

### Post by Paqman on 2013-01-01
> **KiwiNZ said:**
> Use 12.04 until 3d is sorted. I am not using or recommending 12.10.

I've found 3D on 12.10 to be a huge improvement over 3D on 12.04 or earlier. The Dash was laughably slow on 12.04, to the point where I was using Synapse instead. So at the very least I'd say it's highly dependent on your hardware, and worth giving both 12.04 and 12.10 a go to see which performs best on any particular machine.

Not thrilled about 2D being dropped myself. Although I can see it's a pragmatic decision it does mean that 12.04 is now the end of the line for Ubuntu on my netbook, which is a shame as that machine probably has another 2-3 years of useful life in it at least.

---

### Post by zombifier25 on 2013-01-01
> **OluszDes said:**
> Flickering is  something else, but crashing means, you just cannot get the desktop  working and you have to reboot it with the power off button. If you have  used Knoppix, you'd know that Compiz doesn't "flicker" in it. If you  check the OZ Unity Remixes of Ubuntu, Onyx64, BlackOpal64 and 32, you'd *never* find Compiz flickering.



When you say that's "a little error." Its a warning!  Compiz is too powerful, it can eat into your distro. Compiz is *that* powerful, Ubuntu decided to use it as the base of their Unity 3D, *even *though  the Compiz devs say it is buggy. How did you use Compiz in your 10.04,  if CCSM is "an abomination?" How come it works in Debian in full blast?  How come it works in Lxde Knoppix? Install a Debian distro with CCSM  already installed in it and see, whether that "little error" appears  there.Or even a Arch, Gentoo based distro.

Its time for New Year!

*Najlepsze*[COLOR=#222222][FONT=arial] &#380;yczenia z okazji nadchodz&#261;cego [/FONT][/COLOR]*Nowego Roku*[COLOR=#222222][FONT=arial], spe&#322;nienia marze&#324; oraz wspania&#322;ej sylwestrowej zabawy! [/FONT][/COLOR]Happy new Year and may your wishes com true! Have a nice time at the New Year Ball!

First off, I didn't mean "error", I meant "warning". Wonder how that slipped in there. And if you saw the end of my post, I said "warning".

And secondly, I was a little unclear in my post, so let me clear p a few stuffs.
Yes, I'll give you that 0.9 is less stable than 0.8, which is commonly used in non-Ubuntu distros, and Compiz in 11.10 is buggy as heck, but have you gave it an honest try, especially the Precise version, which is meant to be rock solid? When 11.10 came out, Compiz was barely usable, so bad that I wiped it out and installed 10.04. But now, the Compiz devs are working rigorously to improve its performance, and now it's stable for everyday use, and that's all I need (heck, I can even play Portal 2 on it :D )

They put that warning in there because it's a common thing for users to accidentally screw up their systems by tweaking Compiz settings (I forgot to mention that along with placing a warning there, they also disabled the ability to disable the Unity plugin in the Unity session), not just because of the fact that Compiz tends to crash because of enabling/disabling some plugins. I personally have seen too many posts about screwing up the desktop using ccsm in the 11.10 times.

I hope that's clearer.

---

### Post by MG&amp;TL on 2013-01-01
> I haven't come across any other application that gives 3D effects in Lxde, Gnome, Xfce. I don't know, whether Kwin works with Lxde, Gnome, Xfce. 
GNOME is an exception to all the below, as it's implemented as a monolithic WM/DE combination at the moment.

As for LXDE, Xfce, and KDE, any X11 compositor could work. Compiz, Kwin, Metacity to a degree, Mutter, and odd applications like skippy.

> I am referring to gnome-wm, not metacity. I read that metacity doesn't need hardware acceleration. [http://readm3.org/os/ubuntu/extended-compiz-config](http://readm3.org/os/ubuntu/extended-compiz-config) Everything works very well with gnome-wm.. 
Ahah! [http://manpages.ubuntu.com/manpages/natty/man1/gnome-wm.1.html](http://manpages.ubuntu.com/manpages/natty/man1/gnome-wm.1.html) - gnome-wm is a launcher for window managers. I assume Compiz is being used as your default.

> I don't know, whether two window managers could work simultaneously. Only gnome-wm is working.
I suppose technically they could, but it wouldn't work very well, even with my limited knowledge of X11. Most window managers check for already running WMs on startup, and either kill them or quit. Anyway, see my earlier comment about the gnome-wm program.

 > I was looking at it just yesterday. You are experienced in it, could you make a write up about i1?
Sure thing. Off-topic, but it's in Recurring anyway, so I'll make an exception and keep it short and sweet.

[B]To get started:

[/B]1. Install DWM (dwm? Dwm? DWM?). ```
sudo apt-get install dwm
```2. Read the manpage (and probably make notes). Otherwise, you will very likely be stuck when you launch it. ```
man dwm
```3. Logout, select the "dwm" session. Expect to get used to a new way of working. Not a lot of fun to start with, but very efficient once you get used to it. If you've ever used vi, the keybindings are sort-of similiar.

[B]To configure:

[/B]1. Get dwm's source. ```
bzr branch lp:ubuntu/dwm
```2. Edit the source files. You'll need to have a basic grasp of C to do this, or just stick closely to the format already there. You probably want to stick to the header file.

No, this isn't user-friendly. I'm pretty sure it's not intended to be. 

> Because dwm is customized through editing its source code, it&#8217;s  pointless to make binary packages of it. This keeps its userbase small  and elitist. No novices asking stupid questions. There are some  distributions that provide binary packages though.Note I don't agree with that, but it does keep source code small and efficient.

3. Rebuild. If you survived this far, you probably already know how to, but rebuild and reinstall the package:

```
make
``````
sudo make install
```> Nice speaking to you! Wish you are very happy new year!
Happy new year to you too!

---

### Post by OluszDes on 2013-01-01
Thank you very much for the dwm right up. I'd get into that sometime this week.:) 

> **MG&TL said:**
> GNOME is an exception to all the below, as it's implemented as a monolithic WM/DE combination at the moment.

As for LXDE, Xfce, and KDE, any X11 compositor could work. Compiz, Kwin, Metacity to a degree, Mutter, and odd applications like skippy.

Ahah! [http://manpages.ubuntu.com/manpages/natty/man1/gnome-wm.1.html](http://manpages.ubuntu.com/manpages/natty/man1/gnome-wm.1.html) - gnome-wm is a launcher for window managers. I assume Compiz is being used as your default.

I never tried Kwin in gnome, so I don't know, whether it'd work with gnome. Without Compiz, I don't think there would be any 3D effects in Gnome, Lxde or Xfce. I downloaded Knoppix 7.05 and that has all kind of Compiz effects. Knoppix uses Compiz 0.8.x. Klaus Knopper is quite a brainy person!

 > I suppose technically they could, but it wouldn't work very well, even with my limited knowledge of X11. Most window managers check for already running WMs on startup, and either kill them or quit. Anyway, see my earlier comment about the gnome-wm program.

Uninstalled Compiz completely to check that. No 3D effects, but everything else worked, so gnome-wm was doing its work by itself.  

Too sleepy after the Sylwester night. I suppose you too. Have a great 2013 year!:)

---

### Post by MG&amp;TL on 2013-01-01
> Thank you very much for the dwm right up. I'd get into that sometime this week.:) Cool. I think you'll like it. :)

> Without Compiz, I don't think there would be any 3D effects in Gnome, Lxde or Xfce. I downloaded Knoppix 7.05 and that has all kind of Compiz effects. Knoppix uses Compiz 0.8.x. Klaus Knopper is quite a brainy person!
 That he is, but try "kwin --replace" in Xfce or LXDE. Works pretty well if I recall.

> Uninstalled Compiz completely to check that. No 3D effects, but everything else worked, so gnome-wm was doing its work by itself.  gnome-wm would have then fallen back to (I presume) metacity. :)

> Too sleepy after the Sylwester night. I suppose you too. Have a great 2013 year! :)
Yup, you too!

---

### Post by Marzata on 2013-01-05
Came from Gnome 2 and got addicted to Xfce (Xubuntu). And love it!

---


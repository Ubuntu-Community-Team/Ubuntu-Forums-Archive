---
title: "Mac OS X and Linux similarities"
date: 2008-09-10
forum: Recurring Discussions
---

### Post by sharifi14 on 2008-09-10
I've been using Linux and OS X side-by-side for some time now (my desktop is a Mac, my laptop runs Ubuntu 8) and it's working out really well for me.

I understand that both operating systems share the same foundations in UNIX.

Why does Mac OS X look so much more polished and consistent in user interface, and integrate so much better with different apps than Linux does? Wouldn't the fact that they share a similar foundation in UNIX mean they have the same 'polish'?

Sorry if this is a somewhat ignorant question, I'm just looking for a straight answer (if at all there is one!).

---

### Post by Rolcol on 2008-09-10
Mac's native programs don't use X11 but Cocoa.  The UI is made by a single corporation rather than a community so everything works together.  The cores may be the similar since they're based on Unix but it's what runs on those cores that make them different.

---

### Post by SunnyRabbiera on 2008-09-10
Polish is a subject of debate really, by Polish what do you mean?
The apps look more colorful?
Streamlined?
Perhaps developed better?

I think the real thing to blame here is that Linux software isnt developed by linux itself, there is no real corporate core for linux and nor there ever will be... or should be for that matter.
Linux is a collaborative OS, Ubuntu just packages its applications and doesnt really develop them.
The interaction of application and OS is different in linux, in most respects it makes linux stand on its own...
No big wig company, no big wig ideals.
But if you are basing a OS based solely on appearance you are using the wrong OS bud.

---

### Post by Sealbhach on 2008-09-10
The various Linux apps are made by different developers with their own tastes and preferences. It's amazing it all fits together as well as it does at all.

You can make Ubuntu look quite slick, have you not looked at the desktop screenshots thread?


[http://ubuntuforums.org/showthread.php?t=906733](http://ubuntuforums.org/showthread.php?t=906733)


.

---

### Post by markbuntu on 2008-09-10
The only difference is that the mac stuff is all integrated together to give a singular look and feel. Mac is like going to the shopping mall, any shopping mall, anywhere. Linux is like going to New York City, or Hong Kong, or London, or Rio.

Some people prefer the comforting knowledge that any mall they go to anywhere on the planet will be basically the same experience, this is mac. Other people prefer the excitement and adventure of cities, which differ wildly in the experience of the visitor, this is linux.

mac= shopping mall
linux=city

You can tweak your linux to look and behave exactly like a mac, but you cannot tweak your mac to look and behave like any linux.

While you can make a shopping mall in a city, you cannot make a shopping mall into a city.

---

### Post by SunnyRabbiera on 2008-09-10
> **markbuntu said:**
> 

While you can make a shopping mall in a city, you cannot make a shopping mall into a city.

I have seen some pretty big malls though :D

---

### Post by Zzl1xndd on 2008-09-10
The polish in the Mac does come from the integration where everything is made under 1 roof. If you toss on things not made By Apple or at least without Cocoa (meaning using X-11 like in Openoffice) it sticks out like a soar thumb.

---

### Post by elmoosecapitan on 2008-09-10
Here is the way I look at it. Mac is a proprietary version of Linux that has had large amounts of time and money invested into providing very elaborate (and relatively efficient) user interfaces. This is of course at cost of locking the hardware with software. [Peach schnapps]("http://http://xkcd.com/323/") is also involved.

---

### Post by mrsteveman1 on 2008-09-10
I have to say, the OS X windowing system is much better than X11. It's been able to do compositing since OS X was released ~8 years ago. There are some comments on a slashdot thread from the guy who wrote Apples windowing system about why they avoided X11 and a lot of them are still true today.

EDIT: heres the thread, this is one of the guys who wrote the windowing system for OS X [http://developers.slashdot.org/comments.pl?sid=75257&cid=6734612](http://developers.slashdot.org/comments.pl?sid=75257&cid=6734612)

That's part of it, they have a very nice windowing system. They also have some nice toolkits to work with and in general Mac users seem to expect more out of things. 

Now, as for polish, there are a few areas in Ubuntu that could use some work, some of it has to do with X11, some of it is drivers (screen tearing), some of it is just making sure things display correctly. The default Ubuntu look is very basic, probably on purpose, but it can be made to look very nice easily.

Architecturally, OS X and Linux aren't all that similar. They are both POSIX compliant, but underneath they are quite different even down to the lowest layers of the kernel.

---

### Post by rossjman1 on 2008-09-10
Easy. Apple has millions of dollars to spend on developing their OS and since Mac seems to focus on looks and usability then it's going to be polished and well put together. On the other hand, GNU programs are developed by volunteers from around the world only communicating over the web for no money. The goal of each Linux program is that it does its job. It doesn't have to integrate with anything. Of course GNOME and KDE have their own standards and libraries (gtk+ and qt) that tries to fix this issue, but it kind of fails, really.

---

### Post by sharifi14 on 2008-09-11
Thanks for all the feedback, my question has no doubt been answered!

It all seems to boil down to the interface being built under one roof rather than spread across the globe, but I also notice that Apple has set out some strict [human interface guidelines]("http://developer.apple.com/documentation/UserExperience/Conceptual/AppleHIGuidelines/XHIGIntro/chapter_1_section_1.html"). I understand that a lot of Linux programs use the GTK theme (and it works brilliantly well) but is there a strict set of rules (or 'suggestions') when writing programs for Linux? If not, does this contribute to the lack of interface conformity?

---

### Post by starcannon on 2008-09-11
Money and a tightly controlled environment == A very uniform interface.

As pointed out earlier in this thread, Linux is a bunch of independent projects, with independent ideas about "how things should work and look" all contributing to the final product.

What would be nice is to allow some sort of easy Gnome, KDE, and XFCE integration for the developers, so that they can code once, and let the various desktop managers control how things look. I am an egg on these issues, so if that is already available please excuse my ignorance; and on that note, if it is already available, then I have little clue as to why it is not heavily utilized.

Anyway, just my .02 on the subject. Great thread and topic of consideration.

~starcannon.

---

### Post by sharifi14 on 2008-09-13
> **starcannon said:**
> What would be nice is to allow some sort of easy Gnome, KDE, and XFCE integration for the developers, so that they can code once, and let the various desktop managers control how things look.
See, that makes sense but I thought that's what the Gnome GTK and KDE Qt themes did.

My GTK theme makes all my program have consistent GUI controls but somehow there isn't a single program that conforms to a 'look and feel'. For example, when I open a new program on my Mac, it feels like I'm still in the same environment that I have learned once and now know well, but on Linux it feels like I've got to learn the **whole** program from scratch whenever I open a new program.

> **starcannon said:**
> I am an egg on these issues, so if that is already available please excuse my ignorance; and on that note, if it is already available, then I have little clue as to why it is not heavily utilized.
I would be interested to know if there are any human interface guidelines for Linux or Ubuntu, and if there are, why there is such little consistency in user interface. And if there aren't any, why not.

---

### Post by Mornedhel on 2008-09-13
There sure are.

[http://library.gnome.org/devel/hig-book/stable/](http://library.gnome.org/devel/hig-book/stable/)

Why so little consistency ? Well, if you're using only Gnome apps, developed by people who actually read and respected the HIG, they *will* be consistent. However, you have to take into consideration developers who don't respect the HIG ; applications which use another toolkit (Firefox, VLC...) or were even designed with another desktop environment in mind (raise your hand, Gnome users who run Amarok...).

As for the KDE/Gnome integration, I don't believe this is possible. Skinning Gnome apps to conform to the KDE theme, and vice-versa, is possible, but underneath it's still GTK or Qt. You can't very well change this, unless you get the Gnome people to suddenly switch to Qt (unlikely) or the KDE people to switch to GTK (even less likely), not to mention the other desktop environments. So "code once, run on multiple environments" is impossible. The logic behind both toolkits is different ; the function calls are different.

---

### Post by sharifi14 on 2008-09-14
> **Mornedhel said:**
> There sure are.

[http://library.gnome.org/devel/hig-book/stable/](http://library.gnome.org/devel/hig-book/stable/)

Why so little consistency ? Well, if you're using only Gnome apps, developed by people who actually read and respected the HIG, they *will* be consistent. However, you have to take into consideration developers who don't respect the HIG ; applications which use another toolkit (Firefox, VLC...) or were even designed with another desktop environment in mind (raise your hand, Gnome users who run Amarok...).

Wow - I just read that HIG document and it is more thorough than I would have imagined the Gnome HIG to be!

The reason for my confusion as to why virtually every single program on Linux looks different seems to be because none of the programmers respect the HIG too well, perhaps because they are all cross-platform and therefore not focussed on one single desktop environment look and feel. For example, Firefox and OpenOffice.org don't look 100% 'native' on any OS, and Picasa and Google Earth aren't even technically written for Linux (which is annoying when all the menu bars suddenly look like they're from Windows 2000). And as for the GIMP, God only knows why it has been split into 3 different windows... you'd think they know better...

---

### Post by Mornedhel on 2008-09-14
> **sharifi14 said:**
> The reason for my confusion as to why virtually every single program on Linux looks different seems to be because none of the programmers respect the HIG too well, perhaps because they are all cross-platform and therefore not focussed on one single desktop environment look and feel. For example, Firefox and OpenOffice.org don't look 100% 'native' on any OS, and Picasa and Google Earth aren't even technically written for Linux (which is annoying when all the menu bars suddenly look like they're from Windows 2000).

Exactly. That's what you get for developing for a completely cross-platform toolkit : easier to develop, easier to make portable, but looks the same everywhere (and thus, out of place everywhere).

> **sharifi14 said:**
> And as for the GIMP, God only knows why it has been split into 3 different windows... you'd think they know better...

The GIMP is the original reason for the developement of GTK "GIMP ToolKit". The decision to split it into multiple windows instead of having a single grey background behind it probably made much more sense since the user could use an entire viewport for only the GIMP. I also think there's a plugin for the GIMP somewhere to get the SDI interface you want.

---

### Post by sharifi14 on 2008-09-14
> **Mornedhel said:**
> The GIMP is the original reason for the developement of GTK "GIMP ToolKit". The decision to split it into multiple windows instead of having a single grey background behind it probably made much more sense since the user could use an entire viewport for only the GIMP. I also think there's a plugin for the GIMP somewhere to get the SDI interface you want.

I'll have to take a look at that plug-in for GIMP - it's a fantastic program for free, like much open source software, but that 3-windowed setup only can work for me on a Mac.

Well my question has no doubt been answered, and thank you for all the feedback. I'm no programmer so I can only appreciate the look and feel of the final product as an end-user.

I would say that if Linux/Ubuntu wants to seriously compete in the home user desktop/notebook market, it needs to do more than bundle free but completely isolated programs - it needs to ensure an entirely consistent GUI (at least across the bundled programs). The groundwork has clearly been done in the Gnome HIG.

Anyhow, thanks for all your help, let's just hope an Ubuntu programmer happens to find this thread!

---

### Post by Matthewthegreat on 2008-09-17
I thought the idea of Ubuntu is that *_YOU_* give it the polished look.

---

### Post by Mornedhel on 2008-09-18
A polished look is not only the result of transparency and wobbly windows. Polished look includes consistency. For instance, having the OK and Cancel buttons always follow the same placement and labeling guidelines. This is the developers' job, not the users'. To be more precise, it's the job of the application developers, NOT of the Ubuntu maintainers/packagers.

Bugs are of course often reported and fixed by the Ubuntu community so they can be pushed upstream (so that everyone using the GNOME environment will benefit from it, not just the subset of users who happen to be using Ubuntu), but they're also fixed by the Debian community, the Red Hat community, Mandriva, Slackware...

---

### Post by billgoldberg on 2008-09-18
What are you guys talking about?

If you only use gtk apps in gnome, or qt apps in kde then everything fit together perfectly.

That and the endless theming options, make Ubuntu a lot prettier in my eyes.

Just take a look at this site for an instance. 

[http://ourdesktops.com](http://ourdesktops.com)

You'll see that the Linux desktops are better recieved that the mac ones, even by the mac users.

---

### Post by Mornedhel on 2008-09-18
> **billgoldberg said:**
> If you only use gtk apps in gnome, or qt apps in kde then everything fit together perfectly.

As far as the themes are concerned, yes, it works. It even works to a certain extent if you use GTK apps under KDE and Qt apps under Gnome or XFCE.

There are two issues though : one is GTK applications which do not follow the Gnome HIG (or the KDE equivalent for Qt apps), which can be a minor source of inconsistencies (non-standard buttons, weird menu options...). If you code a GTK application for Gnome, you can for instance put the Preferences dialog in File or Help, but the HIG recommends to use the standard Gnome menu layout, which would put Preferences under Edit. This is, IMHO, part of the polish Ubuntu sometimes lacks and is particularly visible on legacy or unmaintained apps.

Another is cross-platform toolkits. Typically, Java applications tend to look like, well, Java applications. They look the same everywhere and you can often spot them at a glance : "Yup, that looks like AWT/Swing."

The original topic was "Mac OS X and Linux similarities", but at some point it changed into "why virtually every single program on Linux looks different".

FWIW, I am perfectly happy with my Ubuntu installation and would not trade it for OS X.

---

### Post by sharifi14 on 2008-09-18
Mornedhel, you have articulated what I have been trying to say all along. The thread title probably doesn't describe what I wanted to get across, but I think this quote defines this thread perfectly:
 
> **Mornedhel said:**
> A polished look is not only the result of transparency and wobbly windows. Polished look includes consistency. For instance, having the OK and Cancel buttons always follow the same placement and labeling guidelines. This is the developers' job, not the users'. To be more precise, it's the job of the application developers, NOT of the Ubuntu maintainers/packagers.

The following quote is also a great example of what I mean...

> **Mornedhel said:**
> If you code a GTK application for Gnome, you can for instance put the Preferences dialog in File or Help, but the HIG recommends to use the standard Gnome menu layout, which would put Preferences under Edit. This is, IMHO, part of the polish Ubuntu sometimes lacks and is particularly visible on legacy or unmaintained apps.

In my opinion, I am happier to work with OS X because I feel more 'secure' and if I get lost in a new program, chances are I can find my way to that command without having to search online. If Ubuntu could (and the Gnome HIG clearly shows that it can) offer this strange feeling of working out how to use a program in just a few clicks, then I would feel far more secure using it.

However, I am very happy with my Ubuntu installation, I think it is a fantastic achievement being able to create what the open source community has without any paycheck or project managers to guide them along the way. It's free, it's generally pleasing on the eye and feels nice to use software that has been made by a human, not a corporate powerhouse.

---

### Post by david_lynch on 2008-09-18
> **sharifi14 said:**
> I've been using Linux and OS X side-by-side for some time now (my desktop is a Mac, my laptop runs Ubuntu 8) and it's working out really well for me.

I understand that both operating systems share the same foundations in UNIX.

Why does Mac OS X look so much more polished and consistent in user interface, and integrate so much better with different apps than Linux does? Wouldn't the fact that they share a similar foundation in UNIX mean they have the same 'polish'?

Sorry if this is a somewhat ignorant question, I'm just looking for a straight answer (if at all there is one!).I suppose there is no accounting for personal tastes. I like OSX, and I have a couple macs at home. I had a macbook pro that I always carried on the road when traveling, but I sold it a couple months ago, since I prefer using my ubuntu laptop, and it does everything I need. :KS

OSX and linux have a similar solid unix foundation, but the GUI really has nothing to do with the low level plumbing.

I will admit that mac apps all have a uniform look, since the style is tighly controlled, while linux is capable of a wide range of styles. If you like the mac look, good for you - but IMHO the compiz cube, effects and eye candy on my ubuntu laptop are way sexier than OSX - YMMV!
:guitar:

---

### Post by spupy on 2008-09-20
> **sharifi14 said:**
> It all seems to boil down to the interface being built under one roof rather than spread across the globe, but I also notice that Apple has set out some strict [human interface guidelines]("http://developer.apple.com/documentation/UserExperience/Conceptual/AppleHIGuidelines/XHIGIntro/chapter_1_section_1.html"). I understand that a lot of Linux programs use the GTK theme (and it works brilliantly well) but is there a strict set of rules (or 'suggestions') when writing programs for Linux? If not, does this contribute to the lack of interface conformity?

Well, there is freedesktop.org. Its goals are standards which are to be used by all desktop environments. Also:
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
which aims to "standardize the internal structure of Linux-based operating systems."

Similarities:
- BASH! OH YEAH!
- Even if OS X and Linux interfaces aren't very similar, they at least look more consistent. Look at poor Windows - chat programs, anti-virus software, media players, etc - they all have different candy colored interfaces that annoy me so much. (I have couple of other rants about interfaces, but I'll leave them for later.)

---

### Post by javajames97 on 2011-08-30
> **markbuntu said:**
> The only difference is that the mac stuff is all integrated together to give a singular look and feel. Mac is like going to the shopping mall, any shopping mall, anywhere. Linux is like going to New York City, or Hong Kong, or London, or Rio.

Some people prefer the comforting knowledge that any mall they go to anywhere on the planet will be basically the same experience, this is mac. Other people prefer the excitement and adventure of cities, which differ wildly in the experience of the visitor, this is linux.

mac= shopping mall
linux=city

You can tweak your linux to look and behave exactly like a mac, but you cannot tweak your mac to look and behave like any linux.

While you can make a shopping mall in a city, you cannot make a shopping mall into a city.

although i hate to say it (being an open source junkie myself) these 'shopping malls have expanded to the extent that they have many arenas within which people pretend to be in rio or london or new york. Unfair as it may seem, the mac seems to be able to take pride in the fact it can morph and do whatever every other OS is doing, with things like fink, wine, parallels, ect. 

Though i would comment that we have retain our customizability, which mac seriously lacks.

little late though, soz

---

### Post by KiwiNZ on 2011-08-30
No posts for three years, it's sleep time

---


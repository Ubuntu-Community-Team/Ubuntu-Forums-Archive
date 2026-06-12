---
title: "Your Dream Web Framework.."
date: 2007-10-18
forum: Programming Talk
---

### Post by #Reistlehr- on 2007-10-18
Edited: Directed to PHP Developers.

Ok, so i've been working on a PHP5 framework with a few other fella's i met around the net. We have a project going on Sourceforge, and people say it's sounding promising.

Our goal is to have a complete OOBE (Out of Box Experience, and yes i'm stealing it from Microsoft because us linux users are better). It's designed to be 100% modular, with an XML datasheet and an installer file, that the module author can basically port ANY script (sensible script i should add).. and have it work, without a lot of modifications.

I want to get some input, on what would it have to have to make you use it? What are some features, that programmers would like to see in an API/Framework to make them develop for it, other than a large clientbase.

Oh, and it's OpenSource, GPLv2, so it's free, of course, when it's finished.

I don't have my mindset on replacing PHP-Nuke, or phpBB, but it would be nice ;-)..

---

### Post by Wybiral on 2007-10-18
> **#Reistlehr- said:**
> I want to get some input, on what would it have to have to make you use it?

A language other than PHP :)

---

### Post by #Reistlehr- on 2007-10-18
> **Wybiral said:**
> A language other than PHP :)

I think a big turn on is if people had a framework at their fingertips, and by that, i mean on their desktop. By creating an application, with a sort of browser support, and say, support for a specific module for the web framework, as long as they have internet, they can use it like any old program, but on the go, and on the rest. 

A great example, lets say, i make a module that has a Microsoft Word type base, and you are typing a school report on your computer at home, using the desktop application, you can go to school, print it out from the webpage, and then hand in the paper. Or, you get a memo at work, you scan, or upload, and when you get home, you download it, view it from one centralized area. 

Of course, this part is just merly brainstorming.

Yes, i want to take on google. I have a great disdain for google, built on a basis of jealousy.

---

### Post by pmasiar on 2007-10-18
> **#Reistlehr- said:**
> It's designed to be 100% modular, with an XML datasheet and an installer file, that the module author can basically port ANY script (sensible script i should add).. and have it work, without a lot of modifications.

So you are the first PHP coders who ever thought about modular, easy to use design? All those before you were just weenies with no clue?

Obviously, dozens (hundreds) of PHP projects tried to do what you try now, and for many reasons (it is not easy in any language, and especially not in PHP) they were not as successful as to smash any competition. What other previous experience you have to suggest that you will win big this time, where all those other experienced hackers failed?

> I want to get some input, on what would it have to have to make you use it? What are some features, that programmers would like to see in an API/Framework to make them develop for it, other than a large clientbase.

No, I would not consider using PHP in any system where I need to hack in. Only as a closed box, in last resort.

read [http://en.wikipedia.org/wiki/Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) about better design of interactive system, and think why in PHP is hard to implement. Then you will understand why ppl prefer other (non-PHP) languages.

You just lost me when you said you want to take on Google. Another wannabe as the guy 'cubytes', and telling you what you think will cost me more infraction points. I let someone else do it. Look up cubytes posts, to see how ridiculous claims some people do.

---

### Post by Wybiral on 2007-10-18
> **#Reistlehr- said:**
> I think a big turn on is if people had a framework at their fingertips, and by that, i mean on their desktop. By creating an application, with a sort of browser support, and say, support for a specific module for the web framework, as long as they have internet, they can use it like any old program, but on the go, and on the rest.

A great example, lets say, i make a module that has a Microsoft Word type base, and you are typing a school report on your computer at home, using the desktop application, you can go to school, print it out from the webpage, and then hand in the paper. Or, you get a memo at work, you scan, or upload, and when you get home, you download it, view it from one centralized area.

Of course, this part is just merly brainstorming.

Yes, i want to take on google. I have a great disdain for google, built on a basis of jealousy.

That still doesn't relieve the fact I wouldn't use it in one of my projects due to its use of PHP. That stuff can be done in any number of languages. I'm not saying anything bad about your project, but you asked what it would to take for me to use/develop with... And I'm saying, for me, it would require a better language.

Also, I would sell my soul to Google to work with them, not against them. Google is an incredibly intelligent company filled with possibly the brightest developers around the world.

---

### Post by #Reistlehr- on 2007-10-18
Yeah, i already did, and i already know about him haha.

Joomla, Post-Nuke, PHP-Nuke, phpBB.. they are all common developer terms when it comes to internet frameworks. And of course i am NOT the first, and i never SAID i was the first to think of a modular based design framework. What i'm doing, is making it easier for developers to create extentions by implementing libraries and such into the framework, that would relieve time from the module's author, and to make it easier for the modules themselves to be created.

You need to rmember, that this is a WEB Framework, hosted on a dedicated webserver wether over internet, or on the LAN. This is not something you code in any of the C variants. So i am quite concerned and hope you're speaking of atmost .NET, ASP, and/or a java varient. 

Obviously, you're a developer with no sense of humor, and that's what the industry lacks. 

Also, since a VERY large majoritory of hosting companies out there run linux, i'd like to see, let's say, 10% of the Linux hosting packages running .NET/ASP, and i'll decide to code in one of those proprietary languages. Obviously, i'm not holding my breathe, and am anxiously awaiting the release of PHP 6.

Those who have never coded in PHP, don't see the potential it has. They don't respect it, because they think you need a 3rd party application (ie: Browser of some sort), in order to view the complete effects of the engine, when indeed, it is a more powerful command line tool than BASH itself, with limitations, as it is not PHP's objective.

Anyway, to get back on track, most PHP developers, and group projects fail because thye lack the Advertisement, the funds, and the logical background to make it successful. By that statement i am not calling them dumb, i am calling them caught up in the moment, and disregarding key features that can help them utilize the perfomance and scope of their code. I've done it before, and i've seen it done a lot of times too. That's why i was asking for input. It can be done, it has been done, and what ain't broke, fix it. When man-kind reinvented the wheel, we put rubber on it to make it last longer. When the web-developer industry reinvents CMS's or MVC's, we will make them bigger and better. 

"The only place to go is up from here, and the sky is the limit." - lol

---

### Post by #Reistlehr- on 2007-10-18
> **Wybiral said:**
> Google is an incredibly intelligent company filled with possibly the brightest developers around the world.


As would I. I'd sell my soul for two lifetimes to work with and for them. Ii guess no one has gottten used to my sarcastic edge of humor yet.


But in general, this question was aimed more towards PHP developers.

---


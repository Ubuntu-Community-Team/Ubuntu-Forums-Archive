---
title: "Mark Shuttleworth says users can easily disable Amazon ads in Ubuntu"
date: 2013-02-19
forum: Recurring Discussions
---

### Post by C.S.Cameron on 2013-02-19
From The Inquirer:

[http://www.theinquirer.net/inquirer/news/2244932/mark-shuttleworth-says-users-can-easily-disable-amazon-ads-in-ubuntu](http://www.theinquirer.net/inquirer/news/2244932/mark-shuttleworth-says-users-can-easily-disable-amazon-ads-in-ubuntu)

Sounds like the boss listened even if some Forum Admin and Staff tried to stifle the protests.


I'm a little worried about Kernel level though.

---

### Post by 3rdalbum on 2013-02-20
> **C.S.Cameron said:**
> From The Inquirer:

[http://www.theinquirer.net/inquirer/news/2244932/mark-shuttleworth-says-users-can-easily-disable-amazon-ads-in-ubuntu](http://www.theinquirer.net/inquirer/news/2244932/mark-shuttleworth-says-users-can-easily-disable-amazon-ads-in-ubuntu)

Sounds like the boss listened even if some Forum Admin and Staff tried to stifle the protests.


I'm a little worried about Kernel level though.

1. You have always been easily able to disable Amazon search. Sudo apt-get remove unity-lens-shopping.

2. Forum staff have not stifled protests, they have moved threads to 'Recurring Discussions' which is where they should go as these discussions are now old hat.

3. There is nothing kernel-level that sends data to Amazon. That's ridiculous. If you are worried, compile a kernel from kernel.org.

---

### Post by C.S.Cameron on 2013-02-20
> **3rdalbum said:**
> 1. You have always been easily able to disable Amazon search. Sudo apt-get remove unity-lens-shopping.

2. Forum staff have not stifled protests, they have moved threads to 'Recurring Discussions' which is where they should go as these discussions are now old hat.

3. There is nothing kernel-level that sends data to Amazon. That's ridiculous. If you are worried, compile a kernel from kernel.org.

1) Placing a toggle switch in Dash is an advance on having to search the internet for the "Sudo apt-get remove unity-lens-shopping" solution.

2) In my opinion moving current news, (such as above article), to recurring discussions is stifling it.
   You really have to look to find the category "Recurring Discussions". Not something a new user can easily find.

3) From the article:
   "He said that Ubuntu will have a toggle switch in the Dash itself and that the firm will try to incorporate this at the kernel level."

---

### Post by malspa on 2013-02-20
> **C.S.Cameron said:**
> I'm a little worried about Kernel level though.

> **C.S.Cameron said:**
> From the article:
"He said that Ubuntu will have a toggle switch in the Dash itself and that the firm will try to incorporate this at the kernel level."

Here's what he actually wrote:

> Here's how we are going to handle this:

 * We will make a very bold, clear way for you to turn on and off
network queries across ALL scopes for any given session in the dash.
Think about this like the 'anonymous' mode in your browser. Toggle it,
right there in the Dash, and you are totally certain you are not sending
network traffic. We will aim to enforce this at the kernel level, hence
the CC to Jamie S who leads our security team.

 * We will have the ability to configure the Home screen, including
choice of scopes, and the behaviour of individual scopes.

 * Legal notices will all be in one place, in the 'About Ubuntu' part of
the UX, and visible in the install experience too.

Mark

[https://bugs.launchpad.net/unity/+bug/1111808/comments/6](https://bugs.launchpad.net/unity/+bug/1111808/comments/6)

---

### Post by cariboo on 2013-02-20
> **C.S.Cameron said:**
> From The Inquirer:

[http://www.theinquirer.net/inquirer/news/2244932/mark-shuttleworth-says-users-can-easily-disable-amazon-ads-in-ubuntu](http://www.theinquirer.net/inquirer/news/2244932/mark-shuttleworth-says-users-can-easily-disable-amazon-ads-in-ubuntu)

Sounds like the boss listened even if some Forum Admin and Staff tried to stifle the protests.


I'm a little worried about Kernel level though.

I see you are still using the LTS version, so you obviously haven't see how easy it is to turn the function off. Mark's email just stated that it will be even easier to turn off the search function in each scope individually, this is the email he sent to the Unity design mailing list:

> Here's how we are going to handle this:

 * We will make a very bold, clear way for you to turn on and off
network queries across ALL scopes for any given session in the dash.
Think about this like the 'anonymous' mode in your browser. Toggle it,
right there in the Dash, and you are totally certain you are not sending
network traffic. We will aim to enforce this at the kernel level, hence
the CC to Jamie S who leads our security team.

 * We will have the ability to configure the Home screen, including
choice of scopes, and the behaviour of individual scopes.

 * Legal notices will all be in one place, in the 'About Ubuntu' part of
the UX, and visible in the install experience too.

Mark

**Edit** We did not stifle protests, this was discussed endlessly during Quantal development in the U+1 devlopment sub-forum, many users that weren't even testing Quantal chose to comment, I'm sorry if you missed it. We always close the development sub-forum for a version when that version is released, so it may have looked like, to you, that we were trying to cut of discussion about this matter, but that is just the way we normally do things here, just check the archives.

---

### Post by malspa on 2013-02-20
> **3rdalbum said:**
> 1. You have always been easily able to disable amazon search. Sudo apt-get remove unity-lens-shopping.

+1

---

### Post by kevdog on 2013-02-20
Oh humm, -- tired old topic.  Nothing to read here

---

### Post by malspa on 2013-02-20
> **cariboo907 said:**
> I see you are still using the LTS version, so you obviously haven't see how easy it is to turn the function off.

I'm using the LTS version, but how to easily turn the function off has been all over the internet for a long time now. The whole thing is no big deal as far as I'm concerned.

---

### Post by craig10x on 2013-02-20
You can also turn it off from the "privacy" settings (in system settings) there is an on/off button there for it...no need to use the terminal at all ;)

---

### Post by 3rdalbum on 2013-02-20
> **craig10x said:**
> You can also turn it off from the "privacy" settings (in system settings) there is an on/off button there for it...no need to use the terminal at all ;)

True. This disables all default online Scopes, too. Hardly an "I need Google to find this" way of disabling the Shopping lens.

---

### Post by prodigy_ on 2013-02-20
It's relatively easy to disable anything in an open-source OS but this isn't the point. Canonical needs to understand that when you package something with adware it's bad, but when you force your users to opt-out it's worse.

And there's another angle. Canonical doesn't actively contribute to kernel development. And Ubuntu now comes with it's own DE (rejected by the rest of the community) so they don't contribute much to DE upstream either. So what's left? A company that tries to sell (sorry, but the current d/l page is one step away from "pay up or get lost") a Debian derivative and thinks that it has moral right to make even more money by stuffing it with adware.

> **3rdalbum said:**
> 2. Forum staff have not stifled protests...
...after all a bit of tear gas and some rubber bullets have never hurt anyone, right?

---

### Post by craig10x on 2013-02-20
well, prodigy...just to give you an example along your way of thinking, when you go to the linux mint forums you see ads, and in fact you can't even opt out of them...plus...they are on by default!...so (as you would say) that's bad!

This forum has no ads...mint is using ads to help support it, and ubuntu os uses amazon lens to help support it...but at least they are offering an easy "opt-out" if you should choose to do so..

I opt out ON ubuntu OS but i "opt-in" to supporting ubuntu by sending them occasional donations instead :D

---

### Post by prodigy_ on 2013-02-20
> **craig10x said:**
> when you go to the linux mint forums you see ads, and in fact you can't even opt out of them...
I certainly can force them out though. ) But you're right, these forums are the about the only good thing about Ubuntu now.

---

### Post by Roasted on 2013-02-20
> **prodigy_ said:**
> I certainly can force them out though. ) But you're right, these forums are the about the only good thing about Ubuntu now.

Did.. er, really?

---

### Post by mips on 2013-02-20
[http://www.theinquirer.net/inquirer/news/2244932/mark-shuttleworth-says-users-can-easily-disable-amazon-ads-in-ubuntu](http://www.theinquirer.net/inquirer/news/2244932/mark-shuttleworth-says-users-can-easily-disable-amazon-ads-in-ubuntu)

Reality of the situation is I have to agree withe the first comment from the link provided above,

> Unity was bad enough, but once word got out (many moons ago now) that they were sending all of your searches (and probably other information) to Amazon and then threatened us with the "we have root, so we already can grab all your information at will" line (can't be arsed to look up the exact quote, but that's what it boiled down to), there has been NOTHING Shuttleworth or Canonical could ever do or say to convince me to allow them onto any device (desktop, phone, or tablet) of mine ever again.

For me what they did was just wrong. You can take your allegiances etc but the way they went about it would never slide with me.

At the end of the day people have to decide how important their privacy is to them.

---

### Post by arpanaut on 2013-02-20
from my 60's radical days...

Love It or Leave It.

Nobody is forcing anybody to use their FREE operating system.
I think Marks statement about having root was more like 
"hey c'mon we already have root, either you trust us or you don't"
IMHO if you don't trust the purveyors of the system, why the heck are you using it?

---

### Post by CharlesA on 2013-02-20
> **arpanaut said:**
> Nobody is forcing anybody to use their FREE operating system.
I think Marks statement about having root was more like 
"hey c'mon we already have root, either you trust us or you don't"
IMHO if you don't trust the purveyors of the system, why the heck are you using it?

Pretty much sums it up. The whole "We have root" quote was discussed in one of the bazillion other threads about the Amazon lens. What it boiled down to is they control the repos, so they effectively have 'root' not that they actually can see whatever you have on your PC.

---

### Post by Dry Lips on 2013-02-20
I don't use Unity myself, but I would say that it's about time that they introduced an option to easily disable the default logging of keystrokes in order to send it to Amazon. 

Even Windows 8 (a proprietary closed source OS, guys) will let you disable certain forms of information gathering, and it will even let you do that in the installation process!

---

### Post by oldos2er on 2013-02-20
> **prodigy_ said:**
>  And Ubuntu now comes with it's own DE (rejected by the rest of the community) 

Unity is available for Fedora, OpenSuse, and Arch linux via their respective repos, so I would hardly call that "rejected by the rest of the community".

---

### Post by prodigy_ on 2013-02-20
> **oldos2er said:**
> Unity is available for Fedora, OpenSuse, and Arch linux via their respective repos, so I would hardly call that "rejected by the rest of the community".
Heh. I won't be surprised if I see a Gentoo ebuild one day. But take a look at Distrowatch top 100 and tell me how many distros have Unity as their default session.

---

### Post by Paqman on 2013-02-20
It's not really accurate to describe them as ads, either. Nobody pays for your search strings, or to display stuff in your dash. Canonical do get a referral fee if you click through and buy something, but that's not quite the same thing as ads.

---

### Post by iamkuriouspurpleoranj on 2013-02-20
> **prodigy_ said:**
> Heh. I won't be surprised if I see a Gentoo ebuild one day. But take a look at Distrowatch top 100 and tell me how many distros have Unity as their default session.

Which proves what exactly?

---

### Post by iamkuriouspurpleoranj on 2013-02-20
> **prodigy_ said:**
> Canonical doesn't actively contribute to kernel development. And Ubuntu now comes with it's own DE

So what? Can you point to the exact article in the Linux constitution that explicitly states that contribution to kernel development is mandatory.

No? Didn't think so.

Perhaps instead of making up silly rules that you then expect Ubuntu to abide by, you could just run the distro that you do actually like.

---

### Post by Roasted on 2013-02-20
> **prodigy_ said:**
> But take a look at Distrowatch top 100 and tell me how many distros have Unity as their default session.

It's a pretty common knowledge that DistroWatch is not to be utilized as some sort of accurate indicator of... well... anything. Plus, realistically speaking, Unity didn't even reach a "usable" status until 12.04 landed. It's available on other distros, but yeah it's admittedly not default. However, I would be somewhat surprised if Unity would become default in other distros, just considering the relationship between Ubuntu and Unity. Compare that to Gnome or anything else. There's no Gnome distro, just a Gnome desktop environment. There's no KDE distro, just a KDE desktop environment. Same for XFCE, same for LXDE. Ubuntu has something very unique, where they created their own DE for their own distro. The fact that it's available in other distros should be a monumentally huge compliment that somebody took the time to build it on Arch, etc. The fact it's not default doesn't surprise me in the slightest.

Fun thought: What about Mint and Cinnamon? They had heavy involvement in getting that DE off the ground, did they not? Do any other distros have it packaged by default?

---

### Post by Dry Lips on 2013-02-20
> **Roasted said:**
> 
Fun thought: What about Mint and Cinnamon? They had heavy involvement in getting that DE off the ground, did they not? Do any other distros have it packaged by default?

[http://www.cinnarch.com/](http://www.cinnarch.com/) It's in beta stage, though...

And I guess many other distros offer Cinnamon spins. See for instance [http://manjaro.org/](http://manjaro.org/)

---

### Post by mips on 2013-02-20
> **arpanaut said:**
> from my 60's radical days...

Love It or Leave It.

Nobody is forcing anybody to use their FREE operating system.
I think Marks statement about having root was more like 
"hey c'mon we already have root, either you trust us or you don't"
IMHO if you don't trust the purveyors of the system, why the heck are you using it?

No, the whole approach was wrong. They forced stuff on people and afterwards gave them a way out. You don't enable this by default, you have a opt in choice, not a opt out choice and that in my book is what it was all about. Personally I think they lost a lot of trust.

---

### Post by craig10x on 2013-02-20
Linux Mint has a deal with duckduckgo search engine to support it in return for having as the default search engine on firefox in mint...sure, you can easily change it in firefox, and if you install another browser like Chrome, it isn't there anyway....

But my point is...it is installed in the default browser BY default not as an "opt-in" but i don't hear anyone screaming over at the mint forums to Clem (the developer of mint) about it...only at Mark Shuttleworth at ubuntu...

To use a very old cliche'....this is much ado about nothing...

---

### Post by mips on 2013-02-20
> **craig10x said:**
> 
But my point is...it is installed in the default browser BY default not as an "opt-in" but i don't hear anyone screaming over at the mint forums to Clem (the developer of mint) about it...only at Mark Shuttleworth at ubuntu...


Thing is you are comparing apples to oranges. Duck duck go still uses google as far as I'm aware but provides a buffer so user date does not get collected by google. Unity search on the other hand by DEFAULT sends out what you could consider private info. I honestly don't see how you can even remotely compare the two.

In my eyes you don't have a leg to stand on.

---

### Post by Roasted on 2013-02-20
While I feel as though some opinions here are taken rather extreme (and that's an understatement), I do see some degree of value in prompting the user what they want. While I'm not overly excited about seeing this come up, I could almost care less since it's easy to disable. Sure, it may be a feature that should have been present from the get-go, but the fact that they're listening says something. People freaked out with Unity, and now a lot of people love Unity. Companies will take risks and try new things and sometimes make the wrong move. How they handle that those situations is how I judge companies. The fact that they allowed easy to disable features is a severe +1 in the right direction.

---

### Post by Paqman on 2013-02-20
> **mips said:**
> Thing is you are comparing apples to oranges. Duck duck go still uses google as far as I'm aware but provides a buffer so user date does not get collected by google. Unity search on the other hand by DEFAULT sends out what you could consider private info. I honestly don't see how you can even remotely compare the two.


Actually the comparison is very good. Dash searches go first to Canonical, which provides a "buffer" as you call it. They anonymise the data and forward it to Amazon. Because Amazon only sees traffic coming from Canonical (not users) the content of searches isn't able to be linked to any individual.

This is exactly the same thing that a search engine acting a an anonynmiser for Google results. AFAIK DuckDuckGo isn't simply returning Google results, but many others such as Ixquick do.

---

### Post by craig10x on 2013-02-20
> **Paqman said:**
> Actually the comparison is very good. Dash searches go first to Canonical, which provides a "buffer" as you call it. They anonymise the data and forward it to Amazon. Because Amazon only sees traffic coming from Canonical (not users) the content of searches isn't able to be linked to any individual.

This is exactly the same thing that a search engine acting a an anonynmiser for Google results. AFAIK DuckDuckGo isn't simply returning Google results, but many others such as Ixquick do.

+1 Paqman...i don't think he understands that...that is why it is a VERY VALID comparison ;)

Again...no one complains at mint about it (in fact, many there ENCOURAGE IT) here, it's another story...too many complainers here, i think :D

---

### Post by MadmanRB on 2013-02-20
> **Dry Lips said:**
> I don't use Unity myself, but I would say that it's about time that they introduced an option to easily disable the default logging of keystrokes in order to send it to Amazon. 

And this is the issue I must bang my head into a wall over, you see if you can turn it off why gripe and moan about it.,
Just use the privacy controls, its that bloody issue this making this debate entirely pointless.

---

### Post by C.S.Cameron on 2013-02-20
I am wondering how many of the posters to this thread actually have the shopping lens turned on?

Say, what has happened to KiWiNZ? I am sure missing his fine comments.

---

### Post by QIII on 2013-02-20
KiwiNZ has left the Ubuntu Forums by his own freewill and I am not at liberty to discuss further. 

Thank you.

---

### Post by prodigy_ on 2013-02-20
> **Roasted said:**
> It's a pretty common knowledge that DistroWatch is not to be utilized as some sort of accurate indicator of... well... anything.
It's a typical "I don't like your statistics so it must be wrong". And it doesn't even fit in the context of the discussion because we're not talking about which distro is the most popular. One can safely assume that DW top *10* distros combined already got at least 90% of the userbase and that's accurate enough here.

And - newsflash - the community is mostly users, not distro maintainers. Unity is rejected by userbase = rejected by the community. Period.

---

### Post by CloakandPigeon on 2013-02-20
Personally I like the Amazon suggestions that show up in Unity, I can just search for a book I wanted to purchase and its up in seconds, and I imagine casual users would enjoy this as well.  I purchase most of my ebooks from Amazon though so I could be slightly bias. :D

---

### Post by cariboo on 2013-02-20
> **prodigy_ said:**
> And - newsflash - the community is mostly users, not distro maintainers. Unity is rejected by userbase = rejected by the community. Period.

Have you got numbers to back up your claim?

---

### Post by craig10x on 2013-02-20
Perhaps initially unity was largely rejected by the user base, but since then it has really turned around...many, if not most, really like unity now...personally, i think it's a lot nicer then gnome shell...much more refined...

It was really just a matter of many getting use to something DIFFERENT...just like when one who has worked with windows for years and goes to an apple store has to adjust a bit to get accustomed to the way a mac is (with the dock, different kind of search, global top menu, etc)...

---

### Post by CloakandPigeon on 2013-02-20
> **craig10x said:**
> Perhaps initially unity was largely rejected by the user base, but since then it has really turned around...many, if not most, really like unity now...personally, i think it's a lot nicer then gnome shell...much more refined...

It was really just a matter of many getting use to something DIFFERENT...just like when one who has worked with windows for years and goes to an apple store has to adjust a bit to get accustomed to the way a mac is (with the dock, different kind of search, global top menu, etc)...

Have to agree here, Ubuntu and most Linux distros lacked a certain flash and appeal that Unity brought to the table.  I have to say that Unity is the best of both worlds when I look at the Windows Start Menu (non-windows 8) and mac OS X dock.  

I think they want this OS to be pushed to the main stream, and you can't do that without having something user's enjoy looking at and using.  Classic Gnome isn't going to do it for most users.  You have to be mindful of the current user base and also what could potentially become the user base.

---

### Post by C.S.Cameron on 2013-02-20
I got to admit that Unity looks a lot better since I've seen Metro.

---

### Post by Hylas de Niall on 2013-02-21
Remember this?

[http://www.youtube.com/watch?v=n0VX8jH0_E8](http://www.youtube.com/watch?v=n0VX8jH0_E8)

I don't personally get the same warm feeling of being 'part of something' with the recent Ubu's that i used to get with the old (pre-Maverick) releases.

That said, Unity *has* matured very nicely, and the option to disable what may be seen as a disagreeable feature *IS* a good thing.

Still a bit heavy though :(

---

### Post by prodigy_ on 2013-02-21
> **cariboo907 said:**
> Have you got numbers to back up your claim?
In our cruel world the question is have *you* got numbers to refute my claim. If I'm wrong I stand to lose nothing. But if I'm right, you bet on the wrong horse. :)

---

### Post by Perfect Storm on 2013-02-21
I dunno. Non-techies that I have install Ubuntu for like Unity and they are users that have never heard about Linux or know what an OS is.
The most moan I see comes from techies.

---

### Post by CloakandPigeon on 2013-02-21
> **Artificial Intelligence said:**
> I dunno. Non-techies that I have install Ubuntu for like Unity and they are users that have never heard about Linux or know what an OS is.
The most moan I see comes from techies.
 
Reminds me of a quote:
 
Sheldon Cooper: My new computer came with Windows 7. Windows 7 is much more user friendly than Windows Vista. I don't like that. 
 
If tech people had their way Ubuntu would use terminal to install everything still, clearly to go mainstream there are hurdles to cross. Ubuntu isn't alone in this though, nearly every iteration of MS Windows has the tech crowd moaning as well.

---

### Post by qamelian on 2013-02-21
> **Artificial Intelligence said:**
> I dunno. Non-techies that I have install Ubuntu for like Unity and they are users that have never heard about Linux or know what an OS is.
The most moan I see comes from techies.
This hasn't been my experience at all. My non-techie friends find Unity frustrating and annoying to deal with. Most of the Linux users I deal with on a daily basis are non-techie types, and only a very small percentage of them actually like Unity.

---

### Post by prodigy_ on 2013-02-21
> **Artificial Intelligence said:**
> The most moan I see comes from techies.
You mean from people who know what they're talking about? Yeah, that's very surprising.

---

### Post by craig10x on 2013-02-21
> **qamelian said:**
> This hasn't been my experience at all. My non-techie friends find Unity frustrating and annoying to deal with. Most of the Linux users I deal with on a daily basis are non-techie types, and only a very small percentage of them actually like Unity.

Can't see what would be so frustrating about using unity..it's like a "shortcuts taskbar"...you simply put your favorite and most used applications on it for easy "1 click" access to them and for those rarely used apps, just hit the "dash" (search) button on top and start typing the name of the app and, viola, There it is!

Yep...that sounds really hard, don't know if a newbie would be able to handle it...guess you are right :D

And let's see...explaining the "global menu" to them...you see when you point your mouse to the area up here on the top, you see the stuff you are use to seeing on the top of the window you have open...

Yep...that's tough too..i guess they need to go back to the simple, uncomplicated, windows 7 or even 8 (even more fun) ;)

By the way, techies are often the biggest complainers, they expect everything to stay the way they have been, otherwise they get VERY UNHAPPY...

---

### Post by Perfect Storm on 2013-02-21
> **prodigy_ said:**
> You mean from people who know what they're talking about? Yeah, that's very surprising.

No, usually techies likes commands, getting the hands dirty, like to edit config files etc. etc. etc.
They will always think what's best for them and rarely what's might appeal for the masses, and that's fine. But expecting those opinions equals the rest of the worlds is fault. If Ubuntu needs to Linux out to these masses, we need to have something like that may not appeal to the gurus.
It's like think-out-of-the-box-of-the-linux world thing.

---

### Post by qamelian on 2013-02-21
> **craig10x said:**
> Can't see what would be so frustrating about using unity..it's like a "shortcuts taskbar"...you simply put your favorite and most used applications on it for easy "1 click" access to them and for those rarely used apps, just hit the "dash" (search) button on top and start typing the name of the app and, viola, There it is!

Yep...that sounds really hard, don't know if a newbie would be able to handle it...guess you are right :D

And let's see...explaining the "global menu" to them...you see when you point your mouse to the area up here on the top, you see the stuff you are use to seeing on the top of the window you have open...

Yep...that's tough too..i guess they need to go back to the simple, uncomplicated, windows 7 or even 8 (even more fun) ;)

By the way, techies are often the biggest complainers, they expect everything to stay the way they have been, otherwise they get VERY UNHAPPY...
A sarcastic answer like this shows that you haven't given much though to various use cases, and are only prepared to look at things from your own perspective. I need to look after the needs of over 1100 people in a variety of use cases, and Unity is not the right answer for everyone. If it was, there would be no reason for many people to choose an alternative, such as KDE or XFCE.

---

### Post by MadmanRB on 2013-02-21
> **qamelian said:**
> A sarcastic answer like this shows that you haven't given much though to various use cases, and are only prepared to look at things from your own perspective. I need to look after the needs of over 1100 people in a variety of use cases, and Unity is not the right answer for everyone. If it was, there would be no reason for many people to choose an alternative, such as KDE or XFCE.

Indeed, I agree.
But thed bthing is that Unity is rather easy once you get used to it.
But it has a few little issues that I wish were fixed, like the globalmenu in non maximized windows or the disappearing act the close/min/max buttons, or the lack of a proper windows switcher (though that is being fixed for 13.04 but that indicate you have to use a unstable distribution  to use it)
stability issues in Unity...

---

### Post by prodigy_ on 2013-02-21
> **Artificial Intelligence said:**
> appeal for the masses
This reminds me... See, recently I heard about an employee in our company who had to spend about two wonderful workdays manually renaming files in a shared folder. Not sure there was any pattern to it but my IT sense tells me there probably was.

An extreme example, sure, but how often something less noticeable of this kind takes place? Like editing every occurrence of a word instead of using "replace all". Or visually looking for data in a table in a DB client. I know that I don't know exactly what my PC is capable of. Sometimes I still stumble upon incredibly clever pieces of software and I think "wow, I never knew such things existed". But in most cases I assume there there should be some nice and smart solution and I search for it. Many people are completely oblivious however. And this "appeal" attitude helps to breed and nurture their ignorance.

The absolute peak of your "appeal for the masses" is iOS - an incredibly dumbed down sad excuse for an OS, a 100% black box that will never let its users to learn anything forever forcing them to waste their time using less than optimal ways.

---

### Post by craig10x on 2013-02-21
By the way i was trying to be sarcastic...just to drive home a point...UNITY is NOT DIFFICULT to use...i know many windows users who either put all the favorite and most used apps on the windows taskbar or else make shortcuts on the desktop....unity is really just a shortcuts dockbar...plain and simple....should be easy for any newbie to grasp...

If the problem is because it looks different from what they are use to and they can't be comfortable unless the linux distro looks essentially identical, then that is most unfortunate for them...

I don't know, lots of windows users go to mac stores and start playing with them and fall in love with it, even though it doesn't look anything like the windows layout....so, why can't a newbie adjust to the easy to use ubuntu with unity???

---

### Post by MadmanRB on 2013-02-21
> **craig10x said:**
> By the way i was trying to be sarcastic...just to drive home a point...UNITY is NOT DIFFICULT to use...i know many windows users who either put all the favorite and most used apps on the windows taskbar or else make shortcuts on the desktop....unity is really just a shortcuts dockbar...plain and simple....should be easy for any newbie to grasp...

If the problem is because it looks different from what they are use to and they can't be comfortable unless the linux distro looks essentially identical, then that is most unfortunate for them...

I don't know, lots of windows users go to mac stores and start playing with them and fall in love with it, even though it doesn't look anything like the windows layout....so, why can't a newbie adjust to the easy to use ubuntu with unity???


Its all about familiarity, this is why Windows 8 is tanking for many.
Users like things in places they are used to them being, such as a start button at the bottom of the screen.
Ubuntu if you are not used to it could be confusing on where the menu is at.
Though bit does have the ubuntu logo on it...

---

### Post by Hylas de Niall on 2013-02-21
> **MadmanRB said:**
> Its all about familiarity, this is why Windows 8 is tanking for many.
Users like things in places they are used to them being, such as a start button at the bottom of the screen.
Ubuntu if you are not used to it could be confusing on where the menu is at.
Though bit does have the ubuntu logo on it...

I don't remember because i wasn't online bach then, but was there a lot of user dissatisfaction when windows moved from 3.11 to 95? That was a pretty big change too.

---

### Post by Paqman on 2013-02-21
> **prodigy_ said:**
> One can safely assume that DW top *10* distros combined already got at least 90% of the userbase and that's accurate enough here.


No one can't. DistroWatch's methodology does not in any way result in data that reflects the actual userbase of any Linux distro. DistroWatch rankings only show the popularity of a particular page on DistroWatch. There's no causal relationship, and only an extremely weak correlation, between that and the actual userbase.

DistroWatch themselves point this out:
> They correlate neither to usage nor to quality and should not be used to measure the market share of distributions
[(Source)](http://distrowatch.com/dwres.php?resource=popularity)

---

### Post by deadflowr on 2013-02-21
Back on Topic:

The inclusion of a more robust privacy system than the one already in place is a plus for all users.

What should be done, is putting pressure to get it on to systems as quickly as possible.Making this wishlist a reality.

---

### Post by mamamia88 on 2013-02-21
Just because you can easily disable something doesn't mean that it should be enabled by default.  This is probably the most useless "feature" ever.

---

### Post by screaminj3sus on 2013-02-21
I don't get the outrage, what mark said is 100% true. Its extremely easy to *completely* remove the shopping lens. people need to stop making a mountain out of a molehill.

---

### Post by diesch on 2013-02-21
I think the problem is that Canonical didn't make it clear what the intended use of the Dash home is:

Most people seem to use it as the central point to open files and start applications - but Canonical seems to have a different understanding. For them the Dash home seems to be some sort of search engine that collects all sorts of information. To open your files and to start applications you use the file and applications lenses instead.

---

### Post by Dr. C on 2013-02-21
Making network search clear and explicit in the dash is excellent news and very much along the lines of what Richard Stallman suggested in 
> ...To protect users' privacy, systems should make prudence easy: when a local search program has a network search feature, it should be up to the user to choose network search explicitly each time. This is easy: all it takes is to have separate buttons for network searches and local searches, as earlier versions of Ubuntu did. A network search feature should also inform the user clearly and concretely about who will get what personal information of hers, if and when she uses the feature. ...[http://www.fsf.org/blogs/rms/ubuntu-spyware-what-to-do]("http://www.fsf.org/blogs/rms/ubuntu-spyware-what-to-do"). Mark Shuttleworth deserves a lot of praise for his excellent display of leadership in this matter. 

I must say that I am not that surprised given my past very positive experience with Ubuntu over the last six years. I actually suspected that this issue would be resolved at the highest level well before the next LTS release, 14.04 and it has. 

One thing to note is that this one more example of why many Ubuntu users who wish to be conservative should stick to the LTS releases as it becomes very clear that a user who goes from 12.04 directly to 14.04 would not be impacted by this privacy issue at all.

---

### Post by CloakandPigeon on 2013-02-21
> **diesch said:**
> I think the problem is that Canonical didn't make it clear what the intended use of the Dash home is:

Most people seem to use it as the central point to open files and start applications - but Canonical seems to have a different understanding. For them the Dash home seems to be some sort of search engine that collects all sorts of information. To open your files and to start applications you use the file and applications lenses instead.

While it may not have been 100% clear, it surely wasn't hidden, the suggestions come up right underneath your search.  Its not as if they were attempting to hide something and it does offer some good suggestions.  You have the option to disable it, simple enough.

---

### Post by MadmanRB on 2013-02-22
> **mamamia88 said:**
> Just because you can easily disable something doesn't mean that it should be enabled by default.  This is probably the most useless "feature" ever.

Well the fact you can turn it off is a good point, after all if this was real spyware we would not have the ability to turn it off.

---

### Post by aysiu on 2013-02-22
> **MadmanRB said:**
> Well the fact you can turn it off is a good point, after all if this was real spyware we would not have the ability to turn it off.
The kind of spyware I don't like does two things:

1. Doesn't let me know it's running
2. Doesn't allow me to easily turn it off

---

### Post by MadmanRB on 2013-02-22
> **aysiu said:**
> The kind of spyware I don't like does two things:

1. Doesn't let me know it's running
2. Doesn't allow me to easily turn it off

Well yeah, you can do that in 12.10 and 13.04.
Again privacy settings button :popcorn:

---

### Post by graabein on 2013-02-23
Amazon spyware bundled with Ubuntu. It's not good. Anyhow, can't one just install the server edition and add xmonad 'n' stuff oneself?

---

### Post by CharlesA on 2013-02-23
> **graabein said:**
> Amazon spyware bundled with Ubuntu. It's not good. Anyhow, can't one just install the server edition and add xmonad 'n' stuff oneself?

You don't need to install the server edition, just use the minimal iso and install the stuff you want. ;)

---

### Post by Umbra Diaboli on 2013-02-23
You just go to privacy under preferences, and disable the web search.

Then with Unity Tweak Tool, under the "Search" tab you disable "More Suggestions".

After that, your Ubuntu installation will not have that silly intrusive crap Canonical wants to shovel on us.

(Either that, or you install Cinnamon).

---

### Post by CharlesA on 2013-02-23
> **Umbra Diaboli said:**
> 
(Either that, or you install Cinnamon).

Or Xfce, Lxde, KDE, Gnome3, Gnome-shell, etc, etc, etc... :KS

---

### Post by craig10x on 2013-02-23
> **Umbra Diaboli said:**
> You just go to privacy under preferences, and disable the web search.

Then with Unity Tweak Tool, under the "Search" tab you disable "More Suggestions".

After that, your Ubuntu installation will not have that silly intrusive crap Canonical wants to shovel on us.

(Either that, or you install Cinnamon).

Actually, just shutting off the two buttons you will find in the "privacy" section of system settings will take care of everything...simple solution that takes all of 30 seconds... ;)

After you do that, you will only get the normal "dash" search results...

---

### Post by cariboo on 2013-02-23
> **craig10x said:**
> Actually, just shutting off the two buttons you will find in the "privacy" section of system settings will take care of everything...simple solution that takes all of 30 seconds... ;)

After you do that, you will only get the normal "dash" search results...

It seems some people would rather do things the hard way, rather than spending a couple of minutes finding out how to turn off the objectionable behaviour.

---

### Post by alexfish on 2013-02-23
Objectionable behaviour . that's a new one  ,

Some times I call it " a Face Book Reject" or similar. Notable as in , Argumentative Knowing the Facts in the first place . ;)

---

### Post by mamamia88 on 2013-02-24
> **MadmanRB said:**
> Well the fact you can turn it off is a good point, after all if this was real spyware we would not have the ability to turn it off.

YES you can turn it off nobody is arguing that point.  Canonical is obviously trying to monetize Ubuntu and they have every right to do so.  But, they should really try and find a way to do it that doesn't involve showing meaningless search results from amazon on a dash search.  Heck even setting amazon.com as the home page for Firefox on every install of Ubuntu would be a better idea.   I understand they need to make money but they need to figure out a smarter way to do it.  Like I dunno making a product that creates a large user base that is so satisfied that they will gladly donate to the project when prompted to on the download page.

---

### Post by ikt on 2013-02-24
> **mamamia88 said:**
> YES you can turn it off nobody is arguing that point.

Every time someone says Ubuntu is Spyware or Adware or Malware... they are. Which is why Mr. Stallmans message came across to me as hyperbolic. The people who most agree with him likely don't remember the plague of spyware and adware that went around in 2002-2007~ on Windows machines.

They were likely the ones going 'doesn't affect me, I run linux'.

If turning off gater or bonzi buddy or the endless pop ups or anything that came with any number of adware and spyware was as easy as flipping a switch to off, it would have made my job a lot easier, secondly none of those things provided a service that one would argue is valuable, in any shape or form, strongly intrusive pop up advertising that is near impossible to disable is annoying, being able to search for something and having relevant ads come up while you search is google.

> **mamamia88 said:**
> Like I dunno making a product that creates a large user base that is so satisfied that they will gladly donate to the project when prompted to on the download page.

[http://youtu.be/Sh-cnaJoGCw?t=35m30s](http://youtu.be/Sh-cnaJoGCw?t=35m30s)

Most people simply won't donate to something they can get for free, and you're assuming that Ubuntu wants to make most of its money from the download page, as Linus explains:

[http://www.youtube.com/watch?v=KFKxlYNfT_o](http://www.youtube.com/watch?v=KFKxlYNfT_o)

Android isn't super popular because people download .iso disk images off the android website, the main way will be through pre-installation. So Canonical have had to find alternative ways to fund the OS, and the alternate ways include money through amazon ads ala google ads with pictures, through Ubuntu One, through the Ubuntu Software Centre and hopefully through the Ubuntu Phone and Tablet.

---

### Post by mamamia88 on 2013-02-24
> **ikt said:**
> Every time someone says Ubuntu is Spyware or Adware or Malware... they are. Which is why Mr. Stallmans message came across to me as hyperbolic. The people who most agree with him likely don't remember the plague of spyware and adware that went around in 2002-2007~ on Windows machines.

They were likely the ones going 'doesn't affect me, I run linux'.

If turning off gater or bonzi buddy or the endless pop ups or anything that came with any number of adware and spyware was as easy as flipping a switch to off, it would have made my job a lot easier, secondly none of those things provided a service that one would argue is valuable, in any shape or form, strongly intrusive pop up advertising that is near impossible to disable is annoying, being able to search for something and having relevant ads come up while you search is google.



[http://youtu.be/Sh-cnaJoGCw?t=35m30s](http://youtu.be/Sh-cnaJoGCw?t=35m30s)

Most people simply won't donate to something they can get for free, and you're assuming that Ubuntu wants to make most of its money from the download page, as Linus explains:

[http://www.youtube.com/watch?v=KFKxlYNfT_o](http://www.youtube.com/watch?v=KFKxlYNfT_o)

Android isn't super popular because people download .iso disk images off the android website, the main way will be through pre-installation. So Canonical have had to find alternative ways to fund the OS, and the alternate ways include money through amazon ads ala google ads with pictures, through Ubuntu One, through the Ubuntu Software Centre and hopefully through the Ubuntu Phone and Tablet.

True but then again annoying your user base isn't going to help make money either.  I'm just saying that there has to be a better way.  Like maybe create an amazon instant video app for Ubuntu and make a deal with amazon to give you a percent of each sale. Canonical knew what they where getting into when they started out.   Yes, most of the user base wouldn't donate if asked and yes it cost money for development.  But, adding a feature that isn't very useful and may be annoying for some people isn't the way to go about it, even if it's easy to turn off.

---

### Post by The Spectre on 2013-02-24
I am surprised on how upset people are getting over the Amazon search results.

Especially considering that Ubuntu is Free and how easy it is to Disable or Remove the Amazon search results.

Google, Yahoo and Bing have paid Advertising in there Search Results and I am sure that some of the people that are complaining about the Amazon search results in Ubuntu use Google, Yahoo or Bing without a second thought.

It is like the old saying goes...

"You can please some of the people some of the time, all of the people some of the time, some of the people all of the time, but you can never please all of the people all of the time."
 

It is plain and simple if you don’t like it just Disable or Remove the Amazon search results it's that simple. 
At least you are given the option to do so.

 
The Amazon search results don’t bother me at all in fact I wish I could add NewEgg in the search results.

---

### Post by prodigy_ on 2013-02-24
> **The Spectre said:**
> I am surprised on how upset people are getting over the Amazon search results.

Especially considering that Ubuntu is Free
This is exactly why we are upset. Read RMS post on this (first link in my sig). I couldn't possibly describe the problem better than he already did.

---

### Post by Linuxratty on 2013-02-24
> **mamamia88 said:**
>  Like maybe create an amazon instant video app for Ubuntu and make a deal with amazon to give you a percent of each sale.

Yeah,and do this for Netflix too.

---

### Post by tartalo on 2013-02-24
> **prodigy_ said:**
> This is exactly why we are upset. Read RMS post on this (first link in my sig). I couldn't possibly describe the problem better than he already did.

There was a time when every Linux user would understand the difference between "free as in beer" and "free as in freedom" but apparently that's not the case anymore. Others don't even smell what's wrong with the "I have nothing to hide" anti-privacy argument.

I wonder if they know what made Ubuntu even possible.

*Those who cannot remember the past are condemned to repeat it.*

---

### Post by Branimir on 2013-02-24
I am not worried about Unity at all since I use KDE mainly.
Just for fun I have logged into Unity and typed some search.
It's awesome feature , I like it ;)
IMO they need to broaden offers. Say more commercial products
and more intelligent search, say when I type movie to list
any kind of movies not something that has in it's title 'movie'.
or when I type game I want games dammit ;)
Regarding kernel hacking I compile my own kernels,
so not much to worry  about ...

---

### Post by nothingspecial on 2013-02-24
Deja vu :shock:

*Thread moved to **Recurring Discussions**.*

---

### Post by BBQdave on 2013-02-26
> **deadflowr said:**
> Back on Topic:

**The inclusion of a more robust privacy system** than the one already in place is a plus for all users.

What should be done, is putting pressure to get it on to systems as quickly as possible.Making this wishlist a reality.

I use Fedora with Gnome 3. Some challenges that come up from this distro are working with SELinux. That is to say, loosening the security that is built in to allow features and functions the user may want.

In testing Ubuntu Unity, the concerning part for me, is there seems to be a reversal of built in security and privacy. That is to say, you have to take a default install of Ubuntu Unity, and harden it. Perhaps it is easy to turn off keystroke recording or block data sent to Amazon, but in the Linux world it is uncomfortable.

I recognize that hopping on a browser opens you up to data mining. With that application, I am cautious and work on making it as safe to use as possible. But to push that further, and now be concerned about an entire distro...

I think at the end of the day, this is not a good path for Canonical. If a user accepts this type of concept for a distro - it is much easier to obtain Windows or osX than Ubuntu Unity.

Ubuntu Unity is a nice DE. I like the integration of Rhythmbox and other applications - it flows very nicely. Ubuntu has always done a nice job of presenting a polished complete distro. I feel that the current path of connecting consumables with Amazon - built into Unity, diminishes Ubuntu's good history of a fine distro.

---

### Post by CharlesA on 2013-02-27
Fedora has SELinux, Ubuntu has AppArmour.

As always you will sacrifice security for convenience.

---

### Post by BBQdave on 2013-02-27
> **CharlesA said:**
> Fedora has SELinux, Ubuntu has AppArmour.

As always you will sacrifice security for convenience.

True.

And I may misunderstand - Canonical trying to push a feature of convenience with search tie-ins of Amazon, Facebook, and the BBC through dash.

It still seems intrusive. After seeing abuses of users personal data through facebook by third parties like Farmville Games, I think there is potential for abuse in Dash data recording.

---

### Post by mamamia88 on 2013-02-27
> **nothingspecial said:**
> Deja vu :shock:

*Thread moved to **Recurring Discussions**.*

It took a mod 8 pages to realize this?

---

### Post by craig10x on 2013-02-27
@BBQDave:  again...and i and others have mentioned it a zillion times already, you just go to the privacy settings and hit 2 buttons to off...5 seconds and you have no further involvement with it...

Just because they have it on by default doesn't mean you HAVE to use it...it's your option, entirely...

---

### Post by Elfy on 2013-02-27
> **mamamia88 said:**
> It took a mod 8 pages to realize this?

Not at all. It might have taken one mod time to realise it's there - we don't all spend all day reading all posts :)

I knew it was there after a few posts I think, I didn't bother moving it - though I have to say I've not see one post that isn't actually a rinse and repeat.

---

### Post by Paqman on 2013-02-27
> **BBQdave said:**
> After seeing abuses of users personal data through facebook by third parties like Farmville Games, I think there is potential for abuse in Dash data recording.

To their credit, Canonical have set the system up so that as little personally identifiable data is passed to third parties. The origin of search strings is obfuscated, so the third party just sees it all coming from Canonical.

Since by running their operating system you implicitly trust Canonical, you're no more at risk of abuse than you were before.

The only real risk comes from the fact that search strings could themselves contain sensitive user data that rendered them identifiable. If you do require really bombproof privacy then the smart thing to do is just switch off or uninstall the shopping lens.

---

### Post by BBQdave on 2013-03-01
> **Paqman said:**
> The origin of search strings is obfuscated, so the third party just sees it all coming from Canonical.

Since by running their operating system you implicitly trust Canonical, you're no more at risk of abuse than you were before.

The only real risk comes from the fact that search strings could themselves contain sensitive user data that rendered them identifiable. If you do require really bombproof privacy then the smart thing to do is just switch off or uninstall the shopping lens.

OK, I'm gonna go ahead and poke the bear here :D

In Fedora land, there is a bit of an uproar over Gnome 3, because what little intertwining of social network access in the DE - is cause for security concern. There are some interesting discussions going on about how RHEL is going to implement Gnome 3 and be secure in upcoming releases.

Now switching over to Ubuntu land, not only is there intertwining of social network access in the DE, but Unity Dash sends user data to Canonical servers for use by third parties. I have worked with non profit organizations that use Ubuntu, specifically 10.4. But now Ubuntu is a huge no no, as there is sensitive data, medical data - that can not be data mined by *dash*.

I appreciate the financial draw of turning a distro into *Google Consume* or *iTune-buntu*, but it is a shame that a nice polished Linux distro that once provided so many with valuable modern tools - it's now no more than an advert consumption pipe.

Again, I think it is the wrong path for Canonical - it is already being done by *Apple iConsume* and *Windows come exploit the user*.

---

### Post by diesch on 2013-03-01
If you are working with sensitive data you should *never ever* use the standard configuration of any mainstream Linux distribution. having a look at the privacy settings should be just the bare minimum, but quite likely you'll want to remove or replace some software. Failing to do that could even get you into serious legal trouble in some countries.

---

### Post by cariboo on 2013-03-01
> **BBQdave said:**
> OK, I'm gonna go ahead and poke the bear here :D

In Fedora land, there is a bit of an uproar over Gnome 3, because what little intertwining of social network access in the DE - is cause for security concern. There are some interesting discussions going on about how RHEL is going to implement Gnome 3 and be secure in upcoming releases.

Now switching over to Ubuntu land, not only is there intertwining of social network access in the DE, but Unity Dash sends user data to Canonical servers for use by third parties. I have worked with non profit organizations that use Ubuntu, specifically 10.4. But now Ubuntu is a huge no no, as there is sensitive data, medical data - that can not be data mined by *dash*.

I appreciate the financial draw of turning a distro into *Google Consume* or *iTune-buntu*, but it is a shame that a nice polished Linux distro that once provided so many with valuable modern tools - it's now no more than an advert consumption pipe.

Again, I think it is the wrong path for Canonical - it is already being done by *Apple iConsume* and *Windows come exploit the user*.

Ubuntu isn't what your organization needs, as it is purposely designed to be easy to use, and with the features that the average user wants. I'd suggest using Debian stable, as most of what you have learned using Ubuntu is easily transferable, and another advantage is that Debian doesn't provide any closed source binaries itself, so there is one less thing to worry about.

---

### Post by tartalo on 2013-03-01
> **cariboo907 said:**
> I'd suggest using Debian stable
Actually, an Ubuntu user would fell more at home with Debian Sid. But not a bad advise at all.

---

### Post by BBQdave on 2013-03-01
> **cariboo907 said:**
> Ubuntu isn't what your organization needs, as it is purposely designed to be easy to use, and with the features that the average user wants. I'd suggest using Debian stable, as most of what you have learned using Ubuntu is easily transferable, and another advantage is that Debian doesn't provide any closed source binaries itself, so there is one less thing to worry about.

I switched from Ubuntu 10.4 to Debian 6 with backports. Extremely happy with Debian on older hardware. And yes, absolutely for the purposes of this non-profit, Debian is great. With newer hardware, I tried Fedora 16 with Gnome 3 and now cruising along with F18 Gnome 3. So I have found comfort in returning to Fedora - Red Hat Linux, I started out on Red Hat Linux, Yellow Dog Linux.

Ubuntu is a friendly Linux distro to use. I think there are better ways to grow Canonical than data mining through Ubuntu Unity. I hope this path does not cause long term damage to Ubuntu. But at the end of the day, maybe Canonical can carve out some earnings following the trail of Microsoft and Apple. Again though, I think this is massive wreckage of a good Linux distro :(

---

### Post by malspa on 2013-03-03
> **BBQdave said:**
> Again though, I think this is massive wreckage of a good Linux distro :(

Maybe, maybe not. I don't know, still seems like a very good distro to me. It's still kinda like with any other distro, there are some things I like, some things I don't like; with any of 'em, when I do an installation, I tweak it a little bit (or a lot, depending) to suit my wishes/needs. So one of the "tweaks" in Ubuntu would be to turn off the Amazon stuff. About as painless as switching to your favorite desktop background.

---

### Post by craig10x on 2013-03-03
Two simple "off buttons" to hit in privacy to make it non-amazon and your ubuntu is "un-wrecked" (to use your terminology....lol)

---


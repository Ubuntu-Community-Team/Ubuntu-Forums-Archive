---
title: "Will Ubuntu drop Firefox for the Webkit based Epiphany in the near future?"
date: 2009-08-22
forum: Recurring Discussions
---

### Post by nomnomnom on 2009-08-22
Now that it feels like the long slow death of Firefox has begun, do you think that it's dominance in the Linux browser wars is about to end as Webkit becomes the new standard?

Personally I prefer Firefox to every other Webkit browser besides Epiphany. Firefox 3.5 is only just behind Google Chrome for speed in my experience.

---

### Post by Ms_Angel_D on 2009-08-22
I hope not

---

### Post by hetx on 2009-08-22
You have to consider also that Ubuntu is here to help the GNU/Linux and GNOME community too, so going Epiphany is not impossible. You'd still be able to switch back to Firefox easily of course, but it'd get a lot of people to try Epiphany, and the new one is looking very nice.

And since Epiphany is the GNOME browser.

---

### Post by nomnomnom on 2009-08-22
> **hetx said:**
> You have to consider also that Ubuntu is here to help the GNU/Linux and GNOME community too, so going Epiphany is not impossible. You'd still be able to switch back to Firefox easily of course, but it'd get a lot of people to try Epiphany, and the new one is looking very nice.

And since Epiphany is the GNOME browser.

Pretty much what I thought.

---

### Post by steeleyuk on 2009-08-22
On a personal level I'd prefer to see Midori chosen, seems to have seen more development in recent months.

A WebKit browser would be better all round, save space on the disk and gives a single backend for many applications to use.

---

### Post by Copernicus1234 on 2009-08-22
> **nomnomnom said:**
> Now that it feels like the long slow death of Firefox has begun, do you think that it's dominance in the Linux browser wars is about to end as Webkit becomes the new standard?

Personally I prefer Firefox to every other Webkit browser besides Epiphany. Firefox 3.5 is only just behind Google Chrome for speed in my experience.

Plugins > Speed, as long as its fast enough. And it very much is. You could probably make a browser that is uber fast but has no additional features, but whats the point? Today we want to have plugins in the browsers to make them be more than just a browser.

Chrome has the option to be just as good in the future however, which kind of worries me a little. Because once we start using Google for everything, they will be worse bad guys than Microsoft ever was.

---

### Post by nomnomnom on 2009-08-22
> **Copernicus1234 said:**
> Plugins > Speed, as long as its fast enough. And it very much is. You could probably make a browser that is uber fast but has no additional features, but whats the point? Today we want to have plugins in the browsers to make them be more than just a browser.

Yeah, Google Chrome is great speed wise, but without plugins like Adblock Plus, I find it unusable.

---

### Post by gnomeuser on 2009-08-22
Mozilla has ignored the Linux platform for long, they integrate poorly with our desktop and release versions with massive known problems on Linux. 

Till now we have had no real alternatives, however with Chrome and WebKit coming along we have, however here is what I think will push for a replacement.

XULrunner will be their doom, Mozilla has really ignored application designers and made this very hard to use since it's basically just something that goes into Firefox for them. This has lead to many applications switching to WebKit which is much nicer to embed and easier to work with. Additionally is has a smaller footprint and generally has a reputation for providing consist improvements in performance. Just go look at the Firefox 3.5 transition documentation, around half the gecko packages didn't migrate to the new xulrunner but to WebKit. This trend is not going to stop, the near future will very likely bring a situation where we will be carrying the very large xulrunner code for Firefox (and maybe a few other side apps) as our desktops depend on WebKit that will have to be on the CD as well. This makes it very attractive to simply replace Firefox and lets say this becomes worth considering in a years time. That gives the full might of Google 12 months to polish up Chromium, something they will have to do anyways as they are launching their Linux based Chrome OS late this year. Looking at their progress already they are making lots of improvements available every day, they successfully manage a short delivery and user testing loop thanks to the PPA and their own beta/dev channels. They are doing a lot of things right.

I see Firefox has getting fierce competition in the Linux market, I also see it losing unless they improve massively. In 12 months they will have to give us better integration, a cleaner embedding API, process separation (okay they are reportedly working on this), a cleaner UI and they have to show that they are willing to treat Linux fairly. I simply don't believe that is time enough for them to change their culture and improve their codebase.. they will lose this one.

As for Epiphany, I have used it for years but I just don't see it as being an appealing option, development isn't being driven by a large team and development is slower than compared to both the Firefox and the WebKit.

---

### Post by gnomeuser on 2009-08-22
> **nomnomnom said:**
> Yeah, Google Chrome is great speed wise, but without plugins like Adblock Plus, I find it unusable.

But.. there is an adblock plugin :)

---

### Post by HoKaze on 2009-08-22
"long slow death of firefox", huh? I don't think that's going to happen. Most non-lightweight 'standard' distros include Firefox (sometimes in addition to another browser) and I don't think that's going to change anytime soon. Maybe Ubuntu will adopt another browser but with the popularity, plugins and support firefox has I would think they would include it with the other browser.

---

### Post by Copernicus1234 on 2009-08-22
> **gnomeuser said:**
> 
I see Firefox has getting fierce competition in the Linux market, I also see it losing unless they improve massively. 

Unfortunately I see the same thing, and it worries me. I dont want Linux users to use Google applications for everything. Competition is good for us users, and once there is hardly any competition left, the company turns bad guy on us. Its always like that. They make the best applications, but its strange that no other company can compete actually. Something makes them go for the right markets and have the people and resources to dominate that market.

Google is everywhere now. They are even more dominant than Microsoft ever was in the web application world, and are starting to dominate the mobile phone market as well. Soon we will be using Google for everything. Trust me, a future where we use Google applications for everything is exactly like the past 10 years ago with Microsoft.

---

### Post by nomnomnom on 2009-08-22
> **gnomeuser said:**
> As for Epiphany, I have used it for years but I just don't see it as being an appealing option, development isn't being driven by a large team and development is slower than compared to both the Firefox and the WebKit.

But Epiphany has switched to Webkit now and has dropped Gecko as the backend. It also works better than any other Webkit based Linux browsers I have tried (Arora, Chomium, etc..)

> **gnomeuser said:**
> But.. there is an adblock plugin :)

Really?!? I bet it doesn't block AdSense... :P

Where do you get it from?

---

### Post by gnomeuser on 2009-08-22
> **nomnomnom said:**
> But Epiphany has switched to Webkit now and has dropped Gecko as the backend. It also works better than any other Webkit based Linux browsers I have tried (Arora, Chomium, etc..)


Still doesn't give us a strong development team behind the code to fix up problems and add features. Compared to Firefox and Chromium the support is nonexistent which is bad for a distro. I like Epiphany and I do believe from an integration pov it would make a superior offering to Firefox but the smart money is definitely on supporting Chromium.

> 
Really?!? I bet it doesn't block AdSense... :P

Where do you get it from?

There's a proper adblock extension in the work but adsweep should work. Remember to enable extensions in your chromium (/etc/chromium-browser/default should help you). but remember the extension support is still being put into place they are doing it right (for once no required browser restarts to enable newly installed extensions).

[http://www.adsweep.org/](http://www.adsweep.org/)

---

### Post by gnomeuser on 2009-08-22
> **Copernicus1234 said:**
> Unfortunately I see the same thing, and it worries me. I dont want Linux users to use Google applications for everything. Competition is good for us users, and once there is hardly any competition left, the company turns bad guy on us. Its always like that. They make the best applications, but its strange that no other company can compete actually. Something makes them go for the right markets and have the people and resources to dominate that market.


Google unlike any previous players depends on Open Source and releases source under such licenses. They haven't really done anything overtly evil (sure they misbehaved but they are a better player than most). I am not so scared of them donating code and work with the ultimate goal of making computing nicer. Nobody is forcing me to use their services.

> 
Google is everywhere now. They are even more dominant than Microsoft ever was in the web application world, and are starting to dominate the mobile phone market as well. Soon we will be using Google for everything. Trust me, a future where we use Google applications for everything is exactly like the past 10 years ago with Microsoft.

To me the answer seems not to shun Google for their generous donations of code, time and valuable content. It is to offer superior services, I think people will be willing to pay for open services that are trustworthy and ad free, if they are sufficiently well designed. The whole open source movement has been extremely slow to adapt to making web applications and the infrastructure is admittedly a non trivial problem to solve, after all servers and the required resources don't pay for themselves. We have been much more focused on providing the server applications to make such things a reality and providing standard compliant browsers for people to enjoy this new fangled world.

I believe we can do it, I believe we have the tools to do so and the skills. I believe there is a business model to fund such a project. I also know that the longer we wait doing this, the further behind we will be when we as a community realize that we have to do this to stay relevant.

---

### Post by 3rdalbum on 2009-08-22
The question of replacing Firefox with Epiphany was raised a couple of years ago. The Ubuntu developers said no - new users are likely to be familiar with Firefox, it's the most popular browser on Linux, and users with lots of Firefox extensions don't have to give up anything in that regard.

So, no, Firefox is not going anywhere.

---

### Post by Ichtyandr on 2009-08-22
Firefox is not just browser. Due to zotero extension it is also my very loved citation manager environment. Its not only adblock there, some people turn it into a mini os with a lot of functions, so hopefully it improves and doesn't get abandoned

---

### Post by coldReactive on 2009-08-22
> **gnomeuser said:**
> But.. there is an adblock plugin :)

I would rather have a NoScript plugin.

---

### Post by chucky chuckaluck on 2009-08-22
> **Copernicus1234 said:**
> Because once we start using Google for everything, they will be worse bad guys than Microsoft ever was.

i don't know. is google bigger than apple and are they worse?


> **nomnomnom said:**
> Now that it feels like the long slow death of Firefox has begun...

there might be more evidence to suggest that the long slow death of linux has begun.


i find epiphany faster than firefox and always have, but i don't use it because i can't stand anything else about it. so, i vote "i hope not", as well.

edit: forgot the "won't it come with konqueror once it switches all the way over to kde?" part.

---

### Post by johnbunag on 2009-08-22
i hope it doesnt. FF is a good browser. easy to use. and quick.

---

### Post by Mark76 on 2009-08-22
> **steeleyuk said:**
> On a personal level I'd prefer to see Midori chosen, seems to have seen more development in recent months.


That's because it's been adopted as the default browser of the xfce desktop.

---

### Post by NCLI on 2009-08-22
> **chucky chuckaluck said:**
> i don't know. is google bigger than apple Yes > and are they worse?No.

---

### Post by SunnyRabbiera on 2009-08-22
I hope not, as firefox has a lot of good extensions for it I like.
What we really need is our own browser that is compatible with firefox extensions, but not depending on mozilla.

---

### Post by Regenweald on 2009-08-22
I'd much prefer to see Epiphany or Chromium. Sure they need lots of work, but plugins can be written, can't they ? It's not as if firefox has patented browser plugins. As newer browsers gain popularity the plugins will start coming in.

With the inroads that firefox is making into the windows market, we may see less linux development or 'just enough' to keep them happy. That is not the kind of development we need. FF is an amazing browser, but it provides me nothing that Epiphany, Chromium and even Opera provide faster. I guess you can tell i'm not add-on dependent :)

---

### Post by K.Y.A on 2009-08-22
If Firefox gets to the point where it is unusable on Linux, I'm sure the Ubuntu devs will make sure it does. Even if they have to make their own.

I see this more likely happening than switching to something else.

---

### Post by Dullstar on 2009-08-24
It had better not be an IE8, then.

I swear there's a conspiracy if only because I was watching him use Windows 7, and he was having trouble getting to the Firefox website.  So I run over to my main (Linux) machine and go the the Firefox site, and it's up and running.  Suspicious suspicious.

I'm giving the same response I give to KDE replacing GNOME as a default DE:

If they replace it, I download Firefox.  From the repositories if possible just so I don't have to use a browser I have never heard anything about.
I was not pleased that Kubuntu uses Konqueror...  for similar reasons.

And for the replacing GNOME with KDE?
First thing I do is install GNOME!

---

### Post by AmyRose on 2009-08-24
I don't think so, especially now that with 3.5, it's become as fast as Opera. Speed was my main issue with Firefox before 3.5 came out.

---

### Post by starcannon on 2009-08-24
If Ubuntu were to drop FF, I'd just install it from synaptic; so, either way, I'm good with whatever Canonical wants to do on the issue. I do think it would not be the greatest idea to dump FF in the default install/liveCD, but it's not a deal killer for me, it's easy enough to add it from the repo's.

---

### Post by Ubu2009 on 2009-08-24
I hope NOT. Other alternatives like Chrome are good browsers but the reason I like Firefox the most is because of my dependence on add-ons. A Browser without a variety of add-ons is a no use to me.

---

### Post by dandis on 2009-08-25
After Chrome showed me what Webkit can do I am in the process of ditching Firefox. Adblocking is not done at browser level only; there are much more powerful techniques such as HOSTS files, local proxies with custom filters etc.

Chrome is actually SO fast that I can ignore most of the lack of FF plugins I used to use. How could I go back to waiting almost 10 seconds for Firefox to start-up, when Chrome is launched almost instantaneously?

---

### Post by MasterNetra on 2009-08-25
> **Dullstar said:**
> It had better not be an IE8, then.

I swear there's a conspiracy if only because I was watching him use Windows 7, and he was having trouble getting to the Firefox website.  So I run over to my main (Linux) machine and go the the Firefox site, and it's up and running.  Suspicious suspicious.

I'm giving the same response I give to KDE replacing GNOME as a default DE:

If they replace it, I download Firefox.  From the repositories if possible just so I don't have to use a browser I have never heard anything about.
I was not pleased that Kubuntu uses Konqueror...  for similar reasons.

And for the replacing GNOME with KDE?
First thing I do is install GNOME!

I'm testing Windows 7 right now and I have no problem with getting to firefox's website, I can even download it fine. At least M$ plays better with others then Apple does. >.>

---

### Post by Dullstar on 2009-08-25
He MANAGED to do it...  maybe it was downtime, but the timing was awfully fishy.

---

### Post by Dullstar on 2009-08-25
Why?  I accessed the site on Ubuntu.

---

### Post by TheNosh on 2009-08-25
i don't much care if Ubuntu drops firefox, i myself dropped it for Opera when i was using puppy linux, before i had Ubuntu. and even if if stops coming with the default Ubuntu install it won't be hard to download anyway.

also my recent decision to switch to Arch makes me even less concerned with Ubuntu's choices.

The important thing to remember is that default apps don't matter. you can install whatever you want.

---

### Post by coldReactive on 2009-08-25
> **TheNosh said:**
> i don't much care if Ubuntu drops firefox, i myself dropped it for Opera when i was using puppy linux, before i had Ubuntu. and even if if stops coming with the default Ubuntu install it won't be hard to download anyway.

It's possible that once they drop it as a default app, it won't be updated in the repos anymore, and we'll all be stuck with an old version, or rely on a PPA version. I don't like this at all.

---

### Post by TheNosh on 2009-08-25
> **coldReactive said:**
> It's possible that once they drop it as a default app, it won't be updated in the repos anymore, and we'll all be stuck with an old version, or rely on a PPA version. I don't like this at all.

if it gets removed from the repos (which i doubt would happen anyway) it would likely get added to getdeb.net

---

### Post by coldReactive on 2009-08-25
> **TheNosh said:**
> if it gets removed from the repos (which i doubt would happen anyway) it would likely get added to getdeb.net

I didn't say it would get removed from the repos. I said that *"It's possible that once they drop it as a default app, it won't be **_updated_** in the repos anymore"*

And when I mean updated, I mean that when a new version comes out, the repo version gets updated.

---

### Post by TheNosh on 2009-08-25
> **coldReactive said:**
> I didn't say it would get removed from the repos. I said that *"It's possible that once they drop it as a default app, it won't be **_updated_** in the repos anymore"*

i still think the newer version would end up on getdeb.net.

---

### Post by coldReactive on 2009-08-25
> **TheNosh said:**
> i still think the newer version would end up on getdeb.net.

If you ask me, that wouldn't make a whole lot of sense.

---

### Post by TheNosh on 2009-08-25
> **coldReactive said:**
> If you ask me, that wouldn't make a whole lot of sense.

why? there are other programs that are in the repos but have newer versions on getdeb. 

also, worst case scenario (very unlikely in my opinion) is that it's outdated in the repos and not put on getdeb. in that case it could still be downloaded from it's website and compiled.

---

### Post by coldReactive on 2009-08-25
> **TheNosh said:**
> why? there are other programs that are in the repos but have newer versions on getdeb. 

also, worst case scenario (very unlikely in my opinion) is that it's outdated in the repos and not put on getdeb. in that case it could still be downloaded from it's website and ***compiled***.

That will be when that app is never used by me again. Compiling IMO, is annoying.

---

### Post by TheNosh on 2009-08-25
> **coldReactive said:**
> That will be when that app is never used by me again. Compiling IMO, is annoying.

it's certainly not my preferred method of installation, but if firfox was something i thought was really important (personally i don't use it anyway) it wouldn't be a deal breaker.

---

### Post by -grubby on 2009-08-25
I cannot think of one good reason that Ubuntu would stop updating Firefox in the repos if it ever stopped being the default. Plus, I don't even think that you have to compile the upstream version of Firefox - I believe it is a directory with a binary in it.

EDIT: I just checked Firefox for Linux from Mozilla. Turns out that, yes, it does not require compilation.

---

### Post by TheNosh on 2009-08-25
> **-grubby said:**
> I cannot think of one good reason that Ubuntu would stop updating Firefox in the repos if it ever stopped being the default. 
agreed

> Plus, I don't even think that you have to compile the upstream version of Firefox - I believe it is a directory with a binary in it.

i had not realized this. if thats true this is even less of an issue than i thought.

---

### Post by nortexoid on 2009-10-22
> **steeleyuk said:**
> On a personal level I'd prefer to see Midori chosen, seems to have seen more development in recent months.


Are you serious? Midori (0.2.0) is not in any position at the moment to dethrone any of the familiar gnome browsers, especially Firefox. For one, it doesn't work with any google services (yes, you can change the user agent to Safari to get it to work with gmail, but nothing can be done to get it to work with gcal and probably other services I haven't tried) and it crashes several times a day when I use it. It's a great little browser, but certainly not something that should be the default browser for Ubuntu, unless people like broken things by default.

The lastest Epiphany is nice, but it's still got issues too, especially with mime type handling. Using mozplugger, most of the time it can't open a pdf even though it properly calls up the pdf reader to fill the browser. And there's no transparent way of disabling webkit plugins. It's pretty lame.

---

### Post by hoppipolla on 2009-10-22
I don't actually know if UBUNTU will drop Firefox anytime too soon, but I think that unless something special comes out of 4.0 we may see Firefox's market share tumble particularly due to Chrome (and the movement of new browsers that is surrounding it).

We'll have to wait and see :)

I used to love FF, but I have my gripes with it these days.

I don't know whether Epiphany will be the choice though o.O

---

### Post by coldReactive on 2009-10-22
> **hoppipolla said:**
> I don't actually know if UBUNTU will drop Firefox anytime too soon, but I think that unless something special comes out of 4.0 we may see Firefox's market share tumble particularly due to Chrome (and the movement of new browsers that is surrounding it).

We'll have to wait and see :)

It's inevitable, chrome will take over. As much as I extremely LOATHE that. I'll have to stay with firefox forever, due to the various functions I need from it (this includes NoScript, which the other browsers do not have. No matter what you say, there is no alternative to NoScript for me, it's NOT like Adblock or Flashblock at all!)

---

### Post by Mike_IronFist on 2009-10-22
> **nomnomnom said:**
> Now that it feels like the long slow death of Firefox has begun, do you think that it's dominance in the Linux browser wars is about to end as Webkit becomes the new standard?

Personally I prefer Firefox to every other Webkit browser besides Epiphany. Firefox 3.5 is only just behind Google Chrome for speed in my experience.

Absolutely not, Firefox is the most popular Open Source software ever coded, and its user base is growing every day, regardless of its performance regressions. Canonical wouldn't want to promote their software's open source nature and leave out the biggest Open Source success story out of the picture.

Long slow death? Firefox might not be the speed demon it should be anymore, but as far as usage goes, it's growing like wildfire.

---

### Post by samjh on 2009-10-22
> **nomnomnom said:**
> Now that it feels like the long slow death of Firefox has begun, do you think that it's dominance in the Linux browser wars is about to end as Webkit becomes the new standard?

Firefox isn't dying.  It's the most successful open-source web browser in the world, and the most recognised alternative to Internet Explorer.

Just look at these:
[w3schools.com browser statistics]("http://www.w3schools.com/browsers/browsers_stats.asp")
[linuxquestions.org 2009 Browser of the Year]("http://www.linuxquestions.org/questions/2008-linuxquestions.org-members-choice-awards-83/browser-of-the-year-695619/")

If your reference is to the rendering engine, then I think WebKit will become dominant.  But that is not to say that Firefox as a whole product will die.  It is entirely possible that Firefox could be rewritten to use WebKit if such a drastic measure will become necessary for Firefox to remain competitive.

---

### Post by hoppipolla on 2009-10-23
> **Mike_IronFist said:**
> Absolutely not, Firefox is the most popular Open Source software ever coded, and its user base is growing every day, regardless of its performance regressions. Canonical wouldn't want to promote their software's open source nature and leave out the biggest Open Source success story out of the picture.

Long slow death? Firefox might not be the speed demon it should be anymore, but as far as usage goes, it's growing like wildfire.

That's funny, so many people don't seem to see the connection between QUALITY (in the areas people care about and see) and potential success. Firefox has been around much longer than Chrome so of COURSE it's got a bigger market share. It's insane to claim that's indicative of it's quality relative to Chrome. Yes Firefox is a pretty good browser and I think it will stick around to some extent, but pretending it will always be huge or that it's current success ensures success in the future is like sticking your fingers in your ears!

---

### Post by DJ_Peng on 2009-11-07
> **nortexoid said:**
> The lastest Epiphany is nice, but it's still got issues too, especially with mime type handling. Using mozplugger, most of the time it can't open a pdf even though it properly calls up the pdf reader to fill the browser. And there's no transparent way of disabling webkit plugins. It's pretty lame.
This is one of my biggest problems with Epiphany in Karmic. I have to specifically download a PDF file then open it from a local folder just to be able to view it. The same happens with tarballs and DEB's. I miss the option to download and immediately open files that we had with the Gecko version of Epiphany. It's almost enough to make me want to switch to using Chromium as my default browser since at least there I have a little more ease of use. I can even set up three URI's to be my start page in Chromium. In Epiphany? Nope, not yet. I could go back to Firefox, but I specifically stopped using it last year and I really don't want to have to go back to using that bloated piece of code and their disregard for how people have been using the browser for several years.

---

### Post by Digikid on 2009-11-07
No.  They would be stupid to support a browser that has Spyware built into it like Chrome has.

---

### Post by clevin on 2009-11-07
I agree in all my previous tryouts of Ubuntu, the firefox has been NOT nice.

However, in 9.10, its very nice, and never have any problem so far, responsive, quick, and powerful.

I think its unwise for Ubuntu to drop firefox, although it sure can install epiphany side by side by default, but still leave firefox as default browser.

Epiphany is a fine browser, but not good enough.

Ubuntu sure has the obligations to help OSS community, but remember

1. Mozilla is part of OSS as well. and much more successful than gnome, why should OSS community try to kill each other off and then just left control freaks like apple or MS happy?

2. Ubuntu also has a much bigger responsibility to push Linux as a platform, to encourage significant number of windows users to switch, don't you think a familiar browser experience will help a great deal?

Chromeor Epiphany is fine in the world of Linux experts or forever forward looking tech crowd. But there is no reason to lose sight of the long term future of Linux.

Its also unwise to write off the creativity and community of Mozilla, the significant improvement since firefox 2 is a clear evidence of that.

---

### Post by nortexoid on 2009-11-07
> **DJ_Peng said:**
> This is one of my biggest problems with Epiphany in Karmic. I have to specifically download a PDF file then open it from a local folder just to be able to view it. The same happens with tarballs and DEB's. I miss the option to download and immediately open files that we had with the Gecko version of Epiphany. It's almost enough to make me want to switch to using Chromium as my default browser since at least there I have a little more ease of use. I can even set up three URI's to be my start page in Chromium. In Epiphany? Nope, not yet. I could go back to Firefox, but I specifically stopped using it last year and I really don't want to have to go back to using that bloated piece of code and their disregard for how people have been using the browser for several years.

So why not just stick with epiphany-gecko for now? Yeah, they've stopped developing for it, but it's in a pretty good state at present, at least until the webkit version is brought up to speed.

---

### Post by DJ_Peng on 2009-11-07
I would but it's no longer available in karmic. I might be able to build it myself but I'd rather not have too many apps from source rather than from packages. Believe me, I wish I could still use the gecko version. :(

---

### Post by The Funkbomb on 2009-11-07
Firefox is the posterchild of open source.

I cannot think of one other Open Source program that gained so much momentum so quickly.

---

### Post by gnomeuser on 2009-11-07
> **Digikid said:**
> No.  They would be stupid to support a browser that has Spyware built into it like Chrome has.

Spyware? Everything in Chromium that sends data back deals with things such as spyware protection, anti phishing, domain name and search completion. These are all opt out, you lose functionality but you can enjoy a completely call home free computing experience. Chrome the Google product does send what they call a RLZ for interesting events such as searches done via the omnibar but this is not part of Chromium (which is what distributions are likely to ship since this they are free to distribute and compile as they like).

spyware.. back your claims with evidence please.

---


---
title: "safari is BLAZING FAST!!!!!!!!!!`"
date: 2008-03-26
forum: Other OS Talk
---

### Post by jrharvey on 2008-03-26
I just installed the windows version of safari with WINE and it is soooooo fast. I definitely recommend it if you like instant page loading.

---

### Post by Joeb454 on 2008-03-26
Have you tried Firefox 3 yet?

---

### Post by jrharvey on 2008-03-26
have not. Is it good too? is it on linux yet?

---

### Post by -grubby on 2008-03-26
Well I like Opera myself. The last time I tried Safari I hated it (and it was a recent version)

---

### Post by -grubby on 2008-03-26
> **jrharvey said:**
> have not. Is it good too? is it on linux yet?

Firefox 3 has been on Linux from the beginning..Personally I like it more than Firefox 2

---

### Post by jrharvey on 2008-03-26
> **nathangrubb said:**
> Firefox 3 has been on Linux from the beginning..Personally I like it more than Firefox 2

But is it faster? that is the important question. I dont like safari as much as firefox either but it is just so amazingly fast.

---

### Post by SunnyRabbiera on 2008-03-26
so safari works on wine now?
edit: so it does, too bad itunes isn't having as much luck.

---

### Post by Mr. Picklesworth on 2008-03-26
Epiphany with Firefox 3's new engine (as seen in Hardy Heron) is a bit closer to Safari, and it is truly blazing fast! :)

---

### Post by jrharvey on 2008-03-26
I do regret to inform that i ran into my first problem using safari in WINE. :( As blazing fast as it is, I cannot log into my iGoogle account or Gmail. Im not sure what the problem is but its not a safari issue, its a WINE issue i believe. Oh well. SO nobody answered my question. Is firefox 3 faster than firefox 2?

---

### Post by hhhhhx on 2008-03-26
> **jrharvey said:**
> I do regret to inform that i ran into my first problem using safari in WINE. :( As blazing fast as it is, I cannot log into my iGoogle account or Gmail. Im not sure what the problem is but its not a safari issue, its a WINE issue i believe. Oh well. SO nobody answered my question. Is firefox 3 faster than firefox 2?
much much much faster!

---

### Post by scragar on 2008-03-26
yes, it's far faster, it uses less ram as well.

---

### Post by KiwiNZ on 2008-03-27
May want to look at this 
 
[http://www.webuser.co.uk/news/199844.html](http://www.webuser.co.uk/news/199844.html)

---

### Post by Joeb454 on 2008-03-27
And it doesn't crash as much...even though Firefox 3 is still in Beta, for me personally, it's already FAR more stable than Firefox 2 has ever been :)

I've been using Firefox 3 since beta 1 (had Gran Paradiso installed for a while before that too)

EDIT:

Just read the article KiwiNZ posted, and read this: > Safari browser for Windows 3.1 does that mean Safari, for Windows 3.1 (i.e. < Win 95) **OR** Safari 3.1, for Windows (XP/Vista) ;)

---

### Post by scragar on 2008-03-27
have you got safari to stop when you close it? or does the process keep running for you as well?

---

### Post by jrharvey on 2008-03-27
OK so i just installed the linux version of firefox 3 and it is MUCH Faster than V2. Thanks guys, i had no idea. I was always soooo disappointed in the speed of firefox 2 for linux that i rarely ever used it even though its my favorite on OSX and Windows. Although its not as instantaneous as safari when loading huge websites its pretty close. This is good enough for me. Im glad i discovered this today, ive never been one to use beta or alpha versions of anything.

---

### Post by jrharvey on 2008-03-27
> **scragar said:**
> have you got safari to stop when you close it? or does the process keep running for you as well?

it closes for me.

---

### Post by O3. on 2008-03-27
Firefox 3 Beta 4 is faster than safari_in_wine.

---

### Post by k2t0f12d on 2008-03-27
Unless remote servers and/or your ISP can detect your browser's branding and selectively throttle bandwidth on that determination alone, the amount of time it takes for data to get from there to you is a constant.  The speed of the browser is primarily in its rendering engine. Try using Kazehakase:

```
sudo apt-get install kazehakase
```
and see if you notice a visible difference.

---

### Post by scragar on 2008-03-27
> **jrharvey said:**
> it closes for me.

```
ps -A | grep .exe
```check again :P


think your missing the word install:
```
sudo apt-get **install** kazehakase
```

---

### Post by p_quarles on 2008-03-27
> **k2t0f12d said:**
> Unless remote servers and/or your ISP can detect your browser's branding and selectively throttle bandwidth on that determination alone, the amount of time it takes for data to get from there to you is a constant.  The speed of the browser is primarily in its rendering engine. Try using Kazehakase:

```
sudo apt-get install kazehakase
```
and see if you notice a visible difference.
Kazehakase uses Firefox 2's Gecko engine, which is the slowest of any of the currently available engines. Safari uses Webkit, which certainly is faster. For native Linux apps using Webkit, the choices are Epiphany's development branch and Midori. Konqueror's KHTML is similar to Webkit (they share a good deal of code base), and then there's Opera, which also has a very efficient rendering engine.

---

### Post by scragar on 2008-03-27
> **p_quarles said:**
> and then there's Opera, which also has a very efficient rendering engine.

also known as Presto, always makes me think of some sort of magian really...:P

---

### Post by LeoSolaris on 2008-03-27
I picked up swiftfox, which is a tweak of firefox 3 made just for Linux users. I tested out the firefox 3 in the repos, and swiftfox is a bit faster in rendering.

I decided to add it as a repo rather than having to check back with them ever so often. The swiftfox devs are only a little behind the firefox devs, so I am on beta 5 rather than 4 like the Ubuntu repos. 

You guys can get it [here]("http://www.getswiftfox.com"). 

Leo

---

### Post by jrharvey on 2008-03-27
So swiftfox is optimized for linux? Is that kinda like camino for OSX?

---

### Post by scragar on 2008-03-27
firefox has always been slightly more optimised for linux than windows/OSX, swiftfox takes that 1 step futher and optimises it to your processor type.

---

### Post by jrharvey on 2008-03-27
i noticed that there was not an option for core 2 duo so i downloaded the core duo version. I wonder if that is a problem because the core 2 is 64 bit.

---

### Post by blu3ness on 2008-03-27
Maybe you never have the need for this, but try to visit a foreign language site with safari windows. It's ******* horrible. If you consider using wine to emulate windos api, then safari internal mac osx proprietary code to emulate mac osx font rendering, you might as well just go with elinks and feel a million times faster, I'd rather not jump through that many hoops just to get a browser to be "fast".

---

### Post by k2t0f12d on 2008-03-27
> **p_quarles said:**
> Kazehakase uses Firefox 2's Gecko engine

[It doesn't *have* to]("http://ubuntuforums.org/showpost.php?p=4595670&postcount=1")   :-s

---

### Post by djbsteart1 on 2008-03-27
I found that in windows/OSX safari was unstable and very slow at anything with flash and java well in general. Rifefox was always faster for me, but gran paradiso wasn't liked by Bill leading to blue screen so I cannot comment on it as i havnt installed it on Mandy yet. 
As for opera, it is horrible, slow and crashes constantly, it cannot handle more that 20 tabs, where firefox is fine with that many.

---

### Post by TenPlus1 on 2008-03-27
I'm using the latest beta of Opera 9.50, and that's fast :)  even used the latest flash...

---

### Post by Tomatz on 2008-03-27
Isn't safari based on konquror?

---

### Post by MONODA on 2008-03-27
> Isn't safari based on konquror?
i think they juste have the same base, otherwise safari would have to be GPL compliant.

---

### Post by Whiffle on 2008-03-27
Safari uses Webkit, Webkit is a fork of KHTML, and KHTML is konqueror's rendering engine (which is also quite fast )

---

### Post by jrharvey on 2008-03-27
Yes, the latest version of konquerer is also fast but i just cant bring myself to use it. Kinda like i just dont like epiphany, even though it also uses webkit i believe. Safari on linux was cool for about a day but i think Firefox 3 is what i will stick with. It is fast enough for what i need but i cannot seem to use flash with it as i am using 64bit ubuntu. I had it working in firefox 2 but cannot figure it out with ff3. Its not that big of a deal because if i really wanted to i could go back to 2 and use flash.

---

### Post by baumgc on 2008-03-27
Try webkit.

Prepare to have your mind BLOWN!

---

### Post by justin whitaker on 2008-03-27
I never understood the need for speed with browsers.

I can understand the need for fast downloads, particularly if you are downloading multiple items, but in terms of rendering pages...what difference does a few microseconds make? 

Now, if you are saying: I don't want a browser causing a throughput problem with my browsing experience...that I get. But if that were the case, wouldn't we all be using Elinks, or some other console based Browser?

---

### Post by scragar on 2008-03-27
those few secs are the difference between seeing a page and giving up waiting for it on a lot of badly designed sites, and nothing is worse than attempting to click a link, only for the page to suddenly dive 200px to the left to make room for someother content that the browser is only just now starting to parse. Ask anyone who's used IE7 on an old computer, sometimes it actualy uses so much power that it's impossible for it to even show anything until it's done, and if it takes 10+ secs to finish that's 10+ secs I'm waiting for no good reason.

---

### Post by p_quarles on 2008-03-27
> **justin whitaker said:**
> I never understood the need for speed with browsers.

I can understand the need for fast downloads, particularly if you are downloading multiple items, but in terms of rendering pages...what difference does a few microseconds make? 

Now, if you are saying: I don't want a browser causing a throughput problem with my browsing experience...that I get. But if that were the case, wouldn't we all be using Elinks, or some other console based Browser?
The difference is trivial with many pages, but noticeable with larger and more complex ones, to the point where it can be a pain to wait for a page to finish rendering. Shaving time off of those tasks is most welcome. 

Moreover, part of the issue is with efficient rendering. One of the complaints about Gecko is that it hogs system resources. This, in turn, can make other applications less responsive, shorten battery life, etc., etc. Basically, using the minimal resources needed to accomplish the task needed is always a good thing. As you said, though, there are many use cases in which it would be pointless to concern oneself over the differences.

---

### Post by jrharvey on 2008-03-27
> **justin whitaker said:**
> I never understood the need for speed with browsers.

I can understand the need for fast downloads, particularly if you are downloading multiple items, but in terms of rendering pages...what difference does a few microseconds make? 

Now, if you are saying: I don't want a browser causing a throughput problem with my browsing experience...that I get. But if that were the case, wouldn't we all be using Elinks, or some other console based Browser?

Ok lets take a simple page such as iGoogle. In firefox 2 it really took about 12 seconds to render my page, i counted  (thats gmail, weather, news, all that jazz.) When i used Safari 3 (w/ webkit) it rendered the entire page imediately (about 1 second). Thats a HUGE difference in speed when you are constantly on the internet. If your work requires you to do alot of browsing then that is a big boost in productivity. Now that I have tried firefox 3 beta i really like it because it seems to be fairly close to the speed of safari 3.

---


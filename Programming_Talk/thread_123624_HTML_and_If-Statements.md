---
title: "HTML and If-Statements"
date: 2006-01-30
forum: Programming Talk
---

### Post by audax321 on 2006-01-30
Hello,

I'm working on a website and I need to put in some code that determines what javascript menu to load. Basically it needs to be something like this:

if browser is firefox 1.0.7 or less then
  LOAD MENU#1
else
  LOAD MENU#2
end if

Secondly, I need to determine if a browser is internet explorer or not as follows:

if browser is not IE then
  then use this code
end if


How can I achieve this in HTML???

---

### Post by anthro398 on 2006-01-30
HTML doesn't allow for that.  You'll have to use javascript or a cgi include written in Python, Perl, Java, etc.

---

### Post by audax321 on 2006-01-30
Alright, thats fine. How would I do it with javascript then. :)

---

### Post by quonsar on 2006-01-30
point your browser to [www.google.com](www.google.com). search "browser sniffing javascript". or just plain "javascript". then go to one of the hundreds of sites that will come up. there will be numerous examples, explanations and free code snippets. use the force, luke.

---

### Post by audax321 on 2006-01-30
[QUOTE=quonsar]point your browser to [www.google.com](www.google.com). search "browser sniffing javascript". or just plain "javascript". then go to one of the hundreds of sites that will come up. there will be numerous examples, explanations and free code snippets. use the force, luke.[/QUOTE]

Thanks, I tried searching before but all I could find was navigatorisIE crap and I didn't know how to check version numbers. But, browser sniffing javascript seems to have brought up some good results.. :)  I'll check it out tomorrow and see if I can get this working.

---

### Post by exclipy on 2006-01-30
For filtering out/in IE, look up IE Conditional Comments.  For other browsers, you'll have to use a javascript sniffer.

---

### Post by audax321 on 2006-01-31
Well that was a nice disappointment. :) Apparantly Firefox 1.x.x browsers report themselves as Netscape version 5 using navigator.appName and navigator.appVersion!!! So it makes my whole attempt useless. Oh well I'll just tell users to use Firefox 1.5. I guess the website just won't be compatible with older Firefox versions. Now the question is, why Netscape 5??? I thought Firefox had a larger market share that Netscape... seems kind of ridiculous to me.

BTW, this is the website I used: [http://www.webreference.com/js/column6/browser.html](http://www.webreference.com/js/column6/browser.html)

---

### Post by Koobi on 2006-01-31
i believe the right term for what you are trying to do is called ["Browser Sniffing"](http://en.wikipedia.org/wiki/Browser_Sniffing)

Netscape is a part of the User Agent for some versions of firefox but firefox can be distinguished from any other browser (unless the browser is being spoofed intentionally) by considering the entire User Agent.

i can't help you with JavaScript but i can give you a hand with PHP if you want.
you would have to use a 'regular expression' to match the different browsers, i can give you a hand with that as well.



:edit:
I forgot to mention that JavaScript isn't a foolproof method. if the user has JavaScript turned off in his browser, your browser sniffing wont work.


here is an example of what a user agent for firefox 1.5 on Ubuntu looks like:
```

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8) Gecko/20051111 Firefox/1.5

```

you can check yours out [here](http://www.koobi-studio.com/downloads/php/classes/KdirLister/info.php)

---

### Post by LordHunter317 on 2006-01-31
Browsing sniffing ruins the Internet.  Doing it means you're a rank amateur.

What specifically are you trying to accomplish?  Why different sites for different browsers?  Almost always, the errors in IE's rendering can be dealt with some patience and a little conditional CSS.

---

### Post by audax321 on 2006-02-01
The reason I was looking into using browser sniffing is NOT because I'm an amateur. I use a javascript menu on the website that I did not create. Unfortunately the latest version of Firefox needs to use the latest version of the menu and the older Firefox version no longer displays the latest version of the menu properly. So, I was going to use browser sniffing to see what version of the browser the user was using and load the appropriate menu. I know browser sniffing is bad and I've never had to use it until now, but in this situation there was not much choice... no amount of conditional CSS and patience was going to make the menu magically work since the menu itself broke compatibility... trust me I spent quite a bit of time on it. However, I checked the computers at school today and all of them were just upgraded to the latest Firefox, so I don't think I will have to worry about browser sniffing after all. At any rate I've mentioned the problem and told users to act accordingly. So far I haven't gotten any complaints and everything seems to be working great.

The internet explorer problem has already been corrected without sniffing.

So don't worry the internet hasn't been "ruined." :)

---

### Post by LordHunter317 on 2006-02-01
[QUOTE=audax321]The reason I was looking into using browser sniffing is NOT because I'm an amateur.[/quote]No, you don't get it.  If you seriously consider it, then you are one.  It's not ever a solution.

>  I use a javascript menu on the website that I did not create. Unfortunately the latest version of Firefox needs to use the latest version of the menu and the older Firefox version no longer displays the latest version of the menu properly.So fix the javascript.  If you're writing javascript that breaks on specific *versions of Firefox* (that's not part of an extension) then you have a problem.

---

### Post by another_dave_b on 2006-02-01
[QUOTE=LordHunter317]Browsing sniffing ruins the Internet.  Doing it means you're a rank amateur.

What specifically are you trying to accomplish?  Why different sites for different browsers?  Almost always, the errors in IE's rendering can be dealt with some patience and a little conditional CSS.[/QUOTE]
Different browsers have different bugs. Browser sniffing is both useful and necessary.

---

### Post by LordHunter317 on 2006-02-01
No, it isn't.  For CSS you can use conditional CSS, and that resolves nearly all issues.  There's maybe one situations where you might have to pull a CSS hack, but they're few and far between.

For Javascript, you detect *functionality*, not browsers.  You write your code to work with what mechanisms the browser says it has, and Javascript makes this trivially easy to do.  99% of the time, it's as easy as testing for the function's existance before calling it:```
if (window.SomeCoolFunction) {
  // Use window.SomeCoolFunction
} else {
  // Do it another way
}
```And so on.  Again, there might be one or two small cases where a detect is necessary (quirksmode.org shows one between IE and Opera), but they're all rare, small, usually unheard of corner-cases.

---

### Post by audax321 on 2006-02-01
[QUOTE=LordHunter317]No, you don't get it.  If you seriously consider it, then you are one.  It's not ever a solution.

So fix the javascript.  If you're writing javascript that breaks on specific *versions of Firefox* (that's not part of an extension) then you have a problem.[/QUOTE]

As I said before I didn't write the javascript for the menu and I'm not going to rewrite it over this bug. The browser sniffing is just allowing the visitors that go to the site with 1.0.7 to view the site... I don't view that as a bad thing. And if their browser is detected incorrectly, it would default to the new version of the menu which would simply display incorrectly as it is right now. It's only helping the situation, not hurting it. Its not as if I'm supporting IE's bad programming by making it work with my site (which is W3C compliant). As I said this is something wrong with the current version of the menu itself. Maybe it will be fixed in the future, or maybe it won't but this provides a temporary fix.

Now, if it makes you feel bigger to go on forums and call others amateurs then you have some serious issues. Try to place yourself in other people's shoes before you go off on a self-righteous rant about why everything should be done your way. Surprising as it is, there can be multiple solutions to one problem, and in this case wasting time rewriting a menu that might have a fix released next month is not a solution.

---

### Post by Koobi on 2006-02-01
i don't think anyone needs to get offended here over what someone called you. this is only the internet :)

i honestly believe that browser sniffing is useful but should be avoided as far as possible...but it that all depends on your target audience.

if you're building a site that will be accessed by a set of employees at a company, for example, and you know they use Browser A and Browser B only and your are required to use some fancy JS/CSS, then i suppose you can sniff for the browser.

i'd prefer to build a site to suit the lowest common denominator, i.e. a site that is compatible with all browsers with no browser sniffing needed.

---

### Post by audax321 on 2006-02-01
I agree, browser sniffing can be useful such as the position I'm in. I wasn't really getting offended, just amazed at the statement that even if someone considers this, they are an amateur. It just came across as narrow-minded to me. At any rate, I've emailed the developer about this issue between FF 1.0.7 and 1.5, so hopefully I can resolve this and move on.

---

### Post by Lord Illidan on 2006-02-01
[quote=audax321]I agree, browser sniffing can be useful such as the position I'm in. I wasn't really getting offended, just amazed at the statement that even if someone considers this, they are an amateur. It just came across as narrow-minded to me. At any rate, I've emailed the developer about this issue between FF 1.0.7 and 1.5, so hopefully I can resolve this and move on.[/quote]

In some cases, browser sniffing can do more harm than good, especially if the coder is a noob and has no idea about javascript. Usually the need for it can be resolved by good coding.
But when there is really a problem, like the one you are mentioning, then no, you are not an amateur.

---

### Post by LordHunter317 on 2006-02-01
> **audax321]As I said before I didn't write the javascript for the menu and I'm not going to rewrite it over this bug.[/quote]Then you're an amateur.  Period.  That's the correct solution, and you're not willing to do it, which isn't the mark of a professional.

> Maybe it will be fixed in the future, or maybe it won't but this provides a temporary fix.Unless the real fix is like 40 manhours worth of work, I don't buy placing a tempory fix in instead.

> Now, if it makes you feel bigger to go on forums and call others amateurs then you have some serious issues.I don't.  The point was to illustrate how useless of a techinque it is, and the fact that no properly trained professional does it, ever.  It doesn't work said:**
> Surprising as it is, there can be multiple solutions to one problem,Perhaps, but only a small subset are correct solutions.

---

### Post by LordHunter317 on 2006-02-01
[QUOTE=Koobi]if you're building a site that will be accessed by a set of employees at a company, for example, and you know they use Browser A and Browser B only and your are required to use some fancy JS/CSS, then i suppose you can sniff for the browser.[/quote]Which isn't writing forward-looking code and is sensless when then mechanism that provides future-looking code (functionality detects) is no harder to code than a browser detect.  All it changes is the contents of the if() conditional, and it's not hard to figure it out.

So even in that case, it makes no sense.

[quote=audax321]I agree, browser sniffing can be useful such as the position I'm in. I wasn't really getting offended, just amazed at the statement that even if someone considers this, they are an amateur. It just came across as narrow-minded to me. [/quote]People far smarter than you or I, like the author of quirksmode.org, say the same thing.

---

### Post by anthro398 on 2006-02-01
I agree.  If you write, or use (which is, I believe, what you said you're doing) some code that needs a sniffer to function correctly, then there is a problem.  Use it as you like.  I love to email people to tell them that their sites are broken.  In fact, I often change the user agent of my browser since it should never be necessary data and I prefer to be incognito.

---

### Post by audax321 on 2006-02-01
> 
I agree. If you write, or use (which is, I believe, what you said you're doing) some code that needs a sniffer to function correctly, then there is a problem. Use it as you like. I love to email people to tell them that their sites are broken. In fact, I often change the user agent of my browser since it should never be necessary data and I prefer to be incognito.


I'm amazed at how much of a big deal everybody is making out of this. I've used this applet for 3 years and have NEVER needed to sniff for a browser. And the one time I do everybody is complaining about bad code... well yeah there is some bad code in this release. But chances are it is just a bug, that needs to be ironed out like any other software. I wouldn't be surprised if they know about it and chose to support the higher version of Firefox for the time being because the older version definitely didn't work with 1.5 when it was released. Also, this menu was released immediately following 1.5's release so I wouldn't be surprised it that is what happened. Again, the sniffing was just a TEMPORARY fix until the java code was corrected. No need to get so uptight about it. And go ahead and tell me my site is broken. I'll email you back and tell you it's a temporary fix until I find a permanent solution.. then what ???

I'm getting tired of this going back and forth garbage about whether browser sniffing is good or bad. So here's my final opinion, and everyone is welcome to their own without it turning into an "I'm better than you" contest:

1. In emergency cases like mine where there is a potential bug that is under review and may be corrected I think there is nothing wrong with browser sniffing. The people who are messing with their user agent are going to get a messed up page either way until the bug is fixed so they can deal with it. At least it will work for others that need it. Again, this should only be temporary until the problem can be corrected. IF I GET AN EMAIL BACK FROM THE DEVELOPERS SAYING, TOUGH DEAL WITH IT... THEN I WILL SWITCH TO A DIFFERENT MENU... BUT ITS TOO EARLY TO DO SOMETHING CRAZY LIKE THAT. If I had all the time in the world, i'd try other menus but the website down-time needs to be taken into consideration...and well I don't have all the time in the world right now.

2. Wide spread browser sniffing, I agree, is bad especially with code you know is not maintained and has no hope of being corrected. It's only making excuses for bad programming.

So there, in my opinion, everyone here is right. I just have problems with statements like: it's ALWAYS bad... no, it has it's uses like in case #1 above... it just shouldn't be relied on forever.

And LordHunter317, CONGRATULATIONS you can program in JavaScript... you should build yourself a nice huge shrine and remind yourself of your professionalism daily. Well I can't. I have to rely on others to write it the large chunks of JS for me... as far as web developing my knowledge ends after HTML and CSS. Again, I just maintain a website for a non-profit organization at my school (THAT'S RIGHT I DON'T GET PAID FOR THIS). My job right now is to get the schedule and all the other info about events out to members as efficiently as possible. Because the school is running 100% FF 1.5 I have no other choice but to use the broken menu code for now. I just wanted to put in temporary compatibility for FF 1.0.7. As I said I emailed the developers to get a solution and am confident I'll get one. I've had problems in the past and they are very helpful.  As far as this amateur professional crap... I don't consider myself an amateur.. those are people that use MS Frontpage to make their sites. You're right, I'm not a professional. I'm just an average to above-average user who knows browser sniffing isn't the best thing to do but in this situation is a valid choice IN MY OPINION until a permanent fix is found... sorry, my goal in life right now is to finish my medical education not program perfect JavaScript. I leave that to the people that do it. It would do you well not to place judgement on people you know nothing about or don't understand their particular circumstances.

> People far smarter than you or I, like the author of quirksmode.org, say the same thing.

I'm sure the really really smart author at quirksmode.org probably was referring to using browser sniffing as a permanent measure as bad practice (in some cases, its temporary use can be effective). If not, then I think he is narrow-minded as well no matter how smart he is. I've met plently of really really smart dumb people in my life. Also, I don't think it fair to bring him into this without him being here to defend or offer his own opinion into this matter. But, while we're on the subject, you might want to actually go read quirksmode.org:

> A useful but often overrated JavaScript function is the browser detect. Sometimes you'll need to give specific instructions or load a new page in case the viewer uses, for instance, Netscape 3.

What I get from this is that the author agrees that browser detection is USEFUL, but shouldn't be overused and most likely not used as a permanent measure. He does mention at the bottom of the page on browser detection to avoid its use and I agree with that... I don't think me using browser detection for a few weeks while I find a permanent fix for the menu is wrong and I feel the author would agree with me. And according to your argument since the author is allegedly smarter than you or I, you shouldn't be allowed to have your own opinion???

This is a HUGE post and my last one on this thread. You can all argue amongst yourselves.

---

### Post by LordHunter317 on 2006-02-01
[QUOTE=audax321]I'm amazed at how much of a big deal everybody is making out of this. I've used this applet for 3 years and have NEVER needed to sniff for a browser.[/quote]**Then you shouldn't need to do it now**

Here's an obvious suggestion (so obvious that I shouldn't even have to mention it): if the new version doesnt' work, **then why not stay with the old one?**

>  But chances are it is just a bug, that needs to be ironed out like any other software.Right, so the solution isn't to hack around it unless necessary.

>  I wouldn't be surprised if they know about it and chose to support the higher version of Firefox for the time being because the older version definitely didn't work with 1.5 when it was released.That screams incompetence on their part to a very high degree.

> Again, the sniffing was just a TEMPORARY fix until the java code was corrected.So?  It's still a terribly poor fix.  It's not even a complete fix.

> 1. In emergency cases like mine where there is a potential bug that is under review and may be corrected I think there is nothing wrong with browser sniffing.But there is.  Here are the facts:[list][*]Browser sniffing is unreliable[*]It's no eaiser to implement than the functionality detects[/list]Given both of those facts, there's no rational reason to ever consider using a browser detect.  Even if you have no javascript skills, there are more reasonable courses of action: like going back to the old version (nothing gained, but nothing lost), or learning javascript (it's not a terribly complicated language unless you're using continuations).

> The people who are messing with their user agent are going to get a messed up page either way until the bug is fixed so they can deal with it.And if those two sets have an intersection that's non-empty?  

> IF I GET AN EMAIL BACK FROM THE DEVELOPERS SAYING, TOUGH DEAL WITH IT... THEN I WILL SWITCH TO A DIFFERENT MENU... BUT ITS TOO EARLY TO DO SOMETHING CRAZY LIKE THAT.See, I would have switched menus long ago -- Javascript menus aren't hard to write to support all browsers, so whatever they're doing that constantly breaking it screams incompetence.

> 2. Wide spread browser sniffing, I agree, is bad especially with code you know is not maintained and has no hope of being corrected. It's only making excuses for bad programming.Which is what you're apparently doing here.

>  Well I can't. I have to rely on others to write it the large chunks of JS for me...You seemed quite willing to write some JS here.  As a site administrator, you had other valid options that you should have exericsed first.  You should have emailed the developers about a regression before even posting here.  You should have considered (and probably should have) reverted to the old version.  Yes, FF 1.5 is still broken, but it was always broken, so you haven't regressed.

> Again, I just maintain a website for a non-profit organization at my school (THAT'S RIGHT I DON'T GET PAID FOR THIS).Wonderful, neither  do I for many jobs I do.  You can act professional regardless, and you're not.

> I'm just an average to above-average user who knows browser sniffing isn't the best thing to do but in this situation is a valid choice IN MY OPINION until a permanent fix is found...I'm not really sure that's true here, but had you explained all of this *initially*, you might have illicted a different response from me.  

Which is 99% of the problem here: you didn't describe the problem adequately.


> It would do you well not to place judgement on people you know nothing about or don't understand their particular circumstances.Solving the problem requires knowledge both of your skills and the circumstances surronding the problem.  If you don't give me adequate information about both, I must assume to recommend a solution at all.  



I'm sure the really really smart author at quirksmode.org probably was referring to using browser sniffing as a permanent measure as bad practice (in some cases, its temporary use can be effective). If not, then I think he is narrow-minded as well no matter how smart he is. I've met plently of really really smart dumb people in my life. Also, I don't think it fair to bring him into this without him being here to defend or offer his own opinion into this matter. 

> But, while we're on the subject, you might want to actually go read quirksmode.org:Where did you even find that?

>  And according to your argument since the author is allegedly smarter than you or I, you shouldn't be allowed to have your own opinion???No, that's a non-sequitur.  You tried to pull an appeal for authority, and so I made a proper one.

This is a HUGE post and my last one on this thread. You can all argue amongst yourselves.[/QUOTE]

---

### Post by LordHunter317 on 2006-02-01
Ahh, I found it:> [Browser Detect](http://www.quirksmode.org/js/detect.html)
A useful but often overrated JavaScript function is the browser detect. Sometimes you'll need to give specific instructions or load a new page in case the viewer uses, for instance, Netscape 3.

**If you're new to JavaScript, don't use this script.** Please read the object detection page first.(emphasis mine). **Next time, take the whole quote *in context.***[/quote]

---

### Post by Single on 2006-02-02
audax321, you don't need to bother really. 
Those that can't live without acting like an elite and getting the proper attention will most likely disappear themselves if they are ignored.

---


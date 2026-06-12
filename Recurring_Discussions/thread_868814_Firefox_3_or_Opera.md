---
title: "Firefox 3 or Opera"
date: 2008-07-24
forum: Recurring Discussions
---

### Post by Raistlin82 on 2008-07-24
Since my move to Ubuntu a couple of months ago I've found Firefox to be great, but since version 3 its been a downhill experience (with the browser not the OS - which is awesome!!) if anyone can help fix the problems i  have encountered please let me know or tell me pro's and cons of opera i'd really appreciate it!

---

### Post by bbqsandwich on 2008-07-24
> **Raistlin82 said:**
> If i have closed Firefox and then later want to open it again i get the error message - Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

Well, to kill the Firefox process, you can open a terminal and type

```
ps -e
```

You will see a list of processes. Find firefox, and look for the four-digit process number next to it. Then in a terminal type:

```
sudo kill ####
```

where #### is the process number. But that doesn't address your greater problem of performance issues.

Personally I prefer Firefox over Opera because some sites just don't work well in Opera. Also Firefox has great add-ons to customize it, like NoScript, Greasemonkey, Stylish, Firebug, etc.

---

### Post by Raistlin82 on 2008-07-24
Next time it happens i'll try your suggestions.... dont know why I didnt think of sudo kill, doh! Still a bit of an annoyance though.  Is it possible to downgrade to a pervious version of Firefox or is that just a bad idea?

---

### Post by KenBW2 on 2008-07-24
Opera is a little more bloated with extra features, but it has a lot of what I used in extensions OOTB. And it definitely processes JavaScript faster.

But FF is Open Source :)

---

### Post by SNuxoll on 2008-07-24
Hey, where's Epiphany in your list!

---

### Post by stevoo on 2008-07-24
i have to agree FF3 for ubuntu is bad. It used to be worse in  the beta hanging there for ever and have to  force shut it down. But it has been a bit better in the last release. 
What i have noticed is that usually if not all of the time, flash makes it hang or quits FF3. 
Unfortunately i found no solution to my problem, but perhaps it is because i am using flash 10 beta.

---

### Post by bbqsandwich on 2008-07-24
> **Raistlin82 said:**
> Next time it happens i'll try your suggestions.... dont know why I didnt think of sudo kill, doh! Still a bit of an annoyance though.  Is it possible to downgrade to a pervious version of Firefox or is that just a bad idea?

It is possible to downgrade but I would advise against it because the latest version has the latest patches against security threats.

But if you really want to do it, try one or both of the two sets of instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=770789](http://ubuntuforums.org/showthread.php?t=770789)

---

### Post by ice60 on 2008-07-24
opera is better then firefox, so you should use opera lol.

you can get the process id of firefox like this -
```
pidof firefox
```

and you can kill every process that has the name firefox in it with this command
```
pkill firefox
```
firefox should be the only program with firefox in it's name so you should be safe to just run that!!

opera is about as customisable as firefox, maybe more so, but no one seems to know about it, i don't know why???

---

### Post by tuxxy on 2008-07-24
Firefox performs better for me when its working flawlessly, Opera worked straight out of the box better though.

---

### Post by Raistlin82 on 2008-07-24
> **bbqsandwich said:**
> It is possible to downgrade but I would advise against it because the latest version has the latest patches against security threats.

But if you really want to do it, try one or both of the two sets of instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=770789](http://ubuntuforums.org/showthread.php?t=770789)

thats kinda what i figured, would rather stay up to date with all the security updates.  Anyone else have the mid-scroll hang on Firefox?

---

### Post by rockstarrem on 2008-07-24
I feel like Firefox is the better browser right now, the community helping it is bigger and you can get a ton of support for it. Mine works perfectly, but I DO love Opera as well, so I'm not a fanboy here. I just prefer Firefox.

---

### Post by pi.boy.travis on 2008-07-24
Opera might not be open source, but they aren't joking around when they call it the best browser on Earth!  Opera is the only closed source software I use.

---

### Post by Raistlin82 on 2008-07-24
> **SNuxoll said:**
> Hey, where's Epiphany in your list!

sorry, you can tell I'm a bit of a noob but not come across Epiphany! I'll have a look.  Still pretty tempted to give Opera a chance, me thinks its time to find some reviews


Edit: So... Just installed and downloaded Opera, first impressions... performance wise I've visited a few sites and had no hang whilst scrolling and everything looks as it should do, so thats better than Firefox.... I prefer the Firefox layout/controls, but I imagine that its just a case of getting to know a browser thats new to me.  Will keep both on for the time being whilst I decide which is best for me, or if its worth keeping both of them installed

---

### Post by Raistlin82 on 2008-07-24
Me Again!! Just had a question about Opera, is there any way to open a new tab without it popping up in front of the current one?  I looked in tools>preferences and the options there, but had no joy.  

With Firefox I can view a page, see a link on it, click open in new tab and carry on reading the  same page, with opera i click on new tab and the new tab opens up and i have to click back to the page i was reading, I know it sounds small but its really getting on my nerves!

---

### Post by aysiu on 2008-07-24
All right. Is this a support request or a "Which do you like better?" discussion?

I've moved some of these posts into [a new support thread](http://ubuntuforums.org/showthread.php?t=869132). The rest I've kept here for a "Which do you like better?" Recurring Discussion.

---

### Post by Raistlin82 on 2008-07-24
Good call, sorry!

---

### Post by Orlsend on 2008-07-24
I like FF Better.

Opera still ok though...

But remember Opera used have adds and suck the money out of People!

---

### Post by cardinals_fan on 2008-07-24
> **Orlsend said:**
> 
But remember Opera used have adds and suck the money out of People!
Do you have any evidence to back that up, or are you just spreading FUD?

---

### Post by aysiu on 2008-07-24
I voted Opera performs better, but I still prefer to use Firefox because of its tab behavior, find-as-you-type feature, and a few other things.

---

### Post by cardinals_fan on 2008-07-24
I'm actually using Kazehakase at the moment, but Opera is still MILES better than Firefox in my book.

---

### Post by Barrucadu on 2008-07-24
> **Raistlin82 said:**
> Me Again!! Just had a question about Opera, is there any way to open a new tab without it popping up in front of the current one?  I looked in tools>preferences and the options there, but had no joy.  

With Firefox I can view a page, see a link on it, click open in new tab and carry on reading the  same page, with opera i click on new tab and the new tab opens up and i have to click back to the page i was reading, I know it sounds small but its really getting on my nerves!

Middle click the link. Works in FF too, I think.

> **aysiu said:**
> I voted Opera performs better, but I still prefer to use Firefox because of its tab behavior, find-as-you-type feature, and a few other things.
You can change the tab behaviour in Opera, and to use a similar find-as-you-type feature, press '.' or ',' then begin typing.

---

### Post by markbuntu on 2008-07-24
Neither one of them works worth a crap without flash10b1.

---

### Post by scragar on 2008-07-24
I like firefox more, mostly because firefox is available on 64 bit without messing about, but also, because it's open source and offers tons of plugins.

PS, before compairing speed between firefox and opera be sure to disable plugins on firefox, otherwise it'll slow it down and it won't be a fair comparison.

Oh, and why is swiftfox not on your list, just because it's optimised firefox.

---

### Post by LaRoza on 2008-07-24
> **cardinals_fan said:**
> Do you have any evidence to back that up, or are you just spreading FUD?

Opera did have ads, a long time ago, and did have a cost (to get rid of them)

It has none of that now, and hasn't for a while...

---

### Post by scragar on 2008-07-24
> **LaRoza said:**
> Opera did have ads, a long time ago, and did have a cost (to get rid of them)

It has none of that now, and hasn't for a while...

it did look better with the advert though(strangely), the top menu was just so much better looking when it only took up half of the space(everything felt better placed). Of course the advert was a bit of an annoyance, if you were lucky though you could get chunks of time where no advert would display for some reason(since it always downloaded the adverts to display I'm assuming bad links or something similar).

---

### Post by dodle on 2008-07-24
I don't have a lot of experience with Opera, but I really liked Firefox until version 3 came out.  I still think it's a great browser, but it's very buggy on both of my Xubuntu machines.

---

### Post by aysiu on 2008-07-24
> **Barrucadu said:**
> 
You can change the tab behaviour in Opera Not to the behavior I want. Believe me--I've tried all three options. I often want to keep one tab open for later use and then work with the other tabs in the meantime. With Opera, no matter what setting I have (even "Cycle in tab order," which would seem the most logical one), closing any tab will keep bringing me back to this "open for later use" tab of mine.

---

### Post by mrgnash on 2008-07-25
Which performs better? Opera. Which do I like better? Firefox :P

---

### Post by Raistlin82 on 2008-07-25
> **aysiu said:**
> not to the behavior i want. Believe me--i've tried all three options. I often want to keep one tab open for later use and then work with the other tabs in the meantime. With opera, no matter what setting i have (even "cycle in tab order," which would seem the most logical one), closing any tab will keep bringing me back to this "open for later use" tab of mine.

+1

---

### Post by chickpea on 2008-07-27
> **Raistlin82 said:**
> Me Again!! Just had a question about Opera, is there any way to open a new tab without it popping up in front of the current one?  I looked in tools>preferences and the options there, but had no joy.  

With Firefox I can view a page, see a link on it, click open in new tab and carry on reading the  same page, with opera i click on new tab and the new tab opens up and i have to click back to the page i was reading, I know it sounds small but its really getting on my nerves!

you can do that by middle-clicking on a link, clicking on a link holding Shift + Ctrl, or right click > Open in Background Tab:)

---

### Post by chickpea on 2008-07-27
i choose Firefox3. i think it's improved performance so much that i don't have to be frustrated any more. and i haven't have good experiences on Opera9.5 so far. it's sometimes shown me weird rendering that when i go back to a page i read previously it shows it without any CSS styling and slower JavaScript execution than older versions. i'm sure i'm not using a beta version...

---

### Post by ellalan on 2008-08-08
Hi Barrucadu
Thanks for that tip about Find-as-you type for which I have been looking all over the place.

---

### Post by ooobuntooo on 2008-08-08
Please use Firefox instead of Opera. Opera is not open source and the Linux edition is not completley recognised as running on a Linux OS. It comes up as "unknown". You wouldn't want to be responsible for a miscount in the census would you?

---

### Post by ooobuntooo on 2008-08-08
> **Raistlin82 said:**
> +1

Hey Raistlin82, you live in Huddersfield? Awsome!
I used to live there before I moved to France! You a member of the Huddersfield Linux Users Group?

---

### Post by billgoldberg on 2008-08-08
I've used the new opera version for a while and it's great.

I'm back on FF3 though.

I found opera to be less stable than FF and it is a closed source program.

I do like the speed dial funtion and their tabs management.

---

### Post by Barrucadu on 2008-08-08
> **ooobuntooo said:**
> Please use Firefox instead of Opera. Opera is not open source and the Linux edition is not completley recognised as running on a Linux OS. It comes up as "unknown". You wouldn't want to be responsible for a miscount in the census would you?

Completely untrue, here is my user agent:
> Opera/9.51 (X11; Linux x86_64; U; en)

---

### Post by cardinals_fan on 2008-08-08
> **ooobuntooo said:**
> Please use Firefox instead of Opera. Opera is not open source and the Linux edition is not completley recognised as running on a Linux OS. It comes up as "unknown". You wouldn't want to be responsible for a miscount in the census would you?
Not only is this completely false, I couldn't care less about a miscount in "the census".

---

### Post by Canis familiaris on 2008-08-08
> **cardinals_fan said:**
> not only is this completely false, i couldn't care less about a miscount in "the census".

+1

---

### Post by Raistlin82 on 2008-08-09
> **ooobuntooo said:**
> Hey Raistlin82, you live in Huddersfield? Awsome!
I used to live there before I moved to France! You a member of the Huddersfield Linux Users Group?

Hi there, no not a member of the group only a newcomer to the world of linux! Did you study at the Uni?

---

### Post by ooobuntooo on 2008-08-11
> **Raistlin82 said:**
> Hi there, no not a member of the group only a newcomer to the world of linux! Did you study at the Uni?

Nah, I never went to uni. I went to New College for a couple of years.

---

### Post by TheSlipstream on 2008-08-13
I was an Opera user for a year or so, back in the Windows days. I use Firefox now, and the only things I really miss -- Speed dial and IRC inbuilt -- I have Add-Ons for. I just see Firefox as more customizable, plus it has GTK support. 

I like to stand behind one of the great open source giants anyway, Firefox probably has easily the most users of any open source software, and is taking on IE.

I don't like that Opera is closed source that much, but it's certainly a very nice browser, but I just love all my FF plugins. ;)

---

### Post by null byte on 2008-08-13
Firefox 3. 

Stable, fast and secure. 

I find Opera not so "solid".

Also, I like Firefox's design more than Opera's.

---

### Post by Ozor Mox on 2008-08-13
I try to use free software where possible, and I like Firefox, so I stick with that.

---


---
title: "Can't watch Heroes on www.nbc.com"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by tysonh on 2008-10-21
I don't seem to have a problem watching any other online videos including youtube. For some reason I can't watch Heroes episodes online at nbc.com.  Anyone have any idea's?  Both my firefox and flash plugin are the most up to date.

---

### Post by EXCiD3 on 2008-10-21
Does yours look like its loading but then do nothing? I had the same problem with their player when i went to watch Chuck.

---

### Post by eternalnewbee on 2008-10-21
Hi there,
A simple explanation could be that the server can't handle the traffic. But I'm really just guessing.

---

### Post by Thelasko on 2008-10-21
Did you try Hulu?  Do you have Ad-Block Plus enabled?  I've never used nbc.com but Hulu won't play video with ABP enabled.  You can select "disable on hulu.com" from the ABP menu to disable it for that site only.

---

### Post by Wicked-Cricket on 2008-10-21
I have the same issue on the Fox, CNN and a number of others. Youtube and simple flash sites work for me as well so I'm not sure what the deal is. I already upgraded to Flash 10 which solved some issues (like Firefox closing due to certain embedded flash). Lets figure this out!

---

### Post by Archmage on 2008-10-21
Keep in mind that you must live in the US to see the episodes on [www.nbc.com](www.nbc.com).

---

### Post by M4rotku on 2008-10-21
I have to boot into windows to view Chuck on nbc.com as well.  I think it might have something to do with the online episodes being sponsored by Windows.  So, I think they would have it set up so that you can only view it in Windows.

It has nothing to do with the traffic.  I didn't have any problems once I booted into Windows.

---

### Post by VorDesigns on 2008-10-21
More guessing; I was able to watch the first presidential debate on CNN via FF on Ubuntu but I was unable to watch the second debate.
Based on that, my guess is that some component fork has been orphaned or an accessory application is no longer properly associated.
I can't watch Life on NBC.com but I have few issues with other sites.
Additionally, the java based pcAnywhere client that I got to run late last year by reinstalling java with FireFox on Gutsy worked without manipulation on Hardy until the last FF patch last month.

---

### Post by eternalnewbee on 2008-10-21
[QUOTE=M4rotku;6006177]I have to boot into windows to view Chuck on nbc.com as well.  I think it might have something to do with the online episodes being sponsored by Windows.  So, I think they would have it set up so that you can only view it in Windows.


No disrespect meant but that sounds a bit far fetched. ( Although nothing is impossible ).

---

### Post by DArtagnon on 2008-10-21
It's possible that they use Silverlight instead of Flash, and I don't think the linux Moonlight is available yet.

[http://www.bennadel.com/blog/1326-Ewwww-Watching-Olympics-On-NBC-com-Requires-Microsoft-Silverlight.htm](http://www.bennadel.com/blog/1326-Ewwww-Watching-Olympics-On-NBC-com-Requires-Microsoft-Silverlight.htm)

---

### Post by Thelasko on 2008-10-21
Has anyone tried changing [their user agent string?]("https://addons.mozilla.org/en-US/firefox/addon/59")

---

### Post by timcredible on 2008-10-21
i can watch any of the previews or 2 minute synopsis, but no full episodes, nbc must have sold out to microsoft and be blocking non-windows machines.  i even tried setting my browser id to ie on vista.  so, if you want to watch episodes on nbc.com, you need to write to them and let them know that it doesn't work for linux.  that's really the only way to get this to work.

---

### Post by eternalnewbee on 2008-10-21
No offence meant, but how could they be blocking out non-window machines?

---

### Post by Steveway on 2008-10-21
> **eternalnewbee said:**
> No offence meant, but how could they be blocking out non-window machines?

Most propably DRM.

---

### Post by eternalnewbee on 2008-10-21
What's DRM?

---

### Post by Thelasko on 2008-10-21
> **eternalnewbee said:**
> No offence meant, but how could they be blocking out non-window machines?

The simplest method is [user agent sniffing.]("http://en.wikipedia.org/wiki/User_agent")

---

### Post by VorDesigns on 2008-10-21
> **eternalnewbee said:**
> No offence meant, but how could they be blocking out non-window machines?

Easy, browser connects passes information so that web site knows what the browser is and how it works; I could go pull an Internet Information Server or Apache log to show you how much information is actually gathered by the server alone but, just trust me, it is easy.
Try going out to MS's web site in WinX and first use IE, then use FireFox; you will see a significant difference in appearance and serviceability.  They could write their web sites to the same functionality but they choose not to.

---

### Post by jerome1232 on 2008-10-21
It's because they use the move media player, it's getting more and more popular, they use a flash program to install it (which won't work on Linux obviously) A workaround I've found that works is to install wine, install the windows version of firefox in wine, install flash, go to their website and install the move player, and enjoy the show.

edit: There's actually a very good reason for them using this player, we can only hope it gets ported to Linux sometime soon.

---

### Post by eternalnewbee on 2008-10-21
That was enlightening.
Talk about politics...

---

### Post by tysonh on 2008-10-22
When I try to watch the episodes it just loads and loads but no video.  The firefox error console spits out some stuff.  I"ll post the screen shot maybe someone knows a easy work around.

---

### Post by Magnes on 2008-10-22
> **jerome1232 said:**
> edit: There's actually a very good reason for them using this player, we can only hope it gets ported to Linux sometime soon.

Don't count on it. Wasn't Move Player bought by Microsoft recently? :(
I send them an e-mail with question when will Linux version be available. I think more people should.

---

### Post by jerome1232 on 2008-10-22
Was it really? That makes me sad because I had heard rumors of rumors of rumors that they were thinking about thinking of making a Linux client. If Microsoft bought it I can count on it not getting updated to work with the newest firefox when it comes out.

[http://www.movenetworks.com/](http://www.movenetworks.com/)

it looks like NBC is actually not one of their clients so I'm not sure what they are using that's not Linux friendly.

edit:I'm liking that move networks less and less, this is from their faq
How can Move Networks report on every viewer and every viewing experience?

> Move Networks&#8217; media player is a tiny browser plugin viewers acquire through a quick download. Because each viewer must have the plugin installed in order to watch television on Move Media Player, Move Networks is able to gather important viewership statistics for every single viewer and viewing experience. The Move plugin records what shows are watched, exactly how long viewers spend watching during each viewing session, the location and time of day of viewing, and much more. Detailed, accurate, 1:1 reporting from Move Networks gives publishers business intelligence for monetizing their Internet television business.

---

### Post by Steveway on 2008-10-22
> **eternalnewbee said:**
> What's DRM?

Welcome in the year 2008, DRM has been around for some time.
[http://en.wikipedia.org/wiki/Digital_rights_management](http://en.wikipedia.org/wiki/Digital_rights_management)

---

### Post by zaphodbblx on 2009-02-15
> **Thelasko said:**
> Did you try Hulu?  Do you have Ad-Block Plus enabled?  I've never used nbc.com but Hulu won't play video with ABP enabled.  You can select "disable on hulu.com" from the ABP menu to disable it for that site only.
unfortunately they usually dont have full seasons and of course the ones I missed are the ones Hulu dosn't have...I guess fox and abc just dont want our patronage
heres a copy of a letter I wrote to them.
 lets all send them a letter(rational ones please). it wont change till they feel their loosing money!


To whom it may concern,
         Do you ever plan on offering Linux support for your media player? 
I am a consumer who watches Fox and ABC and also WOULD buy the products they advertise, just like people who use microsoft branded products. I am the primary purchaser of grocery,luxury and electronic items in my home so by not reaching me these networks loose advertising dollars and sales.
I also take the time to contact those advertising on these networks and tell them WHY I chose to buy a competitors  product over theirs. Why don't these networks and by extension move networks want my patronage?
sincerely
B********
Linux user and consumer
--

---

### Post by woodgdo1 on 2009-03-26
I don't know if anyone cares, but I started a petition to see if Move Networks will listen to us. Let's see if we can wake them up... Spread the word!

[http://www.petitiononline.com/movlinux/petition.html](http://www.petitiononline.com/movlinux/petition.html)

-Doug

---

### Post by Zimmer on 2009-03-26
Have you tried Heroes at BBC.CO.UK? 

I would be interested to know if you can view episodes from there. 

I can , using HH 8.04  and the BBC I-player ...

---

### Post by jdeslip on 2010-01-21
Why do you think NBC uses Move Media Player?  It does not.  ABC, FOX (until today) and CW use it, but not NBC.  NBC.com full episodes don't work on Ubuntu... but it is not because of Move Media Player.  Any other ideas?

---

### Post by t4thfavor on 2010-01-28
It's annoying, thats all. I would just expect it to work, how hard is it to keep using flash... I wouldn't doubt that the Microsoft sponsorship had something to do with this.

---


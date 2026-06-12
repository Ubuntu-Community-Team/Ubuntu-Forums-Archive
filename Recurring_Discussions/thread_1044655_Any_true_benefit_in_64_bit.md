---
title: "Any true benefit in 64 bit?"
date: 2009-01-19
forum: Recurring Discussions
---

### Post by valros on 2009-01-19
I use Ubuntu for everything but Valve software, installed 64bit as I have the AMD 9850 Quad Core. Im thinking of reinstalling 32bit, the problems with 64bit are almost unbearable, Java doesnt work, Flash is unstable, and benchmark tests seem to show no difference between i386 and amd_64. I currently have 4gigs of 1066 and might upgrade to 8, how does ubuntu 32bit handle 4gigs of memory? Will 32bit be able to take full advantage of the 9850? And last, would there be and difference in the performance in Wine/WoW?

---

### Post by 73ckn797 on 2009-01-19
> **valros said:**
> I use Ubuntu for everything but Valve software, installed 64bit as I have the AMD 9850 Quad Core. Im thinking of reinstalling 32bit, the problems with 64bit are almost unbearable, Java doesnt work, Flash is unstable, and benchmark tests seem to show no difference between i386 and amd_64. I currently have 4gigs of 1066 and might upgrade to 8, how does ubuntu 32bit handle 4gigs of memory? Will 32bit be able to take full advantage of the 9850? And last, would there be and difference in the performance in Wine/WoW?


Flash and Java have been fixed and work great in Ubuntu 64bit. That is why I now use it daily.

Not any real visible difference that I see between 32 & 64. I have both on 2 160Gib drives. Slightly more snappy in 64 but not all that much.

---

### Post by howefield on 2009-01-19
> **valros said:**
> I currently have 4gigs of 1066 and might upgrade to 8, how does ubuntu 32bit handle 4gigs of memory?

32 bit will only be able to use around 3.2 gigs of your memory, unless you use the PAE enabled kernel.

Wine should work as it does in 64 bit.

---

### Post by valros on 2009-01-19
Is this just a bug, when viewing flash(youtube only so far) the flash "box" will grey out when switching between windows, the page needs to be reloaded for it to continue working.

---

### Post by 73ckn797 on 2009-01-19
> **valros said:**
> Is this just a bug, when viewing flash(youtube only so far) the flash "box" will grey out when switching between windows, the page needs to be reloaded for it to continue working.


I think that the latest flash, from Adobe, works very smoothly in Ubuntu. I never have that issue anymore.

---

### Post by sunny_nwho on 2009-01-19
The flash grey box still happens to me. I think it is a firefox error. when i restart the browser it is normal again.

---

### Post by Kilz on 2009-01-20
> **valros said:**
> I use Ubuntu for everything but Valve software, installed 64bit as I have the AMD 9850 Quad Core. Im thinking of reinstalling 32bit, the problems with 64bit are almost unbearable, Java doesnt work, Flash is unstable, and benchmark tests seem to show no difference between i386 and amd_64. I currently have 4gigs of 1066 and might upgrade to 8, how does ubuntu 32bit handle 4gigs of memory? Will 32bit be able to take full advantage of the 9850? And last, would there be and difference in the performance in Wine/WoW?

Might as well just install Windows.

---

### Post by Yellow Pasque on 2009-01-20
The real gains for 64-bit come in apps that make use of large integers (video de/encoding, Photoshop, scientific apps, some resource-intensive games, etc.) If you're willing to sacrifice some performance for possible better stability,  go for it.

However, before abandoning 64-bit, make sure you try the native 64-bit Flash plugin (not the one in the repos) and Sun's pre-release 64-bit Java plugin. Your post doesn't make clear whether you're using these or openjdk & nspluginwrapper.

---

### Post by Sef on 2009-01-20
> However, before abandoning 64-bit, make sure you try the native 64-bit Flash plugin (not the one in the repos) and Sun's pre-release 64-bit Java plugin. Your post doesn't make clear whether you're using these or openjdk & nspluginwrapper.

OpenJDK has a 64-bit version.

---

### Post by jespdj on 2009-01-20
It happens far too often that people have some problem with their Ubuntu system and blame it on the 64-bit version, while they really don't know why they're having their specific problems. Most of the time it's not because they're using the 64-bit version.

Installing 8 GB RAM makes little sense if you're going to use a 32-bit operating system.

---

### Post by SeanHodges on 2009-01-20
> **valros said:**
> I use Ubuntu for everything but Valve software

Valve's Steam client, and all of the Valve games that I have tried, work well in Ubuntu using the Wine compatibility layer. This also applies in 64bit (which is what I use).

> **valros said:**
> installed 64bit as I have the AMD 9850 Quad Core. Im thinking of reinstalling 32bit, the problems with 64bit are almost unbearable


> **valros said:**
> Java doesnt work

Yes it does. Please expand on your problem.

> **valros said:**
> Flash is unstable

Not usually. Again, no'one can help you without a little info to work from. Have you asked for help elsewhere in these/other forums?

> **valros said:**
> and benchmark tests seem to show no difference between i386 and amd_64.

64bit does not directly boost performance of the system. Certain operations will be faster, but in general it allows the O/S to make better use of multi-threading and support a larger amount of memory. Also, benchmarks designed for 32bit applications/operations will show no boost because the processor will run them in 32bit compatibility mode.

[Wikipedia]("http://en.wikipedia.org/wiki/64-bit") is a good starting place for this kind of information. 

> **valros said:**
> I currently have 4gigs of 1066 and might upgrade to 8, how does ubuntu 32bit handle 4gigs of memory? Will 32bit be able to take full advantage of the 9850? And last, would there be and difference in the performance in Wine/WoW?

Sounds like you will need 64bit Ubuntu/Windows to support your 8 gigs. As howefield pointed out, you will be utilising 3.2 gigs otherwise.

---

### Post by dabl on 2009-01-20
> **jespdj said:**
> It happens far too often that people have some problem with their Ubuntu system and blame it on the 64-bit version, while they really don't know why they're having their specific problems. Most of the time it's not because they're using the 64-bit version.



Very, very true, and easy to prove.  The front page of this 64-bit Forum lists the most recent 20 posts.  Just out of curiosity, I've been counting the number of posts that are actually raising a true 64-bit concern, versus the ones that are just another video or USB stick problem.  Typically I see 2 or 3 posts, out of 20, that _could possibly_ be attributable to the 64-bit architecture (most of them repeat topics like flash or java, that have been addressed a zillion times already).

I guess people install the 64-bit OS, then post the first issue they see to this forum ...  :?

---

### Post by Yellow Pasque on 2009-01-20
> **Sef said:**
> OpenJDK has a 64-bit version.
Yes, and it works well enough for most users, but the last time I checked, it doesn't support the latest Java JDK features and isn't feature-complete. The OP is complaining of Java issues and blaming it on "64-bit", so I suggested he/she install the native Sun 64-bit (even though it's in beta/"pre-release" status)

---

### Post by toasty_ghosty on 2009-01-20
> **howefield said:**
> 32 bit will only be able to use around 3.2 gigs of your memory, unless you use the PAE enabled kernel.

Wine should work as it does in 64 bit.

PAE kernel? Would this explain why I only see 7.8 gigs out of 8? Because I am not using a PAE kernel?

---

### Post by Yellow Pasque on 2009-01-20
> **toasty_ghosty said:**
> PAE kernel? Would this explain why I only see 7.8 gigs out of 8? Because I am not using a PAE kernel?
If you're using 64-bit, you don't need a PAE kernel. If you're only seeing 7.8GB, it's probably because of BIOS quirks (memory hole remapping, reserved memory, etc.)

I never thought I would use the phrase "only 7.8GB", but then again, Bill Gates thought 640K was enough for all users.

---

### Post by steeleyuk on 2009-01-20
I switched over to 64-bit a couple of weeks ago. Its been excellent. Flash 10, even though its officially in alpha has been rock solid.

Converting the same film on 64-bit as on 32-bit takes about 20 minutes less.

---

### Post by toasty_ghosty on 2009-01-20
> **Temüjin said:**
> If you're using 64-bit, you don't need a PAE kernel. If you're only seeing 7.8GB, it's probably because of BIOS quirks (memory hole remapping, reserved memory, etc.)

I never thought I would use the phrase "only 7.8GB", but then again, Bill Gates thought 640K was enough for all users.

Thanks. I was somewhat sad to see that it only saw 7.8 when I first installed 64-bit...

---

### Post by jespdj on 2009-01-20
[PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension) is a "trick" to enable a 32-bit OS to use more than 4 GB RAM.

It does not apply to 64-bit operating systems; there is no 4 GB (or 8 GB) limit for 64-bit operating systems. (In theory, a 64-bit system could address 2^64 bytes = 16 exabytes, or more than 16 million gigabytes!).

---

### Post by SeanHodges on 2009-01-21
> **jespdj said:**
> (In theory, a 64-bit system could address 2^64 bytes = 16 exabytes, or more than 16 million gigabytes!).

16EB ought to be enough for anybody.

---

### Post by Sef on 2009-01-21
>      Quote:
                                                                      Originally Posted by **Sef**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6583534#post6583534")                 
                 *OpenJDK has a 64-bit version.*
                                 
Yes, and it works well enough for most users, but the last time I checked, it doesn't support the latest Java JDK features and isn't feature-complete. The OP is complaining of Java issues and blaming it on "64-bit", so I suggested he/she install the native Sun 64-bit (even though it's in beta/"pre-release" status)That is correct.  In the [64-bit sticky]("http://ubuntuforums.org/showthread.php?t=774956") section on 'Missing From OpenJDK' Live Connect is mentioned as not implemented yet.  Do you know any other features that are not implemented in OpenJDK.  I will add them to the 'Missing From OpenJDK' section.

---

### Post by FrancoNero on 2009-01-21
it would be nice to see a Jaunty 64 progress list. I'm assuming sun's 64bit java might be ready by then? flash, too? shouldn't ubuntu enforce 64bit use as soon as most major problems are worked out? after all, 32bit linuxes carry lots of stuff with them to make them downward compatible... it's time for the future :)

---

### Post by philinux on 2009-01-21
I'm testing jaunty 64bit on my second HD. Flash and java work just great. And the new xorg is miles better by the way.

---

### Post by jespdj on 2009-01-21
> **FrancoNero said:**
> it would be nice to see a Jaunty 64 progress list. I'm assuming sun's 64bit java might be ready by then? flash, too?
Sun promised that there will be a 64-bit Java plugin in Java 6 update 12. Currently they're at update 11. Let's hope that update 12 comes out in time to make it into Jaunty.

The same with Flash - let's hope there will be a final (not beta) release of 64-bit Flash before Jaunty.
> shouldn't ubuntu enforce 64bit use as soon as most major problems are worked out? after all, 32bit linuxes carry lots of stuff with them to make them downward compatible... it's time for the future :)
There are really no major problems with 64-bit Ubuntu compared to 32-bit Ubuntu. And if there's a 64-bit native Sun Java and Flash, I really don't see any reason anymore to use 32-bit Ubuntu (unless you have an older computer that doesn't have a 64-bit capable processor).

The download page for Ubuntu currently says:
> 32bit version: This works with most computers
64bit version: May provide additional capabilities to computers that are able to use 64bit software
In other words, the 32-bit version is the default version, and 64-bit is an alternative for people with newer computers only.

It would not be a bad idea if this would be changed in one of the next releases, so that 64-bit is the default version:
> 64bit version: This works with most newer computers
32bit version: Use this version if you have an older computer that does not have a 64-bit capable processor

---

### Post by hyper_ch on 2009-01-21
the question should be: Is there still any reason to use 32bit?

---

### Post by VastOne on 2009-01-22
> **dabl said:**
> Very, very true, and easy to prove.  The front page of this 64-bit Forum lists the most recent 20 posts.  Just out of curiosity, I've been counting the number of posts that are actually raising a true 64-bit concern, versus the ones that are just another video or USB stick problem.  Typically I see 2 or 3 posts, out of 20, that _could possibly_ be attributable to the 64-bit architecture (most of them repeat topics like flash or java, that have been addressed a zillion times already).

I guess people install the 64-bit OS, then post the first issue they see to this forum ...  :?

I have never used anything but 64 bit Ubuntu and have yet to have any problem that could not be solved by answers within this forum....:D

On another note to you dabl, in another thread I saw you give very good explicit instructions on installing nVidio drivers (ctrl + alt + f1 gdm off etc etc)...I struggled with installing nvidio .22 of the nvidio drivers for 2 days following those instructions to a t...and failed (gdm would not turn off) UNTIL I saw another thread that said to use ctrl + alt + F2 and one try and they installed...

Any thoughts on that one?

Thanks

---

### Post by stchman on 2009-01-22
Running 64 bit allows you to use large amounts of RAM.

---

### Post by Kilz on 2009-01-22
> **dabl said:**
> Very, very true, and easy to prove.  The front page of this 64-bit Forum lists the most recent 20 posts.  Just out of curiosity, I've been counting the number of posts that are actually raising a true 64-bit concern, versus the ones that are just another video or USB stick problem.  Typically I see 2 or 3 posts, out of 20, that _could possibly_ be attributable to the 64-bit architecture (most of them repeat topics like flash or java, that have been addressed a zillion times already).

I guess people install the 64-bit OS, then post the first issue they see to this forum ...  :?

> **jespdj said:**
> It happens far too often that people have some problem with their Ubuntu system and blame it on the 64-bit version, while they really don't know why they're having their specific problems. Most of the time it's not because they're using the 64-bit version.

Installing 8 GB RAM makes little sense if you're going to use a 32-bit operating system.

Both quoted for the pure truth they express.

IMHO Its because of Ubuntu's mission. To make a easy to use and install linux distro. What that is attracting is sometimes people who dont care about anyone but themselves and have no respect for others. They dont even feel they need to read the plain information that is in their face. The sticky's have held the answers to a ton of questions, but its much easier to ask a question that has been asked a trillion times because they only need to read one or two replies to get the info.
If you suggest that someone search or read a post, another well meaning byt enabling person will post the same regurgitated info in a post below yours therefore negating the possibility of the user looking at the page or even searching the forums.

Ok, Ill go back to pretending we are all so happy that the sun is crying honey.

:D

---

### Post by yt_l9 on 2009-01-22
> **sunny_nwho said:**
> The flash grey box still happens to me. I think it is a firefox error. when i restart the browser it is normal again.

Try changing your flash player extension in Firefox.  I had similar issues using mplayer/totems flash, disabling that fixed my issue.  I am currently using Adobe's version without incident.

In relation to the value of 64 bit; I have multiple virtual guest machines running within my Ubuntu host, each with at least 2Gb RAM.  This is not really possible with a 32 bit host.
I use the guest machines to 'safely'work in Windows when needed and also test out betas of software and OS's.

---

### Post by Axdrenalin on 2009-01-22
> **jharris1993 said:**
> Kilz (*et. al.*),

Far be it from me - a rank newbie on this forum, knowing full well that there is nothing lower, or dumber, than a forum neo - to say thee nay, but I feel constrained to do so.  So please bear with me. . .

Reference:  "Welcome Message" sent to me less than five minutes ago when I registered for this forum:

.......

This is what Ubuntu is all about (AFAIK), inclusion instead of exclusion, friendliness instead of hostility, help instead of indifference.

If the rank newbie is beginning to raise your ire after all this time, maybe (if I may humbly suggest), you should take a break and let other, less jaded people, help carry the torch while you relax and regenerate.

What say ye?

Jim

The post above that Jim made is pure GOLD, and I just wanted to say thanks for posting it. I lurk a whole lot more than I'll ever post, gleaning info as much as possible without having to ask too many questions, but I don't feel too bad about asking questions after reading that post. In his very first post, Jim pretty much covered what these forums are (or should be) about.

But back on topic - I'm glad to read that they've ironed out more of the flash compatibility quirks in 64 bit linux. That was one of the things that irked me the most about switching completely back in the day, and it looks like the time is getting *real* close to make the move on my main boxen.

Thanks to all for the info and input in these forums.

Ax

---

### Post by CoreyB. on 2009-01-22
> **Temüjin said:**
> The real gains for 64-bit come in apps that make use of large integers (video de/encoding, Photoshop, scientific apps, some resource-intensive games, etc.) If you're willing to sacrifice some performance for possible better stability,  go for it.

However, before abandoning 64-bit, make sure you try the native 64-bit Flash plugin (not the one in the repos) and Sun's pre-release 64-bit Java plugin. Your post doesn't make clear whether you're using these or openjdk & nspluginwrapper.

Will 64-bit Adobe flash be in the repos by the release of Jaunty?

---

### Post by Kilz on 2009-01-23
> **CoreyB. said:**
> Will 64-bit Adobe flash be in the repos by the release of Jaunty?

Since its only an alpha , I wouldn't hold my breath waiting for it to be included.

---

### Post by Kilz on 2009-01-23
> **Axdrenalin said:**
> The post above that Jim made is pure GOLD, and I just wanted to say thanks for posting it. I lurk a whole lot more than I'll ever post, gleaning info as much as possible without having to ask too many questions, but I don't feel too bad about asking questions after reading that post. In his very first post, Jim pretty much covered what these forums are (or should be) about.

But back on topic - I'm glad to read that they've ironed out more of the flash compatibility quirks in 64 bit linux. That was one of the things that irked me the most about switching completely back in the day, and it looks like the time is getting *real* close to make the move on my main boxen.

Thanks to all for the info and input in these forums.

Ax

Give a man a fish, feed him for a day.
Teach a man to fish, feed him for a lifetime.

---

### Post by jharris1993 on 2009-01-23
> **Axdrenalin said:**
> The post above that Jim made is pure GOLD, and I just wanted to say thanks for posting it. I lurk a whole lot more than I'll ever post, gleaning info as much as possible without having to ask too many questions, but I don't feel too bad about asking questions after reading that post. In his very first post, Jim pretty much covered what these forums are (or should be) about.

Thanks to all for the info and input in these forums.

Ax

Ax, (and everyone else)

First:  Though I may have felt justified in my "rant" - and yes this does get my ire up - but that's the moose's problem.  It was both inappropriate and un-justified for me to flame the forum like that.  ](*,) <-- Abject apologies

As soon as my mommy lets me out of my room for loosing my temper :p I'll get back on my Ubuntu (8.10) box and calm down. (laughing!)

Closer to the mark - I have a nice Compaq system that has an AMD 64 X2 in it, and I have it set to quad-boot.  Vista 32.  XP 32, and (drum roll!) both 32 and 64 bit versions of Ubuntu 8.10

And I've been playing with it all day (while mommy was out!) and I have noticed certain things about Ubuntu in general, and 64 bit in particular, that I'll share:

1.  Ubuntu (8.10, etc.) is the - literally - **FIRST** Linux system that I felt was "civilized" enough to actually consider installing on my wife's and my mom's computers.  I played with Ubuntu a bit, then did a Debian install (on the same hardware), and Jeez Louise!!  Any time you get sick of the "nonsense" in Ubuntu land, go load up the last stable Debian.  Half didn't work, and the other half was broke!  Right outta the box, I ended up spending more time in a terminal window than I did on the desktop...)  I trashed that setup, wiped the disk, and re-loaded Ubuntu!

2.  Literally running both, (I almost typed "8" and "16" bit - darn, I'm dating myself again! :-\"),  32 and 64 bit versions of Ubuntu - updated, using the same hardware, etc. side by side - and the only way I can tell 'em apart is because I edited the background artwork so that one says "32 bit" and the other says "64. . ."  They both launch like a gassed-up Saturn-V, purr like a kitten, and (when the light turns green), they both have a quarter-mile of flaming rubber behind 'em before Vista figures out where the boot block is. . .  XP's a bit better, It's already found the boot block, but it's still thrashing around building my desktop.  That's assuming it doesn't develop a sudden case of amnesia and can't figure out it's own name.  [-(

3.  Rough spots?  Sure!  (and I wrote the bugs too.)  At least *HERE* I get to write bugs when I find something that has me shaking my head in wonder.   Pretty soon, if I behave, maybe they'll let me test a few... (more laughter!)

The one thing I will say - I too love to lurk these forums and soak up the raw experience - I see people moaning and groaning about this or that.  64 bit,  Such-and-so driver doesn't work on my Timex Sinclar, IPv6 is hozed. ("No, it's not! Yes it is!  NO, it's NOT!!  Yes it IS!! - [female voice:] CHILDREN!  BEHAVE!!!!)

This stuff is (mostly) done by people who do it because they want to, not because they gotta do it.  And for a "freeware" operating system - they've done one heck of a bang-up job. Hells bells!  These guys kick the (------) out of software that costs THOUSANDS more than this. (note, _plural_ thousands).  And if you don't believe ME, just go wander into some extreme-reliability server farm somewhere and count the number of boxes running Windoze...  $20 for each one you find.

OK, you got me; there are two dusty desktop units over there in the corner that haven't been re-loaded with Linux.   Yet.

OO is as slick as a smelt.  There's a CAD program (freeware again) that spits in AutoDesk's eye.  Scribus (love it!) can do anything Quark and Pagemaker can do, for about $3k less....  And it's all freeware.

The least we can do is say "thanks!!"

Which I do.

(now. . . . .  Where did I hide my tranquilizers? . . . :D )

Jim

---

### Post by crimesaucer on 2009-01-23
Both the official 64bit Adobe Flashplugin 10.0.d21.1-1 and the official Sun 64bit jre_beta 6u12_b03-1 are working perfectly for me on my Arch64.


..... even 6 months ago flash with the nspluginwrapper and java with OpenJDK6 and "IcedTea" worked pretty damn good..... but these new official releases are much better.

---

### Post by crimesaucer on 2009-01-23
> **Sef said:**
> OpenJDK has a 64-bit version.

I used that with the "IcedTea" plugin before Sun had the 64bit beta version: jre_beta 6u12_b03-1


jre_beta 6u12_b03-1 works SO MUCH better for Java web applets.

---

### Post by jharris1993 on 2009-01-23
> **CoreyB. said:**
> Will 64-bit Adobe flash be in the repos by the release of Jaunty?

Dunno.  They haven't told me yet.  (grin!)

What I *DO* know is this:

I have both 32 and 64 bit 8.11, (Intrepid?  Yea, that's right!). on a Compaq laptop that I use for testing - most Linux distro's HATE my laptop.  Ubuntu slipped behind the wheel and felt right at home.

Flash:  I went to run my favorite network speed-checker ([COLOR=Red][http://www.speakeasy.net/speedtest](http://www.speakeasy.net/speedtest)[/COLOR]) which uses a custom flash app by Ookala, and Firefox told me I was missing a plugin to view the "content" (the actual speed test window).

I was offered three choices when Firefox asked if I wanted to check out the updates.
1.  Adobe Flash for Firefox.
2.  An open source (sflash?) -gnome plugin for flash.
3.  A GNU-flash clone (also open source)

This being the 64 bit box, and knowing how everyone is having problems with Flash, I decided to mess with it.

I tried the #2 item (Sflash?  Not sure), loaded it up, restarted Firefox, and the test came up like a monster!  It was a bit jerky though - especially at the end of the download test.  So I dropped it and downloaded the "OFFICIAL" flash from Adobe.  Reran the page, same jerky behavior.  Never saw this on the 32 bit box...  Darn.  A 64 bit issue.

A little looking around my desk area disclosed that the "blue" (active - turned on) wireless light on the front underside of my laptop was lit.  (Huh?!)  Being on a wired connection - _that_ could be interesting...  So, I quashed wireless and changed the startup settings so Wireless does not auto-connect.

Re ran the speed test using both plugins again.  SMMMMOOOTH as silk!  In fact, the "speed" reading using s-flash was about 5 to 10% faster than the Adobe version.  Interesting!

So - the bottom line is this - at least as of Jan 23, 2009 - the flash problem seems to be squared away - unless it's a different issue.

BTW, my laptop has a Nvidia video chipset, and I downloaded the latest-and-greatest video drivers from the (multiverse?) to run it.  Not OS, but they work.

BTW, I *DID* notice that my window title bars were flaky with visual-effects (eye candy) turned on, so I turned it off.  Got tired of seeing the top half of my windows and dialogs disappear at random.  Have you tried Flash with visual effects turned off?  What video card and driver are you using?

Ax,  if my experience is any help, your "big box's" current operating system may be DOOMED!

Jim

---

### Post by Axdrenalin on 2009-01-26
> **jharris1993 said:**
> Ax, (and everyone else)

Such-and-so driver doesn't work on my [SIZE="5"][COLOR="Red"]Timex Sinclar[/COLOR][/SIZE]

...........

Ax, if my experience is any help, your "big box's" current operating system may be DOOMED!


Jim

Jim, You really are dating yourself talking about Timex Sinclair's on here. My first computer was a TS1000 years ago.:D

I appreciate you offering the assistance. I'll likely take you up on it as I tinker and explore more.

Ax

---

### Post by FrancoNero on 2009-04-07
*bump* three months later. status update on java64 and flash64 ?
i might do the FINAL switch to ubuntu within this month (despite the frustrations i'm still having), as i'm getting a 4gb RAM machine i wanna use the ubuntu64 version. so just asking what the status is by now...

---

### Post by hyper_ch on 2009-04-07
the same as has been half a year ago.

---

### Post by Therion on 2009-04-07
> **FrancoNero said:**
> *bump* three months later. status update on java64 and flash64 ?> **hyper_ch said:**
> the same as has been half a year ago.
Yeah, that's pretty much the story.  If you want to use Flash and Java on a 64-bit install of Ubuntu, you install the packages just like you would under a 32-bit distro.

---

### Post by hyper_ch on 2009-04-07
there is a 64bit flash plugin :)

---

### Post by Mehall on 2009-04-07
> **hyper_ch said:**
> there is a 64bit flash plugin :)

it's buggy as fsck

---

### Post by hyper_ch on 2009-04-07
tried it?

---

### Post by Mehall on 2009-04-07
> **hyper_ch said:**
> tried it?

Briefly.

it's a bit marmite: It works for some fine, no issues at all.

others, it crashes every 5mins.

I only used it very briefly.

---

### Post by hyper_ch on 2009-04-07
so you didn't try it ;)

---

### Post by SeanHodges on 2009-04-08
The Adobe 64bit Flash plugin works fine, as well as it does for 32bit.

The Gnash one on the other hand, still needs a little work :) As of Intrepid I haven't been able to view Youtube videos without switching to the Adobe plugin, anyone happen to know if this is fixed in Jaunty?

---

### Post by FrancoNero on 2009-04-12
ah now I'm getting the replies on the current status that I was hoping for :D

so I should be safe with the proprietary plugins (personally I'm not hardcore anti-proprietary, as long as it works...), right?

---

### Post by xir_ on 2009-04-12
for me the best benefit for 64 bit... quantum chemsitry cant be done in 32 bit.

---

### Post by SomeGuyDude on 2009-04-12
Other than Picasa not working right, it's pretty flawless for me.

---

### Post by gn2 on 2009-04-12
There was a 64-bit Flash update on the 24th of February, it works really well and is a piece of cake to install, you don't even need to use the CLI :shock:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml) (instructions also work on 8.04)

As for the benefit of 64-bit over 32-bit, one word springs instantly to mind: encoding.

Encoding tasks complete much faster in 64. [http://tinyurl.com/6adooq](http://tinyurl.com/6adooq)

---

### Post by rivenathos on 2009-04-12
With Ubuntu 8.10 32-bit, a couple of my machines began requiring "compatibility mode" to boot the Live CD.  Once installed, everything worked as specified.  It was still something that got me to experimenting.  The first thing I noticed was that the only machines having issues with upgrading were 64-bit capable ones.

Now, on these 64-bit capable machines, I inserted the Ubuntu 8.10 64-bit disc.  There was no need for "compatibility mode" anymore.  Even though the machines only had 1 or 2 GB of RAM, their hardware benefited from 64-bit.  In fact, I even noticed some slight issues with video had cleared up.

So, for my 64-bit machines, yes, there was an observable and true benefit to using 64-bit.

---


---
title: "Netflix in Ubuntu, no native Method"
date: 2010-06-15
forum: Recurring Discussions
---

### Post by Intel91 on 2010-06-15
I was wondering if anyone has found any other ways of watching Netflix instant on ubuntu, other than loading up a virtual windows machine and watching it like that (which takes up a lot of space).

If not, I have found a new method of doing it that only requires about 25mb of space, instead of an entire operating system. I'd rather not mention the method until I hear back if there are other ways, and until I've positively tested it on another console.

If there are no other good methods I will post up a tutorial today or tomorrow, depending on if/when I have internet.

---

### Post by doas777 on 2010-06-15
none that i am aware of, and I've been paying attention to this issue. I look forward to seeing your workaround.

---

### Post by dartmusic on 2010-06-17
I've found nothing that works...would love to hear your idea.

---

### Post by Intel91 on 2010-06-20
Sorry it took me so long to reply, it took me so long to get Internet again, but I won't go into that.

Anyways, after playing around a bit more, I realize this method is really only suitable as a plugin for a media center, like boxee. The reason is it inherently has a media center feel because it was designed with a 10 foot UI... for the wii. The method is emulating the Wii on linux with dolphin then running a 20mb trimmed Netflix iso, adding up to about 25mb total. Not a great work around, but a small one. There are controller problems as well, in that it likes using the wiimote. However, I'm going to call it here, and if anyone else is interested then perhaps someone will create a boxee plugin out of this concept.

I'm working on a way to run it natively in firefox, and believe it or not but with todays moonlight update it may be looking a bit more optimistic, I'm getting further than ever before with it.

---

### Post by /bee/ on 2010-09-24
Um... This doesn't really look deserving of the "Solved" tag.

---

### Post by Fableflame on 2010-09-24
Emulating the Wii just to watch Netflix?
What if your computer can't handle emulating a Wii?
I have a slow processor and only a 1GB of RAM.

---

### Post by alexhrdr on 2010-09-28
Yes, this is not really solved.  I went away from Ubuntu for a while because I was having problems doing my daily work but most of that is now resolved.  Netflix seems to be one of the few remaining down sides so I'd be very interested in a solution.  Thanks for working on it!

---

### Post by Greyowl750 on 2010-10-12
just use Virtual box, install xp and you can watch it...+++you get to use all those handy dandy programs you cannot run on Ubuntu wine.:)

---

### Post by marcottebj on 2010-10-13
This is definately not solved.  Virtual box is not a solution.  What's the point of running XP in a VM?  You still have to have a license for Windows.  Why not just run Ubuntu in a VM on XP? 
 
... oh wait... if you have XP, you really don't need Linux for anything.  
 
I have my blackberry syncing, I have my Ipod syncing, I can do my homework and open office documents, Evolution is a great free alternative to Outlook.  Now, if I could just watch movies on Netflix or use my Ubuntu PC as a media server to stream movies from Netflix to my PS3.  
 
Until that happens, I'll have to keep running Windows 7, and Ubuntu will just be a neat toy on a USB thumbdrive.

---

### Post by anjilslaire on 2010-10-13
> **marcottebj said:**
> Now, if I could just watch movies on Netflix or use my Ubuntu PC as a media server to stream movies from Netflix to my PS3.  
 
Until that happens, I'll have to keep running Windows 7, and Ubuntu will just be a neat toy on a USB thumbdrive.

Netflix is a native app on the PS3,no computer needed at all. No need for Windows for that purpose.

---

### Post by Wulfe on 2010-10-13
> **marcottebj said:**
> This is definately not solved.  Virtual box is not a solution.  What's the point of running XP in a VM?  You still have to have a license for Windows.  Why not just run Ubuntu in a VM on XP? 
 
... oh wait... if you have XP, you really don't need Linux for anything.  
 
I have my blackberry syncing, I have my Ipod syncing, I can do my homework and open office documents, Evolution is a great free alternative to Outlook.  Now, if I could just watch movies on Netflix or use my Ubuntu PC as a media server to stream movies from Netflix to my PS3.  
 
Until that happens, I'll have to keep running Windows 7, and Ubuntu will just be a neat toy on a USB thumbdrive.


You are obviously one of those Winblows users who does not see outside of the box. In this case a Virtual Box. If all you are is complaining about Netflix being the reason for not using Linux, then maybe you should stay on Winblows as Linux is not the Operating System for you. Linux is more then a Toy its a comprehensive OS that exceeds anything Winblows could dream of in productivity. If all you have to base your opinion on is the fact that its some "toy" and the fact that you are too lazy to run a VM or don't want to research the effort to have Netflix. then do us all a favor and don't let the door hit you on the butt on your way out. These kinds of posts do not answer any of the questions at hand and do not support the thread in any way.

As for the thread, to stay on subject, i have been running VM of my raw XP partition as to prevent having to constantly boot in and out of Linux to go over to Winblows every time I need something that requires a lame .dll or some stupid DRM (ty silverlight) to run that WINE does not work well with. This has been doing just fine for me on the Netflix issue. I do however recommend using XP as the primary OS for this VM running though even when not being ran as a raw partition XP sees to be the easiest on memory and cpu usage. Loading in Windows 7 or Vista for Netflix would be a waste, and not to mention a huge load on your system resources. If you have you have your old XP disk lying around then try this method for now till Netflix gets off its but and finally gives us the support for Linux like they promised would already be here back in June.....

Also as a side note make sure to at least allot 10GB for your Disk or you will be having problems installing everything you need and keeping a comfortable amount of space needed for XP the rest of the settings you may leave at default.

---

### Post by Innate Ideas on 2010-10-20
I found a method to watch streaming Netflix movies in Ubuntu. It doesn't solve the DRM issue but does solve my issue, which was that I wanted to watch streaming Netflix movies on my Ubuntu desktop in VLC without using VMware or Virtualbox. 

The short story is that I use the PlayOn media server software from Mediamall Technologies running on a Windows XP PC as a sort of DRM proxy. It's not free but it's cost is reasonable, and there is a 14 day trial license so you can test to see if it works for you. I mount the UPnP multimedia files shared from the PlayOn server to my Ubuntu desktop via the djmount command. Then I can browse and play my Netflix movies in VLC. More detail describing this at [www.innate-ideas.net](www.innate-ideas.net).

---

### Post by ivarn on 2010-10-20
> **Innate Ideas said:**
> I found a method to watch streaming Netflix movies in Ubuntu. It doesn't solve the DRM issue but does solve my issue, which was that I wanted to watch streaming Netflix movies on my Ubuntu desktop in VLC without using VMware or Virtualbox. 

The short story is that I use the PlayOn media server software from Mediamall Technologies running on a Windows XP PC as a sort of DRM proxy. It's not free but it's cost is reasonable, and there is a 14 day trial license so you can test to see if it works for you. I mount the UPnP multimedia files shared from the PlayOn server to my Ubuntu desktop via the djmount command. Then I can browse and play my Netflix movies in VLC. More detail describing this at [www.innate-ideas.net]("http://www.innate-ideas.net").
Thanx but not a solution at all really. Still easier to use thepiratebay. Netflix simply MUST fix this.

---

### Post by marcottebj on 2010-11-11
True.  At the time of my post, however that was not the case.

---

### Post by marcottebj on 2010-11-11
> **Wulfe said:**
> You are obviously one of those Winblows users who does not see outside of the box. In this case a Virtual Box. If all you are is complaining about Netflix being the reason for not using Linux, then maybe you should stay on Winblows as Linux is not the Operating System for you. Linux is more then a Toy its a comprehensive OS that exceeds anything Winblows could dream of in productivity. If all you have to base your opinion on is the fact that its some "toy" and the fact that you are too lazy to run a VM or don't want to research the effort to have Netflix. then do us all a favor and don't let the door hit you on the butt on your way out. These kinds of posts do not answer any of the questions at hand and do not support the thread in any way.

As for the thread, to stay on subject, i have been running VM of my raw XP partition as to prevent having to constantly boot in and out of Linux to go over to Winblows every time I need something that requires a lame .dll or some stupid DRM (ty silverlight) to run that WINE does not work well with. This has been doing just fine for me on the Netflix issue. I do however recommend using XP as the primary OS for this VM running though even when not being ran as a raw partition XP sees to be the easiest on memory and cpu usage. Loading in Windows 7 or Vista for Netflix would be a waste, and not to mention a huge load on your system resources. If you have you have your old XP disk lying around then try this method for now till Netflix gets off its but and finally gives us the support for Linux like they promised would already be here back in June.....

Also as a side note make sure to at least allot 10GB for your Disk or you will be having problems installing everything you need and keeping a comfortable amount of space needed for XP the rest of the settings you may leave at default.
Ubuntu is great for a free OS.  I've installed it on countless computers, and steered many users away from Windows in favor of Ubuntu.  It's a very powerful, and versatile OS.
 
 The standard answer to every problem seems to be "run XP in a VM", however.  I guess even Windows 7 offers that as their compatability solution, however.  
 
My point is simply that most of us don't want the hassle of running a VM for compatability.  Posting that as the solution to a thread and calling it solved is ridiculous.  I agree that the issue belongs to Netflix, and not Ubuntu.  Moonlight is a promising solution.  
 
Bottom line: In a competition between XP, and Ubuntu it's a pretty close match.  Ubuntu has the upper hand because it's free.  
 
The problem is... if I have to tell my customers to run XP in a VM on their Ubuntu box to get their apps to work, they aren't likely to see the point of switching to Ubuntu.  As a community we have to abandon this VM thing as a solution to every problem, or Ubuntu is never going to become a serious mainstream competetor to Windows.   And lets face it.   That's the point of Ubuntu, otherwise we'd all be running Slackware.

---

### Post by SeijiSensei on 2010-11-11
> **ivarn said:**
> Thanx but not a solution at all really. Still easier to use thepiratebay. Netflix simply MUST fix this.

Don't blame Netflix.  It's the rights holders who make the rules.  The rules say that you can only stream our films on closed-source proprietary platforms where we can enforce all the DRM options currently available via technlogies like Microsoft Silverlight.  There'll probably never be an open-source Netflix viewer, nor do I expect them to make a Linux-specific proprietary player either.  The market is way too small, even in comparison to the console platforms.  Plus I suspect that Hollywood just doesn't trust Linux users out of the fear that they'll be able to break the DRM somehow.

---

### Post by ocean! on 2010-11-15
sorry to bump a few days old thread but, after reading snide remarks about ubuntu and linux in general, i had to actually sign up and respond.

ubuntu, linux and the sort: yes its free. when we say free, we do not mean its free as in something some one gives you for free. as one would say "free beer" ;)

when it comes down to the word "free" it means freedom.

and in freedom we mean liberty. the constitution. what it means to be a actual american. a human.

yes windows has its uses to some, but when you "buy" windows, you are not "buying" windows. you are buying a license. thats the number you type in when you do the so called "activation". in all reality, you are only renting it. and m$ can do what they want with it, and they can make you do what they want you to do with it. 
if they added "return your copy asap" in the eua tonight. tomorrow you would have to return it. plain and simple. they are able to change anything at anytime and by clicking "yes i agree" well, yes, you agree.
 people should read the end user agreements to the items they digitally sign. and yes it is a contract, a digital contract.

also, before i step off my soap box, let me say this:

there is one true free, one true free as in free beer:
the key to everything, morpheus's proverbial "the one", the truth, the honest, the god given, the 100%, bees knees reason linux is important is this, and only this;

information, the ability to receive and understand information, knowing  what is actually going on and happening on this true real non-rose  tinted earth type of information. being free to see, hear, speak and understand every inch, every speck, every one and zero, every person, every dog, every cat, every left, every right, every leg, every brain, well, hopefully you get the point.

the internet is information, how we acess said information must not and can not be restricted or filtered.

windows does just this, it is far from blatant now, but that could change at the drop of a hat. 
linux my friend ,does and will put a stop to the censorship of information.

so when you purchase and use windows, *****$ and giggles aside, you are actually losing a right. you are losing a true and honest civil liberty that we Americans hold dear. a god given "right".
you are losing the right to choose, the right to free speech. my friend. the idea even, the idea behind the word "right".

he who controls the information controls the world.
think about this the next time your upset over something so petty.

thanks
ocean

---

### Post by snowpine on 2010-11-15
Welcome to the forums, Ocean! Epic first post; I think you hit the nail on the head. :)

---

### Post by Flos Headford on 2010-11-15
Sorry for totally off-topic query: I have spent an hour and more trying to find out how to post a new question, but I eventually felt forced to jump onto a thread - yours (at random).
Please. please, please someone tell me how to post a query (start a new thread) - I used to know, once upon a time, but I forgot to write it down. A long time ago, I complained about how difficult this was to find, and I'm afraid the Thought Police might have taken my "New Thread" button away......
Thanks, buddies,
Phil Headford

---

### Post by Flos Headford on 2010-11-15
PS - I agree - a jolly well-written post, Ocean! I wish they were all so edifying.
Phil

PPS - How DID you DO that?
F

---

### Post by ocean! on 2010-11-15
> **Flos Headford said:**
> Sorry for totally off-topic query: I have spent an hour and more trying to find out how to post a new question, but I eventually felt forced to jump onto a thread - yours (at random).
Please. please, please someone tell me how to post a query (start a new thread) - I used to know, once upon a time, but I forgot to write it down. A long time ago, I complained about how difficult this was to find, and I'm afraid the Thought Police might have taken my "New Thread" button away......
Thanks, buddies,
Phil Headford
 [http://www.uluga.ubuntuforums.org/search.php?do=process](http://www.uluga.ubuntuforums.org/search.php?do=process)

---

### Post by ocean! on 2010-11-15
> **Flos Headford said:**
> PS - I agree - a jolly well-written post, Ocean! I wish they were all so edifying.
Phil

PPS - How DID you DO that?
F
[B]   

a jolly well-written post[/B]
                      thanks
[B]
 I wish they were all so edifying.[/B]
                   this was my first post.



**PPS - How DID you DO that?**
                    im confused, how did i do what?
do you mean "ppa:"?

alas, why choose this thread? i must say this is one heck of a important thread to try and derail!
j/k.......... maybe.

---

### Post by ocean! on 2010-11-15
wow, think i may have pushed some buttons.


(this is geared towards the shill bot not flos)

yay! shill bot is gone!

later guys, im done, i have said my piece and i hope the next time some one goes to complain about any gpl distro they think about what i said!!

i wont be posting anymore,
well ive never been much of a "forum" type of guy.

but i do respect all of the information, tips, tricks, and expertise i have absorbed from reading everyones posts!
thank you to every single one of you that are here on the real. even the ones who are not, you keep us going!
keep up the fight guys! 
we will show these bagbiters who boss!

im off to see the wizard wearing my white hat!.

---

### Post by marcottebj on 2010-11-18
[COLOR=black][FONT=Verdana]Yes.. well stated.  Although we can all appreciate what Ubuntu symbolizes; you may be overstating it a bit (in my opinion).  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I’m for using one OS.  Live with it’s limitations, and move on.  If we can get something to work… great! That’s why I search these threads, but I feel my time gets wasted when I find a thread marked solved, but the solution is simply “run Windows”. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]My original thread was simply an attempt to point out how silly that is from the standpoint of a pragmatist.  I mean.. C’mon![/FONT][/COLOR]

---

### Post by LinuxMaster9 on 2011-01-01
> **marcottebj said:**
> [COLOR=black][FONT=Verdana]Yes.. well stated.  Although we can all appreciate what Ubuntu symbolizes; you may be overstating it a bit (in my opinion).  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I’m for using one OS.  Live with it’s limitations, and move on.  If we can get something to work… great! That’s why I search these threads, but I feel my time gets wasted when I find a thread marked solved, but the solution is simply “run Windows”. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]My original thread was simply an attempt to point out how silly that is from the standpoint of a pragmatist.  I mean.. C’mon![/FONT][/COLOR]

I thoroughly agree! I think that to say the solution to your problem is to "run windows" when you are on the LINUX forum is just wrong. Not only are you say that Linux can not do something that Microsoft can, but in essense you are telling someone to go throw 140-400 down the drain just to do 1 or 2 things. The statement to "run VM" is more reasonable than Run Windows.:mad:

---

### Post by Hunter Tech on 2011-01-12
Im new to linux, about 2 days actually and i just discovered this issue.  I cant play netflix with it, i do not have another OS i mistakenly tossed my 7 disc away and linux was my solution to buying 7 again.  So far i have been happy, until now fortunately my blu ray player does have netlfix option on it but it is nice to have one screen playing Niptuck and working in the other which now i cant do.  

From the sound of this thread it doesnt appear that there is going to be a solution to this problem other than running windows which means i have to get creative in attempting to feed my laptop into my 2 desktop monitors which is running 7, i dont think that is going to be possible, and after buying KVm switches and such may end up being more expensive than just buying 7 again.

---

### Post by anjilslaire on 2011-01-14
AS long as you have your Windows 7 keys still, you can get the ISOs legitimately from DigitalRiver
[See here]("http://www.mydigitallife.info/2009/11/10/windows-7-iso-x86-and-x64-official-direct-download-links-ultimate-professional-and-home-premium/")

---

### Post by plowdawg on 2011-01-18
Hi, I would like you to know I have gotten it to at least attempt to load the Netflix player by spoofing my FireFox user agent string to one of FireFox for Windows and installing Moonlight (latest preview version).  You can see a screen shot on  [http://pessetto.com/netflix/NetFlixDRM.png ]("http://pessetto.com/netflix/NetFlixDRM.png")

Steps to this far:
1. Install Moonlight Preview
2. Install DRM package
3. Install User Agent Switcher in Mozilla
4. Adda a Windows user agent string to UserAgent Switcher
5.  Switch User Agent to Firefox on Windows
6. Navigate Netflix

IF anyone can get any farther it would be appreciated.

---

### Post by justNiz on 2011-01-19
Netflix's trend is clearly towards totally removing its DVD service, and also to continue to ignore support for streaming to PC Linux-based computers. see here for justification:
[http://blogs.techrepublic.com.com/opensource/?p=1745](http://blogs.techrepublic.com.com/opensource/?p=1745)

As a Ubuntu user who doesn't own and refuses to ever buy a copy of Windows, Netflix will by their own hand have exactly 0 service I can use, so will be losing me as a subscriber.

As I and many others will soon have our Netflix money available to spend with someone else, I wonder if anyone (e.g. Mr. Shuttleworth) has given a Linux-friendly equivalent of the Netflix service any thought?

---

### Post by ronnielsen1 on 2011-01-19
> Emulating the Wii just to watch Netflix?
What if your computer can't handle emulating a Wii?
I have a slow processor and only a 1GB of RAM.

It beats a wii. A wii is equivalent to a P3 768 MHZ

---

### Post by aysiu on 2011-01-19
> **justNiz said:**
> 
As I and many others will soon have our Netflix money available to spend with someone else, I wonder if anyone (e.g. Mr. Shuttleworth) has given a Linux-friendly equivalent of the Netflix service any thought? If so, I hope it's more reliable than Ubuntu One. That sort of service is less about technology and more about business. There would have to be all sorts of meetings and licensing agreements with movie studios, and most certainly some kind of DRM.

---

### Post by ijumpship on 2011-01-19
I just had to register.This one makes me fumes.

let me first give a slight background of myself.
I previously manage 106 computers spread over 6 branches all based on windows.moving from Win98 to Winxp for desktops  with servers from Winnt to Windows2003.[SIZE=5]**It was a pain.**[/SIZE]

You had to have an administrator for Networking,One for Antivirus,One for database and another for General operations.other task such as web-service were outsource.

My first experience was with debian some three years ago then mythdora and finally all "**UBUNTU**'S" , and I was willing to Unlearn windows because I found I could practically do almost anything I dream with Linux.

So the moral,What do you want? 

I only have a limited time to watch movies so I am contented to rent 40 movies for the month $40 from the box at the supermarket.and a $14 subscription to Netflix no streaming. I can hardly count the amount of movies I watch.I get 18 channels from Over the Air TV,**that is** enough bad news for me.
So  now I am still able to have enough money leftover to Wine and Dine a lovely partner.:popcorn:
My cable bill used to be $104/per month but with repeated movie channels and add-ons.it was over $200.I am no longer a couch potato,I am no longer stress with gossip and bad cable news.
**Savings=1 RK box for Sports (including subscription),and a HDPVR.**:grin:

**Yes I am free**.Oh my doctor says I am losing weight.which is good for my health.:razz:

Do the maths.you will run from windows.

By the way Next year you upgrade and have to throw out that burden of or through the windows Yes!  I will be there taking it apart for a lovely **Mythbuntu Media center** for someone who love my home network setup.

***What Am I doing Now? I am here cleaning some trojan off a windows 7 machine using Ubuntu Live.***

---

### Post by kjano on 2011-01-22
why not use amazon.com 'video on demand' works great on ubuntu - i used it every week.

---

### Post by ridetheteapot on 2011-01-22
> **plowdawg said:**
> Hi, I would like you to know I have gotten it to at least attempt to load the Netflix player by spoofing my FireFox user agent string to one of FireFox for Windows and installing Moonlight (latest preview version).  You can see a screen shot on  [http://pessetto.com/netflix/NetFlixDRM.png ]("http://pessetto.com/netflix/NetFlixDRM.png")

Steps to this far:
1. Install Moonlight Preview
2. Install DRM package
3. Install User Agent Switcher in Mozilla
4. Adda a Windows user agent string to UserAgent Switcher
5.  Switch User Agent to Firefox on Windows
6. Navigate Netflix

IF anyone can get any farther it would be appreciated.
What drm package? is there a hacked roku module floating around?

---

### Post by ijumpship on 2011-01-25
[Thanks kjano]("http://ubuntuforums.org/member.php?u=290421")

As I said I do not get to watch movies frequently but I looked at the amazon and will definitely be doing so this weekend.

Just a note to everyone "Nothing in life is "free". even if you are a Christian,you need time to collect so called "**Manner**"."**Time is Money**" plus you need some container to collect it.otherwise you will  not be able to maximized  your collections.

I deeply appreciate everyone who provide us with the various alternative Operating systems and applications.

I will not gripe on anyone who wants to focus on one set of customers.Every successful business person will tell you "if you do not cater for all customer you are deem to failure as your market shrinks"

Look at the development of linux over the years.I no longer think "linux is a passing fad or for geeks".its a force.When I see kids with refurbish laptops with Ubuntus.I laugh.

**Thank You the development team of Canonical and all other distro.  **

Netflix might need to do this for their development but there are so much alternatives.
The so called "[B]Par with the rich kid cause you will get rich syndrome"
[/B]
Forget them.Give us alternatives here like the one mention above,so that anyone who read forum this will move quickly to other choices.

By the way did anyone notice the third party installation like XBMC included  in MCC of Mythbuntu Maverick when you install auto builds?

Yes your Home Theatre Experience just get better.Netflix will soon learn.

---

### Post by bschumacher on 2011-01-26
Not really a fix, however as the linux community is quite large now perhaps it would be a sound business plan to start a competition with Netflix. I'm sure with all of the development talent in the community this would not be hard feat to achieve. I guess it would need some financial backing but other than that problem solved. Perhaps **canonical **would be on-board with this idea as it would directly affect their user base and be a great source of recurring income.

Just my two cents.

---

### Post by aysiu on 2011-01-26
> **bschumacher said:**
> Not really a fix, however as the linux community is quite large now perhaps it would be a sound business plan to start a competition with Netflix. I'm sure with all of the development talent in the community this would not be hard feat to achieve. It's more of a business problem than a technological one. Your company has to get the major film studios to agree to license their films to you to stream, and they probably won't agree unless there is some kind of proprietary DRM attached to the stream.

---

### Post by sxfx on 2011-01-28
Hey guys,

Been a reader, and linux user for years now, but first time posting.

Anyways, I found this thread, and even though I can't shed any light on a fix.  I do have some interesting news to you.

[http://www.betanews.com/article/Google-acquires-Netflix-Vudu-and-Blockbusters-streaming-video-DRM-provider-Widevine/1291420252](http://www.betanews.com/article/Google-acquires-Netflix-Vudu-and-Blockbusters-streaming-video-DRM-provider-Widevine/1291420252)

I also know that one of their goals is to bring netflix for Android, and ChromeOS, which as many of you probably know are ran on a linux kernel

In other words, native netflix support is right around the corner.

---

### Post by ridetheteapot on 2011-02-02
roku runs linux and netflix, but there are nda's keeping the drm out of other peoples hands (as i understand it at least). i doubt it will be different for google.
maybe if its ported to x86 machines for chromeOS someone will dump it and get it working though magic, but it would be illegal, and i dont think anyone has done that for roku's ARM(i am guessing) version

---

### Post by toupeiro on 2011-02-04
I do admit to being frustrated about the whole "not on linux" edict in the netflix camp.  That said, I use their service, and I have no plans on cutting them off solely because of their position on linux desktops and devices.  To me, it's just timing and knowledge.  I believe netflix will come around.  I don't think netflix understands linux desktops.  Not supporting linux is doing nothing but carving out niches for their competition which is definitely on the rise with rumors of Amazon including unlimited streaming to Prime customers and some of the other services popping up.  The Android market alone is a prime example of this.  Other services are already in this space getting paying customers.

DRM or not, guess what, if you support windows, and windows can be virtualized, I can make ffmpeg put exact dimensions around the video in that vm in a lossless format, and the DRM banter was all for nothing.  The people who want to exploit streaming content are going to do so.  Some of us, dare I say most of us, just want to use our OS of choice and be entertained, and are more than willing to pay for said entertainment.

As it happens, I am a fan of my Roku box, and so I have a delivery mechanism for netflix thats acceptable, but sure, I would like to use my services on my linux laptop when I am away on work.  If Amazon does extend this rumored unlimited streaming to prime members, that move would be enticing enough to say goodbye to netflix.  As mentioned in this thread, Amazon does support linux desktops and devices.

---

### Post by joekm on 2011-02-04
I get your point, but I actually have Ubuntu installed through VMplayer on Windows 7 so I can access tools only available through Linux.

So, it does happen ;)

> **marcottebj said:**
> This is definately not solved.  Virtual box is not a solution.  What's the point of running XP in a VM?  You still have to have a license for Windows.  Why not just run Ubuntu in a VM on XP? 
 
... oh wait... if you have XP, you really don't need Linux for anything.  
 
I have my blackberry syncing, I have my Ipod syncing, I can do my homework and open office documents, Evolution is a great free alternative to Outlook.  Now, if I could just watch movies on Netflix or use my Ubuntu PC as a media server to stream movies from Netflix to my PS3.  
 
Until that happens, I'll have to keep running Windows 7, and Ubuntu will just be a neat toy on a USB thumbdrive.

---

### Post by bug770515 on 2011-02-05
Funny, they don't like Android, too. Android is the most popular phone "open" operating system. It's Linux based.

at least Hulu works. \\:D/

---

### Post by theShaggy on 2011-02-18
It's disappointing that they don't seem amenable, even, to an Ubuntu-specific program in the non-free repositories or something.  Y'know, something built by them, with DRM involved, for Ubuntu-based systems.

Would that be completely contrary to the philosophy of the Linux movement, or is it workable?  You wouldn't be allowing the browser to run it with open-source Moonlight, rather you'd be running a program built like the Netflix apps on the Wii or PS3.

They do have an API developers forum, but it seems like these threads (here and also over on that forum) tend to devolve into "Man Windows sucks/Linux rocks/Microsoft is full of crap" discussions.

---

### Post by Cruisergeek on 2011-03-05
I would definitely be interested to see netflix work on ubuntu however one primary thought comes to mind when I think about Netflix on Ubuntu.  "My iphone and ipad are both linux and they work great."  Has anybody investigated how IOS receives the video.  I know IOS is an old form of linux and while I know I'm a very knowledgeable Windows developer and quite new to linux I do know that both IOS and Ubuntu are linux based and that simple IPA file might contain a tip or trick that would allow netflix to function on Ubuntu.

---

### Post by aysiu on 2011-03-05
> **Cruisergeek said:**
> I would definitely be interested to see netflix work on ubuntu however one primary thought comes to mind when I think about Netflix on Ubuntu.  "My iphone and ipad are both linux and they work great."  Has anybody investigated how IOS receives the video.  I know IOS is an old form of linux and while I know I'm a very knowledgeable Windows developer and quite new to linux I do know that both IOS and Ubuntu are linux based and that simple IPA file might contain a tip or trick that would allow netflix to function on Ubuntu.
The iPhone and iPad do **not** run Linux.

But there are other devices (for example, Roku box) that do run on Linux and stream Netflix.

---

### Post by StephenDavison on 2011-03-05
> **Cruisergeek said:**
> I would definitely be interested to see netflix work on ubuntu however one primary thought comes to mind when I think about Netflix on Ubuntu.  "My iphone and ipad are both linux and they work great."  Has anybody investigated how IOS receives the video.  I know IOS is an old form of linux and while I know I'm a very knowledgeable Windows developer and quite new to linux I do know that both IOS and Ubuntu are linux based and that simple IPA file might contain a tip or trick that would allow netflix to function on Ubuntu.

From where did you learn that Apple iOS is based on Linux?  I don't think that is true at all beyond the argument that Mac OS-X (and by extension iOS) and Linux have some common ancestry from UNIX.  

Regardless, I don't think any device using an embedded Linux kernel should be confused with a desktop/server Linux distribution.  That is as misleading as comparing something like Android or webOS to Ubuntu.  Consequently, something like a Roku player supporting Netflix has very little to do with supporting Netflix on Linux with Firefox.

Anyway, that's the way I understand the situation.  Correct me if I'm wrong.

---

### Post by gearard on 2011-03-05
We all have choices, Linux being one of them. I love netflix but mostly stream through the Roku box for the TV. You can view Hulu plus on Linux and should be able to view Amazon prime. both are subcription services but alternatives to Netflix.

---

### Post by The Flying Penguin on 2011-03-06
Practicality dictates that I run Windows in a VM for the sole purpose of streaming Netflix. I have some old computers sitting around with XP licenses though so its kinda like why wouldn't I take the only real workaround available that allows me stream Netflix while running Ubuntu?

I know some people see this as a bulky and awkward workaround but I feel it is rather effective considering there is nothing else I could do except stream Netflix from a dedicated PlayOn server that would run under Windows anyway and wouldn't due much good for me when I'm traveling due to my slow DSL I have at home.

I run an extremely stripped down version of XP called MicroXP. It uses around 40MB Ram upon startup and takes up around 300MB of space on a fresh install. It frees up enough resources that I am able to stream in full screen at my native resolution of 1366x768 without any stuttering. This is on a 1.3GHz Core 2 Duo cpu.

I setup the same thing on my mom's laptop except I created a shortcut on the top Gnome bar with a nice pretty Netflix icon that automatically launches the stripped down XP used solely for Netflix. I have it set so XP launches in full screen, hid the Widows taskbar, set Firefox to launch automatically in full screen mode, and set the instant que library on the Netflix website as the home page.

XP is now essentially an independent Netflix application that runs with minimal overhead and starts and is ready to watch in under 25 seconds. Honestly, it almost feels like I'm running a native Netflix app for Linux because the process feels so seamless and integrated despite using the website for movie browsing and playback. I may try setting up Zinc or a similar application which will act as front end for Firefox and provide a more tv friendly set-top box like experience with better remote support and movie navigation akin to a 360, Roku, etc. That would certainly complete the package.

This is all on a some budget AMD V120 2.2GHz single core cpu running at 1280x720 over HDMI.

If you have an XP license, I would at least give this method a try. If you lack a license, pick yourself up a junk computer from the curb on garbage day. The license stickers are almost always left on the case.  I've picked up a couple free XP licenses this way in the past. Free bloatware. Not a bad deal right? :P

Oh, and now that select Verizon Wirele ss 4G LTE Android smartphones will be able to play Netflix natively, perhaps a Netflix app won't be too far away. I've heard some talk that led me to believe the app may rely on code from select processors in order to work but I couldn't find any information supporting what I heard. The HTC Thunderbird apparently has a compatible cpu if restrictions do exist. The Netflix app been spotted on a running Thunderbird at the show Verizon put on not too long ago. The rep who was demonstrating the phone said they didn't have a strong enough signal inside the building otherwise he would have been able to give a demonstration but Netflix is indeed supported. We'll see if that holds true once its released.

EDIT: Yup. The app is going to rely on a form of hardware DRM.
[http://blog.laptopmag.com/netflix-for-android-demoed-on-qualcomm-ti-chips-with-drm-support](http://blog.laptopmag.com/netflix-for-android-demoed-on-qualcomm-ti-chips-with-drm-support)

---

### Post by ijumpship on 2011-03-08
Let me give my final thought to this as it was the post which made me rant and start.

If you are not welcome do not force the issue.

Quite frankly,I do not see the craze for Netflix.

Most of the time you want a special movie it will say that its not yet available to stream,yet you can get it via the post.

The other movies are available elsewhere,I understand the "Male Ego".We cannot get it so lets hunt it to submission.

The is one fight that not worth winning.

The other day,I called my "Outsource Support Service", I told her my OS she said in a tone "I am train in Windows and Mac,hence I cannot  resolve your problem,Get one of these OS and called back please"


What the heck every body want you to give up "Choice".Thanks for freedom I have a choice

and thats my dollar bill

---

### Post by aysiu on 2011-03-09
> **ijumpship said:**
> I understand the "Male Ego".We cannot get it so lets hunt it to submission. Don't forget the females on these forums... and also the males who do not fit into masculine stereotypes.

---

### Post by The Flying Penguin on 2011-03-09
Ok, so if you have a powerful enough machine to run Windows 7 in a virtual machine and aren't against doing so for any philosophical or ideological reasons but simply lack the license, then this should help.

I hope I am not out of line by posting this link. I sincerely apologise if I am. I am in no way trying to promote Microsoft. My sole  intent is to help my fellow Ubuntu users and those who are trying out  Ubuntu.  I've seen posts on this site from people who said Netflix was a major and sometimes the sole reason for not switching to Ubuntu. So hopefully, this will help add to the Linux population ;)

Anyway, here is the link for the free Windows 7 Enterprise 90-day trial that Microsoft offers. If all you are going to use it for is Netflix and a few other apps, then it wouldn't be that big of a deal to reinstall it four times a year. 32 and 64 bit download links are at the bottom of the page.

[http://technet.microsoft.com/en-us/evalcenter/cc442495](http://technet.microsoft.com/en-us/evalcenter/cc442495)

Too bad they don't offer an XP trial for download...

---

### Post by Cruisergeek on 2011-03-10
> **StephenDavison said:**
> From where did you learn that Apple iOS is based on Linux?  I don't think that is true at all beyond the argument that Mac OS-X (and by extension iOS) and Linux have some common ancestry from UNIX.  

Regardless, I don't think any device using an embedded Linux kernel should be confused with a desktop/server Linux distribution.  That is as misleading as comparing something like Android or webOS to Ubuntu.  Consequently, something like a Roku player supporting Netflix has very little to do with supporting Netflix on Linux with Firefox.

Anyway, that's the way I understand the situation.  Correct me if I'm wrong.

Sorry everybody.  I was troubleshooting a video driver issue for about 24 hours straight beforehand and was very tired and just wanted to watch some Netflix but my xbox was on the fritze.  I was confused when I said Linux and meant to say Unix.

---

### Post by ish05 on 2011-03-20
> **The Flying Penguin said:**
> I run an extremely stripped down version of XP called MicroXP. It uses around 40MB Ram upon startup and takes up around 300MB of space on a fresh install.

I created a shortcut on the top Gnome bar with a nice pretty Netflix icon that automatically launches the stripped down XP used solely for Netflix. I have it set so XP launches in full screen, hid the Widows taskbar, set Firefox to launch automatically in full screen mode, and set the instant que library on the Netflix website as the home page.

XP is now essentially an independent Netflix application that runs. I'm running a native Netflix app for Linux.

If you have an XP license, give this method a try.[/url]

I am not new to Linux. But, I am a novice. I am currently running LinuxMint10, which is an Ubuntu based OS, on several netbooks. The Dell Mini 910, Dell Mini 1012 and HP Mini 110. I have my XP licence and this sounds like a great way integrate netflix into my low spec Linux netbooks. I wonder if this workaround can be applied to the OnLive game service? I keep a Laptop running windows 7 for a few instances where I haven't yet got something working on Linux. Very interesting. Thank you.

---

### Post by winterlight on 2011-04-03
I'm a little new to the ubuntu world so...

I just tried getting microXP to run on my ubuntu machine.  it's a year old alienware so the specs are pretty high

The problem is microXP looks like a windows exe.  Running it with WINE makes WINE terminate with a "serious" error.  It seems like the microXP install has to be some kind of ubuntu executable.  (Just guessing here)

Any1 able to do this?

My overall goal is to watch Netflix on Ubuntu.  I was hoping a windows emulator running a browser with silverlight was the solution...

Thanks.

---

### Post by Richter12x2 on 2011-04-08
> **toupeiro said:**
> I do admit to being frustrated about the whole "not on linux" edict in the netflix camp.  That said, I use their service, and I have no plans on cutting them off solely because of their position on linux desktops and devices.

I've used Netflix for years and never really had a problem with their service.  But I have an Android phone, and run Ubuntu Linux, and Blockbuster just launched their Android streaming app.  If Blockbuster's service works on Linux and Android and is competitively priced, I'm going to say I have to consider changing partners.  I know Netflix had the market tied up for years, but at least if Blockbuster does eventually go under, maybe I'll have a few months of actual support while Netflix hopefully gets its act together.

---

### Post by SeijiSensei on 2011-04-08
> **Richter12x2 said:**
> But I have an Android phone, and run Ubuntu Linux, and Blockbuster just launched their Android streaming app.

You do know that Android != Linux, yes?  Android applets don't run natively on Linux, and any app like Blockbuster's must be a binary blob with the require DRM stuff inside.

---

### Post by Richter12x2 on 2011-04-08
> **SeijiSensei said:**
> You do know that Android != Linux, yes?  Android applets don't run natively on Linux, and any app like Blockbuster's must be a binary blob with the require DRM stuff inside.

I don't remember ever making that implication?  That was actually pretty succinct for one of my posts.  Let's do the Cliff's Notes thing:

Netflix doesn't support Android and it doesn't support Linux.  If Blockbuster supports both and is priced comparably, I'll ditch Netflix, even though I've been a Netflix subscriber for years.  I already have a Blockbuster App on my phone.

---

### Post by SeijiSensei on 2011-04-08
I missed the "if Blockbuster's service works on Linux and Android" part.  Sorry!  

It's hard to know what BB's fate will be, or why Dish Network wants it.  I think Dish may want the network of storefronts as much as anything else.  It gives them a ready-made physical infrastructure that they can use to start marketing to consumers in malls and the like.  Rather like the Apple Stores.

---

### Post by Elep.Repu on 2011-05-18
I agree that Virtualbox is not a solution.
Intel Celeron processors don't exactly excel at emulating operating systems just to run netflix. I'm downloading ReactOS right now just for kicks just to see if *that* works better. But probably not.

The video quality is horrendous

---

### Post by darkorical on 2011-05-18
So a few days ago Netflix started rolling out their android streaming app. I haven't had a chance to try yet but has anyone thought to try to use the droid sdk and the netflix app on Ubuntu?

---

### Post by nutz on 2011-05-21
It seems to me the best option is to just use a service that works with your computer. I signed up for Netflix back in the day when they streamed everything in Flash which worked perfectly. When they switched over to Silverlight I couldn't stream content anymore so I just canceled my service.

Let the ones that support platform agnostic standards be rewarded with your patronage. There are other companies out there that want your business.

---

### Post by Geremia on 2011-05-27
> **bug770515 said:**
> Funny, they don't like Android, too. Android is the most popular phone "open" operating system. It's Linux based.And their reason for not supporting Android is that it's not secure enough. Right...

---

### Post by Geremia on 2011-05-27
> **aysiu said:**
> But there are other devices (for example, Roku box) that do run on Linux and stream Netflix.And no one has ported these apps to Ubuntu?

---

### Post by Geremia on 2011-05-27
> **The Flying Penguin said:**
> Practicality dictates that I run Windows in a VM for the sole purpose of streaming Netflix. Why not use [WINE]("http://www.winehq.org/")? After installing WINE ([FONT=Courier New]sudo apt-get install wine[/FONT]), running```
winetricks ie8
```will install Internet Explorer 8. Then you probably need to install some Active X DLLs, etc. I haven't gotten this to work, but it seems promising if pursued.

---

### Post by aysiu on 2011-05-27
> **Geremia said:**
> And no one has ported these apps to Ubuntu?
They aren't apps.

---

### Post by aysiu on 2011-05-27
> **Geremia said:**
> Why not use [WINE]("http://www.winehq.org/")? After installing WINE ([FONT=Courier New]sudo apt-get install wine[/FONT]), running```
winetricks ie8
```will install Internet Explorer 8. Then you probably need to install some Active X DLLs, etc. I haven't gotten this to work, but it seems promising if pursued.
It doesn't work.

---

### Post by demiurgicdaemon on 2011-05-28
It is now supported on Android...guess they just weren't motivated to port before now
Wonder if anyone will have a workaround soon.

---

### Post by IWantFroyo on 2011-05-28
Workaround for what? I have Netflix on my rooted HTC Aria (from .apk). I hear Chrome is gonna get an extension soon, for in-browser streaming

---

### Post by Shpadoinkle on 2011-05-30
Does anyone know if it is possible to make the Netflix app for Android work on Ubuntu?

---

### Post by Geremia on 2011-05-30
> **Shpadoinkle said:**
> Does anyone know if it is possible to make the Netflix app for Android work on Ubuntu?There's an Android app for Netflix? I thought it was still unsupported.

---

### Post by aysiu on 2011-05-30
> **Geremia said:**
> There's an Android app for Netflix? I thought it was still unsupported.
They support about five Android devices officially. Some other ones you can get working if you're rooted.

---

### Post by The Flying Penguin on 2011-06-04
> **Geremia said:**
> There's an Android app for Netflix? I thought it was still unsupported.

Yes, but they only officially support like five devices so it will only show up in the Market if you have one of those devices. Otherwise you have to download the .apk elsewhere.

> **aysiu said:**
> They support about five Android devices  officially. Some other ones you can get working if you're  rooted.

Yeah, I have it working on my Thunderbolt. I rooted it and installed the  CM7.1 pre-alpha as that was the only rom it would work on at the time.  There is a patch now to get it working on other rooted roms as well.

I have Hulu working too. I feel so naughty lol :p

---

### Post by Geremia on 2011-06-04
> **The Flying Penguin said:**
> Yeah, I have it working on my Thunderbolt. I rooted it and installed the  CM7.1 pre-alpha as that was the only rom it would work on at the time.  There is a patch now to get it working on other rooted roms as well.Is rooting the same as installing Gingerbread? I didn't want to do that because the sources came from possibly suspicious URLs, not the Android developer website.

---

### Post by The Flying Penguin on 2011-06-05
> **Geremia said:**
> Is rooting the same as installing Gingerbread? I didn't want to do that because the sources came from possibly suspicious URLs, not the Android developer website.

No its not the same. Gingerbread is simply the next version of Android being released for smartphones. Rooting gives you super user power and is a seperate procedure. However, unless your carrier releases an official Gingerbread update, you will have to root your phone before you can update it to one of the community developed gb roms.

Xda is a trusted source to get roms. You wont have to worry about anything malicious if you get one there.  That's where I got my Gingerbread rom with Netflix support from. I'm not about to wait around on Verizon or Netflix when there is such a great community actually solving problems and bettering the Android experience.

---

### Post by perlwonk on 2011-06-10
I watch Netflix from a Linux box every night. How? I went to Fry's and bought a Boxee Box. I love it. My guess is we can't watch Netflix from Ubuntu for licensing reasons. This is not helpful and needs to be fixed. The problem is, it's a political fix and not a technical one.

---

### Post by omskates on 2011-06-15
> **perlwonk said:**
> I watch Netflix from a Linux box every night. How? I went to Fry's and bought a Boxee Box. I love it. My guess is we can't watch Netflix from Ubuntu for licensing reasons. This is not helpful and needs to be fixed. The problem is, it's a political fix and not a technical one.

Boxee Box has the DRM embedded in its chip.  Its all about the DRM.  Some root their phones but they already had the DRM support there.  OEM builds of Android won't give you the DRM needed, nor will any FOSS app for Ubuntu.

---

### Post by rico001 on 2011-06-21
> **The Flying Penguin said:**
> Ok, so if you have a powerful enough machine to run Windows 7 in a virtual machine and aren't against doing so for any philosophical or ideological reasons but simply lack the license, then this should help.

I hope I am not out of line by posting this link. I sincerely apologise if I am. I am in no way trying to promote Microsoft. My sole  intent is to help my fellow Ubuntu users and those who are trying out  Ubuntu.  I've seen posts on this site from people who said Netflix was a major and sometimes the sole reason for not switching to Ubuntu. So hopefully, this will help add to the Linux population ;)

Anyway, here is the link for the free Windows 7 Enterprise 90-day trial that Microsoft offers. If all you are going to use it for is Netflix and a few other apps, then it wouldn't be that big of a deal to reinstall it four times a year. 32 and 64 bit download links are at the bottom of the page.

[http://technet.microsoft.com/en-us/evalcenter/cc442495](http://technet.microsoft.com/en-us/evalcenter/cc442495)

Too bad they don't offer an XP trial for download...
Actually I think XP has a 30 day activation by default?

Speaking of android there is an android sdk, that allows you to install and run an emulated SD card image, wonder if that would work?  Netflix - Android Market, and then instructions for the windows emulator are here, but you could grab the linux build,:  [http://www.howtogeek.com/howto/21831/how-to-test-drive-google-android-on-your-pc-without-buying-a-phone/](http://www.howtogeek.com/howto/21831/how-to-test-drive-google-android-on-your-pc-without-buying-a-phone/) it requires Java also, for the Google android market it says you need a google login, You probably need a quad core, its slow

---

### Post by Adonn on 2011-07-17
I think XBMC (the Media Center that's ported to several OS's), works for this ... If you install the xbmcflicks addon, it will stream your movies to the media center from netflix.

---

### Post by The Flying Penguin on 2011-07-23
> **Adonn said:**
> I think XBMC (the Media Center that's ported to several OS's), works for this ... If you install the xbmcflicks addon, it will stream your movies to the media center from netflix.

Xbmcflicks will only stream under Windows. It basically just embeds IE or FF in xbmc so Silverlight is still required.

---

### Post by perspectoff on 2011-07-25
The Netflix app for Android is here:

[https://market.android.com/details?id=com.netflix.mediaclient](https://market.android.com/details?id=com.netflix.mediaclient)

The Android OS can be installed into a Virtualbox (or QEMU or VMWare) virtual machine using the Android-i86 installer found here:

[http://www.android-x86.org/documents/installhowto](http://www.android-x86.org/documents/installhowto)

---------------------------------------------------------------

The alternative is to install the 32-bit Linux Android SDK, which provides an emulator. This requires:

ia32-libs
sun-java6-jdk

and the Linux Android SDK found here:
[http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

Then the ADB is used to install apps:
[http://developer.android.com/guide/developing/tools/adb.html](http://developer.android.com/guide/developing/tools/adb.html)

Canonical is reportedly working on a method to run Android apps without having to install a full Android environment, but they've been at it for about 2 years, so who knows.

---

### Post by aysiu on 2011-07-25
> **perspectoff said:**
> The Netflix app for Android is here:

[https://market.android.com/details?id=com.netflix.mediaclient](https://market.android.com/details?id=com.netflix.mediaclient)

The Android OS can be installed into a Virtualbox (or QEMU or VMWare) virtual machine using the Android-i86 installer found here:

[http://www.android-x86.org/documents/installhowto](http://www.android-x86.org/documents/installhowto) Have you actuall run Netflix on Android through VirtualBox?

---

### Post by tjones00 on 2011-07-26
> **Adonn said:**
> I think XBMC (the Media Center that's ported to several OS's), works for this ... If you install the xbmcflicks addon, it will stream your movies to the media center from netflix.


Can anybody verify this statement. If it's true it's huge news.

[http://forum.xbmc.org/showthread.php?t=87552](http://forum.xbmc.org/showthread.php?t=87552) states
> **Limitations:**
Windows and OSX - All Features will work
Linux - No Playback Support, you could use it to add/remove/search for items, but playback will not work
 - Linux Playback is not supported and will not be unless Microsoft  makes Silverlight for Linux, or Netflix uses something else (There's  some chatter about HTML5). There are no workarounds at this time.

 dated *Last edited by fekker; 2011-01-07*


HTML5 sounds interesting

---

### Post by ifraser on 2011-08-04
> **ronnielsen1 said:**
> It beats a wii. A wii is equivalent to a P3 768 MHZ

Hah, try playing a few games on a Wii emulator (if you can find a good one), then come back and talk.  Try even running a GameCube game using Dolphin: I bet you have framerate issues.  The problem with the console-emulation-thing isn't CPU speed, it's the graphics cores.

---

### Post by allmaechtig on 2011-08-08
Could we try and use moonlight to get netflix to run. somehow forcing it to push that program rather then silverlight? just an idea that popped into my head this morning...

---

### Post by aysiu on 2011-08-08
> **allmaechtig said:**
> Could we try and use moonlight to get netflix to run. somehow forcing it to push that program rather then silverlight? just an idea that popped into my head this morning...
No, Moonlight doesn't work for Netflix.

---

### Post by kansasnoob on 2011-08-08
I finally cut off my cable due to financial constrictions ................ well I didn't like most of the local stuff anyway and I was down to the "local" plan, and I prefer being able use the computer because it's truly interactive :)

With my setup I can easily watch videos on my 22" wide-screen monitor while fiddling around with my older PC :)

But it would be nice to be able to stream Netflix using Ubuntu. I really don't want to do the USPS route. The idea of sticking discs that have been handled by who knows who into my computer bothers me.

I hope something breaks soon :D

---

### Post by aysiu on 2011-08-08
While it would be nice to stream with Ubuntu, there are so many other devices that will stream Netflix: PS3, Wii, iPad, iPhone, Android phones, Roku...

---

### Post by kansasnoob on 2011-08-08
> **aysiu said:**
> While it would be nice to stream with Ubuntu, there are so many other devices that will stream Netflix: PS3, Wii, iPad, iPhone, Android phones, Roku...

I'm leaning towards this from WD:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136593](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136593)

But that'll be a month or two or three :)

I can do Hulu and Hulu plus just fine on my PC so I'm not media starved ;)

BTW the new Roku (Roku2) boxes kind of made me mad because only the most expensive has "wired" capabilities :mad:

---

### Post by slavinzing56 on 2011-08-08
[COLOR=black][FONT=Verdana]Yes.. well stated.  Although we can all appreciate what Ubuntu symbolizes; you may be overstating it a bit (in my opinion).  [/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I’m for using one OS.  Live  with it’s limitations, and move on.  If we can get something to work…  great! That’s why I search these threads, but I feel my time gets wasted  when I find a thread marked solved, but the solution is simply “run  Windows”. [/FONT][/COLOR]

[COLOR=black][FONT=Verdana]My original thread was simply an attempt to point out how silly that is from the standpoint of a pragmatist.  I mean.. C’mon![/FONT][/COLOR]

---

### Post by aviedw on 2011-08-08
> **anjilslaire said:**
> Netflix is a native app on the PS3,no computer needed at all. No need for Windows for that purpose.
I was actually going to suggest the same thing. I have apple TV and PS3. I have each device connected two different tv's. But what i do not understand is that if Netflix is internet based and nothing is really installed on the computer to watch the movies, why doesn't it work. The type of browser should be the biggest hurdle. I'm wondering if chrome or firefox could construct a add-on that would allow for the viewing of the videos.

---

### Post by buckeyered80 on 2011-12-29
Try Amazon Prime. It works nicely on Linux.

---

### Post by 231 on 2012-01-14
i feel that windows is doing a monopoly on using net flix !,and is prejudiced to boot ! You can get net flix if you have a blu ray dvd connected to the internet,4g cell phones that have nothing to do with windows at all. i am a member of net flix i have 2 pc asus net books Eee one with windows xp no problem i can use google chrome,or explorer I have a second pc same make,but a system you xubuntu
 I use Google chrome and meet the requirements except it is not micro soft windows I do not know who is responsible for not letting me use the system I just spoke with some one from Verizon i  asked him how are they allowed to use netflix if i under stood something about the system and i may not have met the requirements . As far as that is concerned 0s13 or higher and i asked at net flix i thought it had to do with the pc. He said no it was just that it is not windows i told him i can get sy fy you tube,hulu,crackle ch4,7,
etc he under stood but said not windows
   I said the same thing rep from Verizon. He said might be need-
ing a flash player. What do you think?

---

### Post by #HardCrash# on 2012-01-16
This might be a dumb question but im new to linux. If all the new phones are linux kernal based and netflix works on them, then is there a way to install the apk on a desktop? I havent tryed it at all but it makes scence that it might work. And on another point the only reason that I can find that netflix wont work is that the desktop version requires silver light, ( witch to the best of my knolage is just anti pirating softwate ) witch is microsoft only. So is there a way to emulate this software or trick netflix into thinking its there?

---

### Post by SeijiSensei on 2012-01-16
> **#HardCrash# said:**
> This might be a dumb question but im new to linux. If all the new phones are linux kernal based and netflix works on them, then is there a way to install the apk on a desktop?

Android may use a Linux kernel, but it has a lot of other stuff to boot.  Much of it is Java-based. So no.

> And on another point the only reason that I can find that netflix wont work is that the desktop version requires silver light, ( witch to the best of my knolage is just anti pirating softwate ) witch is microsoft only. So is there a way to emulate this software or trick netflix into thinking its there?

That's an incorrect description of Silverlight, and there is an open-source clone called Moonlight, but it won't work with Netflix.  Netflix uses the proprietary "digital-rights-management" code in Silverlight to restrict access and copying.

All of this has been covered in numerous postings in this and other Netflix-related threads.  Did you read this thread from the beginning?  I recommend that as a policy before posting in other threads from now on.

---

### Post by ijumpship on 2012-03-03
I Hate when people re-hash or flog  a dead horse.
Silverlight is neither anti-piracy or worth griping about.

Anybody who think they can stop people from copying or distributing are downright off their flipping rockers.

They are just preventing you and me and making us dumber and dumber,while other countries around the world are creating waves and making something better than them.

Just look at 8  and  6 cylinder cars.While one country was hook to those gas guzzlers, another was producing 4 cylinders and becoming first world at it.Anything you produce today people will make better than it.
It is why you ought to continue developing what you have or come with better ideas.**Creativity**,It is Called.**STOP Making US DUMB **and call it piracy.

When the first record cut on vinyl some body was there to carry it on,now we have MP3 Players.Do you want us to still use vinyl or Cassette tapes? while the world is using MP3s

Now to my Gripe. Get some form of other media Players and stop complaining.Search for answers.I use Roku as my front ends hook to My back-end so I have the pleasure of all worlds.

Once you have mythbuntu setup,man all your world is done.Cut the cable save you money and forget the griping.Maybe another country have long since create there Netflix alternatives and is laughing at us now.

Soon we have to borrow money from them,purchase that same service,we are restricted from.
Its Like a father hiding the booze but him and his friends are having a wonderful time.STOP THE Griping.

Thank everbody for Linux,I smell freedom,I Taste it ,I eat it.No More activation,virus cleanising, pin to the donkey tails.

Thank You all developers,I have seen the Light,Not the incoming Train

---

### Post by ex_isp on 2012-03-08
Best explanation of why no Netflox (deliberate) on Linux

Reed Hastings is not only CEO of Netflix but on the board of Microsoft, food for thought.

Read more here:
[http://www.techrepublic.com/blog/opensource/the-netflix-linux-conjecture-how-netflix-snubs-the-linux-community/1745](http://www.techrepublic.com/blog/opensource/the-netflix-linux-conjecture-how-netflix-snubs-the-linux-community/1745)

Would love to hear opines on this... I'll be "listening"

Ex

:popcorn:

---

### Post by chrisgianti on 2012-05-06
!!!???POSSIBLE SOLUTION???!!!

Hi guys. Thanks for all the positive posts in here. I was reading and something just occurred to me.

When I read this whole thing, I thought 'well we can all watch netflix on android' if not Ubuntu.

Then I thought...aren't android phones Linux based? I remember reading that when I was researching rooting my phone. And I looked it up just now..."**[B]Android**[/B] is a **[B]Linux**[/B]- **[B]based**[/B] operating system for mobile devices such as smartphones"

So, if you can watch Netflix movies on an android phone with an android app called Netflix, which is Linux based, can't you run that app on your computer?

Hence watch netflix on ubuntu...by running it as an android application on Ubuntu

[http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml](http://news.softpedia.com/news/How-to-Run-Android-Applications-on-Ubuntu-115152.shtml)

I'm a Linux newbie...been using Ubuntu for 4 weeks (trying to get GNS3 to communicate with Virtual Box which I've failed at, btw)...so I might not be able to get this one to work for a few weeks, but I know there's some Linux geniuses in here which will do it like butter.

I hope ya'll can run with this ball...

---

### Post by aysiu on 2012-05-06
> **chrisgianti said:**
> 
So, if you can watch Netflix movies on an android phone with an android app called Netflix, which is Linux based, can't you run that app on your computer? No, you can't.

> Hence watch netflix on ubuntu...by running it as an android application on Ubuntu Give it a shot. It won't work.

From [How to watch Netflix (Watch Instantly) in Linux](http://how-to.wikia.com/wiki/How_to_watch_Netflix_%28Watch_Instantly%29_in_Linux): > This how to works around this problem in a very non-ideal way. It relies on running Windows in Linux. > **Other methods that DON'T work** ... Android SDK's Android emulator, and run the Android Netflix app[list][*]Android SDK
    [*]Android SDK's emulator
    [*]Note: This is rather unlikely to work on account of the slow speed of the ARM emulator.
    [*]Further note: this has been tested and does not in fact work with the current netflix app, which runs in the emulator, but fails when trying to play a movie (as of 9/2011)[/list] I'm retitling this thread "no native method" so people don't keep coming here looking for a solution. When there is a solution, I will retitle the thread back.

---

### Post by moocow1452 on 2012-05-09
> **aysiu said:**
> I'm retitling this thread "no native method" so people don't keep coming here looking for a solution. When there is a solution, I will retitle the thread back.


Kind of a Thread Hop, but I know there was the PCSX2 method that was kicking around Reddit for a while. It only works on paper afaik, but has anyone gotten a proof of concept off the ground?

[http://www.reddit.com/r/linux/comments/kzlaf/want_netflix_on_linux_with_pcsx2_now_you_can_has/](http://www.reddit.com/r/linux/comments/kzlaf/want_netflix_on_linux_with_pcsx2_now_you_can_has/)

---

### Post by aysiu on 2012-05-09
There are a lot of methods that work on paper. Until someone posts a how-to that more than one person responds back with "This worked for me!" that involves Ubuntu Linux and does not involve Windows virtualization or some kind of slingbox scenario, then I'm keeping the thread titled as is so as not to mislead people that the working method is contained within.

---

### Post by kansasnoob on 2012-07-15
Does anyone else have trouble with Crackle also?

I've tried a few flicks on my old Win XP box that I use for Wubi testing and some videos will play (sadly no full screen due to P4M800 gpu) but on Ubuntu they totally fail to load :(

If vet bills weren't eating me alive I'd grab a ROKU but the dogs come first :)

It's rough with nothing but HULU right now :(

Edit: It's also election time so even the news sucks :^)

---

### Post by moocow1452 on 2012-07-15
In theory, you could use PlayOn or Plex to stream the Netflix and Crackle over if you still have an XP box, also use Remote for VLC and the PlayOn mobile app on Android to be able to airplay to a old box that could never handle flash, but can do preprocessed transcodes okay,

There is also the theoretical PS2 emulator workaround, but you would be the first to get it to work

---

### Post by kansasnoob on 2012-07-15
> **moocow1452 said:**
> In theory, you could use PlayOn or Plex to stream the Netflix and Crackle over if you still have an XP box, also use Remote for VLC and the PlayOn mobile app on Android to be able to airplay to a old box that could never handle flash, but can do preprocessed transcodes okay,

There is also the theoretical PS2 emulator workaround, but you would be the first to get it to work

I already know about Netflix. I was just curious about other users experience with Crackle :)

It seems like a crap-shoot to me. Most of the time I can search a movie title in Hulu and if it's available on Crackle I can watch it.

But if I go straight to Crackle and dig it up it typically won't play. Seems odd :confused:

I'd love to watch Seraphim Falls. I know it bombed at the box office but I must see myself :D

---

### Post by bobsan on 2012-07-15
Hi,

I just tried. Crackle works perfectly in Firefox and Chrome. But in Chrome you need to disable adblock or the video won't load. In FF it will load even if adblock is activated. Hope that helps.

---

### Post by kansasnoob on 2012-07-15
> **bobsan said:**
> Hi,

I just tried. Crackle works perfectly in Firefox and Chrome. But in Chrome you need to disable adblock or the video won't load. In FF it will load even if adblock is activated. Hope that helps.

Far out! I never even thought about checking add-ons :(

Works like a snap now :D

Watching Christine, love it because my first car was a '58 Dodge Coronet Lancer.

---

### Post by perspectoff on 2012-12-30
There is a new Netflix-desktop app that runs under Wine in Ubuntu. It is available from a Launchpad repository here:

[https://launchpad.net/~ehoover/+archive/compholio](https://launchpad.net/~ehoover/+archive/compholio)

---

### Post by Hylas de Niall on 2013-01-07
Slightly off topic, but the latest Fuduntu comes netflix wine enabled.

*'Netflix! Netflix is now on Fuduntu. As stated in an earlier announcement, using the development tree of WINE and a new patch that allows for Silverlight to work in WINE, Netflix is now available on Fuduntu by simply installing netflix-desktop and then running it from Applications > Sound & Video > Netflix Desktop.'*

[http://www.fuduntu.org/blog/2013/01/07/fuduntu-2013-1-release/](http://www.fuduntu.org/blog/2013/01/07/fuduntu-2013-1-release/)

---

### Post by moocow1452 on 2013-01-07
Makes sense, I can run it on Peppermint AOK, so it should be able to run just fine and dandy on other Debian based systems, if not more universally.

---


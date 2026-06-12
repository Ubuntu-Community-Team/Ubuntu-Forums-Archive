---
title: "Kick a dead horse Pulseaudio thread"
date: 2009-02-05
forum: Recurring Discussions
---

### Post by ridetheteapot on 2009-02-05
K, i'm sure there is 1 million threads already but i have to vent.
I hate pulseaudio, i hate it so hard.

What is the point first of all?
alsa still has to be around (and so does esound if you don't want to lose features)
dmix was a pretty fine solution for software mixing, and i never had a problem with it, furthermore what can pulse do that jack + alsa/dmix didn't already do?
What about line-in? Do all setups use alsa for line-in passthrough (and is it because pulse is high latency??)

Personally I am really surprised that pulse is already so mainstream, it seems like its half finished.

The only new feature i have noticed is seprate sound servers for each user... but logging out and back in kills pulseaudio in such a way that its still running but no sound comes out so i can't really use it anyway.

pulse doesn't replace anything or add new features, and at least for me is just something i have to CONSTANTLY tinker with to keep running correctly.

Solved ------------------------

Personally now pulse is running much nicer; and i guess that fast tracking out before it was ready got it stable much faster - not to mention compatibility with legacy sound is pretty righteous now. lazerous

---

### Post by wolfen69 on 2009-02-05
just uninstall it and use alsa. i did, and it works great now.

---

### Post by Martje_001 on 2009-02-06
> **ridetheteapot said:**
> pulse doesn't replace anything or add new features, and at least for me is just something i have to CONSTANTLY tinker with to keep running correctly.
I *does* add new features.

See it this way: Alsa is primitive. If we never include Pulseaudio by default, bugs will never get fixed and we will be stuck with our primitive Alsa for another 5 years :).

---

### Post by Vince4Amy on 2009-02-06
> **Martje_001 said:**
> I *does* add new features.

See it this way: Alsa is primitive. If we never include Pulseaudio by default, bugs will never get fixed and we will be stuck with our primitive Alsa for another 5 years :).

Primitive or not Alsa actually works. Nearly Every Distro which uses PulseAudio is unusable to me now unless I remove it, but in some distros I can't do that as it takes away most of the system. 

I do believe that it's not Pulseaudio which is at fault though, it's the developers who can't implement it properly, it works with no problem at all on Fedora for example. But for the most part until it gets implemented properly I say Pulseaudio has gotta go.

---

### Post by jbysmith on 2009-02-06
I can understand the resentment against Pulse.  When it was first pushed I had all sorts of problems with it.  Granted, it *does* add a lot of neat features, but was nowhere near as stable as ALSA.  

Definitely going to have some "growing pains", as it's a work in progress.  Personally, I would have loved to see an option in the installer where you can specify to use either the stable ALSA or the experimental PulseAudio.  

Once they get all the kinks worked out and the third party code supports it better, it'll be very nice.  The features it provides are pretty snazzy. 

Isn't specific to Linux either.  Vista went through this exact same sort of thing.  (I *have* to have it on a partition unfortunately for my line of work.)   The jump from XP to Vista completely borked audio drivers for some manufacturers due to *major* changes under the hood.  Anyone with a Creative Labs card knows the pain on this one... the whole half-assed Creative drivers vs the "illegal" Daniel_K driver fiasco was especially ugly if you follow Creative Labs forums. So much flaming against CL I had to turn up the air conditioning every time I read their forums.

---

### Post by ridetheteapot on 2009-02-06
i got rid of pulseaudio.... back to normal operation.
With alsa i can just configure it and not look at it again, as it is i have had basiclly the same asound.conf for years know that i just drop on a new machine.
I don't really know what you mean by primitive, but if you mean basic, i have to say thats my favorite part.

and i don't know about new features... but i like having jack installed and its got a lot of the same features that make pulseaudio cool.

I guess i see why what you mean about having bugs worked out faster if its included by default... but then again that kind of means that ubuntu's 'just works' goodness is sacrificed a little.

---

### Post by Vince4Amy on 2009-02-06
> **ridetheteapot said:**
> i got rid of pulseaudio.... back to normal operation.
With alsa i can just configure it and not look at it again, as it is i have had basiclly the same asound.conf for years know that i just drop on a new machine.
I don't really know what you mean by primitive, but if you mean basic, i have to say thats my favorite part.

and i don't know about new features... but i like having jack installed and its got a lot of the same features that make pulseaudio cool.

I guess i see why what you mean about having bugs worked out faster if its included by default... but then again that kind of means that ubuntu's 'just works' goodness is sacrificed a little.

Yes I do think that it should have been out of 8.04 (Definitely out of 8.04 as it has a terrible implementation and it's LTS and it hasn't has any updates to make it work better yet, you still have to tweak it to get it to work properly) perhaps it should have been held off of 8.10 as well.

---

### Post by solwic on 2009-02-06
*kicks the dead horse on his way past the thread*

Pulseaudio sux!  ALSA RULEZ!

WOOOOO!

:rolleyes:

---

### Post by zero244 on 2009-02-06
I totally agree, pulse audio has caused me problems as well.
I found a way to work around pulse audio without removing. At least I think I have.

If you uncheck it on sessions, does that disable it.?


Ive read if you remove it, it messes up your gnome desktop id. Making updates tricky.

---

### Post by wolfen69 on 2009-02-06
> **zero244 said:**
> 


Ive read if you remove it, it messes up your gnome desktop id. Making updates tricky.

well, i've uninstalled pulse 3 seperate times with no ill effects. then again, i don't update everything. i kind of pick and choose when it comes to the optional updates.

---

### Post by ridetheteapot on 2009-02-07
> Ive read if you remove it, it messes up your gnome desktop id. Making updates tricky.

i already had dumped the ubuntu-desktop package because of other stuff i got rid of (ie gstreamer), all its for is if ubuntu thinks that an app is integral to ubuntu they can add it as a dependency of the desktop package so it will automatically get installed next time gnome-desktop updates (thanks but no thanks)

---

### Post by markbuntu on 2009-02-07
The problems with pulseaudio in Ubuntu are myriad and for the most part the fault of Ubuntu.

1. Pulseaudio was deployed before it was ready. This is sort of understandable since Hardy is going to be around until 2011 and just sticking with alsa would have precluded much of what pulse brings to the party for years. Firefox 3.0 was also not ready so consider that. 

2. Even more egregious, the tools needed to control and use pulseaudio, like the volume control, were left out of the desktop seed. As a result users were left with no way to actually use pulseaudio. They also left a lot out of the alsa libs and pulse modules that would make everything work together.

3. The default sound configuration was set up in a manner that guaranteed that users, especially those migrating from previous releases, would have nothing but trouble and frustration with their sound using applications as soon as they treid to use anything but rythmbox.

Sometimes I think that someone among the Ubuntu devs deliberately sabotaged the whole scheme with reasonable arguments that ultimately resulted in this catastrophe.

OK, that is the end of my ranting, now for the good things.

The days of one hardware device for your listening and talking pleasure are over and the alsa sound server is unable to deal with that in any reasonable fashion. People are plugging in all sorts of devices to their computers that need sound services. Pulseaudio makes it very easy to use multiple hardware devices. 

There is another deeper consideration that many are not aware of. Sound hardware drivers have moved to the kernel so new protocols for accessing them need to be enforced for security reasons. Applications should not be able to access the hardware drivers directly. In fact they should not care or know what the hardware is. Pulseaudio strictly enforces this protocol so many applications, like wine and audacity and skype failed with pulseaudio because they make assumptions about hardware or try to control it. The wine devs have even fessed up to this.

The alsa sound server, implemented before the drivers moved to the kernel, allows applications to directly address the hardware. This creates security problems in the kernel space.

We are in a transition period now. The low level sound hardware drivers have moved to the kernel and the kludged together alsa sound server is not up to the task of providing sound services and protecting the kernel space and so must be rewritten or abandoned. Pulseaudio can protect the kernel space but is not quite up to the task of providing the services.

But this is the situation in Ubuntu Hardy and Intrepid which are using pulse 0.9.10 which is now almost a year old. There has been much progress over the last year and the latest pulseaudio release 0.9.15 is in final testing. It fixes many of the problems and adds much of the stability and functionality missing from 0.9.10 like detection of digital devices and better bluetooth support.

We can only hope that Ubuntu makes a better effort with Pulseaudio in Jaunty and backports these improvements to Hardy and Intrepid.

If you have more than one sound making device and are using pulseaudio

---

### Post by wolfen69 on 2009-02-08
> **markbuntu said:**
> 
We can only hope that Ubuntu makes a better effort with Pulseaudio in Jaunty and backports these improvements to Hardy and Intrepid.

If you have more than one sound making device and are using pulseaudio

sometimes unfortunately, things must regress to move forward. and the only way to get feedback and improve, is to release early and get it out to as many people as possible. some people see this as bad, and others see this as necessary. i lean towards the necessary group. linux does not have billions of $$ to throw at problems, therefore we need the community to come together and tackle these issues head on.

someday soon, pulse audio problems will be a thing of the past, and they will have people like the early adopters to thank. good or bad, that's how it is. see also KDE4.

---

### Post by Vince4Amy on 2009-02-08
The thing is though, Pulseaudion in Hardy is **Still** broken and this is an LTS release, even if I use Hardy with the latest updates to 8.04.2 Pulse is still broken and I either remove it or go on these forums and fix it. But yes as I've said before the fault is not with pulse as it works great in Fedora.

---

### Post by za.zen on 2009-02-09
> **Vince4Amy said:**
> The thing is though, Pulseaudion in Hardy is **Still** broken and this is an LTS release, even if I use Hardy with the latest updates to 8.04.2 Pulse is still broken and I either remove it or go on these forums and fix it. But yes as I've said before the fault is not with pulse as it works great in Fedora.

I've always wondered what is so broken about Pulse audio.  I mean, I have sound in every application I run, and I use Pulse (I think).  

What's the big deal with it?

---

### Post by Vince4Amy on 2009-02-09
It's little things like when on Youtube watching a video and then sound in aMSN Stops working, It's simple little things but this is LTS so I'd expect it to be fixed. It does work in Intrepid.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) - That is incredibly useful for people but it's sometimes easier to just uninstall pulse. Too many distros implemented too soon, openSuSE 11.0 (Gnome), Ubuntu 8.04, Fedora 8 (Though this got fixed in 9 and works flawlessly in 10).

---

### Post by za.zen on 2009-02-09
> **Vince4Amy said:**
> It's little things like when on Youtube watching a video and then sound in aMSN Stops working, It's simple little things but this is LTS so I'd expect it to be fixed. It does work in Intrepid.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) - That is incredibly useful for people but it's sometimes easier to just uninstall pulse. Too many distros implemented too soon, openSuSE 11.0 (Gnome), Ubuntu 8.04, Fedora 8 (Though this got fixed in 9 and works flawlessly in 10).

I see.  I've noticed similar issues (like losing sound in Rhythmbox when Firefox is open to a page like yahoo.com that uses Flash).  I didn't realize that this was why nobody liked Pulse.  

Thanks for the info.  :)

---

### Post by BLTicklemonster on 2009-02-09
If Pulse Audio were a joke, Henny Youngman would be telling it. It's that bad.
It's so bad that networking with windows computers is better. It's that bad.


well, that's my opinion, anyway.

:popcorn:

---

### Post by Rhemat on 2010-02-22
I've been having problems with PulseAudio, and it is worse than losing sound in one application, when I open another application with sound.  When PulseAudio breaks on me, it takes every application that uses sound with it.  Firefox will hang if I try to view a flash object, so does Rhythmbox, PRBoom, etc.  What's worse, is that it likes to break on me every two days.  It seemed fixed for a while, and I thought that a patch had fixed it.  Yesterday, however, in the middle of a session, PA just breaks.  So I have to reinstall it.
Now, if I read correctly from one of the previous posts, the Ubuntu-Desktop package that depends upon PA isn't the actual Gnome Desktop, just Ubuntu specific items?  If that is the case, I would love a guide to leave out PA.
If any Ubuntu Developers are reading this:  Give us the option to use PulseAudio, don't force it on us.

---

### Post by 3rdalbum on 2010-02-22
> **Rhemat said:**
> 
If any Ubuntu Developers are reading this:  Give us the option to use PulseAudio, don't force it on us.

Please create a new thread rather than bumping this ancient (in Linux terms) post.

---

### Post by jounihat on 2010-04-09
> **3rdalbum said:**
> Please create a new thread rather than bumping this ancient (in Linux terms) post.

I think the post is not so ancient, as the same PulseAudio problems still exist. It Should be ancient, but it isn't.

Just replaced PA with Alsa. The flash in Firefox loses sound after a while, and sound in Wine is not working if any other program is using sound. I hope no one is actually getting paid for developing this thing. Yes, I know some testing can be done by the users, but if even the basic things (hello! flash is the #1 thing today!) are not working, someone should take a look in the mirror.

---

### Post by rifter on 2010-04-14
> **jounihat said:**
> I think the post is not so ancient, as the same PulseAudio problems still exist. It Should be ancient, but it isn't.

Just replaced PA with Alsa. The flash in Firefox loses sound after a while, and sound in Wine is not working if any other program is using sound. I hope no one is actually getting paid for developing this thing. Yes, I know some testing can be done by the users, but if even the basic things (hello! flash is the #1 thing today!) are not working, someone should take a look in the mirror.

I agree.  I find especially hilarious markbuntu's defense of pulseaudio:
> 
We are in a transition period now. The low level sound hardware drivers have moved to the kernel and the kludged together alsa sound server is not up to the task of providing sound services and protecting the kernel space and so must be rewritten or abandoned. Pulseaudio can protect the kernel space but is not quite up to the task of providing the services.

But this is the situation in Ubuntu Hardy and Intrepid which are using pulse 0.9.10 which is now almost a year old. There has been much progress over the last year and the latest pulseaudio release 0.9.15 is in final testing. It fixes many of the problems and adds much of the stability and functionality missing from 0.9.10 like detection of digital devices and better bluetooth support.

We can only hope that Ubuntu makes a better effort with Pulseaudio in Jaunty and backports these improvements to Hardy and Intrepid.


Well here it is 2010, with Karmic and we still have major problems with pulseaudio in performance as well as just plain working at all.  Heck we even have a thread declaring that _[color=blue][thread=1368141]sound is the worst problem in Karmic because of pulseaudio[/thread][/color]_.

Honestly I would like to know what these "features" are that make pulseaudio so great, and why it is somehow better than more venerable mixers like esd.  To me the only reason we have a mixer is that unlike other OSs the audio drivers don't mix sound (which according to that thread is not even true anymore with ALSA), which is a whole other ball of wax.  We've had to put up with mucking with mixers all this time in linux because of that, but it seems silly to always be switching horses as soon as things start to work.

In any case, several people in this thread have said that there are features in pulseaudio that make it "cool" and such.  Well what are they?  Considering that all we need is to be able to use more than one application with sound at once, with as little performance hit as possible, with some reliability.  Is that really so much to ask?

---

### Post by uRock on 2010-04-15
> **jounihat said:**
> I think the post is not so ancient, as the same PulseAudio problems still exist. It Should be ancient, but it isn't.

Just replaced PA with Alsa. The flash in Firefox loses sound after a while, and sound in Wine is not working if any other program is using sound. I hope no one is actually getting paid for developing this thing. Yes, I know some testing can be done by the users, but if even the basic things (hello! flash is the #1 thing today!) are not working, someone should take a look in the mirror.

Why is flash the number 1 thing? not every person sit watching youtube all day.

Instead of using whine, why not just use Windows?

I have had no problems with pulse audio nor flash on my system.

---

### Post by donovan1983 on 2010-04-15
I haven't really had any issues with PulseAudio. In fact, I had to install it in Kubuntu because otherwise I could not have more than one app using the sound card at a time. It surprised me to learn that it still isn't installed by default in Kubuntu. I also like how I can set it up where certain apps will use a certain soundcard (I have an external one just for music) and it's transparent to the application. The only minor issue I have with PulseAudio is that the control apps for it are old and in Kubuntu are missing most of their icons on buttons or even the padevchooser notification area applet.

---

### Post by rifter on 2010-04-16
> **uRock said:**
> Why is flash the number 1 thing? not every person sit watching youtube all day.

Instead of using whine, why not just use Windows?

I have had no problems with pulse audio nor flash on my system.

Lots of people hate Flash, but it has been taking up more and more websites, and unfortunately you often cannot use them without flash.  But, yes, people do watch youtube (_[color=blue][although youtube is working on replacing flash now](http://www.youtube.com/html5)[/color]_), _[color=blue][hulu](http://www.hulu.com)[/color]_, _[color=blue][homestarrunner](http://www.homestarrunner.com/)[/color]_, _[color=blue][newgrounds](www.newgrounds.com)[/color]_, _[color=blue][unforgotten realms](www.urealms.com)[/color]_, and _[color=blue][other sites with flash](http://games.yahoo.com)[/color]_.  Heck that last site I used to always use as a test to see if flash was working, and you can always scare up a decent game of Go there while you're at it.

As for why to use wine, well the whole point of using wine is to not have to use windows anymore.  What would be the point of having to reboot, or use another computer, every time you want to use one program or game?  I'll tell you what, there is no point, and eventually people decide that, too, and they do not come back to Linux anymore when they do.

Bottom line is people use their computer for what they want to do, and they will use the tools necessary for the job.  For any platform to serve their purpose it has to deliver.  And, sure, there is always a tradeoff.  There are no perfect systems, and there is no perfect software.  In the end, you go with the solution you can most put up with that delivers as much of what you want to do as you can find.  But I will say this; anytime past 1985 at the latest with computers sound is a pretty basic request.  And for more than 10 years now flash has become more important, to the point where it is pretty basic, too now.  Phones have flash.

Linux has supported advanced audio and flash for a very long time now.  It has just been historically a pain to get things right in the beginning.  Part of the charm of Ubuntu for me was that they were a distro that realized the 5000 things everyone was having to do after installing every distro, every time, and said "why don't we just have the install give you mouse buttons, a scroller, a sound mixer, a browser, and make it easy to install flash and java?"  you know, for starters.

Unfortunately one of the sad truths about Linux is that for some reason just when we get one kind of system working someone prevails upon the community to replace it with something new.  It's not necessarily Ubuntu's fault that they jumped on the bandwagon.  I don't really know the details.  I just know that in the past few years we've been through 3-5 init systems, 3-4 device file system standards, I don't know how many file system standards, and for the longest time we've dealt with 3 big projects for sound drivers which have at different times jostled their way to the top of the heap, and 3-4 sound mixers (actually a lot more than that, but there tended to be about 3 that were on top).  

A few years ago, I thought esd was finally shaping up to be how we did sound mixing, and Ubuntu set up esd for you at the outset rather than have to muck with it too much.  You still had to tell some apps to use it (that has not changed today except that a lot more apps seem to make it easier to do without recompiling), but it was there and it worked.  Now we have pulseaudio out of nowhere.  It's a very new system, and I am sure that the people who made it have very good reasons for having a new sound mixing project and think that it is the best thing ever, just like the guys who wanted to replace init with xinit and now upstart, etc (oh yeah, I left out the inetd replacements, and there are of course the replacements for bind, sendmail, ...).  

But the user doesn't care.  They want their computer to work.  They want to have sound, and be able to configure their system.  Unfortunately linux development leading to completely new ways of doing things, with incompatable apis and config files, get in the way of that.  And when you take something that worked, and replace it with something new, you would hope that the new thing works at least as well as the old, if not better.  People don't care if pulseaudio is designed and coded better.  They care about performance.  They care about how much cpu is used by the sound mixer and whether it works or not.

And when it does not, they will complain.  And the developers, who mostly are working for free, will feel slighted.  But that's just how it is.

---

### Post by rifter on 2010-04-16
Oh and, funny story, but it is as though pulseaudio is getting its revenge on me for speaking ill of it.  Initially the only real problems I had with it was that certain applications, and wine, had severe performance issues and stuttering if they were told to use pulseaudio (in fact, I have pretty much set all of them not to).  What's funny about that is that when you have pulseaudio installed, it has wrappers for esd and the like, so telling an application to use esd is just telling it to use pulseaudio through a different interface.  Yet that fixes the problem for me.

Anyway, pulseaudio's revenge is that now I have started to have pulseaudio start to take up 90-100% cpu all of a sudden.  Killing pulseaudio and letting it restart brings cpu usage back to normal, but after awhile it happens again.  I'd read that people had trouble with pulseaudio taking up cpu, and that it had worse performance than other systems, but I hadn't had enough problems yet to deal with the pain of ripping it out and replacing it with something else.  This mirrors my issue with compiz, that has similar problems and is similarly difficult to just replace from what I gather.

---

### Post by uRock on 2010-04-16
As long as youtube doesn't got the same route Netflix did with using Silverlight.

---

### Post by cariboo on 2010-04-17
> As for why to use wine, well the whole point of using wine is to not have to use windows anymore. What would be the point of having to reboot, or use another computer, every time you want to use one program or game? I'll tell you what, there is no point, and eventually people decide that, too, and they do not come back to Linux anymore when they do.

Wine is even a worse kludge then some people consider pulseaudio. For me pulse works the way it should, I can open as many flash videos as I want and get sound from all of them.

Most people have more than one computer in their household. Why not have at least one running windows, so that Windows programs work properly instead of using work-arounds to get them to work in wine.

If you would rather put up with wines foibles, why not at least pay Codeweavers for their version, and have the satisfaction of knowing that the programs you use will work properly.

---

### Post by rifter on 2010-05-09
> **cariboo907 said:**
> Wine is even a worse kludge then some people consider pulseaudio. For me pulse works the way it should, I can open as many flash videos as I want and get sound from all of them.

Most people have more than one computer in their household. Why not have at least one running windows, so that Windows programs work properly instead of using work-arounds to get them to work in wine.

If you would rather put up with wines foibles, why not at least pay Codeweavers for their version, and have the satisfaction of knowing that the programs you use will work properly.

Why not run Windows? Don't get me started!  Man that would be a whole other thread and offtopic for these forums.  But if we wanted to run windows we would run windows.  We are running Ubuntu instead for a lot of reasons.  Why should we pay Microsoft and feed the beast?


As for codeweavers, who said we're not using their product?  But it might surprise you that their product, and cedega's is WINE! The only difference is they can use some closed source solutions to handle certain things like copy protection.  So you'd still be running wine if you use their product, and you'd still be dealing with the same problems with pulseaudio. Another hint for you: pulseaudio is there whatever you are running, because it is the underlying sound system in Ubuntu unless you replace it with something else. 

And it's simply not true that those products magically make everything work.  There's nothing magic about software, despite what Steve Jobs might tell you.  Quite apart from pulseaudio problems, a lot of the same programs (maybe most?) that don't work with wine would still not work with those products.  

But there is good news, because wine itself is getting better all the time. So far, just about everything I want to run runs in wine, although there may be tweaks required which thankfully winetricks assists with and the appdb generally enumerates.  Only two things I wanted appear to be broken: .net service pack installs (which actually have been problematic even on Windows, and break because microsoft is doing naughty things with the installer), and the latest punkbuster (which also is broken on windows).  Unfortunately in the latter case there's not much hope of getting it fixed on any wine product, because of the way it works.  But this, too, is offtopic.

What is ontopic is the way that pulseaudio interacts (or fails to) with wine, and the weirdness that the esd wrapper to pulseaudio seems to mostly fix that problem.

---

### Post by cariboo on 2010-05-10
I've used the codeweavers products, I know it is wine. I have found a way to do everything I need in Linux except for a replacement for QucikBooks, I have run QuickBooks using wine, but I just don't trust my data running it that way. That and trying to get my 80 year old parents to use something other than Windows, is why I keep a couple of systems running Windows around.

Instead of trying to run Windows programs using wine, I would rather spend my time helping lobby software producers to start creating Linux versions of their programs.

---

### Post by uRock on 2010-05-10
> **cariboo907 said:**
> Instead of trying to run Windows programs using wine, I would rather spend my time helping lobby software producers to start creating Linux versions of their programs.
I have been trying to do that with Mike Meyers at CompTIA with their practice exams, but their receptionist keeps saying they don't get enough requests for it.

Same with Cisco. I have harassed them a few times to make a 64bit version of PacketTracer. I love that program and it is irritating to have to run 32bit ubuntu in a VBox just to run the program. I am thankful ubuntu is free and I can do this.

---

### Post by Ms_Angel_D on 2010-05-10
Moved to recurring discussions to avoid thread closure.

Testimonials & Experiences is not a discussion/debate section of the forums.

Angel

---

### Post by bobbob1016 on 2010-05-10
I haven't had any issues with pulse in years, since the first or second release it was included in by default.

---

### Post by kopcicle on 2010-06-12
google Pulseaudio sucks About 90,200 results (0.22 seconds) 

So I'm not alone and this is something of a dead horse . If nothing else kicking it makes me feel better . 

First of all a hearty double shot of mid-roasted Jamaican Blue Mountain to [idyllictux]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") for an easy to follow and nearly complete method of holding the beast PA (PulseAudio) at bay .
I did say nearly complete .

It seems that through some incompletely documented update that I have yet to find ,vestiges of the dreaded beast have once again appeared in my machine . Starting Skype (that works just fine w/o PA btw) seems to produce a kidnapping of my audio hardware by a non-existent PA (having been completely removed as well as following the above link) and failing to release it even after a kill . Following this something as simple as "twinkle" aborts with "failure to access, audio device busy ..." and nothing short of a reboot so far has been a cure . I am still looking for the kidnapper with lsof | grep some such but not being a serious nerd the process of extracting resources used by an app and creating a diff from another app escape me . I just know it's broken .

Movies that played over my small home network now have to be imported whole and entire to the media center to play with anything approaching audio . Previously ALSA worked just fine . PA as a default addition to ubuntu for the sake of "put out something broken for the community to fix" rather than extensive testing in alpha/beta and multiple platforms is just plain irresponsible and wrong . Because of PA and it's invasive ,system wide intrusion 10.04 LTS is unavailable to me on not one but 4 different platforms . Simply editing /grub/menu.cfg directly in 10.04 to remove "quiet splash" allowed HID to load before PA and access to the keyboard was possible ! How is that for invasive ?

Sun Microsystems (may it rest in peace) made a good living out of being a solution in search of a problem for a good number of years but it worked .
The ubuntu community is not in need of under developed , operating system invasive (if you don't check the "items to be removed" in the synaptic dialog box when completely removing PA you will find your entire desktop environment gone) obfuscated from the user , insane machinations to make it work [try this if you have a spare week or so ]("http://ubuntuforums.org/showthread.php?t=789578")  when simply it's eradication and removal would do the community more good in the short term and possibly be a lesson to the core developers that release to community in order to speed the maturity by way of bug reports and fixes is akin to a soup with 90,200 unhappy chefs producing an inedible brew . A solution in need of a problem indeed .

How about a solution to a problem for the benefit of the community . I don't recommend we line up PA against the wall with all the lawyers and shoot (sry , personal pet peeve ) but rather place PA in quarantine at the risk of it's further development taking place in a vacuum rather than in real world computing . PA may yet be the next thing but does anyone remember the lesson of application integration that was M$ internet explorer ? (and I'm not talking about the legal ramifications ) .

I full well realize that what I'm suggesting is a fork in ubuntu development , one with and one without PulseAudio . I think the time is well over due for the masses to be heard . Please , in a meaningful way , DEVELOPERS , ask your user base if PulseAudio has a place in their desktop as it is now ,not as some intend it to be . remember where good intentions get you . 

Screw it I'm done . I'm FFFR away from leaving ubuntu simply over this one issue . I wonder if I'm alone . Other than the 90.200 hits I found on google

---

### Post by XubuRoxMySox on 2010-06-12
Up until Lucid, **[COLOR="Blue"]Xubuntu[/COLOR]** did not ship with PulseAudio. Now allofasudden it appears in the LTS version?? Egads.

Perhaps it was an oversight or something... but I'm sure I'm not the only one sticking with Karmic Xubuntu just to avoid that most troublesome of audio nightmares.

At least until Karmic reaches EOL...but okay for now,

Robin

---

### Post by kopcicle on 2010-06-13
Just call me a ranting fool but if there is any way I could arrange to drive a stake through PA's heart ...

~kop

---


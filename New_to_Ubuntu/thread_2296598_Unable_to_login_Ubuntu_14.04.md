---
title: "Unable to login Ubuntu 14.04"
date: 2015-09-27
forum: New to Ubuntu
---

### Post by roy32 on 2015-09-27
I have installed the stable version 14.04 on a Compaq laptop. There is no Win OS on the PC. However when booting I am unable to login either as a guest or under the pw protected user. Doing so simply cycles me back to the login screen.
During login the screen displays a "you are not currently connected to wifi" (or similar message) however I can see wifi sources listed. Selecting my own wifi does nothing (ie no pw request). 
Repeated installations produce same situation. Sometimes I have entered wifi key during installation, sometimes not. No difference, login still impossible.
Over 10 years I have repeatedly tried to use Linux (usually Ubuntu) but this sort of problem always happens and I usually give up trying for another couple of years. It would be nice to see it working for a change.
Roy

---

### Post by uninvolved on 2015-09-27
Hmm... Well, is it just starting to login and then returning to the login screen? If so it's pretty trivial to fix that - assuming it's an Xauthority permissions error.

Having said that, well, you're probably used to doing things the Windows way. I can understand that and it is frustrating initially. However, keep in mind that you're changing because you're wanting something different and don't look at it like it's difficult but, rather, like it's a new and fun adventure. Remember the joys of first learning to use a computer? If you don't then, well, Linux might not be for you - but I suspect it is something you may like seeing as you've come this far.

So, let's try to get this fixed.

Take a look here:
[http://ubuntuforums.org/showthread.php?t=2296572&p=13363450#post13363450](http://ubuntuforums.org/showthread.php?t=2296572&p=13363450#post13363450)

Carefully follow the directions that are linked from that page. It's not that difficult once you get the idea of things - you needn't understand it all nor understand it right away. Just take it as it comes. Personally, I have been using Linux off and on for many years and came from a Unix background. I've also used Windows and a Mac. I try to break something every day. It's how I learn to fix it. When I fix it then I'm learning more about it.

I remember an older essay about Linux is Not Windows - I forget the authors name. He used a good analogy. Linux is a box of Legos. If you don't like to play with Legos then this may not be the right OS for you. I'm not a zealot or anything so I'd suggest that you use the OS that suits your needs best. No matter what OS that is, it should fit your work flow and enable you to do the task at hand as best and efficiently as possible. 

Ah - a quick search query away and I've found that essay. If you have a minute then you might want to read it.
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Best of luck and let us know if the solutions suggested on the initially linked answer are doing the trick for you. If not we can try a few other things and get more information.

---

### Post by roy32 on 2015-09-27
Thanks UIV.
Well, I'm Lego-neutral but at least in Lego all the locating pins are set at the same pitch...
I'm actually trying to set this PC up for a disadvantaged person's very basic requirements - email, browser etc  - with the side benefit of familiarising myself.

Your first link doesn't really help except for mention of F2 "at the login screen". Maybe i'm thick but this isn't at all clear. The embedded link in that post transfers me to another post which is dense with references to syntactical stuff that it really, really shouldn't be necessary to address just to get the system running. My only experience of Unix-derived applications is using Cygwin to run some scripts 15 years ago and I have no real interest in struggling to memorise command-line whatsits if at all possible. I'm _old_.

I didn't really come here to *complain *about Linux but I do find it perverse that after all this time it resolutely refuses to allow even an experienced person to install the OS. The expiry of XP support was a golden opportunity for Linux to get some traction in the wider universe; which it hasn't as far as I can see.

I've been in variants of this situation previously several times. Despite which I actually managed to install Ubuntu on an ancient laptop lacking a working CD/DVD and with a BIOS that wouldn't allow USB booting. It took me weeks on and off and I have no recollection how I succeeded; it's too slow to be any use even so and the audio sounds like an electrical storm.

But it would be nice to make this one run. Any clarification of the "F2" stuff?
Roy

---

### Post by uninvolved on 2015-09-27
At the login screen try to login a couple of times (it will fail and cycle back).
Press F2 - you should get a black terminal screen. (Note: It might be CTRL + ALT + F3 actually - my bad. I could have sworn I used F2 but the page indicates otherwise and I'd trust that before trusting my memory.
Login - use the username and password that you assigned.
Enter this: chown username:username .Xauthority[FONT=Ubuntu] (Replace username with the name you logged in with. The 'chown' is changing the ownership.)
Press the ALT + Right arrow button until you get back to the login screen. 
Try to login with the user/password as before.

That's what worked for me, at any rate. If it doesn't work then we can try something else. I used the answer supplied by the user "SiddharthaRT[/FONT]" and they have some other suggestions but I did not actually need them, as it turns out. If it doesn't work (the first one) then don't be too alarmed - just try the rest of them. If it doesn't work then, by all means, keep asking and someone's likely to know how to get you squared away. I've managed to fix this sort of thing a few times though the last one was the most recent and that was the solution for me.

And there's nothing wrong with us old duffers. My early days were on Unix, then Windows, then Solaris specifically, and then back to Windows, and it has been just Linux exclusively for quite a while now but I bounce between distros with an alarming frequency. I'm not sure why you're having such a hard time - it's typically pretty trivial to get an OS installed these days. Except for Plan9... I've yet to get that installed and booting, but I digress.

Hopefully someone will come along with some more insight. There's a slim chance, albeit a chance still, that Ubuntu is simply not going to work and you may need to try a different distro. There are a number to choose from but, honestly, I've had fewer issues with Ubuntu (and derivatives) than I've had with others and I've used a variety of hardware along the way. 

Dumb question time - does the OS boot and run properly in live mode from a live DVD/USB disk?

---

### Post by roy32 on 2015-09-27
Thanks again. I'm about to try your suggestions but before I do, two observations.
I did another clean reinstall with a hardwired network connection (recognised) but at the start a splash screen appeared for a couple of nanoseconds complaining about a something-or-other (ACP? API?) "probe failure". If this is a critical warning the guy who wrote the timeout needs firing (oh, hang on, no-one gets paid? which probably explains quite a bit). I also selected the online update options - and it took about 10 times as long to install; I watched carefully as the various stages passed and saw no errors reported.
After completion same old same old...
---------------
Ok. inserted [COLOR=#000000]chown me:me .Xauthority alt RA > login screen...
[/COLOR]your instructions are a bit ambiguous but this didn't work. I then returned to the command line and at the login prompt entered my user name (me) /return/pw
which was accepted and gave me a screen of licence info. Alt right arrow back to login screen, logged in,
same old same old.
Repeating this I new see "system error detected" with the option to report - but no diagnostic information....
Roy

---

### Post by roy32 on 2015-09-27
OK more information - sort of.
I have just installed "Mint 17.2" alongside Ubuntu which seems to be based on the same code. Despite much screen flashing during installation this seems to work, sort of. It logs on automatically but the app updater start screen requires password to launch the various options - and the daft thing doesn't recognise the password! And yes, I'm using the right kb layout and no special characters just alphanumerical.
However the Firefox browser runs, it accesses the web (hardwired only so far) and I can see the file structure. Which, although problems are surely lurking, is a big improvement on bl00dy Ubuntu.
I'll persist with this for a while and see what happens and if it's ok I'll re-install over the Ubuntu partition. I dread to think what's required to get rid of it within the running OS.
Roy
Too soon: this is useless too. The screen is totally unstable even when moving the cursor around. 10 years on and I'm yet to achieve an even basically usable installation of Linux. No wonder hardly anyone uses it. Unable to try updating drivers since the stupid junkware doesn't recognise a simple password. Only too believable.

---

### Post by QIII on 2015-09-27
Unless you are prepared to think that all of the rest of us are just pretending to use Ubuntu, the hasty generalization of it based on a sample size of one is inappropriate.

You are certainly having problems, and I am sorry that is happening.  We are here to help and we will as we can.

Could you please post an image (from your cell phone camera if need be) showing the message about not being connected to wifi and giving a list?  I don't think I have ever seen that before.

Please give the community some time to help diagnose this.  Your experience is *not normal* -- so it may take a bit for others to understand what is going on.

I'm not a Linux apologist, so I don't have any problem telling you that life is too short to be vexed so by something like an operating system.  If it doesn't work for you, don't beat your head bloody against a wall.  That's just silly.  Use what works for you.  There is absolutely nothing wrong with that.  

(By the way, there are far more devices running some form of Linux than Windows.  Your car has electronic subsystems that run on Linux, as did the machinery that was used to build it.  So I'm pretty well convinced it works.  You are communicating with us over an internet backbone which is substantially built on Linux servers.)

---

### Post by roy32 on 2015-09-27
Thank you but I admit defeat.
This isn't a hasty generalisation. It's based on repeated attempts over the years to use *any *version of Linux. Although I'm not a programmer I came from a background of print media production and ended up managing a very complex system (national newspapers) including a hefty custom application (>50K lines of C++ code plus a custom postscript interpreter) which I helped develop (functional design, UI, installation/training and management.) This involved looking very critically at how people interact with software - it would take a long time to explain but newspaper production admits no failures if you want to stay employed. 
Every time I look at Linux I see assumptions about how the user interprets stuff which are just lousy and very, very easy to improve. Splash screens that vanish in less than a second for example.
I just tried to update Flash and was faced by a choice of about 5 different options for Linux. When I took a guess I ended up with a compressed file which when extracted gave no indication whatsoever of how to install the update. _I have a simple password; the system fails to recognise it even when I'm already logged on_.
Again, I've been through this so very many times and the number of obstacles to even basic use of this OS are just incredible. After > 30 years of everything from BBC Bs, Amstrads, dos PCs, Macs, NT 3.5, 4 and on and on, it just amazes me that Linux is so incredibly obtuse as to defeat me every time - or at least exhaust my patience. I realise that Linux is widely used in server rooms everywhere but why it's never been refined sufficiently to enable ordinary users to install and use without all this ludicrous song and dance routine is incomprehensible. I see no possibility that it will ever make inroads into the dominance of Win or MacOS at the desktop level. Clearly there's a big community of people out there for whom the esoteric obscurity of Linux is an attraction in itself; most people simply want to use an OS that remains as invisible as possible.
I'm not wasting another minute of my time on Linux for the moment - if ever - but I thank you for your futile attempt to help me get it running! Life's too short.
Roy

---


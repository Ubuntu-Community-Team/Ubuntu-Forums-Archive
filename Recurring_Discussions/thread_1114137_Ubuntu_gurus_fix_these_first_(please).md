---
title: "Ubuntu gurus: fix these first (please)"
date: 2009-04-02
forum: Recurring Discussions
---

### Post by LeBurt on 2009-04-02
Greetings Ubuntu veterans and newbies,

I'm just back from reading [an article (and comments) from Slashdot]("http://linux.slashdot.org/article.pl?sid=09/04/02/1317246") and it prompted me to create this thread in a hopeful, if naive, attempt to address the problem.

Some background first. I've been using Ubuntu for about 2 years and I must admit that it's been a mostly enjoyable experience. However, still today, there are aspects of it that I find mildly frustrating. In fact, I sometimes shake my head in disbelief, thinking "how can this be in a modern OS?". I know, it's free, it's democratic, it's evolving. Heck, changes from one version to another are often amazing and have made me stick with the product. On the other hand, well, some very basic and critical issues are left standing while new, less important features are being introduced (a new notification system comes to mind... pretty, but pretty useless if you ask me).

So, what I'm hoping here is to put forward a list of all that needs fixing first. This is entirely from a user perspective and should only be seen as positive criticism. If you are serious with making Ubuntu a mainstream, desktop-ready OS, it is essential that a list such as this one not only exists, but is considered seriously as a tool for improvement. 

As a simple rule for this thread, I think it would be best to avoid nitty-gritty specifics and stay at a comfortable cruising altitude of 5,000 ft. Avoid discussing bugs, hangups, config parameters. Instead discuss general issues, as I have below.

So here are my 2¢ that will, I hope, prompt others to provide theirs. Again, think of this as system-level positive criticism. 

------------------

1) Sound. 

When talking about basic general stuff, here's an ideal example for you. Sound in Ubuntu is way too complicated. There is no way I can be brought to care about PulseAudio, ALSA or what have you. All I want as a user is sound that works all the time. Regrettably, it's not so easy. 

As an example, consider configuring Skype's audio parameters. From the playback device list, I have like 8 choices in there. I once had the bad idea of playing with those, the soup got sour and now audio appears disrupted everywhere else on my system. Forums tell me "get rid of PulseAudio", try this and that, blah blah. I'm so turned off by the whole thing that I'll just wait for Jaunty.

Strictly from a user point of view, one would expect sound to be a "mature" aspect on any OS that should just work without any fooling around.

2) Video playback.

I once dreamed of having my own Linux-based PVR for everything media. Bad idea. There's no way you can compare video playback in Ubuntu to any other modern OS. It chops, tears, stays blank for the first 5 seconds of a file being played.

I tried different video players, played with settings, nothing worked. Forums tell me to try new drivers from Nvdia (see point 3) but then I also need to upgrade the player (see point 4). Honestly, I prefer waiting, maybe someday I'll have decent video playback out of the box.

3) Driver installation.

This is what one would expect when installing a driver:
a) download driver
b) double-click to install driver
c) use driver

Instead, you must follow an intricate procedure that sometimes implies compiling, manually editing config files, activating the driver from a GUI dialog. While I can do all these things, I can't seem to find them exciting. For one thing, I never really was able to shake off the feeling of not knowing exactly what going on. I'm not exactly a newbie in operating and maintaining my OS, but I somewhat relate this feeling to that of my aging parents who are "scared of breaking something" in all matters computers. Not a good thing.

4) Application updates.

Ubuntu does a great job updating itself when new libraries are available. Applications, on the other hand, don't seem to follow suit. It's be nice to have a prompt saying that a new version exists for Gimp, or Skype, or Firefox. Sadly that's not the case. Updating applications is a manual process sometimes as intricate as installing a driver and then you're never sure if the old one is still there, how to remove it, etc.

5) GUI responsiveness.

I may have been spoiled with responsive GUIs in the past. Fact is, I find Ubuntu's GUI (ie Gnome) to be slow and unresponsive. Example: how many time have I wanted to resize a window and ended up selecting a bunch of icons on the desktop instead. The procedure I follow is easy and universal: move the mouse pointer to a window corner, click and drag to the right size. Well, I find that doing this too fast doesn't work. I must slow down, wait for the cursor to change to the slanted double-arrow, click, wait, start dragging slowly. You get the hang of it after a while, but it's still pretty much annoying.

-------------------

All right, that's it. I know there are going to be some people answering this thread with this or that workaround or witty comment about me having overlooked something somewhere. Thanks, but that would be beside the point. 

The point here is: hey Ubuntu gurus, fix these first. Please...

---

### Post by Mooose? on 2009-04-02
1) Usability
2) Usability
3) Usability

The focus is on bugzilla, on clean code, on distro's, with pretty much zero effort going into the end user experience.  Usability, in this day and age, I would argue is possibly even _more_ important than code quality.

Usability is not dumbing down, it is not pretty graphics, it is simply making things more productive for your end users.  Unfortunatley it is one of the most misunderstood aspects of software design - in fact many do not even believe it exists!

There is a formula to define usability that goes like this:

U = (T * R) + M

U = Usability
T = Time taken to perform action
R = Number of repetitions of an action
M = Time spent reading the manual or researching (total)

With your goal, as a developer, to get U as low as possible for all values of R.  For example stick an average untrained user in front of a terminal and ask them to edit a file.  It would take _hours_ for a non-trained user to be able to do what you're asking - if at all.  Sure as R increases then U drops, and offsets the high initial M, but that means it is only usable for experts.  Likewise if something is so dumbed down that T never really goes down in the name of making M non-existant, this is a failure too.

The ideal of a usability is that the user should _never_ be 'stuck' and need to google or ask what to do, the user interface should provide all the information a user needs (provided they understand the subject).  Sensible defaults, drop down lists, logical workflow, sticking to known conventions etc, etc.

The problem of usability and Linux is it is so endemic and entrenched that it will require a siesmic change in the attitude towards these subjects.  

Apple understand this very well, and are doing well because of it.  Microsoft have really picked up the ball with Windows 7 - I am very impressed, but Linux seems to be ignoring it entirely, instead focusing on drivers, bugs and bundled apps.

The problem is, as was on the Slashdot article, bug reports, fine, criticisms of functionality and usability = flamed to a crisp.

---

### Post by 3Miro on 2009-04-02
1. Sound may use improvement, however, if Skype is having trouble with the sound it is Skype's problem not Ubuntu. I have skype mute my mic everytime I try to make a call and the only way to fix it is to uncheck "allow skype to adjust the volume".

2. I have never had video problems, all video on my systems works faster and smoother than windows. 5sec blank screen is a setting/driver problem.

3. Sorry,but System -> Administration -> Hardware Drivers +checking a box is by far superior to searching on the web or anything. That is for propriety drivers, for open source drivers, the kernel takes care of it so you don't even have to do anything. Drivers are an issue for the driver provider and no Ubuntu.

4. Wine for example has its own repo database and so do many apps outside of the standard Ubuntu apps. Those update properly, however, if a company doesn't provide repository and/or updates for their programs, it is the company and not Ubuntu's issue. (BTW Gimp and FireFox update automatically, Skype also does if you install another repo database [http://www.medibuntu.org/](http://www.medibuntu.org/) )

5. When I read your post it seems that you either don't know Ubuntu very well or most likely have a problem with your installation. I find both Gnome and KDE to repond just fine.

That is not to say Ubuntu is perfect, it is not, however, your points are actually not valid in this case.

The biggest problem with Ubuntu is that unlike Windows or MacOS people are trying to install their own versions as opposed to having it pre-reinstalled. Installing Ubuntu is much easier than any other OS, as long as you have some knowledge, most people do not have that. Most people would never be able to install and set up their own copies of windows either. Until manufacturers start providing pre-installed Linux on a mass basis (great job system76), then there would hardly be any problems.

---

### Post by LeBurt on 2009-04-02
3Miro:

1) The Skype example is just that, an example. From a system perspective, sound on Ubuntu is way confusing.

2) How much tweaking did it require? Never had a clean install with good video playback, never. Why do you think Nvidia is introducing VDPAU?

3) Clicking the box is easy, it's getting the driver to appear in that box that's difficult. [This]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide") and [this]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") should convince you.

4) If I'm not mistaken, Firefox updates minor releases but I seem to recall that I had to wait until Intrepid to get Firefox 3. No amount of waiting for the auto-update got me any closer.

5) Well well, not understanding an OS is one thing, not understanding my own senses is another. If I say the OS is slow, it's slow, period. No amount of rebuttal is going to change that.

Aside from being slightly insulting, saying that my points are not valid is absolutely missing my point. Linux suffers from that kind of attitude. I'm not looking for pointers to obscure tweaks that will circumvent my problems, I'm looking for someone with a system-level view of the system that might say: really? Anybody else experiencing the same things?

---

### Post by SeanBlader on 2009-04-02
I read that article on PCWorld too, and I agree completely with LeBurt.

And Miro's 6th sentence is the exact example of something that *IS* important being either taken out of context or just being tossed aside. All his point are exactly valid. If drivers worked out of the box from the kernal level then ndiswrapper wouldn't have to be used from the command line. You wouldn't have to guess that you needed to install vpnc to connect to the office network. Those are just examples that I've had, but just because you haven't had problems with video or sound doesn't mean that your grandmother wouldn't, and that is an obstacle to bug number 1.

Part of the challenge is the effort that Canonical has gone to in order to make sure that Ubuntu is totall free as in open source free from the outset. So if you install DVD libraries, you are outside of that free box. If you install Java you need to accept a license agreement, and if you use the nvidia or ati drivers, you're into proprietary land. This is specifcally a policy restriction that will never help fix bug number 1. In the end, if you try to work towards fixing [https://launchpad.net/ubuntu/+bug/1](https://launchpad.net/ubuntu/+bug/1) first, everything else starts to take priority.

And thinking in that route: Should the funds magically become available, is Ubuntu ready for a billion dollar marketing campaign? I'd say the driver/hardware support isn't there and the usability is lacking. Power users are decent users, novices? Not quite.

---

### Post by wolfen69 on 2009-04-02
> **LeBurt said:**
> 
2) Video playback.

I once dreamed of having my own Linux-based PVR for everything media. Bad idea. There's no way you can compare video playback in Ubuntu to any other modern OS. It chops, tears, stays blank for the first 5 seconds of a file being played.


over 4 years, 5 different computers, and every version of ubuntu, video playback has always been perfect for me. i also have 14 customers using ubuntu and a couple of friends. no problems there either.

i have also done MANY installs on about 30 other computers for testing purposes, and find ubuntu to be great at video. perhaps it is time for you to get a new computer. i have never experienced any of the problems you have, and have done MANY more installs and testing than you. i believe my experience with ubuntu trumps yours. besides, if everyone had the problems you do, no one would use it, and computer companies would not preinstall it with their pc's. believe me, it's your computer.

why is it that no one believes that it could be their hardware at fault?

go ahead and say it. "IT"S NOT MY HARDWARE!" :rolleyes:

if you were to use my computer with ubuntu 9.04 on it, you would never use another OS again. it's the single best OS experience i've ever had. this is coming from someone that used to be a windows power user. install ubuntu on a real machine, and you will change your tune.

i also run a PVR during football season running mythbuntu. works as good as windows media center did for me. please don't spread FUD about ubuntu just because of your 1 inept pc.

---

### Post by TyrantWave on 2009-04-02
Webcam and Microphone support.

That's all I ask really.

---

### Post by anjilslaire on 2009-04-02
> **Mooose? said:**
> 1) Usability
The ideal of a usability is that the user should _never_ be 'stuck' and need to google or ask what to do, the user interface should provide all the information a user needs (provided they understand the subject).  Sensible defaults, drop down lists, logical workflow, sticking to known conventions etc, etc.

Just to be sure that no one's being biased, Windows does not achieve this either, and is just as full of usability problems as a modern linux distro. Most users don't see this because they've been using Windows for 5-10 years and they understand Windows.

Lets be fair now.

---

### Post by Aflack on 2009-04-02
holy hell i just want stuff to be simple instead of like having to manually edit config files and stuff. and i dont know what half the updates are its all like libns2.0 and stuff. more than library stuff i just cant think of any cause i dont look at them anymore.

---

### Post by 3Miro on 2009-04-02
I don't mean to be insulting or even disrespectful to anyone. If that is the way it came out, I am sorry.

The only time I had less then perfect video on my Linux was with a GF7300GT by EVGA. I have always used NVIDIA and all other cards worked flawlessly (yes I was thinking it is an Ubuntu problem, but it wasn't). I have tried 5 Video cards on my machines and at least 5 on friends computers. Other than that one case, all other video was perfect.

For the Driver issue: Canonical cannot possibly do anything about nvidia's proprietary driver, neither can Microsoft do anything short of witting their own drivers. With the speed at which video cards change, unless nvidia releases the source, we are at their mercy. If nvidia prioritizes windows over Linux, it is not a Ubuntu problem, it is a problem with nvidia. Read up on KDE 4.0 and the problems they had with nvidia.

All the points are problems, but they are beyond Ubuntu's control (except for the sound, for which I agree with you).

I don't doubt that you have trouble with the GUI, however, it is not inherit to all Ubuntu or even to Ubuntu in general. If the GUI is not functioning properly it is most likely a driver/hardware/setting issue. Which least to my point, if people had professionals, that known what they are doing, install Linux on their computers those problems wouldn't be there. A system76 laptop works out of the box, java, flash and everything. It took me 3 hours to install flash on my desktop, because I am not a professional who knows what he is doing.

---

### Post by lykwydchykyn on 2009-04-02
I've been reading complaints about Linux for six years, and nothing you're saying is out of the ordinary.  If the developers don't know these things are issues, they are living under rocks somewhere with their fingers in their ears.

Before anyone gets the idea that such is the case, let me assure you all these issues are being addressed in some way when it is even possible.  Driver support for instance:  You want it to be something where you download a driver file and run it.  You know what the devs want?  They want every piece of hardware to work with Linux WITHOUT YOU DOING A BLESSED THING.  How's that for easy?  Unfortunately there are some things standing in the way of that reality, namely hardware companies that don't care about supporting Linux.  They are being worked around when it is possible.

Sound is a pickle.  The problem is every attempt to clean up and fix Linux sound introduces either another layer of abstraction, or yet another subsystem to be compatible with.  It's a pretty well known issue.

In any case, I recommend people who want to criticize Linux do it the right way:  Get involved.  Every major FOSS project has a public bugtracker.  You don't have to be a software genious to bring up usability issues or suggest improvements.  I personally submit bugs and feature requests to numerous projects, and I can tell you they DO get read and devs are responsive.

Criticizing Linux on a Linux user forum probably will garner negative responses.  Don't view this as the "Linux community" avoiding issues, because most of the time these folks aren't developers and can't fix the things you're talking about.  Take your issues to the people who can fix them, and see if you don't get a more positive response.

---

### Post by change_mode on 2009-04-02
Yes, the sound issues need to be addressed.

Point 2 and 5 look like a misconfigured system on your side (graphics drivers).

The linux devs can't possibly keep up with the drivers of every single piece of hardware. New hardware will always take a while to be properly supported, unless the manufacturers provide linux drivers. You should talk to them.

Same with program updates. You only get security updates, because everything else would be too much work for the maintainers.
If you want newer versions of your programs, you can use the latest Ubuntu release or try to get .deb files - they're really easy to install.

---

### Post by 3Miro on 2009-04-02
Another possibility for the updates are community run repos, such as Mediubuntu and I am also using winehq and WICD ones. People run repos with much newer drivers and programs, however, there is always a potential risk of an update to break something old.

---

### Post by LeBurt on 2009-04-02
_wolfen69_: I have no doubt that you installed a great many PCs with no problem on video playback. Unfortunately, you not around to work on my inept one (how do you know it's inept, are you spying on me?) and it doesn't work so well. Willing to overlook the fact that you and I may have different definitions of a quality playback, I declare that before ANYBODY says that Ubuntu is desktop-ready, it's got to have the video playback working on mine using the download-install-use scheme outlined above. BTW, you need to brush up on your spying skills because my PC is far from inept. And just in case you're wondering, it's not the user either... ;)

_3Miro_: Sorry to say that this 8500GT shears and tears video like there's no tomorrow. Also, I'm not complaining about the quality of the drivers, after all, it takes a while to come up with a good low-level software that speaks well up and down. My point is more about the ease to install the said software. Perhaps Canonical can't do anything about the driver itself, but maybe it can provide a mechanism for all driver providers to make them easy to install? And correct me if I'm wrong but aside from the proprietary stuff, all code in Ubuntu is open and free so why do you say they can't do anything about it? Fact is, they won't do anything about it because they're too busy providing useless features like a smooth splash screen and a new notification system. I'm sure I'm not the only one thinking the priorities are a bit wrong here.

_lykwydchykyn_: Get involved? That's what I'm doing right now. My level of involvement is this one: to provide a high-level system view of priorities.

_change_mode_: Misconfiguration: I'm sure you're right. Doesn't change my point. As for application updates, I'm thinking Ubuntu could come up with a means to make applications register themselves for regular updates. Canonical doesn't have to do the work, just provide the means.

Again everyone, you can come up with a million excuses about hardware and software and person-behind the keyboard. The fact is, Linux is nowhere ready for mainstream and until someone starts looking at it from a system perspective, it will likely stay that way.

---

### Post by lykwydchykyn on 2009-04-02
> **LeBurt said:**
> 
_lykwydchykyn_: Get involved? That's what I'm doing right now. My level of involvement is this one: to provide a high-level system view of priorities.


To whom?  Hear my point:  You are welcome to come to this USER forum and say whatever you like; but it's not going to change anything.  Nobody here is in a position to directly change things.  The developers of Ubuntu and other FOSS projects have set up channels to hear back from users; use them.  I'm not saying that to put you off; I'm saying it to encourage you to get involved the right way.

> 
Again everyone, you can come up with a million excuses about hardware and software and person-behind the keyboard. 

It's not about excuses.  It's reality.  Again, we're users; we're the ones who have by-and-large had a good experience with Linux and learned to cope with the problems.  Fortunately for all of us, the development community doesn't sit around making excuses.  You want a solution?  How about this:

[http://www.linuxdriverproject.org](http://www.linuxdriverproject.org)
> 
We are a group of Linux kernel developers (over 200 strong) and project managers (over 10) that develop and maintain Linux kernel drivers. We work with the manufacturers of the specific device to specify, develop, submit to the main kernel, and maintain the kernel drivers. We are willing and able to sign NDAs with companies if they wish to keep their specifications closed, as long as we are able to create a proper GPLv2 Linux kernel driver as an end result. 


There is no excuse for a manufacturer not to support Linux.  We've got a crew of over 200 developers ready to make drivers free of charge and put them in the mainline kernel.  You want to help?  Next time you find a piece of hardware that doesn't work with Linux:
 - Complain to the manufacturer
 - Let them know you will only be buying products that work with Linux
 - Inform them about the Linux Driver Project

> The fact is, Linux is nowhere ready for mainstream and until someone starts looking at it from a system perspective, it will likely stay that way.

What, precisely, do you think folks like Canonical, Novell, RedHat, Debian, and all the other distribution builders do?  Their job is to take all these separate parts and assemble them into a system.  Their job is to tackle the end-user experience.  And if they're falling short, they have channels where you can let them know.  In Ubuntu's case, that'd be Brainstorm and Launchpad. 

Please don't interpret this post as flames.  Don't walk away going "this guy's flaming me for criticizing Linux".  You see problems, and you want to see them fixed.  That's good.  Now channel that energy into the proper venues.

---

### Post by sudoxe on 2009-04-02
Although my laptop is a hardware nightmare (Compaq, uses I think 3 proprietary drivers), I think someone should make a generic nVidia driver that "just works" :)

and maybe just an Atheros AR5007/AR242X driver :)

Nothing that Ubuntu can do about it, but they're my dreams :)

---

### Post by wolfen69 on 2009-04-03
> **LeBurt said:**
> _wolfen69_Willing to overlook the fact that you and I may have different definitions of a quality playback, I declare that before ANYBODY says that Ubuntu is desktop-ready, it's got to have the video playback working on mine using the download-install-use scheme outlined above.

are you saying that i will accept shoddy quality video? wrong. i am a perfectionist when it comes to how my computer runs. all my videos are flawless.

as far as your comment about ubuntu not being ready until it works on yours, well, i'll leave that one alone. 

please tell my 14 non-techie customers (for whom ubuntu runs perfect) that ubuntu isn't ready for primetime, i'm sure they will dump it immediately and go back to windows just because you said so.

btw, i tried to install vista on a few computers that had a sticker on them that said: "vista ready". guess what? vista ran like crap or barely at all on them. i guess based on that experience, windows isn't ready. 

i have even had a couple computers that would not run xp well, but they ran ubuntu fine. what if i had always been a linux user who decided to try xp, and for some reason it did not work well with my machine? should i condemn the OS as a whole? should i tell the world it's not ready?

it's a fact that ubuntu will not work on every computer in the world. accept that and move on. there are 1000's of possible hardware configurations and other things to consider. it is impossible to please everyone.

the bottom line is, that *your* computer is not the gold standard by which an OS is judged. going by *your* rationale, ubuntu works perfect for me, therefore it is ready for the world. do you even have a little clue about the point i am trying to make? 

no OS ever made will work on every computer. understand that, and you will begin to be at peace with yourself, instead of bashing everything that is not perfect for you.

---

### Post by spotrick on 2009-04-03
IMO, Ubuntu is excellent in all respects that matter, with one exception: Intrepid broke vpnc on my Dell laptop, and I have not been able to use it effectively since. This is a major pain since I talked work into buying me a laptop so I could work at home, and not having vpnc functional is an embarrassment!

I consider vpn to be mission-critical software, so if someone who understands it could please fixe it, I will kiss the ground they walk on. :)

---

### Post by stderr on 2009-04-03
Hehe, perhaps if we all chill out a little :)

LeBurt's raised some decent points, and he/she is correct that Linux devs don't always take the "novice end-user experience" viewpoint. And we all know sound is a bit of a mess. 

But, you have to remember Winblows has loads of paid devs working overtime on UI. (Personally, I can't use the Winblows UI without tonnes of cussing and lots of punching the desk). Linux devs are, on the whole, more interested in bug fixes, functionality improvements, improving hardware support etc. Although I am impressed by the volume of GUI work going on with Ubuntu ATM. And, of course, hardware support is difficult when you're not as rich and powerful as the big M$.

End of the day, lykwydchykyn is pretty much correct: these forums are largely user forums, and it's unlikely that (m)any relevant devs will see and take note of this thread on this forum. With Linux, you tend to get more achieved by posting to the package-specific forums, or their IRC channels, or e-mailing their devs, or using their bug-tracking systems etc. 

However, I think some of your issues have probably rung a number of bells with people on these forums :D 

(... including myself. For example, when I reboot, which is once in a blue moon, one of the first things I do is kill Pulseaudio. Still haven't bothered removing it from the session... )

---

### Post by Lunx on 2009-04-03
Sound in Ubuntu and Linux in general does have problems, but before people rush to blaming it all on the OS, consider the following quote I found in this thread

[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

> []b]Hardware[/b]
At the bottom is the hardware, usually a sound chip on the motherboard. While only a few basic chips are generally used, OEMs have great latitude in configuring them. both physically and in the software/firmware that interfaces the chip to the operating system. For example, some manufacturers decide to have two microphone jacks on their machines, one in front, one in back, others reconfigure the input and output ports. so maybe the line in becomes the side or lfe output for surround sound. Sometimes they do this within the same model of a computer. 
Needless to say, this has created widespread confusion among users and the driver writing community. 

Then there are sound cards, the most popular are the Creative Labs Soundblaster cards. These have alternately frustrated and infuriated linux users since linux fist started and the situation has not much improved until now. Recently Creative has completely given up on writing its own crappy linux drivers and released some information to the community. But still.... Other manufacturers include C-Media who OEMs cards to many resellers including Turtle Beach and SIIG among others. These cards are well supported as are the high end professional audio cards from Hammersmith and M-audio. This is by no means a complete list, just some examples.

Finally, there are the bazillion little usb things you can plug into you computer. These are independent devices and many will change your sound configuration as the Sound Server finds them and adds them to its list, sometimes at the top making them the default, sometimes somewhere else. You need to check in your sound server to find them and set them up. Most of these should work out of the box because they are supposed to conform to usb standards but unfortunately some do not, especially older stuff and stuff that has gone through many revisions. 

If you just bought the latest greatest obscure thingamabob and it doesn't work, you need to realize that unless one of the other 15 people who bought it is a linux developer, or knows one, it probably be a little while before it is supported.

---

### Post by mb_webguy on 2009-04-03
> **LeBurt said:**
> Again everyone, you can come up with a million excuses about hardware and software and person-behind the keyboard. The fact is, Linux is nowhere ready for mainstream and until someone starts looking at it from a system perspective, it will likely stay that way.I could make the exact same arguments you're making against Linux not being ready for mainstream use for Windows.  

1) Sound:  When I installed Vista, my system didn't have sound *at all*.  Vista didn't support my audio card even though it was a fairly common card by a major manufacturer and had been on the market for over a year.  I had to go to the manufacturer's website, download the driver, and install it myself.

2) Video:  Windows won't play certain common video formats without downloading and installing arcane codecs and codec packs.  In Ubuntu, I can install all of these codecs with between one and three commands in the terminal, or with a few clicks in Synaptic.  And I've never had any problems with tearing or choppiness on any of the many Linux machines I've run, except when I was using the wrong video card driver.  Ubuntu lets me choose these from the Hardware Drivers list if one is available -- and if it's not, then the hardware manufacturer is at fault for not providing a Linux driver or not providing the specs for their hardware so Linux developers can write one for themselves.  The same would be true of Windows if the hardware manufacturer didn't provide a Windows driver.

3) Driver Installation:  In Windows, I have to actually install drivers!  Sure, some hardware is automatically detected, and the drivers automatically installed.  But for the hardware that isn't, I have to search online for the driver, download it, and install it.  And the specific installation method varies by manufacturer.  In Linux, if the hardware is supported by open-source drivers, it just works, with no installation of drivers required.  If the hardware requires a proprietary driver that is available, then I can install it with a couple of clicks in Hardware Drivers.

True, some hardware isn't well supported, but this is *entirely the fault of the hardware manufacturers*.  If they don't release a Linux driver, and don't release the specs for the hardware so that Linux developers can write one for themselves, then those Linux developers essentially have to reverse-engineer the hardware in order to figure out how to write a driver for it.

And consider this:  for any given hardware, there's almost certainly an alternative that is supported by Linux.  Since Linux is a voluntary community effort, we should be glad that some people out there actually devote themselves to writing drivers for hardware produced by manufacturers that don't release Linux drivers, instead of using supported hardware and assuming everyone else will, as well.

4) Application Updates:  Windows doesn't automatically update *any* software, except for bug releases and security updates.  Did Windows automatically update my XP to Vista when it was released? Did Windows update my version of Office when Office 2007 was released?  And that's software *produced by Microsoft*.

Sure, some Windows applications have the ability to automatically notify you of updates, some will even automatically update themselves.  But that's entirely application-specific, and *the same is true of some Linux applications!*  

So at this point, Ubuntu is actually a bit ahead of Windows, since Ubuntu can automatically upgrade itself (and its applications) whenever a new version is released!

And unlike in Windows, if you *do* want regular software updates, you can have them.  Canonical provides Launchpad so that developers can offer people recent builds of software.  And other distributions have rolling release schedules that continuously provide the latest versions of software.  (Ubuntu doesn't, because a stepped release schedule makes it easier to ensure a more stable system.)

5) GUI Responsiveness:  Windows is nowhere *near* as responsive as Ubuntu, in my experience.  In both Vista and XP, I've clicked to open an application and had nothing happen, so clicked again with again no result, only to have two instances of the application open an intolerable amount of time later.  If Windows is installed on a system with low memory, it simply crawls.  I've clicked to minimize a window and had to wait 10 seconds or more for it to actually do it.  And there's very little you can do to tweak the Windows desktop environment to improve performance.

Linux, on the other hand, is as responsive as you want it to be.  If Ubuntu is slower than you'd like, turn off desktop effects.  If that's not enough, switch to a lighter desktop environment like Xfce.  If that's not enough, drop the desktop environment entirely and just use a window manager like Openbox.  And if *that*'s not enough, you don't even have to use a graphical environment at all, since you can boot directly to a command prompt.

The simple fact is that no OS on the market is perfect, and all have some problems that someone could point out as indicative that the OS isn't ready for mainstream.  And you know what?  In my experience, far fewer people with little or no prior experience with Windows have complaints about Linux than people who have used Windows for years.  Based on the specific complaints I've seen, I really think that it's not that they don't have any basis of comparison, but rather that the Windows users see fault with Linux whenever something doesn't work exactly like it does in Windows.  

Linux isn't Windows, will never be Windows, and shouldn't try to be Windows.  Linux does some things differently.  Sometimes, the Linux way is better, sometimes it's not, but most of the time it's *just different*.

---

### Post by BGFG on 2009-04-03
1) Sound. 

Skype is a poor example to use. It is not being actively developed by the company responsible for it. this is not GNU/Linux's fault. Pulseaudio is also feverishly being worked on by dedicated individuals.

2) Video playback.

It must be you :) i have used the latest available beta drivers in both linux and windows. linux gives better performance. Since de-activating my swap file i no longer get the tracking delays i used to experience when skipping through a video file.

3) Driver installation.

This is what one would expect when installing a driver:
a) download driver
b) double-click to install driver
c) use driver

this is EXACTLY how 'Install Hardware Drivers' works. I clicked 'use' and nvidia 180.37 was downloaded and installed on my system. With the latest round of updates, 180.44 was automatically installed. 
in the case of drivers that need to be compiled, AGAIN, this responsibility lies squarely at the feet of hardware manufacturers. Microsoft does not make drivers, hardware manufacturers make drivers for windows.


4) Application updates.

i constantly get updates for programs that i use, It may take a litle while for the newest version to hit the repos, but they get there, then the 'useless' as you put it, notification system asks me if i'd like to install it. Your point may be a few years too late.

5) GUI responsiveness.

Something is wrong, again, with your hardware or reflexes. You can always use gconf to configure edge sensitivity. The combination of 64bit, ext4 and Gnome is the most responsive thing i have ever felt.

-------------------

All the topics you have mentioned are in a constant state of development and improvement. You sound like an end user who knows what he is about. I suggest a little more research into optimizing your system, it will pay you huge dividends. much like it did for me ;)

---

### Post by spiderbatdad on 2009-04-03
Am so pleased with the new nofication system; not only is it smooth and attractive, but very useful. I especially like the way it is integrated with pidgin, so that I don't have to toggle or re-toggle window focus. It simply has a nice notification, containing the message...in the perfect location too.

Windows is a joke...are we actually entertaining it as a comparison, in terms of what an OS should do, and as an example of usability?

---

### Post by Arup on 2009-04-03
The reason I use Ubuntu is because of speed of apps, videos load way faster than Vista x64, so do programs, I have not had a single issue related to videos, voice etc. The GUI has way better response than in Windows. Its a dream to encode videos and audio with pure x64 codecs taking full advantage of my x64 CPU. Apps like GkrellM has no paralel in Windows world, even Stardict is excellent although could do with better voice support. Overall I find Ubuntu way superior to my Vista installation and I am not the only one among my colleagues to think so. Many have tried Ubuntu and with proper guidance, have never looked back.

---

### Post by mdurham on 2009-04-03
So what do I answer if the following applies to me:
Never, but it's not the best OS
or
Sometimes and it does affect my work

Bad poll!

---

### Post by change_mode on 2009-04-03
> **LeBurt said:**
> 
_change_mode_: Misconfiguration: I'm sure you're right. Doesn't change my point. As for application updates, I'm thinking Ubuntu could come up with a means to make applications register themselves for regular updates. Canonical doesn't have to do the work, just provide the means.

Yes, they do have to do the work, because they're the ones who take the blame when something goes wrong.
They even go through the code before introducing updates, for security reasons.

> **LeBurt said:**
> 
Again everyone, you can come up with a million excuses about hardware and software and person-behind the keyboard. The fact is, Linux is nowhere ready for mainstream and until someone starts looking at it from a system perspective, it will likely stay that way.

Can't really take that argument serious after you showed quite a few times that you don't understand how it all works.
If Ubuntu isn't ready for mainstream use, then no OS is, except for preconfigured Mac systems ;)

---

### Post by 3rdalbum on 2009-04-03
Driver installation is a difficult one. Windows has the luxury of only having to support exactly TWO architectures - x86, and x86_64. And those are mostly compatible. Linux supports so many architectures, and as you know you can't take a binary from one architecture and run it on another. Linux is designed so that a driver as source code can be compiled for another architecture and used without problems.

Hence, the need for compiling a driver. I don't know what you're complaining about with this, though - I use exactly one custom driver that needs updating whenever I have a kernel update, and it takes about 10 seconds to recompile and reinstall the driver. It's literally "make && sudo make install".

The whole Windows thing of "double-click this program, click next and we'll install a binary driver" is much of the reason why nobody* uses 64-bit Windows - all the "binary drivers" are compiled for 32-bit, and since Windows is a proprietary platform, nobody gives you the source code to compile a 64-bit edition for your 64-bit system.

*When I say "nobody", I mean "not anywhere near as many people as who run 64-bit Linux"

---

### Post by Mooose? on 2009-04-03
> **anjilslaire said:**
> Just to be sure that no one's being biased, Windows does not achieve this either, and is just as full of usability problems as a modern linux distro. Most users don't see this because they've been using Windows for 5-10 years and they understand Windows.

Lets be fair now.

Why is Windows even relevant? I am talking about problems with Linux here, and your answer is essentially 'Windows sucks'. To use the usual car analogy, if I went into a dealership and required five minutes of struggling to get the car door open and when I mentioned this fact was told that 'other manufacturers are just as bad' I would not want anything to do with that company.

Also, Linux is substantially worse in usability than any of it's competitors.  This is fact which I even outlined a mathematical proof for due to the fact that FOSS advocates deal with usability concerns by pretending they don't exist.  Usability is fundamental to design, it cannot be addressed by patches, bugfixes or just by adding a skin.  It is integral to the software design process.  Just as you can't retrofit security as an add on when you're done (Look at MS) you cannot just add on usability as an afterthought.

I'd say your point is 100% wrong.  You are so entrenched in the Linux way of doing things you do not realise that there is a better way, simply as you have already invested the time to learn the convoluted system to the point where it seems normal, ignoring anyone who approaches from the outside who has not spent the time researching.

I run Windows 7 as my main platform and it is a radical departure from XP (and even Vista).  It is different, but it is better.  Essentially the problem is that the developers do not listen to their users and largely their ego's will not accept that they need to listen to users and UI experts who will drastically change the very nature of their projects.

I say all this as a developer myself.  While I do get offended and annoyed a lot of the time at user criticism (it's hard not to take criticism of your creation personally) I largely have no choice but to take it on board and deal with it.  And while I may not like it the software is generally improved as a result of it, and it makes me a better developer in trying to understand how users see these things.

---

### Post by Mehall on 2009-04-03
> **LeBurt said:**
> 1) Sound. 
2) Video playback.
3) Driver installation.
4) Application updates.
5) GUI responsiveness.

Never had a problem with any of those.

I'm not saying that just because mine works fine they can stop development on everything or anything daft, I'm just saying that many or maybe even MOST people DON'T have these issues.

3) Use Jockey. I've had no issue, at all.

4) Yes, because running Synaptic, hitting "Mark all upgrades" then "apply" (or my preferred route, "sudo apt-get update && sudo apt-get upgrade") is SOOO much easier than having windows update itself, then having three different updates processes going on, and a few more to do whenever you start a different program.

5) If you think Gnome is a bit bloated, use a different DE or WM.

I am a KDE man, never had any real issue, btu I'm using Openbox just now because I like Crunchbang Linux, and it's super fast, and generally very responsive (except for when opening Firefox, when it can take a short bit of time, but that's the same in Windows too.)

---

### Post by BGFG on 2009-04-03
ok guys, this thread is going exactly nowhere. Lets stop bumping it. we've seen this particular post before. We'll see it again. I'm off :)

---

### Post by LeBurt on 2009-04-03
Ok ok, I'll follow stderr and slow down a little. I didn't mean to start a war here, just trying to do a bit of rallying work. BTW, I think the user forum is exactly the right venue for this kind of discussion. Making a list and passing it on to devs is like a drop in the ocean. Rallying tens, hundreds, thousands of users to a unified view has got to have better impact (like, a bucket of water in the ocean). I'll stick here for a while.

As far as I understand, we have two types of people speaking on this forum:

Type Alpha: the Linux power user who spent much time learning, tweaking, configuring, fine tuning. Type A has already found a solution for most of his problems and has developed a kind of zen patience for the unsolved ones, alongside a reflex to guide every non-type-A user down the rabbit hole, a rite of passage into the intricacies of their world.

Type Omega: the Linux curious, newbie or lightly experienced, arriving on the scene with a lot of preconceptions from other systems, and therefore a lot of expectations as well. Type O is no doubt positively surprised by the recent advancement in the Linux foundation, but oftentimes a little turned off by what's missing. Like the [song]("http://video.google.com/videoplay?docid=2514730680283477734") says: "I got a girlfriend and things to get done.". When Type O expressed feelings about what's missing, he gets slapped across the room for mentioning a subject that I can only refer to as taboo.

Technicalities aside, humanly speaking, there's an unhealthy relationship between the two types and that is what's slowing the process down. Let's face it: before an OS, any OS, can be declared as ready for mainstream, it has to please both types. I'm sure everybody here grasped that my previous declaration:

> I declare that before ANYBODY says that Ubuntu is desktop-ready, it's got to have the video playback working on mine

is but a metaphor. I'm no more important than any other type O, I'm simply speaking for all of them.

There are undoubtedly enough Linux developers in the world tackling ALL the issues as they come. I somewhat feel that something is still missing. This organic project has grown in every direction. Canonical is trimming it to make it more appealing and doing a wonderful job. Passers by are looking at it for the street and saying: nice, but not quite so that I'll bring this home.

What's missing is simple: a coherent user community that doesn't whimper at the first sign of type A's defending their views. We need a good, healthy, constructive argument that doesn't degenerate into flame wars. Is that too much to ask for? 

So, back to the original list:

1) Sound: I sense agreement on this one. It stays.

2) Video playback: so it's a driver issue. Fine by me. Patience will solve this one as interest in Linux grows. Pass.

3) Driver installation: Hmm, need more user comments. What your experience with installing / updating drivers? Does it work for you? _3rdalbum_: I see your point. Most drivers do come with a script to automate the whole process. They also come with a lengthy manual procedure in case things go wrong. This is a Linux-only paradigm and in my opinion, a bad one if it's ever going to interest the type O users of this world.

4) Application updates: no so bad after all, fair enough. Pass.

5) Interface responsiveness: I'm surprised by this one as everyone here appears to think that Gnome's response time is very good. Anyone?

And new ones from comments:

6) Webcam and mic: that's a driver issue, related to my point 3
7) vpn: too specific. Let's keep a high-level view. Is anything wrong with Ubuntu networking in general? I personally never experienced any...

---

### Post by LeBurt on 2009-04-03
> **BGFG said:**
> ok guys, this thread is going exactly nowhere. Lets stop bumping it. we've seen this particular post before. We'll see it again. I'm off :)

See what I mean?

---

### Post by billgoldberg on 2009-04-03
> **LeBurt said:**
> Greetings Ubuntu veterans and newbies,

I'm just back from reading [an article (and comments) from Slashdot]("http://linux.slashdot.org/article.pl?sid=09/04/02/1317246") and it prompted me to create this thread in a hopeful, if naive, attempt to address the problem.

Some background first. I've been using Ubuntu for about 2 years and I must admit that it's been a mostly enjoyable experience. However, still today, there are aspects of it that I find mildly frustrating. In fact, I sometimes shake my head in disbelief, thinking "how can this be in a modern OS?". I know, it's free, it's democratic, it's evolving. Heck, changes from one version to another are often amazing and have made me stick with the product. On the other hand, well, some very basic and critical issues are left standing while new, less important features are being introduced (a new notification system comes to mind... pretty, but pretty useless if you ask me).

So, what I'm hoping here is to put forward a list of all that needs fixing first. This is entirely from a user perspective and should only be seen as positive criticism. If you are serious with making Ubuntu a mainstream, desktop-ready OS, it is essential that a list such as this one not only exists, but is considered seriously as a tool for improvement. 

As a simple rule for this thread, I think it would be best to avoid nitty-gritty specifics and stay at a comfortable cruising altitude of 5,000 ft. Avoid discussing bugs, hangups, config parameters. Instead discuss general issues, as I have below.

So here are my 2¢ that will, I hope, prompt others to provide theirs. Again, think of this as system-level positive criticism. 

------------------

1) Sound. 

When talking about basic general stuff, here's an ideal example for you. Sound in Ubuntu is way too complicated. There is no way I can be brought to care about PulseAudio, ALSA or what have you. All I want as a user is sound that works all the time. Regrettably, it's not so easy. 

As an example, consider configuring Skype's audio parameters. From the playback device list, I have like 8 choices in there. I once had the bad idea of playing with those, the soup got sour and now audio appears disrupted everywhere else on my system. Forums tell me "get rid of PulseAudio", try this and that, blah blah. I'm so turned off by the whole thing that I'll just wait for Jaunty.

Strictly from a user point of view, one would expect sound to be a "mature" aspect on any OS that should just work without any fooling around.

2) Video playback.

I once dreamed of having my own Linux-based PVR for everything media. Bad idea. There's no way you can compare video playback in Ubuntu to any other modern OS. It chops, tears, stays blank for the first 5 seconds of a file being played.

I tried different video players, played with settings, nothing worked. Forums tell me to try new drivers from Nvdia (see point 3) but then I also need to upgrade the player (see point 4). Honestly, I prefer waiting, maybe someday I'll have decent video playback out of the box.

3) Driver installation.

This is what one would expect when installing a driver:
a) download driver
b) double-click to install driver
c) use driver

Instead, you must follow an intricate procedure that sometimes implies compiling, manually editing config files, activating the driver from a GUI dialog. While I can do all these things, I can't seem to find them exciting. For one thing, I never really was able to shake off the feeling of not knowing exactly what going on. I'm not exactly a newbie in operating and maintaining my OS, but I somewhat relate this feeling to that of my aging parents who are "scared of breaking something" in all matters computers. Not a good thing.

4) Application updates.

Ubuntu does a great job updating itself when new libraries are available. Applications, on the other hand, don't seem to follow suit. It's be nice to have a prompt saying that a new version exists for Gimp, or Skype, or Firefox. Sadly that's not the case. Updating applications is a manual process sometimes as intricate as installing a driver and then you're never sure if the old one is still there, how to remove it, etc.

5) GUI responsiveness.

I may have been spoiled with responsive GUIs in the past. Fact is, I find Ubuntu's GUI (ie Gnome) to be slow and unresponsive. Example: how many time have I wanted to resize a window and ended up selecting a bunch of icons on the desktop instead. The procedure I follow is easy and universal: move the mouse pointer to a window corner, click and drag to the right size. Well, I find that doing this too fast doesn't work. I must slow down, wait for the cursor to change to the slanted double-arrow, click, wait, start dragging slowly. You get the hang of it after a while, but it's still pretty much annoying.

-------------------

All right, that's it. I know there are going to be some people answering this thread with this or that workaround or witty comment about me having overlooked something somewhere. Thanks, but that would be beside the point. 

The point here is: hey Ubuntu gurus, fix these first. Please...

I agree with point 1-4, not with 5. 

**1) Sound. **

I just switch everyting to ALSA, for consistancy.

PulseAudio is still a mess on Ubuntu 8.10. 

Switching desktops causes playback to skip, same for scrolling in firefox, wtf?

ALSA doesn't have that problem.

I had the same problem with Skype on my netbook, I had to try different stuff for 15minutes until the mic worked.

**2) Video playback.**

The current drivers that Ubuntu installs in Ubuntu 8.10 just don't cut it. 

I have a 22 inch monitor (1680x1050) and playing an xvid video fullscreen means laggy playback.

Now I have installed newer drivers and all is well, but still it's annoying.

It must be noted that the Vista driver (I use that one on Win 7), isn't much better.

It performs way better, but crashes at least once a day.
[B]
3) Driver installation.[/B]

Things could be easier, but I don't really have a problem installing drivers. I can see how other users might have that problem.

**4) Application updates.**

As we all know the repos are locked for application updates.

While that has it's advantages to the rolling release model, I believe they should make a few exceptions for popular software apps.

---

### Post by koenn on 2009-04-03
> **LeBurt said:**
> 
So, what I'm hoping here is to put forward a list of all that needs fixing first. 
If you are serious with making Ubuntu a mainstream, desktop-ready OS, it is essential that a list such as this one not only exists, but is considered seriously as a tool for improvement. 

The point here is: hey Ubuntu gurus, fix these first. Please...

Noble effort, but if you're serious about contributing to making Ubuntu a mainstream, desktop-ready OS (sic) or have the issues you mention, addressed, then you should

A/ talk to the people who actually have impact on Ubuntu's development - Ubuntu devs, upstream projects, Canonical, ...

B/ talk to those people in a way that facilitates their work or aligns with the way they've organised themselves (think: launchpad, dev mailing lists, ... )

C/ speak their language : specs, analysis, use cases, blueprints, road maps, ...

D/ acquire the authority to have them listen to you and pay attention to what you say. This is most often achieved by being a reputed developer yourself.



I'm afraid typing out a post on a user support forum won't help much.

---

### Post by wolfen69 on 2009-04-03
> **Mooose? said:**
> 
Also, Linux is substantially worse in usability than any of it's competitors.  This is fact which I even outlined a mathematical proof for due to the fact that FOSS advocates deal with usability concerns by pretending they don't exist.

you're too funny. please go have a beer with steve and bill.

do you honestly think you're going to change anyone's mind here?

lastly, your "points" are some of the worst i've ever seen. at least most windows fanboys bring up better points than your %#$@. FUD at its best.

---

### Post by LeBurt on 2009-04-03
koenn:

A/ Later, that's step 2. Step 1 in my answer to your point D/ below.

B/ Same answer

C/ Not necessary and in fact, this is the very paradigm I'm trying to break: user input, non-technical, high-level, requirements-driven, you get the idea. If you have done any amount of software engineering for clients, you know this. Clients will tell you their requirements, as low-tech and fuzzy as they may be, and you have to translate them into models, interfaces, workflows, etc. Is this here any different?

D/ Or, represent a large enough user community that says "hey folks, look up, we're here and these are our needs" in the language of C/ above. Does such a community exist somewhere because if so, I'd gladly join them rather than start this completely naive effort from the start. One way or another, it has to be done.

---

### Post by wolfen69 on 2009-04-03
> **LeBurt said:**
> Does such a community exist somewhere because if so, I'd gladly join them rather than start this completely naive effort from the start. One way or another, it has to be done.

i like your sincerity. [Get Involved]("http://www.ubuntu.com/community/participate").

---

### Post by cotcot on 2009-04-03
Another vote on sound. Just take some statistics on the thread titles.

---

### Post by koenn on 2009-04-03
> **LeBurt said:**
> koenn:

C/ Not necessary and in fact, this is the very paradigm I'm trying to break: user input, non-technical, high-level, requirements-driven, you get the idea. If you have done any amount of software engineering for clients, you know this. Clients will tell you their requirements, as low-tech and fuzzy as they may be, and you have to translate them into models, interfaces, workflows, etc. Is this here any different?

D/ Or, represent a large enough user community that says "hey folks, look up, we're here and these are our needs" in the language of C/ above. Does such a community exist somewhere because if so, I'd gladly join them rather than start this completely naive effort from the start. One way or another, it has to be done.

It's still going to take more than a thread on a forum. There's already a ton of those in Recurrent Discussions. And in Brainstorm.

But you seem to have given this some thought already, sso I'll just wish you good luck.

---

### Post by days_of_ruin on 2009-04-03
> **TyrantWave said:**
> Webcam and Microphone support.

That's all I ask really.

Huh? What is there to support? They are plug and play on ubuntu.

---

### Post by Tibuda on 2009-04-03
> **days_of_ruin said:**
> Huh? What is there to support? They are plug and play on ubuntu.
It depends on which manufacturer. Just like any hardware.

---

### Post by Keithhed on 2009-05-24
bump

---


---
title: "Is Linux becoming as arrogant as Apple and Microsoft?"
date: 2011-11-30
forum: Recurring Discussions
---

### Post by mauvebic on 2011-11-30
DISCLAIMER: Let's dispense with the obvious Gnome3/Unity examples, its been discussed ad nauseam

It seems to me over the years developers have been taking an harder line over what they think is best for users, even though the line between developer and user is a lot more blurry in linux than it is in microsoft/mac.

I can cite a few examples:
[LIST]
[*]**ATI proprietary drivers**
My graphics used to work wonderfully until my card ceased to be supported and i had to resort to the open source drivers. In the years since, ive found many threads complaining about substandard graphics (usually tearing, distortions, and blockyness) yet these bugs never get fixed and rather than finding a way to re-integrate the proprietary drivers for cards that aren't really that old, were told to upgrade our graphics card even though when i reboot into XP to play games i have no problems there.
[*]**Being forced to upgrade your system for latest version of your favorite software**
i detest having to upgrade a system i am perfectly content with just to get the latest VLC player. Not to mention the hours (if not days) of tinkering to restore all my settings (and finding that some of those settings have disappeared, because someone else decided for me what's best. (to draw comparison you can still get the latest VLC version in windows XP)
[*]**how they keep changing the default applications** and ramming it through distribution upgrades
Again, anyone whos been around long enough already made up their mind which software is best for what. Having rhythmbox, banshee, shotwell, etc.. rammed down my throat through upgrades when im perfectly content with VLC + audacious + chromium just means ill be spending an hour or two doing apt-get purge <insert unwanted app>
[/LIST]

When i think about all the frustrations ive had over the years, linux isn't that much different from apple's walled garden or microsoft ramming DRM down our throats. The only diference is in what linux chooses to ram down our throats. Its not just an Ubuntu thing, considering the derivative nature of three quarters of all the distributions. The frustrations are quite similar across spectrum.

And let me also dispense with some common retorts

> No one's forcing you to use linux
Quite right, thats why i never completely switched. I keep XP for certain tasks just like linux excells at others. Both with their own frustrations.

> Get involved
Not all developers are OS developers. Speaking for myself, ill stick to php/ajax/SQL. My problem isn't really with the code but with the policies enacted by major distributions.


I've noticed lots of similarities between linux and organized religion. Devs and OS pushers are a lot nicer to people they're trying to convert than they are to their longtime users, perhaps because they think they already own us and we wont leave.

---

### Post by kio_http on 2011-11-30
1) Ati's choices have nothing to do with linux
2) If you support new things on old OS's, the old apps it was intended to run with will stop working (you may like Arch linux)
3) Apps choices vary from user to user, there is no universal config to suite everybody

How can an OS kernel be arrogant???

---

### Post by mauvebic on 2011-11-30
> **kio_http said:**
> 1) Ati's choices have nothing to do with linux
2) If you support new things on old OS's, the old apps it was intended to run with will stop working (you may like Arch linux)
3) Apps choices vary from user to user, there is no universal config to suite everybody

1) ATI didn't change, the kernel did.
2) so its either upgrade to a release you dont want, or stick with old software. Doesn't explain why i can still get the latest VLC in XP but not in linux w/o upgrading.
3) i know, but it would be alot more sensible to let users choose between default config and their config *during* the installation, save alot of us hours of hassle.

---

### Post by mauvebic on 2011-11-30
> **kio_http said:**
> 
How can an OS kernel be arrogant???

please don't be so basic, you know im talking about linux as in the OS and all the distributions therein. unless you want me to specifically list every single dist, might take a while though.

---

### Post by kio_http on 2011-11-30
> **mauvebic said:**
> 1) ATI didn't change, the kernel did.
2) so its either upgrade to a release you dont want, or stick with old software. Doesn't explain why i can still get the latest VLC in XP but not in linux w/o upgrading.
3) i know, but it would be alot more sensible to let users choose between default config and their config *during* the installation, save alot of us hours of hassle.

1) Makes no sense as its ATI that chose not to release drivers for new kernels. E.g Intel on the other hand has Open Source drivers only. Propriety drivers are 100% under AMD/ATI 's control, Ubuntu devs can't do anything.

2) Yes XP is supported, try getting the latest VLC in Win95 Besides the source is there compile it if you want and compile the dependencies one by one too. IE9 is unavailable in XP, WMP 12 is not there in Vista and XP

3) We do not want to ship the OS on a 2TB HDD to let users chose.

4) You could say linux distros. Arrogant is a pretty strong word don't you think.

---

### Post by mauvebic on 2011-11-30
> **kio_http said:**
> 1) Makes no sense

2) Yes XP is supported, try getting the latest VLC in Win95 Besides the source is there compile it if you want and compile the dependencies one by one too. IE9 is unavailable in XP, WMP 12 is not there in Vista and XP

3) We do not want to ship the OS on a 2TB HDD to let users chose.

1) Makes perfect sense, i can still download the driver from ATIs website, it just ain't compatible with the kernels, hasn't been for a long time, and very little is done to address obvious deficiencies in the opensource drivers.

2) try choosing versions from the same decade. XP is older than Dapper Drake, try getting the latest VLC in dapper drake.

3) again, basic. You already know the installer asks to download updates and third party software during install, how dificult would it be to add a dialog offering users their choice of software. You dont need ten DVDs to do that. You could include the defaults on the CD, or let the installer download alternatives. Either way it would save us all from the post-install scripts which have become so popular but take hours to run their course.

---

### Post by haqking on 2011-11-30
Linux is a kernel and not a company.

Microsoft is a company (for profit)

Mac is a product made by Apple (a company for profit)

The generalisation of Linux is incorrect as it is not a single entity or company and is not for profit.

Every distro (company) of Linux have their own agenda generally.

---

### Post by kio_http on 2011-11-30
> **mauvebic said:**
> 1) Makes perfect sense, i can still download the driver from ATIs website, it just ain't compatible with the kernels, hasn't been for a long time, and very little is done to address obvious deficiencies in the opensource drivers.

2) try choosing versions from the same decade. XP is older than Dapper Drake, try getting the latest VLC in dapper drake.

3) again, basic. You already know the installer asks to download updates and third party software during install, how dificult would it be to add a dialog offering users their choice of software. You dont need ten DVDs to do that. You could include the defaults on the CD, or let the installer download alternatives. Either way it would save us all from the post-install scripts which have become so popular but take hours to run their course.

Why would Ubuntu's kernel change. Its ATI that should remake the driver. How can Ubuntu's kernel know how an old proprietary driver works.

2) We all know that XP has had its life extended, see MS support lifecycle page. MS supports releases for a longer period. Dapper drake is unsupported. Why don't you consider an upgrade to Oneiric as something like MS saying you need .net 4 to run x app or XP Service Pack 3

3) It will confuse new users. Use SuSe studio if you want or remaster Ubuntu.

Anycase use another OS if you disagree with this policy then.Like I disagree to code for Windows Metro as I don't like [the policy]("http://ubuntuforums.org/showthread.php?t=1888336")Like I also disagree with your attitude (I find it arrogant) and disagree to participate further in this thread.

Note: You can start a company to fund the support of dapper drake if you want, might cost a few million dollars.

---

### Post by mauvebic on 2011-11-30
> **haqking said:**
> Linux is a kernel and not a company.

Microsoft is a company (for profit)

Mac is a product made by Apple (a company for profit)

The generalisation of Linux is incorrect as it is not a single entity or company and is not for profit.

Every distro (company) of Linux have their own agenda generally.

I dont contest any of that. When i speak of linux im generalizing for all distributions (simply because registering on each forum and posing the question to each distribution would be too time consuming)

If i had to respond to that though i'd still ask if free software is really that much better than paid software. In free software you have choices yes, but what is freedom if your choices are being restricted from the top?

Mac and Win are still arrogant, but at some point they still have to follow the money and respond to consumer demand.

---

### Post by mauvebic on 2011-11-30
> **kio_http said:**
> Why would Ubuntu's kernel change. Its ATI that should remake the driver. How can Ubuntu's kernel know how an old proprietary driver works.

2) We all know that XP has had its life extended, see MS support lifecycle page. MS supports releases for a longer period. Dapper drake is unsupported. Why don't you consider an upgrade to Oneiric as something like MS saying you need .net 4 to run x app or XP Service Pack 3

3) It will confuse new users. Use SuSe studio if you want or remaster Ubuntu.

Anycase use another OS if you disagree with this policy then.Like I disagree to code for Windows Metro as I don't like [the policy]("http://ubuntuforums.org/showthread.php?t=1888336")Like I also disagree with your attitude (I find it arrogant) and disagree to participate further in this thread.

1) the kernel did change. fact of life. it changes with every version, and if the option existed for a modern kernel that is more backwards-compatible, i would most certainly use it.

2) New version will still be compatible for XP for some time to come regardless of what microsoft thinks of XP. Simply because there's demand for it and most people dont wanna buy a new computer just because the OS demands it.

3) New users aren't that dumb. They might be new to linux, but a dialog box is a dialog box regardless of the OS. Anyone whos evern taken a census/survey knows how to check a box, be it with a pointer or a pencil.

Who knows maybe i am arrogant, but no more than the rest here. Might have something to do with the fact that i started out using [this]("http://3.bp.blogspot.com/-7MaZtq_Cfxk/TmT9LllDDSI/AAAAAAAAFe0/um60DNrGkd0/s1600/old+toshiba+laptop-1.jpg")

Either way, i dont think its arrogant to question the direction of leadership. Debate and dissent are the pillars of freedom.

It's also worth mentioning that there's a recession on in many parts of the world, and its going to get worse. Most people dont earn what programmers earn and the average consumer will be looking to extend the life of their current hardware and gadgets as buying them on credit is becoming increasingly impossible. I just think we should take notice and work on that backwards-compatibility a bit more.

---

### Post by CryptAck on 2011-11-30
> **mauvebic said:**
> 
2) so its either upgrade to a release you dont want, or stick with old software. Doesn't explain why i can still get the latest VLC in XP but not in linux w/o upgrading.


Unfortunately to the user, many OSS development projects work differently than commercial software development efforts. Often in OSS only a small subset of people volunteer to work on a project. In commercial software, people are paid to develop on a managed application. So in OSS, if a developer volunteers, it is likely he or she will want to work on the "new and cool features" over fixing some random bug due to a incompatibility. In commercial software, the developer is paid and directed by the company as to what they'll work on, so maybe that cool new feature will be added by another development team while the developer's current team will maintain the "current" build. 
 
So imagine several OSS applications continually changing and enhancing. Now imagine you develop for a project that depends on one of these application libraries that every six to twelve months has a new release. With each new release of your project you'll pick up the newest version, and maybe even use some new API, which is not always backward compatible with last. While your application is doing this the Linux distro is doing the exact same.
 
Now in Windows development, if you need a library that doesn't exist  you'll include the DLL with your project. In Linux, you are dependent on the library version that is installed on the system -- which is what causes dependency hell when you attempt to use software that is up-to-date on an old system or is out-of-date on a new system.

---

### Post by uRock on 2011-11-30
This isn't the first time this topic has been discussed => Moved to Recurring Discussions

---

### Post by mauvebic on 2011-11-30
One simple solution would be to allow the user to install more than one version of the same library. It would add the constraint of software having to call a library by specific version number, but it would also make it easier to satisfy dependencies for software that rely on those libraries.

---

### Post by Dangertux on 2011-11-30
Sounds like you need to learn to install software by another method besides the repos. You will find if you learn to satisfy dependencies and compile your own software you can install whatever version you want.

As far as what ATI is doing with proprietary drivers neither Canonical, the Ubuntu development team, nor the kernel development team have any control over what AMD makes a priority.

Hope that helps.

---

### Post by rg4w on 2011-11-30
> **mauvebic said:**
> It's also worth mentioning that there's a recession on in many parts of the world, and its going to get worse. Most people dont earn what programmers earn...
How much do you think a volunteer contributor to the Ubuntu project makes?

> I just think we should take notice and work on that backwards-compatibility a bit more.Did you mean "we" as in "I want to help too" or just what you think others should do for you?

Here's my own take on free software - YMMV, and you're free to feel differently about it:

Free software does what it does, and I can either participate or not depending on my interest level and skill set (though it should be noted that not all contributors are programmers - there's a HUGE need for documentation, the Ayatana list is open for design discussion, and I feel there's a huge opportunity in exploring distributed usability testing).

When software does what I need, I use it and enjoy it. When it doesn't, I use something else.

I'm grateful that others are willing to spend long hours over thousands of days to deliver free software for me to use, and I don't consider it my place to tell them what more I feel they should do for me.

Free software is a gift.

---

### Post by wolfen69 on 2011-11-30
> **mauvebic said:**
> 
2) so its either upgrade to a release you dont want, or stick with old software. Doesn't explain why i can still get the latest VLC in XP but not in linux w/o upgrading.

PPA's or compile. If you don't know how to do it, ask. Many 10.04 users have the latest firefox and vlc player.

---

### Post by haqking on 2011-11-30
I think if you spent your time putting forth the effort to learn how to use your system of choice rather than complaining about others work your time would be better spent.

none of your arguments are valid.

Upgrades are not forced.

Default apps are neither here not there as apps required are different for everyone so choose and use what you like.

Learn to install and compile so you can use what you like in whatever version.

And learn that some issues are external to an OS such as other companies such as ATI/AMD etc.

Infact just learn then come back with a better rant ;-)

perhaps you could learn how to pay for proprietary software or better still learn to code and develop and make improvements yourself.

---

### Post by aysiu on 2011-11-30
ATI drivers are proprietary, but I've experienced hardware regressions on supposedly "open" hardware (Intel, for example).

I also think it's about time we moved away from only one version of each library being installed. Maybe back in the days when hard drive space was scarce that made sense (or maybe for servers, as opposed to desktops/laptops/netbooks). These days, or even a few years ago, 120 GB or more is standard for home computers. New computers typically come with at least 500 GB of space.

Granted, most people don't care to use the latest version of software (I've seen enough Windows users with old versions of Firefox, for example, or a ton of Windows updates waiting to be installed), but the *option* to install new software easily (without adding a PPA for each individual one) should be standard.

Ideally, desktop Linux repositories would be a cross between the Apple AppStore and the Android Market--curated (only for malware, not for "offensive" apps) but with the option to install outside of the repositories. More importantly, like the AppStore and Market, perpetual upgrades available for new applications without having to upgrade the entire OS.

That said, I don't agree that pestering new users with lots of questions is the best for an installer. I remember being a new user and being confused by installers that asked a lot of questions. The solution to bad defaults isn't a lot of questions. The solution to bad defaults is changing the defaults to be *good* defaults. I don't really see that this is a problem across all Linux distributions, though. It really seems to be a major Ubuntu problem. Debian, for example--is that constantly changing default applications? Is Mepis? Is Linux Mint?

I usually don't like snarky responses of the "If you don't like it, fix it yourself" variety, but I will say that Remastersys is dead-easy to use if you want to create your own custom Ubuntu (with exactly the packages you want installed and exactly the wallpaper, etc.).

"Arrogance" is probably not the appropriate word here. And it's not a walled garden either. The real issue with the desktop Linux infrastructure is the do-it-yourself nature of it. Much of the software that gets developed for consumer Linux is based on a "If you want it different, change it yourself" mentality. Even Ubuntu, which is *supposed* to be more of an everyday accessible distribution, is ultimately about what Mark Shuttleworth wants, not what's best for the users. Mark Shuttleworth has made it clear that Ubuntu is what he calls a meritocracy and not a democracy. But his idea of meritocracy isn't that the ideas have merit--it's more that the people with the ideas actually implement them. And that attitude is generally the predominant one in the desktop Linux communities: If you're willing to put in the energy to change things, thing will change. If you just whine about things, nothing will change.

I see a type of merit in that approach. But there are limitations, too. Sometimes people who don't have the skill or knowledge to implement changes actually have good ideas for how things should be implemented, so that's how a lot of good stuff gets missed out on.

This is why, even though I'm grateful for the work open source communities have put into making great applications and operating systems, I am not fanatically devoted to open source. I'm far more concerned about open standards than open source. For example, Opera is a closed source program, but it follows HTML standards, so good for Opera. Google's Gmail is closed source, as is the Gmail app for Android, but Gmail allows you to view your messages through webmail, POP3, or IMAP. You can easily export your address book. It plays nice. Playing nice matters more to me than playing open source.

---

### Post by Witch Lady on 2011-11-30
Yo the OP: how do you expect.the new user to.choose programs during install?

---

### Post by MG&amp;TL on 2011-11-30
Agree with haqking.

I know you said 'get involved is not a valid answer', but I see no complaints from you about web application/utilities. Therefore if you want improvement, go help.

If you want apt-get, don't complain about installing multiple libraries (IDK if I'm right, but I have no doubt dlls get updated too).

If you do need multiple libraries, learn to use *make*  :) Or go the whole hog, and go Gentoo.

---

### Post by Roasted on 2011-11-30
> **mauvebic said:**
> 1) ATI didn't change, the kernel did.
2) so its either upgrade to a release you dont want, or stick with old software. Doesn't explain why i can still get the latest VLC in XP but not in linux w/o upgrading.
3) i know, but it would be alot more sensible to let users choose between default config and their config *during* the installation, save alot of us hours of hassle.

1 - I don't see Nvidia being lazy and not updating their stuff. Just ATI, who is the one to blame, unfortunately.
2 - You can update software. Linux is more stable because the software packages are by default locked. A simple PPA later and, oh my gosh, you have the latest VLC!

---

### Post by KiwiNZ on 2011-11-30
In short the answer to all three is .....No

It is not compulsory to use any of them, don't like a particular OS, don't use it, simple.

---

### Post by satanselbow on 2011-11-30
Really...

You want it to be better? Code it...

Can't code? Learn to code... and don't forget to share the fruits of your labours with the rest of us FOR FREE...

This really is one of the most ignorant / arrogant / pathetically lazy threads here... oh how the freedom's of the internet have removed the need for joined up thinking.

I don't see much choice in software during windows setup. The windows "choose a browser" dialogue causes confusion for many of its users... had a client recently tentatively asking about installing "Microsoft's Firefox"...

---

### Post by Atamisk on 2011-11-30
Can someone explain how ATI's drivers don't work? my lsmod seems to state otherwise?

---

### Post by eric-yorba on 2011-11-30
If you don't like Linux, you can always ask for your money back.

---

### Post by Tibuda on 2011-11-30
Apple and Microsoft never were arrogant.

Linux neither.

RMS always has been arrogant.

---

### Post by kaldor on 2011-11-30
> **mauvebic said:**
> 1) Makes perfect sense, i can still download the driver from ATIs website, it just ain't compatible with the kernels, hasn't been for a long time, and very little is done to address obvious deficiencies in the opensource drivers.

2) try choosing versions from the same decade. XP is older than Dapper Drake, try getting the latest VLC in dapper drake.




1) AMD no longer supports ancient cards. They released their driver specifications and let the community work on them instead (also have 4 paid employees for open source driver dev). The Linux kernel developers have 0% to do with this. It's like blaming Bill Gates if I refuse to make a Windows version of a program I write. The kernel developers aren't going to bend over backwards to make sure a small minority of people using Legacy ATI cards will get the same compatibility. My advice is to get a newer card since it's probably pressing 10 years old by now and not worth modern usage anyway.

The open source driver developers are working constantly and very hard on them. Check their development logs. I'm not saying to "just accept the poor quality", but realize that it's a very difficult process to make good quality drivers. I believe they have superior 2d performance than the blobs do these days, though.

Compatibility is a reason I am in favour of open source drivers. As soon as I get acceptable 3d performance, I'm probably never going to use the blobs again. Open source graphics are majorly important to Linux's progress and uptake. The blobs are not stable enough and cannot be shipped with the distribution. Sadly, the opposite is true for the OSS drivers- they're much more stable than the blob, but their performance in 3d and acceleration is very unacceptable.

2) Dapper Drake is not supported anymore (XP is). Even so, you can still download VLC from their website. Ubuntu 12.04's cycle might help to address the obvious issues when updating, though. Also, you *do* have access to backports.


The arrogance that "Linux" has doesn't make sense. Point fingers at the correct people/organizations.

> **Tibuda said:**
> RMS always has been arrogant.

:)

---

### Post by wolfen69 on 2011-11-30
> **KiwiNZ said:**
> In short the answer to all three is .....No

It is not compulsory to use any of them, don't like a particular OS, don't use it, simple.

Well said. It makes no sense to complain about what something *isn't*, instead of just using what *does* work for you. Linux can be anything *you* want it to be, nothing more, nothing less.

---

### Post by Thewhistlingwind on 2011-11-30
Honestly, if you want to choose your applications at install, you should use the mini.iso or the network install.

On Ubuntu's side, I think that PPA's should be easier to install. Maybe you an option could be added to install a PPA from a softwares entry in the Ubuntu software center?

However, I DO wish that OSS developers would spend more time bug hunting. It's not exactly sexy work but it is important.

---

### Post by cariboo on 2011-11-30
It seems the op of this thread has moved his part of the discussion to the Mint forums, as he doesn't like the answers he's getting here. Thread closed, unless the op requests it be reopened.

---

### Post by aysiu on 2011-11-30
> **eric-yorba said:**
> If you don't like Linux, you can always ask for your money back.
I'm not a fan of this attitude. Really seems to go hand in hand with the anti-Linux "you get what you pay for" attitude. Cost-free software can be and often is very high quality.
[The Linux Community's Mixed Messages](http://www.psychocats.net/ubuntucat/the-linux-communitys-mixed-messages/)

---


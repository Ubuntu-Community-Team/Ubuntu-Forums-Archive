---
title: "The Great Ubuntu Let Down"
date: 2010-10-25
forum: Recurring Discussions
---

### Post by DitchingMS on 2010-10-25
Hi everyone

I'm a relatively new Ubuntu user, having just installed 10.10 about a week ago. I tried 9.04 last year and after so many crashes, driver errors, reinstallations, etc., I gave up on it. I've decided to give it another go but in all honesty none of the problems I saw then have disappeared. I know you fans hate to make comparisons with Windows but fundamentally Windows allows experimentation in relative safety for a beginner yet Ubuntu does not. Specifically, installation of software and drivers. To give an example; last year I installed Linux ATI drivers for my graphics card becuase I couldn't get desktop effects or play the best looking games. I've spent a lot of money on my graphics card because I want things to look good. Yet the ATI drivers broke the system. I tried on and off for days or even weeks to remedy the corruption, supported by the forum, but I just did not have the understanding to go into some recovery mode on boot up and type commands into a terminal. Even when I tried this, the commands were not successful. There was no guidance, no hand-holding, no safe-mode. One more reinstall. The more competent Linux users out there may sneer at my ineptitude but to me, making things user-friendly and safe is very important. I'm a design engineer by trade and I know that however complicated a mechanism is on the inside, you have to make the outside so simple that a monkey could use it. I don't design control panels with all the same colour buttons because you might press the wrong one and I don't design machinery that you could accidentally jam your finger in and I don't design machines that you would need special training or qualifications to operate. My designs are clever and functional but they are safe, and by intuition they guide you through while never losing their primary function.

If I could draw a parallel, fifty plus years ago if you needed to operate a car you might have to know everything about them. You would regularly have to do strip downs, rebuilds, maintenance (decoking engine, greasing bushes, etc.), you would have to start them with a crank. They were involving and complicated. Nowadays you are lucky if the average driver knows how to top up the water or check the oil, yet modern cars are many times more complicated under the bonnet than they used to be. If you want to be a mechanic now then that's great, you can get just as involved as ever, remapping ECUs, changing fuel injection systems, modding, customising, adding new shocks. But the point is, that's optional. That's why everybody can own a car without worrying.

Now to take you back to Windows/Linux: Windows isn't great, nor is it well programmed, nor is it tremendously stable, nor is it cheap nor ethical - but it works with almost every piece of software you can throw at it and if it doesn't have a driver or doesn't like the one you've installed it finds a temporary fix so you can at least make some backups. I'm well aware that things can go awry now and again being a seasoned veteran! With Linux however there is no safety net, no second chance, no failsafe. You install something, reboot and hope for the best.

I'm now in the position where I am planning ditching a functional, compatible, and user-friendly OS (Win XP) to make the move to Ubuntu, but I by nature am an experimenter, an optimiser and a tinkerer. I can do this in Windows without worrying that my next download will be my last. As for Ubuntu, I sing it's praises over its cleverness, its good programming, its user support, its stability, its flexibility and so much more - but fundamentally it will not encourage me to tinker as it has no Backup, Restore, Failsafe or Compatibility mode - at least, not until I'm able to remember all the terminal scripting. I will not take the risk or make the move until I have it.

I'd like to give everyone the opportunity to recommend some good GUI-based apps which can function as a Linuxised 'Windows Restore'. No doubt much better, more reliable but as a minimum, easy to operate, fast, easy to recover from refusing-to-boot systems and thorough. I have tried Clonezilla but it's not intuitive for a beginner, is quite slow (ok I know it's a lot to back up) and is essentially a text-based program. What I want is something that is presented with the confidence and approachability of Windows System Restore.

Don't criticise me for using WSR as an example - I'm aware of it's flaws and of the OS as a whole and as a seasoned programmer I know it's damaged beyond repair - especially Vista and 7 - but it's very hard to break it to the point where you lose everything and Ubuntu offers this as a daily treat.

If you don't agree with me have a look round these forums and see how many users are put off their new Ubuntu OS because of the same problem...

---

### Post by cottfcfan on 2010-10-25
hi Ditchingms,

I can understand your frustration, ive been using Linux now for 2 years, and in the beginning it was a nightmare. Reinstall after reinstall, because of my tinkering. So my solution.
 Install your main usable OS, then alongside it install another system on a small partition to mess with, if it works well on there implement it in the main one, if it dosent, don't.
If you screw it up, 5 minutes and its reinstalled.

---

### Post by Mark Phelps on 2010-10-25
Unfortunately, there STILL is no Ubuntu equivalent of System Restore, or more likely what folks want -- the ability to rollback their install to a prior date.  Whenever I've mentioned that here, I get soundly thrashed because, according to some responders, EVERYONE should know (somehow?) that they should back up their system before doing upgrades.

OK, granted that, but telling someone NOW that they should have done a backup first, when all they did was a version upgrade and now, they have a black screen with a blinking cursor ... this is really of NO HELP to new folks.

My solution is similar to what others have posited -- I maintain two Ubuntu versions at all times.  When I do an upgrade, I erase the oldest version and replace it with the upgrade.  That way, if anything goes terribly wrong, I have the previous version in place.

As to GUI-based backup/restore, I use Clonezilla (yes, it's a text GUI) and while it does take a little mastering, it works very well.  Others use other approaches -- dd and remastersys, but I believe that dd is CLI only and don't know about remastersys.

---

### Post by Megaptera on 2010-10-25
I use Remastersys to create a full backup DVD (something to clutch in my paw!!).

Useful guide from this forum:

[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

---

### Post by onaridge on 2010-10-25
I was an advanced Windows user and recently installed Linux after my latest infestation of viruses and spyware. I was advised to install Ubuntu Lucid Lynx (10.04)LTS because it is stable. I have found it quite forgiving as I have made several mistakes and the system is still as stable as ever. I love it so far. Try 10.04 LTS, you'll probably happier. I also highly recommend buying a copy ($25 used) of Practical Guide to Ubuntu Linux, A (3rd Edition).

---

### Post by philinux on 2010-10-25
Moved to recurring.

---

### Post by Swagman on 2010-10-25
Whilst I share some sympathy to your statements (been there as well on some things) you *** REALLY*** should research (expensive) components before buying them.

This is true for EVERYTHING you buy.

ATI cards are known to be *somewhat* problematic even for Linux Gurus so why buy one to use in Linux?

As for system restore.. Well, I guess it could be useful but then if you have a separate /Home partition you can just re-install over the top and not format /Home. <-- bit drastic I admit.

---

### Post by Quackers on 2010-10-25
Whilst I understand your pain, rummaging around in the fog searching for answers to problems you feel shouldn't exist, I can't agree with your analogies.
You obviously haven't had Windows updates cause your system to be completely unbootable, or a new video driver from Microsoft which crashes your system, or a new wireless driver that stops your wireless card from working. I have had all these things and more. Windows updates once borked my system so badly I had to re-install the system. That's unforgivable to me.
I can't agree that Windows is "functional" when system restore stops working because you installed the anti-virus software that came free with the pc! 
You can start up Windows day after day, then one day it won't find your TV card, or your webcam. No reason, it just couldn't be bothered that day. This is poor.
Windows, in my view, is poorly written. It is needlessly over-complicated in its design and when you consider the time that it has existed, it performs poorly, and is relatively unstable.
It does have one big plus, as far as I'm concerned. It caters for a very wide spectrum of hardware out of the box. This is to be commended. Ubuntu is not so all-encompassing and I personally think it drops support for older stuff too quickly.
With regard to your car analogy, I suspect that is more to do with manufacturers making parts that cannot be repaired. Car parts are now made to be replaced rather than taken off and having bits repaired/replaced. There are no user-serviceable parts now. There is no need for the end-user to know anything now.  The electrickery on modern cars just assists the mechanics to guess at which part to replace, using a very expensive computer.

In short I would agree that a system restore type thing in Linux would be extremely beneficial. It would also take a lot of the nervousness away that we newer users feel when installing, or even updating things.

For backups I have used Clonezilla and have had no problems at all. Restores of images have gone faultlessly. I find the text based interface very usable and I don't think I personally would benefit from a more polished GUI. I find a text-based backup programme focuses the mind, which is not a bad thing.

I would like to hear people's views on Microsoft's operating systems if they were free to use - like Linux.
MS have had decades to sort Windows out and have made billions selling sub-standard software with unethical/illegal ties to their own programmes.
They even dictate to me how many times I can install the software that I have paid a licence for! They dictate what the manufacturer of my computer can include with the package he wants to sell me! Ridiculous power! 

Admittedly there is much to read about with Linux and there is much your system has available to it that you won't even know about unless you come here to see what others do about problems. But that's a good reason to come here. People here are extremely helpful and hugely knowledgable. If you have a problem, ask here. Somebody here will have had the problem, and most likely solved it.

Good luck with your sytem :-)

---

### Post by onaridge on 2010-10-25
Quackers I agree. That's why I dumped Windows on my main, and
in a few months (after I've read the book and everything else I can get my hands on)will dump it off my laptop as well.

I had a Windows update totally hose my system. They've been around long enough to do a better job.

---

### Post by halj32 on 2010-10-25
I use APTonCD to backup everything Ive installed, & if I break the system & cant repair it I just reinstall it.
I like to try new things at the moment I'm using the 2.6.36-1 kernel, few problems with dual monitors but otherwise OK
You can get a free guide for Ubuntu here
[http://kubuntuguide.org/Maverick](http://kubuntuguide.org/Maverick)
[http://kubuntuguide.org/Lucid](http://kubuntuguide.org/Lucid)

---

### Post by Spice Weasel on 2010-10-25
Protip: Separate /home partition. Most important thing you could ever do during installation.

---

### Post by DitchingMS on 2010-10-25
Hi everyone

Thanks for your comments and some great suggestions. Mark, spot on and I have also installed a second Ubuntu partition as you describe (triple boot for safety!) Swagman, I research everything to death and to be fair I bought the graphics card for Windows and don't expect it to work for Linux - but I also didn't expect the official drivers to wreck the system either!

Quackers, take my word I've experienced all the dreadful experiences Windows has to offer. I have lost work, reinstalled, reconfigured, wasted weeks and a load of money because of Windows. I have installed it and configured it so many times over the years it makes me sick to imagine I migt have to do it even once more! It is from a programming perspective exactly as bad as you say and I go along with all the other negatives you highlight.  I won't suggest for one minute that every feature it has works or that it doesn't need a rewrite or massively improved stability - but it does try to remain functioning most of the time in most circumstances. Ubuntu on the other hand is supremely stable, efficient, effective, well supported, very creative and free. The downside of course is that if you do like to update your drivers regularly, or like to tweak settings, or to try new hardware or a piece of software that's been recommended - BEWARE! You may not be able to get back into the OS again. Not unless you're a guru anyway.

If you'd like to draw another parallel (although I still support the car one!) before Windows there was DOS. You could almost imagine that Ubuntu is like the classic DOS package - very good in it's own way and if you know how to use it. You could get some great games in DOS and even try your hand at programming or word processing. But then Windows came along, introduced the familiar GUI and made everything suddenly a lot more simple. Yes, it had the same back-end functionality but it made life a whole lot easier for people who didn't want to worry too much.

All I'm saying is that what I personally want is for Ubuntu to catch up in the user-friendliness it so badly lacks. It has a strong foundation, a good ethic, it is well written and I am proud to be a user of it but I stop short of recommending it to anyone bacuse I know they will not be able to handle it and I'm damn sure I won't be on the end of the phone every five minutes when they incapacitate it.

Perhaps in the next release some bright folk can really give it a much needed boost into the mainstream by making a package of tools and driver support features, backup/restore/rollbacks, Wizards?! If this were a commercial venture it would be in trouble not because of the technology but because it has no mass market appeal. What do we want out of it? Not to pay for it that's for certain! But why can't we embrace the same work ethic for our own benefits? I was one of the people who owned the technically inferior VHS, by the way. Is Ubuntu doomed to be relegated to the Betamax bin?

---

### Post by Quackers on 2010-10-25
I do accept what you are saying, in principle.
I first tried Ubuntu about 3 years ago and it didn't go well. No wireless, dodgy graphics, no sound etc etc etc. It's come a long way since then. I was very pleasantly surprised by how much stuff worked out of the box. Basically everything but the webcam and screen brightness buttons worked straight away. The webcam was fixed with a firmware/driver install, but finding the fix took a couple of weeks :-) Part of the problem for us newbies is finding out where to look for things. It is also true that having come from Windows, when you install a programme you expect a GUI for it. That is often not the case with Linux stuff. On the one hand I am amazed that all these programmes have been written at all (by volunteers) but on the other hand I personally would appreciate a GUI most of the time, or at least to be told there isn't one first :-)

I don't think Ubuntu will end up in the Betamax bin. People are trying it every day. If they can be coaxed into finding out more about Ubuntu early on, rather than just returning to Windows when something doesn't work I believe it will continue going from strength to strength.
People really are sick of Microsh... and their antics.

---

### Post by macem29 on 2010-10-25
while I haven't shared your bad experience, I can empathize....ubuntu is very good when an install
goes well, it is far from intuitive when something doesn't go well, I've said it several times: the OS
needs a real, graphical device manager, new users faced with a problem getting hardware working
are presented with no tools to fix it, some give up right away, some are told to start entering text
terminal commands and give up, some stick it out and learn enough to fix it...wonder what the
proportions are for each group? I'm guessing the latter are a minority

---

### Post by smellyman on 2010-10-26
even worse analogies in the 2nd post.  Ubuntu is like DOS?  Anyway....
 
IMO Ubuntu and many other distros are much more user friendly than Windows, just not as familiar.
 
If you were take someone who has never used either OS, they would like Ubuntu better.  Easier mantanence, much easier to find software, more stable, better security. etc.......

---

### Post by steve7777777 on 2011-01-03
To the OP - you have to realize that Linux is installed on about [1% of the desktops/laptops]("http://en.wikipedia.org/wiki/Usage_share_of_operating_systems").
With such low market penetration it is unreasonable to expect it to support all hardware. 
I'm new to Linux, and recently assembled a PC with components that were known to work. I use the PC for network storage - SAMBA share, HTPC and e-mail (Thunderbird). 

I'm not the most technically capable person, but I'm pleased to say that I got the system up and running and stable with automated backup ([Lucky Backup]("http://luckybackup.sourceforge.net")) in just a few days. There are only a few things that I still need Windows for, and over the next few months I may be able to switch to Linux based alternatives. My XP PC is mostly used to access the Linux PC via [NX]("http://www.nomachine.com/"), and the Linux/Ubuntu box is on 24x7.

From the beginning I decided against using dual boot - Ubuntu/Windows. I do use virtual machine - [VirtualBox]("http://www.virtualbox.org/") to run Vista 32bit for streaming Netflix. 

What I love most about Linux/Ubuntu, is within it's capabilities, it does exactly what I instruct it to do.

---

### Post by cazazo on 2011-03-02
I have to agree to all said! If you have in mind that Linux is a free system designed to be powerful, but certainly not simple!
Besides my webcam that it's no longer supported, everything I wanted configured I could have done! Truth being said some times with a lot of work and research!
I'm grateful to all the developers who had make that possible!
I just would like to see people more keen to face the challenges Ubuntu have ahead! Specially when come to new users! 
I don't feel like "killing" someone just because he/she has depreciated Linux! or comparing "apples" with "oranges" (windows and Linux) two different systems and philosophy! But if I had listen to some responses from some community members... such as "go back to windows, maybe Linux is not for yourself" and so on... I would not be here!
I don't think Ubuntu has let anyone down... If you want to migrate, it has a "price" to learn the new system, but in the other hand I would like to see more compassionate Linux lovers, that can be VERY PROUD of how far Ubuntu has reached, but never ignoring the challenges ahead!

---

### Post by slackthumbz on 2011-03-02
> **Spice Weasel said:**
> Protip: Separate /home partition. Most important thing you could ever do during installation.

This, a thousand times this. Also knock up a shell script to install stuff you want and remove stuff you don't want. Stick it in $HOME/bin and then if anything goes wrong you can do a quick reinstall, set up your software selection, install the updates and be on your way with a relative minimum of hassle.

Having said that all I'm going to stick Debian 6 on my netbook tonight just for gits and shiggles. I know I'm going to have to do a little jiggery pokery to set up the broadcom wireless driver but I'm prepared for that.

---

### Post by rg4w on 2011-03-02
> **DitchingMS said:**
> All I'm saying is that what I personally want is for Ubuntu to catch up in the user-friendliness it so badly lacks. It has a strong foundation, a good ethic, it is well written and I am proud to be a user of it but I stop short of recommending it to anyone bacuse I know they will not be able to handle it and I'm damn sure I won't be on the end of the phone every five minutes when they incapacitate it.
Agreed, and I think Canonical and the Ubuntu developers would probably agree with that too.  That's the goal, and thousands of people are working around the clock to see that happen.

The crux of your experience was summed up in your opening post with this:
> To give an example; last year I installed Linux ATI drivers for my  graphics card becuase I couldn't get desktop effects or play the best  looking games. I've spent a lot of money on my graphics card because I  want things to look good. Yet the **ATI drivers broke the system**.It is indeed unfortunate that ATI's driver support for Linux isn't stronger, and the community has been working hard to make up the difference but it's a tall order for volunteers.

The Certified Hardware list at Ubuntu.com can be a helpful guide in the future:
[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

It's by no means a complete list of compatible systems, but can be a helpful starting point for shopping for a system that'll deliver a strong Ubuntu experience.

I had the good fortune of meeting Jane Sibler, Canonical's CEO, at the SoCal Linux Expo this last weekend, and spoke with her for a few moments after her keynote.

One of the things that impressed me from that brief chat was the investment Canonical is making to provide resources to manufacturers to better ensure compatibility with Ubuntu.  

Most manufacturers spend most if not all of their resources testing with Microsoft Windows, and given the state of the market I can't really blame them.  So it falls on others to step in and provide the skills and tools needed for compatibility.

Canonical is apparently putting a fair amount of resources toward that, and the community at large has been doing a stellar job of writing drivers, testing, etc. to serve that goal.

But given the variety of components out there it's a very difficult task, and unfortunately that means it'll be quite a while yet before we can have confidence that Ubuntu will run flawlessly on all systems.

In the meantime, I've been lucky in that pretty much every machine I've installed Ubuntu on has worked out-of-the-box without issue.  But I know that isn't the case for many who come here needing help, and fortunately the good folks here will almost always be able to come up with a winning solution.

I hope they do for your system as well.

Best of luck with this, and thanks for your posts.  I appreciate the balanced view you're bringing to this discussion, even if it isn't a happy success story just yet.

---

### Post by jwbrase on 2011-03-02
Well, one thing that Ubuntu has that I don't think Windows does, as far as system recovery is concerned, is a LiveCD.

As far as your ATI troubles, I've had similar problems with an ATI card (Radeon 2400 HD in my case). Basically what happened is that ATI stopped releasing Linux drivers for the card between the kernel version used in Intrepid and the version used in Jaunty, so when I upgraded to Jaunty I didn't have working drivers, and that, combined with my not exactly knowing what was wrong at first and doing stupid things, broke the system. I wasn't as surprised to find that it had broken the system as you seem to be, because any driver that the GUI has to go through can break your GUI and send you back to the command line. After trying a fresh install of Jaunty on the machine in question I found that GNOME was broken, but I could get LXDE to work.

All in all, I'm less than happy with the ATI card in that machine. The first time I tried running a 3D program in Windows it bluescreened and I had to update the drivers, and it's never been stellar with OpenGL in Linux or Windows (There's one program I have that's available for both Linux and Windows, but that I use my NVidia/Ubuntu laptop for because it won't run properly under Linux or Windows on the ATI machine).

---

### Post by cottfcfan on 2011-03-03
jwbrace,
I have the exact same card, and have had problems in the past.
Try using the tutorial from here with the latest 11.2 catalyst, it works fine now.
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---


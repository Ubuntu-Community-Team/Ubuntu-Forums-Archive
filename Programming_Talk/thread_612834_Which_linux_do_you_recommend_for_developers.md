---
title: "Which linux do you recommend for developers?"
date: 2007-11-14
forum: Programming Talk
---

### Post by risknet on 2007-11-14
Hello all,

I am to develop our next projects on Linux platform using Java w/ Ruby on Rails, but I wonder which linux distro is really the best for developers.   

Our development tools will be the followings.

Java NetBeans / JBoss
Ruby on Rails / MySQL

I need to get a serious advice on this matter from your working experience on Linux.  I am a .NET developer in Windows currently.

Thank you for your help in advance.

== risknet ==

---

### Post by Kadrus on 2007-11-14
Ubuntu..Debian...I think these will do and they have the needed packages of yours...Both comes with a dozen programming languages packages..I think more..

---

### Post by LaRoza on 2007-11-14
Any one will do, but Ubuntu, if you are already familiar with it will work fine.

---

### Post by j_g on 2007-11-14
Well, there may be some other considerations as well. For example, if you're doing audio/video programming, you may want to consider a distro that has a RT kernel, and various useful programming add-ons (such as Jack) already installed by default, such as Ubuntu Studio. Of course, you can always tinker with a vanilla version of a distro to set it up the same way. But the specialized distro may already have done this for you.

I think there are some other specialized distros too, that are geared for people who are doing work in specific areas, such as distros that come setup with all sorts of security software installed, scientific distros, etc.

But what I'd avoid is distros that do not use a repository of a major distro. (Ubuntu Studio uses Ubuntu's repositories, which is a good thing). You don't want to get stuck using a distro with a limited set of programming tools, nor lacking uptodate versions of the software.

---

### Post by Sockerdrickan on 2007-11-14
Just use Ubuntu it rocks :)

---

### Post by risknet on 2007-11-14
Thank you all for your help!

Yes, I'd better stick to Ubuntu for new development projects.
If you have any other helpful advice, I will be grateful again.

Thank you.

== risknet ==

---

### Post by CptPicard on 2007-11-14
I would like to chime in that if you're going to be a Linux developer, then you should not need to ask the question in the first place. ;) You need to know your platform well enough to fit it to your needs, and all major Linux distributions are plenty flexible enough for a developer.

---

### Post by kknd on 2007-11-14
Any one.

---

### Post by zybler on 2007-11-14
Fedora 8 Live Developer Spin?

---

### Post by Compyx on 2007-11-15
I've always considered Gentoo to be a great development distro. It's source-based  so you can tinker all you want to build a system that suits your needs. It also gives you a good understanding of how a Linux-based OS is built.
And setting up distcc and ccache is a breeze on Gentoo.

The downside of Gentoo is the time it takes to install and maintain since everything is built (and rebuilt) from source, but that's where distcc and ccache really start to shine.

But like others have said, any distro will do. Just pick one with a large repository and good documentation, so Ubuntu would be fine too.

---

### Post by Balazs_noob on 2007-11-15
for your Java needs Ubuntu 7.10. will be perfect
the 1.6_03 jdk is in the repos, and installing Netbeans is also
very easy (there is  a .run file on the netbeans site),
also Compiz-fusion has no problem with swing any more 
:popcorn:
or if you decide to go with eclipse you just untar them ...
can't be easier then that :)
for your ruby needs both netbeans and eclipse has jruby plug-ins but i am not sure about ruby on rails..

good luck , Balázs

---

### Post by jespdj on 2007-11-15
> **Balazs_noob said:**
> for your ruby needs both netbeans and eclipse has jruby plug-ins but i am not sure about ruby on rails..
Rails is also in the Ubuntu repository or you can install it via gem (Ruby's package management system). The latest Netbeans (6.0 beta 2) has good Ruby/JRuby support, including support for Rails.

---

### Post by rjmdomingo2003 on 2007-11-15
Try this test: [http://www.zegeniestudios.net/ldc/index.php](http://www.zegeniestudios.net/ldc/index.php)

Wait, stop the presses! This is my 100th bean! \\:D/

---

### Post by jespdj on 2007-11-15
Have a look at [http://distrowatch.com/](http://distrowatch.com/) - there you can find comparisons between Linux distro's.

---

### Post by Slychilde on 2007-11-16
I didn't see this mentioned yet, but as a development platform stability is probably going to be a must.  I wouldn't suggest a bleeding edge distro.  Go for something more stable/thoroughly tested, like Fedora, Redhat, Ubuntu, Debian, or SuSE.  Do you want support for the OS from the company? That could be a factor, too.

---

### Post by Sockerdrickan on 2007-11-16
Nice avatar lol

---

### Post by risknet on 2007-12-04
Hello all,

OK, according to all of you, I believe that using Ubuntu will simply work for me.  But, here is another question that I like to ask.

I tried KDB and GNOME on Fedora and Ubuntu, and it looks like that KDE desktop environment is much nicer and full of features for developers.

As a developer, which desktop are you using?
I am a software engineer using C/C++, C#, Perl, Tcl, Ruby on Rails in Windows Enterprise environment right now but I like to do some work in Unix side as well.   For this reason, I am trying to use Linux at home to build my development platform.

Any advice from your working experience will be really appreciated.

Thank you again!

= risknet =

---

### Post by Nano Geek on 2007-12-04
> **risknet said:**
> Hello all,

OK, according to all of you, I believe that using Ubuntu will simply work for me. But, here is another question that I like to ask.

I tried KDB and GNOME on Fedora and Ubuntu, and it looks like that KDE desktop environment is much nicer and full of features for developers.

As a developer, which desktop are you using?
I am a software engineer using C/C++, C#, Perl, Tcl, Ruby on Rails in Windows Enterprise environment right now but I like to do some work in Unix side as well. For this reason, I am trying to use Linux at home to build my development platform.

Any advice from your working experience will be really appreciated.

Thank you again!

= risknet =

It doesn't really matter. KDE programs will run in Gnome and Gnome programs will run in KDE. Use whichever one you like best.

---

### Post by ThinkBuntu on 2007-12-04
Ubuntu. Very stable, doesn't require you to hold the OS' hand. I'd actually recommend Mac OS X, but that's not Linux.

---

### Post by jespdj on 2007-12-04
> **ThinkBuntu said:**
> I'd actually recommend Mac OS X, but that's not Linux.
Why, what makes Mac OS X so interesting for developers?

If you're a Java developer, Mac OS X is not optimal, since Java 6 is still not available for the Mac and Apple doesn't really seem to care. For me this was the #1 reason to choose a PC laptop with Linux instead of a Mac. (I'm a professional Java software developer).

The great thing about Linux for developers is that it is almost completely open source, so you can get the sources for everything (except a few proprietary drivers) and there's a very large open source community to welcome you.

---

### Post by LaRoza on 2007-12-04
> **jespdj said:**
> Why, what makes Mac OS X so interesting for developers?


I think ThinkBuntu uses Mac OS X now, and has valid reasons to do so, so the recommendation makes sense.

There are many platforms on which to work, depending on your goals, it is rare one is "better".

As for the previous query about desktop environments, I use Fluxbox, but that is just a preference. No DE is "better" for programming. I use KDE apps, GNOME apps, and others because of their features, not because they are KDE or GDE.

---

### Post by Majorix on 2007-12-04
If you will be strictly developing in Java you could also look at Sun's OS, Solaris. I have never tried it though, so use with caution.

---

### Post by CptPicard on 2007-12-04
> **Majorix said:**
> If you will be strictly developing in Java you could also look at Sun's OS, Solaris. I have never tried it though, so use with caution.

Don't buy into the marketing hype... they may have stuff like "Java desktop environment" and such, but Solaris the OS really has nothing "special" to do with Java. It's a pretty cool heavy-duty Unix though, and you can slap a lot of the Gnu tools on it to make your coding experience pretty similar to being on Linux.

And of course things like Python et al work just the same, in particular because of those said Gnu tools and libs.

Then again, as Linux has got better and better and been taking market share away from Solaris, there is less and less reason to actually choose Solaris over some Linux.

---

### Post by jespdj on 2007-12-05
> **LaRoza said:**
> I think ThinkBuntu uses Mac OS X now, and has valid reasons to do so, so the recommendation makes sense.
Probably it makes sense for him/her, but without saying why (s)he would recomment OS X, his/her comment is not very useful. And I'd like to know what his/her reasons are to prefer OS X.

---

### Post by risknet on 2007-12-05
Thank you again for your advice on my question.

I finally came back to Ubuntu w/KDE installed after spending few days with other Linux distribution packages - Mandriva 2008, Fedora 8, OpenSuse.

I am now setting all of my development tools on Ubuntu...

Thank you again!

== risknet ==

---

### Post by ThinkBuntu on 2007-12-05
I recommend OSX because it's very stable, very fast, and well-supported. You'll spend very little if any time fussing over your OS, whereas with most Linux OS you need to fuss a bit. Ubuntu is an exception, although I've experienced stability issues with the GNOME desktop. If any development environment for the Mac seems outdated, there almost certainly is the version you're looking for provided by MacPorts.

That being said, I believe that if I didn't need to do graphic design, I'd probably be very comfortable developing in Linux. If Apple begins pushing its users to 10.5 which is, as of this post, a steaming chunk of ______, I will consider a switch and use my Mac with 10.4 for graphic purposes, since Photoshop CS3 should be viable for the next 3-4 years.

---

### Post by Vadi on 2007-12-05
I'll echo on the well-supported part.

Don't get me wrong, the forums, irc are great. But sometimes there just isn't someone who knows the answer nearby. That's when you start wondering why to dell ubuntu customers get a $50 a year support plan while you have to pay a min $250...

---

### Post by pmasiar on 2007-12-06
I do not want to start MacOSX vs Linux flamewars, but technically speaking, MacOSX is **not** Linux. It's kernel is not Linux, but BSD - different Unix clone. BSD has different license, different kind of "free" than GPLed Linux, which allows to distribute changed binaries without sources. GPLed packages, like GNU tools, can run there too (same Unix POSIX interface), or can be modified (they came with sources).

As a result, many developers who want nice unix-like system with GNU tools use OSX, but people who want to hack on GNU/Linux, need Linux, not BSD.

Because of GPL, Linux-based software vendors have to be "honest" and cannot keep changes private (as BSD allows), so for them it makes more sense to invest to Linux than to BSD. So Linux development is faster and more versatile, Linux runs on anything from series z IBM mainframes to supercomputers to desktops to handhelds and mobile phones. Apple prefers BSD, because Apple is also hardware manufacturer. BSD allows Apple to integrate software and hardware better than Linux can: Linux is supposed to run on any random PC box with random graphic, sound etc card.

So yes, MacOSX is nice, but it will not run on that old PC you have in the basement whan you want to install edubuntu to learn some networking. Linux is more universal, and it will remain so, even after Apple decides that desktops are not profitable and switches to music players. :-)

---

### Post by jespdj on 2007-12-06
> **pmasiar said:**
> I do not want to start MacOSX vs Linux flamewars, but technically speaking, MacOSX is **not** Linux. It's kernel is not Linux, but BSD - different Unix clone.
Nobody said that Mac OS X is Linux. In fact, ThinkBuntu said in the first post where he mentioned it that it's not Linux.

But you're right, ofcourse. Mac OS X is not free (as in speech) and open, which is ofcourse one of the nice things of Linux.

---


---
title: "Good developer-geared distro?"
date: 2007-08-29
forum: Other OS Talk
---

### Post by wrycatcher on 2007-08-29
I’m a current Zenwalk user (ex-Ubuntu user) and mostly happy with Zenwalk.  I have rarely found anything beyond my ability, even compiling packages from source (probably not the kernel, though). For me, the most desired features of a distro/OS are:

1) a lean, clean distro (minimal, “essential” apps only)
2) development oriented (compilers, debuggers, editor/IDE, etc)
3) function over form (i.e. fast and reliable more important than looks)
4) upgrade-friendly for kernel, components, and applications
5) optimization options for my hardware (enhances numbers 1 through 3 above)

I'm also toying with trying Wolvix and Foresight.  Wolvix for my development system and Foresight maybe for my wife's laptop (currently running Ubuntu Edgy).  There has to be an intuitive, stable distro out there that will manage laptop power better than Ubuntu.

Should I consider Gentoo for my development (desktop) system?  My short list is Zenwalk, Wolvix, or maybe Foresight.

---

### Post by fwojciec on 2007-08-29
My suggestion would be either Slackware, Arch or Gentoo.  Personally I use Arch.

---

### Post by Rumor on 2007-08-29
+1 for Arch Linux

You install the apps you want / need. The community has a strong group of developers and contributors. It is light-weight, i686 optimized and upgrades like a dream.

---

### Post by finferflu on 2007-08-29
Go Arch go! :D

---

### Post by igknighted on 2007-08-29
+1 for Gentoo... The main difference I see with the two is with Arch you spend time futzing around with config files while in Gentoo you spend time compiling.  Personally I prefer Gentoo, but both are very good.

---

### Post by kknd on 2007-08-29
+1 to Arch!

---

### Post by daveshields on 2007-08-30
+1 to Ubuntu. It is based on Debian and so has support for all the development tools you could want.

More importantly, with Ubuntu you get the Ubuntu community:
 

1) Things you develop on Ubuntu will be accessible to any Ubuntu user. If you pick another distro, then you'll have to verify that what works on it also works with Ubuntu.

2) The Ubuntu community will be at hand to answer your questions.

3) The Ubuntu community has reached critical mass. What you need will be supported for the indefinite future.

4) The community is the best source of prospective users to test your new ideas and code. By showing you are part of that community you will be in a better position to attract those new users. The most valuable input to any developer is user feedback, particularly in the form of bug reports. You're more likely to get that input by being part  of Ubuntu.

5) If your goal is to make Linux better the most effective path to that end is, in my view, to make Ubuntu better. To associate yourself with another distro/community is to deny Ubuntu the immediate benefit of your work.

6) Gentoo, while interesting technically and  because of the high quality of the documentation, has a fundamental flaw. It assumes it is best to build everything from scratch for your machine. Yes, that can give good performance, but currrent hardware is more than adequate for development. The extra cycles you get with Gentoo aren't worth the effort.

---

### Post by wrycatcher on 2007-08-30
Thanks Dave, your position regarding Ubuntu is quite zealous.  Yes, Ubuntu it great and yes I like it.  It serves the needs of many users quite well.  I also like what many of the other distros offer and do not want to make Ubuntu into some kind of uber-Linux.  No ubiquitous distro is going to do and be everything that everyone wants.  And I really don't want to see a Linux world where there is one dominant distro that tends to make all the rules and set all the standards.  Too much like what we face now with Windoze dominance.  Part of what makes Linux so great is innovation and choices and I think much of that gets lost when everyone jumps onboard the same bus.

---

### Post by igknighted on 2007-08-30
> **daveshields said:**
> 
4) The community is the best source of prospective users to test your new ideas and code. By showing you are part of that community you will be in a better position to attract those new users. The most valuable input to any developer is user feedback, particularly in the form of bug reports. You're more likely to get that input by being part  of Ubuntu.

5) If your goal is to make Linux better the most effective path to that end is, in my view, to make Ubuntu better. To associate yourself with another distro/community is to deny Ubuntu the immediate benefit of your work.

6) Gentoo, while interesting technically and  because of the high quality of the documentation, has a fundamental flaw. It assumes it is best to build everything from scratch for your machine. Yes, that can give good performance, but currrent hardware is more than adequate for development. The extra cycles you get with Gentoo aren't worth the effort.

4) If you develop software on Gentoo, Arch, Zenwalk or any other distro, it will compile on Ubuntu.  Besides, creating it so it runs on one distro, and having a community that will test it on Ubuntu as well would give you twice as many distros that it runs for sure on... seems like a good deal for me.  (and yes, the different GCC implementations do lead to differences when compiling at times.)

5) This is silly.  Do you try to clean a river by filtering it way downstream?  Of course not!  If you want to code for Linux, contribute way upstream.  Either go to Debian (or some other "mother distro"), or better yet join a project that distributes code for all distros to use.  Ubuntu is a version of linux, and this year it happens to be the most popular.  But it is still not even the *majority* of linux users.  Ubuntu != linux, don't pretend other distros are any less important.  If I had a dollar for every time I had to remind someone of that around here...

6) The reason to run Gentoo as a developer isn't just for the performance boost.  It is to get an understanding of the operating system you are developing for.  Compile some from source, configure a kernel (@ the OP: it's really easy and no matter what you can't break your system, so give it a try), write some config files... do it all.  It could lead to you understanding the OS and how your software fits in better and lead to you coding better software.

---

### Post by wrycatcher on 2007-08-30
Arch Linux, eh?   And Gentoo got an honorable mention, too.  I will have to try some LiveCD versions and check these out.  Wolvix, too.  I guess no one has used any of the Conary-based distros?  What about rPath or Foresight or Oz??  Anyone tried those and have a brief summary of their experience of each's strengths and weaknesses?

Thanks all!  Ubuntu has a phenomenal online community, that I have never doubted.  I'm happy Ubuntu came along and made Linux easier than I had found with earlier Red Hat or Debian distros.   However, now that I have become quite familiar with Ubuntu (and moreover, Linux), I now must find the distro which more closely matches my usage and tastes.  I would never dream of asking Ubuntu to change to suit my particular needs (very development-centered and highly optimized) because then Ubuntu would no longer be the great Linux entry distro that it is!

---

### Post by wrycatcher on 2007-08-30
I totally agree, especially with your reply to #6!  In fact, if I gain a better understanding of Linux, the kernel, modules, how things work in general, won't this perhaps lead to my perhaps contributing in a more meaningful way to the Linux community (I am a developer, after all)?  That seems like a compelling argument in favor of Gentoo, and other tech-savvy distros.

---

### Post by fwojciec on 2007-08-30
To me Arch is a perfect *user* distro, it gives me the latest and greatest of the linux world, it puts me completely in charge of my system so that I can set it up exactly how I want it, it makes the maintenance of my system banal, because of great tools I have at my disposal and the KISS philosophy of the distro in general.  So I would think, at the very least, Arch would be a great choice for your wife's laptop, if you're willing to take time to set it up well, that is.

Arch would also make a great distro for a developer, I imagine, especially if he/she wanted to write original programs and share them with a community of users.  This could be said about any distro, I guess, but there are things that make Arch somewhat unique in that regard, I believe.  AUR in Arch makes it easy to distribute your programs to those who want to use them, and I imagine you'd find that Arch users tend to be unusually willing to try out completely new programs (they are the kind of people who want to be as close to the bleeding edge of linux development as possible, after all) and are, furthermore, generally sufficiently competent to contribute to testing in a meaningful way.  Visit Arch forums and browse through the "Community Contributions" section to see what I mean (you might check out the "General Programming Forum" as well, while you're at it).  So, as a developer, using Arch would give you a wonderful community to share your ideas with, as well as a bleeding edge stable, pretty much fully customizable and easily maintained system to work on.

I agree that Gentoo would make a wonderful developer distro, but I also think that everything you can do in Gentoo you can do in Arch and vice versa.  Gentoo, I would say, makes it more natural for you to fine-tune your system in the finest of fine details (USE flags).  Arch sacrifices that emphasis (not the ability!) for the sake of keeping things KISS for a user, while still making fine-tuning possible if necessary.  Recompiling programs with custom patches or configurations is made very easy in Arch because of ABS, makepkg and other tools that are available.  In my previous post I've also mentioned Slackware, and I stand by that suggestion, because I imagine that a plain vanilla, super-stable system that's transparent and easy to maintain would also make a great environment for developing software.

In the end all the distros mentioned in this thread would serve your purposes well in one way or another.  So it's really a matter of what specific strengths of each distro are most appropriate to your situation and most appealing to your linux sensibilities ;)

---

### Post by ThinkBuntu on 2007-08-30
Zenwalk comes with a great development configuration, from my experience...I know this is narrow, but it's the only distro I've used that out of the box supports perfect code hightlighting and auto-indentation for CSS, HTML, and even CSS nested in HTML <head> tags.

---

### Post by wrycatcher on 2007-08-31
Good to know.  I hadn't played with that part yet.  I was doing Java dev within Eclipse IDE and hadn't really done much HTML editing (I hear Bluefish is very nice, though).

---

### Post by wrycatcher on 2007-08-31
Thanks for the quick summaries of your experiences with those distros.   Right now, I think that Wolven *might* be a good choice for my wife's laptop (needs to be very simplistic and not require much technical knowledge).   I've already begun playing with Arch Linux and so far I like it.  It's quite intuitive and straightforward, but I'm still in the early stages of evaluating it.

---

### Post by fistfullofroses on 2007-09-03
Slackware is the oldest actively developed distribution out there. Among purists it is incredibly popular. Zenwalk was based upon Slackware, as were many other distributions (slax, vector, zenwalk, back|track, and many many more). It is a trusted distribution. It is the Unix of Linux distributions. If you want to do development, you want performance, you want reliability, I *highly* recommand Slackware. Also, if you are a minimalist, Slackware has a very simple menu driven, ncurses installer. It will allow you to select/deselect any package or package group that you wish. Anyway, have fun.

---

### Post by Fbot1 on 2007-09-03
There's opendevelop but meh. I think you would be better off just selecting the packages yourself with your favorite distro.

---


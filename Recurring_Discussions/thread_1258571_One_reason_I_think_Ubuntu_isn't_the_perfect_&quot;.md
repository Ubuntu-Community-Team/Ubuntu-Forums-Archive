---
title: "One reason I think Ubuntu isn't the perfect &quot;Windows converter&quot; distro"
date: 2009-09-05
forum: Recurring Discussions
---

### Post by Pogeymanz on 2009-09-05
I'm not saying that Ubuntu should change or that Ubuntu is wrong, etc. I'm only saying that the ultimate newbie distro should be different.

I think the newbie distro should be rolling release! "WHAT?! THINK OF ALL THE INSTABILITY"

You could still have rolling release without having bleeding edge versions of software.

The reason I say the ultimate Linux-Newbie distro needs to be rolling release is because one of Linux's strongest points above Windows and MacOS is the package management, but it seems wasted by only having security updates. I think Windows converts would be very impressed to see that all of their software updates could be centralized instead of having to update each package separately.

Discuss.

---

### Post by longtom on 2009-09-05
> **Pogeymanz said:**
> I'm not saying that Ubuntu should change or that Ubuntu is wrong, etc. I'm only saying that the ultimate newbie distro should be different.

I think the newbie distro should be rolling release! "WHAT?! THINK OF ALL THE INSTABILITY"

You could still have rolling release without having bleeding edge versions of software.

The reason I say the ultimate Linux-Newbie distro needs to be rolling release is because one of Linux's strongest points above Windows and MacOS is the package management, but it seems wasted by only having security updates. I think Windows converts would be very impressed to see that all of their software updates could be centralized instead of having to update each package separately.

Discuss.

This  ...  is an interesting thought.  To put it differently (as I understand it):

Doesn't matter what version Ubuntu you run, if there is a new, tested version of an application available make it part of the repositories.

ie if somebody runs Ubuntu 8.04 LTS, he still can get Open Office 3.1 since it is the latest, stable release by using the "normal" synaptic process.

I must admit, from the beginning I didn't like having to use old OO and Gimp software on Hardy.  In the meantime I researched the hoops to jump through and did so and all is well.  However, it would have been nice to have it in the repos.

On the other hand I am not sure how much more of an administrative task it would be to update the repos of all supported versions of Ubuntu every time something new or more up-to-date appears.
But doing this every 6 month (with every new distro) might be an idea?

---

### Post by Pogeymanz on 2009-09-05
Well, like I said: Ubuntu has its way of doing things and it isn't going to change.

What I would propose is to not have a 6-month release cycle. You don't need to when you have package management like apt. Just test new versions until they are stable, then update the repos with it and then the user's synaptic will upgrade it. Or the user could even specify a package to not upgrade.

I just think that package management is a unique and strong point for Linux over other OS's. If Linux tries to copy Windows, it will never be as good as Windows, which is why I think it should focus on being different in the most useful way (as opposed to being different just to be different).

And there are rolling release distros, but none are user friendly like Ubuntu. There is Arch, Sidux, Gentoo, Crux (I think), etc, which are all advanced user distros. Then there is Debian which is too stable (read: outdated packages) for desktop use. We need something in between Debian Testing and Debian Unstable that is friendly like Ubuntu.

---

### Post by RabbitWho on 2009-09-05
Well the repos works offline.. even though it's just a link to a download file, why can't it be something that's always changing to include the latest stable releases? 

To be honest until I read that I thought that's what it was doing. 

Updating every 6 months is a lot of hassle.

---

### Post by Tibuda on 2009-09-05
What about if you create a LiveCD with stuff pre-installed based on ArchLinux. Like [Chakra]("http://chakra-project.org/").

---

### Post by longtom on 2009-09-05
> **RabbitWho said:**
> why can't it be something that's always changing to include the latest stable releases? 

To be honest until I read that I thought that's what it was doing. 

Updating every 6 months is a lot of hassle.

It is.  There are other workarounds so, like adding 3rd party repos to your source file, install the keys....

But that is also, imo, unnecessary hassles.  

I would like to hear a valid reason why this (updating of the repos) is not and can not be done.

---

### Post by snowpine on 2009-09-05
Not going to happen because of Ubuntu's development process. Ubuntu piggybacks on top of Debian and would not exist without it. The Ubuntu devs take a "snapshot" of the (rolling) Debian Unstable repos, then spend six months "tweaking" it to make the next Ubuntu release. How would it be possible to make a rolling release distro based on another rolling release distro? You would have to constantly test and tweak every single update that comes through; imagine the manpower involved, and to what end? You might argue that "rolling Ubuntu" could simply mirror the Debian repos (sid or testing), but then it truly becomes what it's sometimes (falsely?) accused of being: "Debian with a brown theme."

Debian Testing is pretty much the perfect "non-bleeding-edge rolling release apt-based distro," and sidux is a fantastic option if you want to live on the bleeding edge. I think the "rolling release Ubuntu" described here would be a pointless duplication of something that already exists.

I also don't understand the obsession with having the newest versions of apps the moment they are released. Do websites suddenly stop working with Firefox 3.0 once 3.5 is released? With Ubuntu, you get a stable system and never have to wait more than six months for the newest apps; that seems like a good compromise to me.

ps I personally prefer to use rolling release distros (I use Arch, Debian Testing, and SliTaz cooking most of the time), so I do understand the benefits, however, I don't think Ubuntu necessarily needs to become one of them.

---

### Post by szadek_ on 2009-09-05
> **danielrmt said:**
> What about if you create a LiveCD with stuff pre-installed based on ArchLinux. Like [Chakra]("http://chakra-project.org/").

This is the kind of stupid post .And what about if you would recommend enabling repositories on synaptic with the latest stuff and upgrade that way ?? 

We all have the freedom to talk about what we use , but this kind of post makes me sick ... 


Well , i always run the latest stuff on my ubuntu installation , just copy and paste repositories onto synaptic and upgraded always with no problems , but it was me ... maybe someone else could encounter problems with that .


And .. ubuntu is the very best distro to begin with ... and to stay with when you are experienced and dont want to have hard work doing things .Its my opinion =) .

---

### Post by Tibuda on 2009-09-05
> **szadek_ said:**
> This is the kind of stupid post .And what about if you would recommend enabling repositories on synaptic with the latest stuff and upgrade that way ?? 

We all have the freedom to talk about what we use , but this kind of post makes me sick ... 


Well , i always run the latest stuff on my ubuntu installation , just copy and paste repositories onto synaptic and upgraded always with no problems , but it was me ... maybe someone else could encounter problems with that .


And .. ubuntu is the very best distro to begin with ... and to stay with when you are experienced and dont want to have hard work doing things .Its my opinion =) .

Why is my post stupid and makes you feel sick? The OP asked for an easy-to-install-and-use rolling-release distro. Chakra fits this very well. It got a GUI installer, a GUI package manager, automatic hardware detection, and is rolling-release.

A note: I don't use Chakra or ArchLinux.

---

### Post by gn2 on 2009-09-05
> **Pogeymanz said:**
> I'm not saying that Ubuntu should change or that Ubuntu is wrong, etc. I'm only saying that the ultimate newbie distro should be different.

I think the newbie distro should be rolling release! "WHAT?! THINK OF ALL THE INSTABILITY"

You could still have rolling release without having bleeding edge versions of software.

The reason I say the ultimate Linux-Newbie distro needs to be rolling release is because one of Linux's strongest points above Windows and MacOS is the package management, but it seems wasted by only having security updates. I think Windows converts would be very impressed to see that all of their software updates could be centralized instead of having to update each package separately.

Discuss.

I think that adopting your suggestion would have absolutely no effect whatsoever on new users of Ubuntu.
Why do I say this?
Because you can change to the next release at the click of a button.
How difficult is that?
"Rolling release" is nothing special, it's just one of the things Arch users like to drone on about incessantly.
How is the Emperor turned out today?

---

### Post by snowpine on 2009-09-05
Wow, that didn't take long... :)

---

### Post by longtom on 2009-09-05
> **gn2 said:**
> 
Because you can change to the next release at the click of a button.
How difficult is that?

No very - if it works.  Maybe have a look around this forum and see how many times it doesn't.

To wonder every 6 months and hope your upgrade of your entire OS goes well and spend a lot of time and effort to fix things that didn't go well opposed to just updating programs which have more functionality  than an older version.

I can see the merit of the OPs suggestion.  

One can, however, get the impression you have a problem with Arch users and therefore don't like the "rolling release" idea.

However - it wasn't "bleeding edge" the Op was talking about.

---

### Post by &#32 Greg on 2009-09-05
Take a look at PCLinuxOS- rolling release, and very far from bleeding edge. They still have Emacs 21.4 in the repos :D

---

### Post by Pogeymanz on 2009-09-05
> **gn2 said:**
> 
"Rolling release" is nothing special, it's just one of the things Arch users like to drone on about incessantly.
How is the Emperor turned out today?

Come on, man. Why the hell did you have to go there? Please stop droning on about Arch users incessantly, it's annoying. Not to mention, you're being very insulting when I didn't do anything to you. Good thing you can hide behind your keyboard and don't have to be responsible or respectful.

<ontopic>
I personally like having the newest stuff. And I did when I used Windows too. I didn't like the fact that a new version of something might come out and I would miss out on it. (*HINT: I went to Arch because I like new stuff. I don't like new stuff because I went to Arch*)

I've gotten a few of my friends to try Ubuntu, but they basically see it as an OS that is probably just as good and easy as Windows, but has less support, so what's the point? They are also competent computer users, so they don't really get viruses on Windows. The only selling point at that point is freedom and package management. Well, they don't care about freedom, so...

I like the idea of Chakra, but I don't know too much about it. It also is probably too bleeding edge for a total newbie. Things are bound to break once in a while. Also, how does the GUI package manager handle .pacnew files and stuff?

---

### Post by Pogeymanz on 2009-09-05
> **szadek_ said:**
> 
Well , i always run the latest stuff on my ubuntu installation , just copy and paste repositories onto synaptic and upgraded always with no problems , but it was me ... maybe someone else could encounter problems with that .

I do the same thing when I use Ubuntu. But a newbie might not really like doing that. Plus, it isn't an official Ubuntu repository, so it could break or have a security issue, or whatever.

EDIT: Sorry, double post.

---

### Post by aysiu on 2009-09-05
> **Pogeymanz said:**
> 
And there are rolling release distros, but none are user friendly like Ubuntu. There is Arch, Sidux, Gentoo, Crux (I think), etc, which are all advanced user distros. Then there is Debian which is too stable (read: outdated packages) for desktop use. We need something in between Debian Testing and Debian Unstable that is friendly like Ubuntu. PCLinuxOS isn't user-friendly?

> **snowpine said:**
> 
I also don't understand the obsession with having the newest versions of apps the moment they are released. Do websites suddenly stop working with Firefox 3.0 once 3.5 is released? With Ubuntu, you get a stable system and never have to wait more than six months for the newest apps; that seems like a good compromise to me. I agree. Most of the *current* crop of Ubuntu users are ex-Windows power users, so they have a tendency to want the absolute latest versions of software the very second those versions become available (or even sooner).

Most Windows users don't really care about the latest software. They just want to get work (or play) done.

---

### Post by gn2 on 2009-09-05
> **longtom said:**
> No very - if it works.  Maybe have a look around this forum and see how many times it doesn't.

[Maybe have a look around the Arch forums to see how smoothly it's updates work]("http://www.google.co.uk/search?q=update+problem+site%3Abbs.archlinux.org&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enGB284GB284")?

> **longtom said:**
> One can, however, get the impression you have a problem with Arch users and therefore don't like the "rolling release" idea.

I have no problem with Arch's update method or it's users, but I'm fed up with Arch evangelists spouting their guff in here.

Take this thread, one reason why Ubuntu isn't isn't the perfect "Windows converter" distro, and it's straight into a diatribe about how Arch's update method is so superior.

If the Arch way is so good, why isn't there a single major computer supplier shipping it's hardware with Arch installed?

---

### Post by &#32 Greg on 2009-09-05
> **gn2 said:**
> [Maybe have a look around the Arch forums to see how smoothly it's updates work]("http://www.google.co.uk/search?q=update+problem+site%3Abbs.archlinux.org&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enGB284GB284")?



I have no problem with Arch's update method or it's users, but I'm fed up with Arch evangelists spouting their guff in here.

You can flip that for Ubuntu too. 'I thought Ubuntu was supposed to be the newbie friendly distro, but look around the forums at all the people who have audio, video, package, or whatever trouble'. Fact is, chances are that if you're posting at a Linux support forum, you have some sort of trouble. It's a bad way of arguing the point.

That said, I don't think that Chakra is a good idea for a *lone* Linux newbie.

---

### Post by gn2 on 2009-09-05
Ubuntu has millions of users of which a small minority post here looking for help, Ubuntu is far from perfect, but the release model that currently exists is not in need of major upheaval.

Some Arch users persistently bang on about it, but there is simply no need to update Ubuntu every six months when there's the LTS option.

---

### Post by aysiu on 2009-09-05
> **  Greg said:**
> You can flip that for Ubuntu too. 'I thought Ubuntu was supposed to be the newbie friendly distro, but look around the forums at all the people who have audio, video, package, or whatever trouble'. Fact is, chances are that if you're posting at a Linux support forum, you have some sort of trouble. It's a bad way of arguing the point. Ubuntu is supposed to be a Linux technical support forum, though, so it makes sense for those posts to be here. It isn't supposed to be an Arch Linux user's evangelistic playground.

---

### Post by lykwydchykyn on 2009-09-05
> **Pogeymanz said:**
> 
You could still have rolling release without having bleeding edge versions of software.

The reason I say the ultimate Linux-Newbie distro needs to be rolling release is because one of Linux's strongest points above Windows and MacOS is the package management, but it seems wasted by only having security updates. I think Windows converts would be very impressed to see that all of their software updates could be centralized instead of having to update each package separately.

Discuss.

I understand the frustration with the big freeze model that drives people to rolling release distros.  But to say that all, or even the majority, of Windows users want the latest software is a generalization I can't agree with.  Most Windows users are accustomed to buying a software title and using it until (a) their computer dies and they have to get all new software or (b) they start getting files that can't be opened by their old software.  Seriously, I know people still using Office '97 or Word 2000.  And let's not forget that any reliable statistics point to Windows XP as the most popular desktop OS.  

So I really find it hard to believe that being six to twelve months behind on any given software title is really holding back a distro for these sorts of users. (if anything, six  months is too fast a turnaround for these folks -- give'em LTS).

It *is* an annoyance for power users, but after a few years of trying different release models I finally settled on Ubuntu because it seems like a nice balance.  When I used Debian testing, things were always breaking, and my work was always being delayed by having to sort out some issue with the latest X server upgrade.  Then I used Mepis (based on Debian stable) and got tired of the prospect of waiting years for the latest cool features I was seeing in Ubuntu or Suse.

I settled on Ubuntu because I know that I have the option of keeping stuff that is working good enough at the same level for six months, and I can be pretty sure that anything new and awesome will be backported to the current release if I really must have it.

Nobody has it perfect, I think.  That's why it's good to have options.

---

### Post by &#32 Greg on 2009-09-05
> **aysiu said:**
> Ubuntu is supposed to be a Linux technical support forum, though, so it makes sense for those posts to be here. It isn't supposed to be an Arch Linux user's evangelistic playground.

So is the Arch forums. My point here is that looking at a support forum and going 'Oh look at all the people with problems' is a terrible way to judge a piece of software. And the whole Arch bashing thing in this thread is rather besides the point, because the whole thing here is the OP wants a user friendly rolling release distro- NOT Arch.

---

### Post by aysiu on 2009-09-05
> **&#32 Greg said:**
> So is the Arch forums. My point here is that looking at a support forum and going 'Oh look at all the people with problems' is a terrible way to judge a piece of software. And the whole Arch bashing thing in this thread is rather besides the point, because the whole thing here is the OP wants a user friendly rolling release distro- NOT Arch.
I guess we're in full agreement then. [list=1][*]Support posts are expected on a support forum.[*]Arch Linux is not intended to be a "Windows converter" distro, so it has no relevance in this thread.[*]Ubuntu support posts should be on the Ubuntu Forums. Arch evangelism or bashing should not be.[/list]

Must have been a miscommunication somehow. Maybe I misread your original post.

---

### Post by aysiu on 2009-09-05
> **&#32 Greg said:**
> So is the Arch forums. My point here is that looking at a support forum and going 'Oh look at all the people with problems' is a terrible way to judge a piece of software. And the whole Arch bashing thing in this thread is rather besides the point, because the whole thing here is the OP wants a user friendly rolling release distro- NOT Arch.
I guess we're in full agreement then. [list=1][*]Support posts are expected on a support forum.[*]Arch Linux is not intended to be a "Windows converter" distro, so it has no relevance in this thread.[*]Ubuntu support posts should be on the Ubuntu Forums. Arch evangelism or bashing should not be.[/list]

Must have been a miscommunication somehow. Maybe I misread your original post.

---

### Post by Pogeymanz on 2009-09-05
> **gn2 said:**
> 
Take this thread, one reason why Ubuntu isn't isn't the perfect "Windows converter" distro, and it's straight into a diatribe about how Arch's update method is so superior.

Arch did not invent the rolling release. My mention of rolling release had NOTHING to do with Arch. And the person who mentioned Arch first was entirely relevant in pointing out that Chakra might be a good answer to my original post.

You, sir, are completely out of line and I don't appreciate the total derailing of my thread. Rolling release != Arch and believe it or not, Arch can be talked about on the Ubuntu forums, especially in the Cafe.

---

### Post by madjr on 2009-09-05
> **Pogeymanz said:**
> I'm not saying that Ubuntu should change or that Ubuntu is wrong, etc. I'm only saying that the ultimate newbie distro should be different.

I think the newbie distro should be rolling release! "WHAT?! THINK OF ALL THE INSTABILITY"

You could still have rolling release without having bleeding edge versions of software.

The reason I say the ultimate Linux-Newbie distro needs to be rolling release is because one of Linux's strongest points above Windows and MacOS is the package management, but it seems wasted by only having security updates. I think Windows converts would be very impressed to see that all of their software updates could be centralized instead of having to update each package separately.

Discuss.

instead of a rolling release it would be much better to **go from 6 months to 1 year releases** or use the **LTS + service packs**

why?

a good example is [getdeb.net]("http://www.getdeb.net") :

[blender]("http://www.getdeb.net/app/Blender") packages

Latest versions:
Ubuntu **Jaunty** 32 bits - **2.49b**  <---new, but not for hardy users

Ubuntu Intrepid 32 bits - 2.48a

Ubuntu **Hardy** 32 bits - **2.48** <------stuck with old version (needs to upgrade early full system just for 1 software..)



HARDY LTS is not dead but hardly anyone supports/packages new software releases for it. Simply because is hard to maintain 2 or 3 versions just 6 months after

yearly releases (with about 8 alphas and 2 betas should do the trick). Or do like Mac/Windows = LTS (2 - 3 year releases) + service packs

am sure that when Chrome OS is out it won't be a 6 month thing and still be pretty successful with lots of software for it

---

### Post by gn2 on 2009-09-05
> **Pogeymanz said:**
> Arch did not invent the rolling release. My mention of rolling release had NOTHING to do with Arch. And the person who mentioned Arch first was entirely relevant in pointing out that Chakra might be a good answer to my original post.

You, sir, are completely out of line and I don't appreciate the total derailing of my thread. Rolling release != Arch and believe it or not, Arch can be talked about on the Ubuntu forums, especially in the Cafe.

Your original post in summary:
*Know what, to get more converts to Ubuntu it should switch to a rolling release, signed, a proud Arch user.*

And you wonder why I'm p'd off with Arch evangelism?

My points still stand, there would be absolutely no benefit adopting a rolling release.
If you believe that any of my posts are out of line, report them.

---

### Post by donato roque on 2009-09-05
I've used openSuse, Fedora and eventually Ubuntu and I prefer Ubuntu's compromises.  Because these talk about a rolling release and a unified package management is about compromising pros and cons.  Ubuntu takes the majority of users' needs into account and they go for the simplest solution.  

Look, if you're concerned about the majority of windows converts, the profile is they just want something that works for their everyday computing.  Rolling release just adds to the complexity for those "windows converts" and makes it harder to sell them Linux.  Simple works, complexity not.  Besides if your level of expertise allows you to explore the realm of the bleeding edge then good luck and go explore.  But don't complain that it's too hard, and you want to make it easier.

---

### Post by woedend on 2009-09-05
Wow.  Why does this Arch/Ubuntu debate come up so often?  They are both great distros, and I switch between them regularly.  Everyone likes to think they use the best OS and will give reasons as to what makes theirs better.  Preaching that arch linux is great in nonrelevant threads can be annoying, but badmouthing one another on a personal basis is even more annoying.  I am in many ways saddened by what this forum has become since I joined(notice the join date).  What I saw in the OP was a good idea that's been brought up MANY times, even before the big upswing in arch users(ie - people who outgrew ubuntu).  It was even intially proposed back in the dev stages(I've been around a while, since warty warthog for ubuntu  at least).  It was called grumpy groundhog but it was never really implemented, just an idea.  Anyways, if you "want" rolling release, just stick with Ubuntu development releases.  Linux is not windows.  Windows gives you one base for years.  Sure service packs are released, but lets take for example windows XP..released..what 2001?  Many people still use this.  The libraries are for the *most* part static, so upgrading is never an issue.  By nature linux based OS's are so modular(perhaps too modular) that everything is built against the newest libraries.   Which means that in many cases you can't just upgrade an individual program by itself because it'd need newer dependencies, which in turn may break another program unless it in turn was updated.  PPA's are a viable solution but even they can cause breakage.  My solution?  Well, I think Ubuntu should keep it's release cycle as is, but perhaps we can unite the PPA's into a single repo.  That is, the PPAs are still kept separate and updated by its maintainer(s), but have a repo that goes in each night and pulls all packages(non-conflicting of course) from all relevant PPAs and have it as an option to enable and use in synaptic.  Ubuntu keeps doing their 6 month release cycle and static releases...and for those who want the latest and greatest...you'll have your option as well.

---

### Post by Cenotaph on 2009-09-05
I think that the core apps and libs that make the OS, the ones supported by Canonical (main restricted) should stay as they are as they are what makes a version of ubuntu.

however, I don't see any reason why universe and multiverse couldn't have a more rolling release approach. Of course, there's always getdeb for latest applications and the apps that are supported by Canonical still wouldnt get the latest (Firefox, Pidgin, etc.) but for games and other apps it would rock.

---

### Post by Pogeymanz on 2009-09-06
> **gn2 said:**
> Your original post in summary:
*Know what, to get more converts to Ubuntu it should switch to a rolling release, signed, a proud Arch user.*

I did not say that at all. I have pointed out several times that I'm not saying Ubuntu should change. I'm saying that another distro should exist. And I only added that signature after I saw a really nasty anti-Arch thread that really made me see some UF members in a different light.

> **gn2 said:**
> 
And you wonder why I'm p'd off with Arch evangelism?

I don't care how you feel. There was no Arch evangelism in my post. Period.

> **gn2 said:**
> 
My points still stand, there would be absolutely no benefit adopting a rolling release.

Fine. And I do appreciate all the counter points to my idea. So, please don't think that I am just upset that you disagree with me.


> **gn2 said:**
> 
If you believe that any of my posts are out of line, report them.
Well, don't be surprised then...

---

### Post by gn2 on 2009-09-06
> **Pogeymanz said:**
> ~ I saw a really nasty anti-Arch thread ~

Which thread was that?

---

### Post by longtom on 2009-09-07
It is a real pity that one user, gn2, derailed this thread for personal reasons.  I thought the OP had some good arguments which let themselves to a meaningful discussion.
However, gn2 felt it more important to project his dislike of Arch users into this thread, also Arch was never mentioned nor hinted to by the OP.

This is a recognised tactic by people and organisations who like to stop meaningful discussion.  Many political groups use it to force an issue.

Since the moderation agrees with this behaviour by not acting, I reckon this thread has gone down the tubes and most people will recognise that a meaningful discussion about the topic intended by the OP is not possible any more.

Maybe some other time....

---

### Post by gn2 on 2009-09-07
> **longtom said:**
> gn2 felt it more important to project his dislike of Arch users into this thread, also Arch was never mentioned nor hinted to by the OP.

1: Show me proof of your claim that I dislike Arch users.
This is absolutely not the case.
What I dislike is Arch users banging on about Arch in the Ubuntu forums.
I'm not alone.

2: The thread was started by someone who proudly labels himself an Arch user and was about switching Ubuntu's update method to the method used by Arch.
How did this idea spring into the OP's thoughts? I'm willing to wager that it was through use of Arch.

Like I have said before, if you don't like my posts, report them.

---

### Post by longtom on 2009-09-07
Well - I am not an Arch user and I think the OP has a good point worth discussing...

But you probably missed that in your Anti Arch crusade.  By now it is not important anymore, I guess....

---

### Post by Hallvor on 2009-09-07
> **Pogeymanz said:**
> I'm not saying that Ubuntu should change or that Ubuntu is wrong, etc. I'm only saying that the ultimate newbie distro should be different.

I think the newbie distro should be rolling release! "WHAT?! THINK OF ALL THE INSTABILITY"

You could still have rolling release without having bleeding edge versions of software.

The reason I say the ultimate Linux-Newbie distro needs to be rolling release is because one of Linux's strongest points above Windows and MacOS is the package management, but it seems wasted by only having security updates. I think Windows converts would be very impressed to see that all of their software updates could be centralized instead of having to update each package separately.

Discuss.


There is already a distro like that. It is very easy to install, has flash, java end codecs preinstalled, has one single repository with all you need, it is rolling release, uses apt for package management, has a GUI for almost everything, and it is very stable. It is called PCLinuxOS and is better for GNU/Linux newbies. No need to reinvent the wheel.

---

### Post by scratman on 2009-09-07
To go back to the original post, and try to answer OPs question, I really do not see rolling release being beneficial to Ubuntu.  I certainly cannot envisage any way that such a feature would entice new users to Ubuntu, not from Windows/Mac anyway.  My reasoning behind this is this....

1, Home users of Windows, for the most part if the figures are to be believed, run Windows XP, an 8 year old operating system.  Some buy a PC with Vista, with all of its' bells and whistles, and then revert to XP.  Why, because the majority of computer users like familiarity.

2, Corporate users of Windows would not see this as an attractive feature in any way.  Business essentially only wants to update things for security purposes.  New software means more training for staff, and that's not an appealing option when the software you have does the job you want it to do.  Businesses are used to upgrading every 3-4 years (when Microsoft effectively forces them to) and most techs will find it difficult to persuade their department manager that this change is a good thing.

3. Let's face it, how many people who use computers use bleeding edge anything?  Alienware sells awesome hardware, but does so to almost nobody.  Corporations all over the world use machines that they rent, with hardware that's 4 years old, homes worldwide are using hardware that's 5 years behind the curve.  It's the same reason you don't see millions of people driving a new car every year:- People like what is familiar.  They like to rely on things they have come to appreciate as reliable.

Is Windows as reliable as it could be?  No.  But rolling release Ubuntu would almost certainly be less reliable, and that's not a marketing feature.

Is that an argument against having a rolling release option?  No not at all, some people would love such a feature.  Is it a feature that would help market ubuntu to a wider Windows/Mac audience?  I don't think so.  In fact, I think a lot of Linux newbies have a hard enough time getting used to a PC without Windows on it, much more change could be bewildering and off-putting.

Now, if you'll excuse me, I'm going to listen to Meddle :D

Scratman.

---

### Post by Pogeymanz on 2009-09-07
> **longtom said:**
> Well - I am not an Arch user and I think the OP has a good point worth discussing...

But you probably missed that in your Anti Arch crusade.  By now it is not important anymore, I guess....
Yeah, I was pretty much ready to give up on this thread because of gn2.

And so what if Arch is what gave me the idea? Since when is that a crime? If I said I wanted to compile something, would I be called a Gentoo evangelist?


> **Hallvor said:**
> There is already a distro like that. It is very easy to install, has flash, java end codecs preinstalled, has one single repository with all you need, it is rolling release, uses apt for package management, has a GUI for almost everything, and it is very stable. It is called PCLinuxOS and is better for GNU/Linux newbies. No need to reinvent the wheel.

That's good to know. I will have to make myself familiar with it and maybe recommend that to my computer-literate friends instead of Ubuntu.

> **scratman said:**
> To go back to the original post, and try to answer OPs question, I really do not see rolling release being beneficial to Ubuntu.  I certainly cannot envisage any way that such a feature would entice new users to Ubuntu, not from Windows/Mac anyway.  My reasoning behind this is this....

1, Home users of Windows, for the most part if the figures are to be believed, run Windows XP, an 8 year old operating system.  Some buy a PC with Vista, with all of its' bells and whistles, and then revert to XP.  Why, because the majority of computer users like familiarity.

2, Corporate users of Windows would not see this as an attractive feature in any way.  Business essentially only wants to update things for security purposes.  New software means more training for staff, and that's not an appealing option when the software you have does the job you want it to do.  Businesses are used to upgrading every 3-4 years (when Microsoft effectively forces them to) and most techs will find it difficult to persuade their department manager that this change is a good thing.

3. Let's face it, how many people who use computers use bleeding edge anything?  Alienware sells awesome hardware, but does so to almost nobody.  Corporations all over the world use machines that they rent, with hardware that's 4 years old, homes worldwide are using hardware that's 5 years behind the curve.  It's the same reason you don't see millions of people driving a new car every year:- People like what is familiar.  They like to rely on things they have come to appreciate as reliable.

Is Windows as reliable as it could be?  No.  But rolling release Ubuntu would almost certainly be less reliable, and that's not a marketing feature.

Is that an argument against having a rolling release option?  No not at all, some people would love such a feature.  Is it a feature that would help market ubuntu to a wider Windows/Mac audience?  I don't think so.  In fact, I think a lot of Linux newbies have a hard enough time getting used to a PC without Windows on it, much more change could be bewildering and off-putting.

Now, if you'll excuse me, I'm going to listen to Meddle :D

Scratman.

You have very good points. I guess I was looking at this a different way. In my mind, people using XP on 5 year old computers are probably never going to switch to Linux. I was thinking that the people who are even capable of installing an OS, would be impressed by a rolling release schedule. Maybe my strategy will be Ubuntu for non-power Windows users and PCLOS for more computer-literate Windows users.

And I love Pink Floyd, so please enjoy Meddle for me. :)

---

### Post by gn2 on 2009-09-07
> **longtom said:**
> Well - I am not an Arch user and I think the OP has a good point worth discussing...

But you probably missed that in your Anti Arch crusade.  By now it is not important anymore, I guess....

Nope, I didn't miss anything, if you look for it you will see what I think of the idea contained in the OP.

If you look in this and other threads where this subject crops up you will find plenty of reasons why rolling release is a complete non-starter for Ubuntu.

The subject crops up often, why do you suppose this thread got moved to recurring discussions?

---

### Post by MarcusW on 2009-09-07
I actually see some point in a distro based on "releases" instead of being rolling, for beginners and for people who prioritize stability. I'm considering trying out some rolling distro, it'll probably be Debian testing since I'm kinda used to the way debian works. :) (the main reason is I like having new things, and I see too many threads with dist-upgrades that messed everything up)

---

### Post by gn2 on 2009-09-07
> **MarcusW said:**
> ~ I see too many threads with dist-upgrades that messed everything up ~

But there is no record of how many times it "just works" for the millions of Ubuntu users who encounter no problem.

---

### Post by MarcusW on 2009-09-07
> **gn2 said:**
> But there is no record of how many times it "just works" for the millions of Ubuntu users who encounter no problem.

That's true, my upgrade to karmic actually went really smooth. As long as I have 500gb free somewhere to backup my system partition I guess it's no problem. (I haven't really had a habit of backing up my stuff though, nothing unexpected has ever caused me to loose data and I never resize or alter a ciritcal partition) Maybe I'll keep running Ubuntu on one computer, and Debian unstable on the other. :)

---

### Post by scratman on 2009-09-08
Another reason that I feel that rolling release is a bad idea for new users is the impression that daily updates can provide.  To most current users, the updates have the effect of "Oh, cool, some new things for my PC.   What can I do now that I couldn't do before?!?"  To new users it may give the impression "Huh, it's so good that they find something wrong with it every single day!!!"

---

### Post by Hallvor on 2009-09-08
> **scratman said:**
> Another reason that I feel that rolling release is a bad idea for new users is the impression that daily updates can provide.  To most current users, the updates have the effect of "Oh, cool, some new things for my PC.   What can I do now that I couldn't do before?!?"  To new users it may give the impression "Huh, it's so good that they find something wrong with it every single day!!!"

I think most new users are used to running updated software on their computers. If they can have all the new software upgraded through Synaptic, that is a good thing and not a bad one. Try telling a Windows user that you can`t run the latest version of application X because you may have to upgrade the entire OS to do so, and he`ll think you are joking. Getting all the latest and greatest packages through Synaptic and having the OS itself upgraded like that is a good thing. And the new user doesn`t even have to reinstall for quite some time.

---


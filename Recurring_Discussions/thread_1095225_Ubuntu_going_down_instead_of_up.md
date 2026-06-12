---
title: "Ubuntu going down instead of up"
date: 2009-03-13
forum: Recurring Discussions
---

### Post by siddartha on 2009-03-13
Why is this distro going downwards to distroy its own work instead of going up and develop something better?

With the last major update the Virtual PDF printer was dumped. It was broken beyond repair for me and those who filed some threads around here. Ok, a few say it still works. But for the others there is no solution. The pack is still in the repository and it is still broken. And the Windows style result with print to file is way inferior in facilities.

This time they are planning to disable Control Alt Backspace for some ridiculous reason (like MacOS X does not have it). Did they really reach the max with the long term distro and now it's downhill for this distro?

And the whole Linux development is heading the same way. Of course you can name here or there a few apps that do their job and do it well. But most of them are in the old console list of apps. If there wasn't for skype and ekiga there won't be an option to instant messengers with the rest of the world. Multimedia players are almost all stuck at the level of the first Winamp - they can do mp3 thanks to a few mature libs, they can do avi, and divx/xvid and almost nothing more. They still have bugs implementing Matroska. They have issues with most subtitle files.

Is this the way of Linux? Trying hard to copy some app? Most PIM apps are either in their infancy, unable have any interaction with any other format than the internal one or you have Evolution which is a Devolution for anybody who does not need a state of the art comp to run a poor Outlook clone. The project started well years ago. At that point the development team decided that being behind Outlook is the way to go and they never renounced this idea. And the integration at this point with Gnome/Ubuntu is pretty much like Internet Explorer and Windows 98 - you can't really get rid of it as long as you want your system to be of some use.

I remember 12 years ago when people were talking about how bad Windows applications were. All bloated and slow. All doing a little of everything and nothing well. All overlapping in functionality yet each missing something so you had three things doing the same function, but each one could bring something extra in another direction. 12 years later its far worse for Linux. Compatibility mostly with itself and with Windows. Thank you Steve Jobs for taking BSD or the Linux crowd would have had zero interaction with that platform. At this point you have the lucky version where you get a disgustingly slow something like Azureus/Vuze and through the work of their developers and the Wine team something lean and fast like uTorrent. Or the unlucky version where you have next to no support.

And don't forget, Linux apps used to be fast. Now the startup is _the_issue_ for one year in hopes to compare with the alternatives. Now [Linux is the slow platform]("http://www.tuxradar.com/content/benchmarked-firefox-javascript-linux-and-windows-and-its-not-pretty"). In the end one excellent platform came to obey the old commercial rule "you get what you paid for". So it's free? Sure. No problem. It will make your computer work for the same amount of money. Zero.

Sure, I get Scribus, Inkscape and a few others which work great even when in development. On the other hand I have ten thousands interfaces written in some scripting language that don't even support all the options of the comand line app they are hijacking.

Is this all?

---

### Post by swoll1980 on 2009-03-13
:-({|=

---

### Post by Firestem4 on 2009-03-13
> **swoll1980 said:**
> :-({|=

Is that the worlds saddest song on the worlds small violin?

---

### Post by swoll1980 on 2009-03-13
> **Firestem4 said:**
> Is that the worlds saddest song on the worlds small violin?

Yep

---

### Post by Mr. Picklesworth on 2009-03-13
We have a PDF printer... just go to Print and choose Print to File. Of course it's going to be flawed at times; PDF printers always are. If you need a good PDF, use Scribus, or PDF export from a program like Inkscape, Abiword or OpenOffice. Or use LATeX.

Further, disabling Ctrl Alt Backspace is similar to removing training wheels. Xorg is now stable enough that we shouldn't need it, and if it seriously does fail we have our workarounds in the kernel. (Alt SysRQ K)
If you are a "power user", go ahead and remove the package "dontzap"

And of course Azureus is slow and bloated. It is in Windows, too. That program's reason to exist is pretty graphs, and they are pretty nice to stare at. There is Deluge and Transmission (I forget which is installed by default) if you want a lean torrent program. I use Transmission; the recent versions have been really nice.

Lastly, of course an app mainly targetted at Windows performs faster under Windows than it does under Linux. The two behave quite differently with regards to memory management. An application aimed soley at Linux can take the unique features of the platform (beyond the kernel, naturally; all the user space goodies Firefox ignores, too) and use them to wonderful extent.
All that benchmark you are linking to tells us is that Linux users should either fork Firefox into a completely Linux-specific branch or use a different browser. (Epiphany now has a vastly improved address bar search, for example, that blows away Firefox's by doing what the Awesome Bar does + integrated searching).

Your last paragraph makes very little sense. First of all, examples would be nice. Secondly, what is "some scripting language"? Thirdly, of course an app will go for simplicity by forgoing some options. If they cram all the options into a list there is no reason to use a GUI, is there? It appears that you know of the existence of those other options (whatever they are), which suggests to me that you know the command line. Thus, stop whining and use the command line. Nobody minds changing automatic login settings with the command line in Windows Vista, so why is it such a problem here?
Finally, GUIs are generally moving to dbus based back-ends. For some good examples look at Telepathy, PolicyKit and DeviceKit. Even before, very few apps used actual command line programs as back-ends, since the source of those programs is easily available. Usually there are working APIs available to get the same functionality without being hackish.

---

### Post by Firestem4 on 2009-03-13
> **swoll1980 said:**
> Yep

:sad:

---

### Post by Skripka on 2009-03-13
I'd demand your money back.

---

### Post by swoll1980 on 2009-03-13
> **Firestem4 said:**
> :sad:

:cry:

---

### Post by odda on 2009-03-13
I think it goes something like this [http://www.youtube.com/watch?v=jbdPUiih020](http://www.youtube.com/watch?v=jbdPUiih020)

---

### Post by Dekkon on 2009-03-13
> **Skripka said:**
> I'd demand your money back.

This is stupid, while I don't agree with everything in this topic but are you going to say this to a company that deploys open-source software and has a problem? 

Linux will never shine if you tell everyone, "You get what you pay for".

---

### Post by swoll1980 on 2009-03-13
> **odda said:**
> I think it goes something like this [http://www.youtube.com/watch?v=jbdPUiih020](http://www.youtube.com/watch?v=jbdPUiih020)

no it's more like [this one]("www.youtube.com/watch?v=0mbnmdL9vY8") or [this one]("www.youtube.com/watch?v=G1UvabfIbl8&feature=related")

---

### Post by Firestem4 on 2009-03-13
> **swoll1980 said:**
> no it's more like [this one]("www.youtube.com/watch?v=0mbnmdL9vY8") or [this one]("www.youtube.com/watch?v=G1UvabfIbl8&feature=related")

I think not. Its more like this 

[http://www.youtube.com/watch?v=8Kkxbw3s2pM](http://www.youtube.com/watch?v=8Kkxbw3s2pM)

(Note: This is known as the Hungarian Suicide Song)

---

### Post by arrancaru on 2009-03-13
Mimimi :(

---

### Post by swoll1980 on 2009-03-13
> **Firestem4 said:**
> I think not. Its more like this 

[http://www.youtube.com/watch?v=8Kkxbw3s2pM](http://www.youtube.com/watch?v=8Kkxbw3s2pM)

(Note: This is known as the Hungarian Suicide Song)

That's a piano though, so it's automatically disqualified.

---

### Post by Firestem4 on 2009-03-13
> **swoll1980 said:**
> That's a piano though, so it's automatically disqualified.

No no. Keep listening. The main instrument is a violin.

---

### Post by swoll1980 on 2009-03-13
> **Firestem4 said:**
> No no. Keep listening. The main instrument is a violin.

OK, that one wins! I almost wanted to kill myself for crying out loud! :cry:

---

### Post by Firestem4 on 2009-03-13
> **swoll1980 said:**
> OK, that one wins! I almost wanted to kill myself for crying out loud! :cry:

Don't do that!

---

### Post by swoll1980 on 2009-03-13
> **Firestem4 said:**
> Don't do that!

Was a joke. Nobody go calling the nut house on me now.

---

### Post by Firestem4 on 2009-03-13
> **swoll1980 said:**
> Was a joke. Nobody go calling the nut house on me now.
... too late =( lol

---

### Post by Bölvaður on 2009-03-13
> **Dekkon said:**
> This is stupid, while I don't agree with everything in this topic but are you going to say this to a company that deploys open-source software and has a problem? 

Linux will never shine if you tell everyone, "You get what you pay for".

You do realize that using linux isnt free... you are either supposed to develop or help others.... or be a jackass and be a freeloader ;)
and if you are the last one perhaps you should get what you payed for.

---

### Post by swoll1980 on 2009-03-13
> **Bölvaður said:**
> You do realize that using linux isnt free... you are either supposed to develop or help others.... or be a jackass and be a freeloader ;)
and if you are the last one perhaps you should get what you payed for.

I would add that if you deploy this as a company, perhaps you should pay for the support. The problem this guy has is easily solved. A call to Canonical would have been easy enough.

---

### Post by amitabhishek on 2009-03-13
Another this vs. that thread

---

### Post by jimi_hendrix on 2009-03-13
> **siddartha said:**
> 
This time they are planning to disable Control Alt Backspace for some ridiculous reason (like MacOS X does not have it). Did they really reach the max with the long term distro and now it's downhill for this distro?

might be time for a distro change soon....
> 
Thank you Steve Jobs for taking BSD or the Linux crowd would have had zero interaction with that platform. At this point you have the lucky version where you get a disgustingly slow something like Azureus/Vuze and through the work of their developers and the Wine team something lean and fast like uTorrent. Or the unlucky version where you have next to no support.

uhh the majority of the mac crowd still doesnt

mac is not linux or bsd

mac is a shiny GUI for unix...and most of the mac os users probably dont know what unix is

---

### Post by mhelmer on 2009-03-13
> **Dekkon said:**
> This is stupid, while I don't agree with everything in this topic but are you going to say this to a company that deploys open-source software and has a problem? 

Linux will never shine if you tell everyone, "You get what you pay for".

> **Bölvaður said:**
> You do realize that using linux isnt free... you are either supposed to develop or help others.... or be a jackass and be a freeloader ;)
and if you are the last one perhaps you should get what you payed for.


Any company that deploys open-source software should understand the risks and stability of using such software. Anybody who is going to whine about open-source code after which the risks are blatantly obvious is moronic. If you can not, or are not, willing and able to take the time to resolve the issue your self then call Microsoft. They would be glad to take your money.


+1 bolvadur

Seems like a lot of people are complaining lately. Just my 2 cents.   :D

---

### Post by Skripka on 2009-03-13
> **Dekkon said:**
> This is stupid.

Yes.

It is a juvenile answer.  A juvenile answer to a silly OP.  I respond to what I see.

---

### Post by aysiu on 2009-03-13
Funny. I blogged about this:
[The Linux community&#8217;s mixed messages](http://www.psychocats.net/ubuntucat/the-linux-communitys-mixed-messages/): [quote=Excerpt]** Free has to be worth something or nothing - make up your mind**
I see a lot of Linux users say that there is a popular misconception that free means lesser in quality. The basic idea is that people are skeptical of free products, but we know free products can be of very high quality.

But if someone complains about Linux, then all of a sudden Linux users say &#8220;Why don&#8217;t you ask for refund?&#8221; or &#8220;It&#8217;s free. How can you complain about something that&#8217;s free?&#8221;[/quote]

---

### Post by Bios Element on 2009-03-13
> **jimi_hendrix said:**
> might be time for a distro change soon....

Last I looked Ctrl-Alt-Backspace was being disabled upstream. So G'Luck with that. Or you could just re-enable it...But that'd be the easy way. ^_^

---

### Post by Kareeser on 2009-03-14
Linux is built on the concept of altruism.

By nature, it's FREE and without any obligation to pay back.

Hence, I'm not going to help out if I don't want to. Simple as that.

Besides, it's not like you'd enforce my (unborn) 3 year-old to submit bug reports, would you? They'd be quite fun to read...

---

### Post by hansdown on 2009-03-14
> **Bölvaður said:**
> You do realize that using linux isnt free... you are either supposed to develop or help others.... or be a jackass and be a freeloader ;)
and if you are the last one perhaps you should get what you payed for.

That is VERY DEEP Bölvaður.

Thankyou.

---

### Post by handy on 2009-03-14
Ubuntu is slow, it tries to be all things to all people just like windows.

Try a different type of Linux if you want more speed?

It worked for me. ;)

---

### Post by mhelmer on 2009-03-14
> **Kareeser said:**
> Linux is built on the concept of altruism.

By nature, it's FREE and without any obligation to pay back.

Hence, I'm not going to help out if I don't want to. Simple as that.

Besides, it's not like you'd enforce my (unborn) 3 year-old to submit bug reports, would you? They'd be quite fun to read...

That may be true but that does not give you the right to complain about it. Which was the original point, pay attention.

---

### Post by JPtux on 2009-03-14
Go do some Arch or Gentoo if you are so fed up with ubuntu.

---

### Post by handy on 2009-03-14
> **mhelmer said:**
> That may be true but that does not give you the right to complain about it. Which was the original point, pay attention.

So, because something is free, the right to complain about it is removed?

If I breath foul air, drink foul water, or use faulty software, I will complain if I choose to, as that is my right.

---

### Post by bigbrovar on 2009-03-14
> So, because something is free, the right to complain about it is removed?

If I breath foul air, drink foul water, or use faulty software, I will complain if I choose to, as that is my right. 
with every right comes a corresponding duty.. when you buy software.. you have obligation to pay for the software which gives you the right to complain or even demand you money back.. with free software you have the obligation to help make it better, whether by filing a bug report, develop to make it better, or write documentations, or anything that you are capable of doing that would improve the state of the software. Most Free  software are licensed under the General Public License which makes it a software for the community. by using that software you become a member of that community, so hence the complaint in your rant also affect you.. see it this way.. its like complaining about the state of the Toilet you your house. when you have never done anything to improve it.. when last did you file a bug, or introduced you ideas or observation to a dev mailing list? free software has a culture and using it alone is not enough, you have to understand the culture.. Ubuntu is You and I

---

### Post by handy on 2009-03-14
> **bigbrovar said:**
> 
with every right comes a corresponding duty.. when you buy software.. you have obligation to pay for the software which gives you the right to complain or even demand you money back.. with free software you have the obligation to help make it better, 

Where is this obligation written in the GPL?

Is this one of those invisible expectations that some people can see & others can't?

If so, then it will forever be a cause of arguments & discord.

If something is not put on public display & written down clearly so that the public can easily understand it then it has no credibility.

A portion of humanity expecting that something is understood by all & is just plain common sense; is far from being a valid foundation for universal understanding.   

> **bigbrovar said:**
> 
whether by filing a bug report, develop to make it better, or write documentations, or anything that you are capable of doing that would improve the state of the software. Most Free  software are licensed under the General Public License which makes it a software for the community. by using that software you become a member of that community, 

Again, this is an ethereal statement, that takes certain things for granted; expecting everyone to see things the same way.  

Which is impossible.

> **bigbrovar said:**
> 
so hence the complaint in your rant also affect you.. see it this way.. its like complaining about the state of the Toilet you your house. when you have never done anything to improve it.. 

If the toilet does not function properly I will complain about it.

If software satisfies my needs, but is unstable, I will dump it & advise others not to use it, explaining the reasons why.  If I choose to complain, I will make my complaints as clear as possible.

Software that does not work properly is worthy of complaint by the user, whether they paid for it or not.  If the software is unpaid for, the complaints can be focussed in a way to help the developers, or to warn people off as far as using the software is concerned, which also helps the community.

> **bigbrovar said:**
> 
when last did you file a bug, or introduced you ideas or observation to a dev mailing list? 

I was involved in a kernel bug 3/4's of the way through last year.  I wrote a how to for Arch users, who did not have a previous version of the kernel in their cache, showing them how they could [*_access & install redundant kernels_*]("http://grubbn.org/otheros/showthread.php?tid=12").

Another how to on [*_downgrading Arch packages_*]("http://grubbn.org/otheros/showthread.php?tid=11").

I have written a detailed how to for [*_installing Arch on the iMac_*]("http://wiki.archlinux.org/index.php/IMac_Aluminium")

I have submitted a ubuntu bug or two, though not for a long time now. 

> **bigbrovar said:**
> 
 free software has a culture and using it alone is not enough, you have to understand the culture.. Ubuntu is You and I

Too true. ;)

---

### Post by siddartha on 2009-05-11
So down it is.

---

### Post by kk0sse54 on 2009-05-11
> **siddartha said:**
> So down it is.

Thank you for returning to the forums and saying in an unfounded  sentence how bad Ubuntu is.

---

### Post by siddartha on 2009-05-12
> **C!oud said:**
> Thank you for returning to the forums and saying in an unfounded  sentence how bad Ubuntu is.

Than you didn't pay any attention. With answers like it's free so shut up you will get a distro like the one just released - slower than XP and not even the graphical upgrades interesting enough to waste the bandwidth. Even this forum is going down. Most of my issues were with only a couple of views and no answers. And trivial questions are not answered by "go ask google"... no, this is where you have a true display of community and people quote the FAQ without even understanding the issue. In a way, just like yourself.

---

### Post by kk0sse54 on 2009-05-12
> **siddartha said:**
> Than you didn't pay any attention. With answers like it's free so shut up you will get a distro like the one just released - slower than XP and not even the graphical upgrades interesting enough to waste the bandwidth. 
Yes I did and when someone dredges up their own thread from months ago and issue a statement such as "So down it is." that's called an unfounded statement because you provide no support for your claim on the *continuing * downward spiral for Ubuntu.

> Even this forum is going down. 

This is nothing new, I've been saying this for the last few months 

> Most of my issues were with only a couple of views and no answers. And trivial questions are not answered by "go ask google"... no, this is where you have a true display of community and people quote the FAQ without even understanding the issue. In a way, just like yourself.

Speaking of go ask google, ever bother trying to google your problem with the residual config ;)

---


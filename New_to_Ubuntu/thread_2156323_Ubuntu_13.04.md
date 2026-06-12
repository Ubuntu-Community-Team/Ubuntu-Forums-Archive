---
title: "Ubuntu 13.04"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by d1lu5ion on 2013-06-21
Hi everyone,

I'm trying to install Ubuntu 13.04 from my cd. Everything works find to a certain point. Then it just freezes. I do have my ethernet cable inside my computer jack while installing. 

I've heard of it working for people without it being connected.. But i'm wondering if that should even be an issue if it is or isn't?

I know my computer can handle it otherwise I wouldn't even bother attempting it..

Anyone have any ideas?

Thanks,

---

### Post by leg on 2013-06-21
I installed 13.04 without a network cable as my port is broken. It realised that I had a wireless connection to use. What about disk space have you got enough of that?

---

### Post by d1lu5ion on 2013-06-21
off the the top of my head I can't remember right now whether I have 1 or 2 TB's.. It's one of those and it's fully empty. It was just meant for ubuntu.. Maybe I'll try it without the ethernet cable when I get home from work later and see if it helps.

---

### Post by leg on 2013-06-21
> **d1lu5ion said:**
> off the the top of my head I can't remember right now whether I have 1 or 2 TB's.. It's one of those and it's fully empty. It was just meant for ubuntu.. Maybe I'll try it without the ethernet cable when I get home from work later and see if it helps.

probably not that then. I only mentioned as the only time an install has stalled on me is when I didn't quite have the specs for it.

---

### Post by varunendra on 2013-06-21
> **d1lu5ion said:**
> I'm trying to install Ubuntu 13.04 from my cd. Everything works find to a certain point. Then it just freezes.

First of all, Welcome to the forums d1lu5ion !

Does the live session work fine (not "Install", just "Try" on the live session)?

If not, try the various boot options available for the live session : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If it works fine in live mode and only installation is problematic, then yes, try disconnecting from net when trying to install. It is not necessarily a problem, not even a common one, but IS one of a few other possible reasons.

**PS:**
If you are new to Ubuntu, I'd suggest to try 12.04 as well, in live session of course, and go with it if it plays nicely with your system. The reason is that it is an LTS - means [Long-Term-Support]("https://wiki.ubuntu.com/Releases") version. It is 'supposed' to be more stable and will be supported till April 2017, while 13.04 will only be supported till January next year (afterwards it'll keep working, but you won't get software or security updates for it).

---

### Post by 3rdalbum on 2013-06-21
If it always gets to a certain point in the install before "freezing", it sounds like it may be a bad disc.

Try re-burning the disc at 8x, or as close to that speed as you can manage. Let the disc cool down outside the computer before putting it into the drive and booting from it.

If you still have problems, check the MD5 hash of the ISO file you downloaded, and see if it matches the MD5 hash published on the Ubuntu website.

---

### Post by d1lu5ion on 2013-06-21
Thanks Guys, I will have to give this a try and report back later. I appreciate all the advice! :) 


> [COLOR=#000000]First of all, Welcome to the forums d1lu5ion ![/COLOR]

[COLOR=#000000]Does the live session work fine (not "Install", just "Try" on the live session)?[/COLOR]

[COLOR=#000000]If not, try the various boot options available for the live session : [/COLOR][https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[COLOR=#000000]If it works fine in live mode and only installation is problematic, then yes, try disconnecting from net when trying to install. It is not necessarily a problem, not even a common one, but IS one of a few other possible reasons.[/COLOR]

[B]PS:
If you are new to Ubuntu, I'd suggest to try 12.04 as well, in live session of course, and go with it if it plays nicely with your system. The reason is that it is an LTS - means [Long-Term-Support]("https://wiki.ubuntu.com/Releases") version. It is 'supposed' to be more stable and will be supported till April 2017, while 13.04 will only be supported till January next year (afterwards it'll keep working, but you won't get software or security updates for it).[/B]


Thank you for the welcoming.

So are you mentioning that 12.04 is generally the best way to go? I'm sorta new to the server stuff so I'm trying to learn as much as I can.

---

### Post by varunendra on 2013-06-21
> **d1lu5ion said:**
> So are you mentioning that 12.04 is generally the best way to go?

'Generally', not necessarily. But if you are going to try the server, then it is even more recommendable since for a server, stability and long term support are preferable over cutting-edge features.

For desktop version, go with whatever suits you best, I just highlighted the difference.

Some people prefer newer and more advanced features over 'supposed' (but not guaranteed) stability and long-term support. For some others, it is a matter of better hardware support (one may support better that the other one). But for majority of newcomers, it is either the lack of information, or the false assumption that "latest must be greatest", or both that make them go with the latest release instead of the latest LTS. So I just made that information available to you. Try them both if you wish or if needed, then go with whatever looks better to 'you'. :)

---

### Post by d1lu5ion on 2013-06-21
> [COLOR=#000000]'Generally', not necessarily. But if you are going to try the server, then it is even more recommendable since for a server, stability and long term support are preferable over cutting-edge features.[/COLOR]

[COLOR=#000000]For desktop version, go with whatever suits you best, I just highlighted the difference.[/COLOR]

[COLOR=#000000]Some people prefer newer and more advanced features over 'supposed' (but not guaranteed) stability and long-term support. For some others, it is a matter of better hardware support (one may support better that the other one). But for majority of newcomers, it is either the lack of information, or the false assumption that "latest must be greatest", or both that make them go with the latest release instead of the latest LTS. So I just made that information available to you. Try them both if you wish or if needed, then go with whatever looks better to 'you'. [/COLOR]:smile:

Ah I see, Thank you. You are right, I think the only way to get a feel of it, is to try them both and see what I like or suits me best.. However, I do like the sound of 12.04 being supported until April 2017! 

Why is 13 only supported for a shorter period of time? -- That's probably the lamest question... :)

---

### Post by varunendra on 2013-06-22
> **d1lu5ion said:**
> Why is 13 only supported for a shorter period of time? -- That's probably the lamest question... :)
Nope! That's a valid and important question. Although what I'll tell you is not an official answer, just my personal knowledge and opinion about it :)

Also, I have a very bad habit of pouring everything I know if a poor innocent user makes the mistake of expressing curiosity about something I know *(or I believe I know)*. So get prepared to suffer the punishment below -

[SIZE=3]**_LTS (Long Term Support) Release_**[/SIZE]

Think of an LTS, like 12.04 as an enterprise release. It is supposed to be stable and supported for a long time, while containing everything that can be offered without compromising the stability. It comes out with only those features that have been tested thoroughly and are supposed to be bug-free, stable and working for most, if not all, users.

Further, its updates *(the default, recommended ones)* contain only those things that have also been tested enough and are supposed to be stable. Of course no software is 100% bug free and this is especially true in active Open-Source projects like Ubuntu. So despite a lot of care, bugs do keep appearing from time-to-time, but a lot less in numbers in an LTS, and *(I assume)* are paid more attention thus getting fixed relatively quicker.

It is released every 2 years in April *(thus always a ".04" version like 12.04, 10.04, 8.04...)*. Before 12.04, only the server version of the LTS was supported for 5 years, while the desktop for only 3 years. From 12.04 *(and onwards)*, it was decided that both desktop and server versions will be supported for 5 years.

There are also "**Point-releases**" of LTS versions, which are nothing but a release of LTS including the latest official updates *(including newer kernel and software packages that have been officially released in its updates)*. These are represented by an additional number in the last *(.1, .2, etc.)*, like the current "Point-Release" of 12.04 LTS is **12.04.2**.

It means that when you install a point release *(the default ISO available at official download links)*, you are getting a version that already contains the updates that have been released since the original release till the date of the release of that Point-Release.

The next LTS will be 14.04, releasing in April 2014.


[SIZE=3]**_Standard Release_**[/SIZE]

Think of them as relatively more liberal, more trendy, sort of 'Enthusiast' releases *(my personal views, hope I'm not offending anyone)*. It contains features and support that could not be included in the LTS because of some reasons. Some of these reasons can be -

[INDENT]* Maybe the feature/suport was not ready at the time of the release of the LTS

* Maybe it wasn't tested enough

* Maybe it was too buggy

* Maybe there were questions about its usability or whether the users would like it or not...[/INDENT]

These "Standard Releases" serve two main purposes -

[INDENT]**1)** For users it serves as a release that lets them enjoy the latest, latest trends and cutting edge features/technology.

**2)** For developers it serves the purpose of extensive mass-testing of features that they intend to include in the next LTS.[/INDENT]

The standard releases are released every 6 months *(in April and October every year, thus the version numbers always being ".04" and ".10")*. Before 13.04, the standard releases were supported for 18 months. Which meant **there used to be times when the developers had to support 10-11 different versions simultaneously** *(for example, in April 2010)*. With the decision to extend the desktop LTS support to 5 years like the server version, this was going to get worse. **This brings us to the answer to your original question -**


[SIZE=3]**_Why is Standard Release Support Period is Short ?_**[/SIZE]

Supporting a release means keeping it up-to-date with latest security patches, latest bug-fixes, updating hardware-support, etc. and doing all this while trying not to break an existing feature/package. This requires a lot of care and work from the developers. Since supporting the LTS is a serious commitment, it is difficult for the developers to support multiple distros simultaneously.

**From 12.04, Canonical decided to get more aggressive on development front, while also hardening stability on the LTS front. So it shortened the support period of the Standard Release to just 9 months. With this change, now _there will be at most 8 different versions to support at a given time_ (including server versions).**
*(just calculated, can be wrong)* ;)

Keeping the "Standard Release" support period short allows the developers to move on to a newer release that contains most of the features that were tested ok in the previous one, replacing or dropping altogether the features that were too problematic, and include the latest ones on a whole new build. Thus -

[INDENT]* The developers don't have to carry the burden of supporting too many different versions with the same purpose. Features that have been proven stable and useful can be moved to the existing LTS in the form of updates, or marked for inclusion in the next LTS.

* They can keep testing the existing not-yet-stable-enough and newer features in the next Standard Release.

* The users who like to enjoy the latest features can move on to the next release (be it LTS or a standard one, whatever is latest)

* The users who prefer stability can stick with the LTS, until the next one comes out.[/INDENT]

That's all of my personal understanding of the reasons why the standard releases have a short support duration (of course based on many articles/discussions I have read, but can't call them as 'Authoritative' statements).

Some useful links elaborating these facts/differences :

[B][INDENT]What Is an LTS : [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Table of Most Recent Releases and Their Support Period : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Difference between LTS and Standard Releases (much less painful post than this one) : [http://askubuntu.com/q/16366](http://askubuntu.com/q/16366)[/INDENT][/B]

---

### Post by BNZBKK on 2013-06-22
Forget the discs and install from a USB  ..I've just installed 12.04 LTS and threw away half a dozens discs before I wised up

---

### Post by Rob Sayer on 2013-06-22
I had to use a usb stick to install on my newest machine since it's a netbook and doesn't have an optical drive.  Now I'll never install from cd/dvd again.  A usb stick is much faster.

I've never installed using the download updates while installing method.  Though you want to run the live cd first to make sure everything more or less works first.  I just install the cd and then run system update after.  If you lost your connection while updating during installation ... it doesn't sound pretty to me.

---

### Post by d1lu5ion on 2013-06-23
Thank you very much for this information. It says a lot!

I'm thinking of trying 12.04 or 12.10 (?) any thoughts on 10?

also I'm wondering if it's possible to install the desktop version and a server together?

Thank you.

---

### Post by varunendra on 2013-06-23
> **d1lu5ion said:**
> I'm thinking of trying 12.04 or 12.10 (?) any thoughts on 10?

also I'm wondering if it's possible to install the desktop version and a server together?

Thank you.

You're welcome!

I don't see the point in trying 12.10. 12.04 has all the good parts of 12.10 (in the form of updates or optional packages).

You can install the desktop version and then install the server packages on it as required (if you need only some functionality of the server).

Or you can install the server version (will be text-only) and then install "ubuntu-desktop" meta-pacakge (or individual packages as required) if you need only 'some' features of the desktop and a gui.

Yet another option may be to install both on separate partitions if you just want to test them or use them alternately.

---

### Post by kurt18947 on 2013-06-23
> **BNZBKK said:**
> Forget the discs and install from a USB  ..I've just installed 12.04 LTS and threw away half a dozens discs before I wised up

Booting from a live USB is faster -- if your machine will support it.  Older machines may not.  It also seems to depend on the USB drive. My experience is that not all USB drives are bootable on all machines.  I bought a USB CD/DVD drive and have never had that fail to boot a bootable disk.

---

### Post by d1lu5ion on 2013-06-24
I was able to install it using the cd. I've installed the desktop 12.04. How do I go about of installing the server for this as well?

---

### Post by d1lu5ion on 2013-06-28
Anyone know how to do this?

---

### Post by 3rdalbum on 2013-06-28
Just use Ubuntu Software Center or apt-get to install the server packages you want. If you want a web server, you can install Apache. If you want a file sharing server, you can install system-config-samba and that will ensure you have the Samba server and an easy program for setting it up.

When you install a server package, it automatically starts up. No need for a reboot, it will always be on when your computer is on.

---

### Post by d1lu5ion on 2013-06-28
> **3rdalbum said:**
> Just use Ubuntu Software Center or apt-get to install the server packages you want. If you want a web server, you can install Apache. If you want a file sharing server, you can install system-config-samba and that will ensure you have the Samba server and an easy program for setting it up.

When you install a server package, it automatically starts up. No need for a reboot, it will always be on when your computer is on.


Thanks, I'm trying to build a website server / music server. Can I do this with the software center? or do I need to search for a server to install? like ubuntu server 12.04 (example)

---

### Post by d1lu5ion on 2013-07-02
Anyone know if ubuntu software center will allow me to do this? When I tried looking for "server" I see things related to servers but I'm not sure which one to use..

---

### Post by su:bhatta on 2013-07-02
u can try to get a new iso n burn it at slow speed...<=8x...

Also, u can use the 13.04 version... update to 13.10...  wait until April '14  then use 14.04 LTS...meantime get to know the system better...

---

### Post by cub on 2013-07-02
> **d1lu5ion said:**
> Thanks, I'm trying to build a website server / music server. Can I do this with the software center? or do I need to search for a server to install? like ubuntu server 12.04 (example)
If you are to set up a web server you could install Apache or nginx. I use a locally installed web server with mysql and php for creating web sites, short tutorial on [http://www.sjolund.se/?p=214](http://www.sjolund.se/?p=214) . I use Ubuntu Studio but the process should be similar enough.

What do you mean by music server?

---


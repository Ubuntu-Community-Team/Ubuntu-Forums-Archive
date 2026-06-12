---
title: "Ubuntu niggles"
date: 2023-12-17
forum: New to Ubuntu
---

### Post by ahumanerror on 2023-12-17
Hi.

Yes I'm pretty new to Ubuntu. I have 22.04.3LTS installed, in fact I have a dual boot with Windows. I'm getting to grips with it and quite like Ubuntu. It's much better on battery and runs way cooler but there's just a few niggles.

One is that sometimes it fails to boot, either freezing while booting or just after I log in - it used to freeze at login often but then there was some updates that I installed and it doesn't do it as much. Annoyingly this is completely random and doesn't seem to have any pattern.

The more frustrating issue recently is with Firefox. When attempting to watch YouTube videos it simply doesn't play them, it constantly buffers and fails to start. There was some recent updates I installed and I've noticed it's not playing videos since then, as far as I'm aware it was fine prior to this. I have tried removing and reinstalling it with the same issue.

Can anybody help with this?

---

### Post by TheFu on 2023-12-17
> **ahumanerror said:**
> Yes I'm pretty new to Ubuntu. I have 22.04.3LTS installed, in fact I have a dual boot with Windows. I'm getting to grips with it and quite like Ubuntu. It's much better on battery and runs way cooler but there's just a few niggles.

I'm not good at helping people really new to Linux, but I'll try.  'niggles' is a new term for me. Looked it up. Probably due to my location in the Southern USA, that term has a derogatory meaning that isn't politically correct here, though it isn't a "bad" word.  Lots of excellent words get effectively removed from our speech so that nobody feels slighted.

> **ahumanerror said:**
> One is that sometimes it fails to boot, either freezing while booting or just after I log in - it used to freeze at login often but then there was some updates that I installed and it doesn't do it as much. Annoyingly this is completely random and doesn't seem to have any pattern.


This is likely a hardware issue that MS-Windows ignores.  Unix/Linux isn't as forgiving and will choke on issues.  Check your system logs.  For any error, always check the system logs first.  Google "ubuntu logs" to learn how.

I hate to say this, but _if_ your computer has an nvidia GPU, nvidia hasn't been a good friend to Linux. Their drivers have a problem of breaking systems, especially video playback, but a few times in the last few years, installing nvidia drivers has actually broken network drivers on Linux systems.  That's crazy, right?  Without networking, Linux is fairly useless.  After all, _the network is the computer._

nvidia mostly works, but there are some configurations in the millions of possible configs that are just a little different which cause issues.
I don't KNOW if nvidia or some other hardware are the core issues.  Look at the system logs. That's where issues will be posted, sometime with instructions to correct it. At a minimum, there should be a hint for the problem. It may not be clear to you what that hint is. Only time and experience can decipher some of those errors/warnings in the system logs.

> **ahumanerror said:**
> The more frustrating issue recently is with Firefox. When attempting to watch YouTube videos it simply doesn't play them, it constantly buffers and fails to start. There was some recent updates I installed and I've noticed it's not playing videos since then, as far as I'm aware it was fine prior to this. I have tried removing and reinstalling it with the same issue.

Yes, Firefox is problematic both due to Mozilla pushing non-production code AND Canonical forcing noobs to use a snap package for it.  Snap packages have added, mandatory, constraints that often break things.  So, what can you do about it?  Or ... what have I done about it, might be a better question.  I've purged my desktops of all snap packages.  By removing the snap subsystem, less RAM gets wasted, less CPU gets wasted. 

There are downsides. Snaps provide constraints to protect other programs and the system from poorly behaved programs or programs that have been hacked by outside people. If you are reasonably careful, this isn't an issue, but if you install software outside the approved Canonical repos, all bets are off.  As a noob, you shouldn't be downloading packages outside the package manager and probably shouldn't be using unknown PPAs.  If you have already downloaded and  install .deb files directly, you've screwed your system.

Ok, with that said, Mozilla makes a stable, enterprise, version of Firefox.  It is called Firefox ESR.  You can find reputable steps to install it, using the Mozilla PPA.  It provides an older version of firefox and isn't a snap package.  Anyway, that's something to consider.  

I don't use a web browser to view videos very often and specifically disable that capability in Firefox for security reasons. Less complex code means fewer bugs, which means smaller attack surfaces for my system.  Browsers are huge attack surfaces and some of the most complex software made.  I usually use mpv and provide the URL to it for video playback.  Other people use vlc. Either should play nearly any video file without DRM on the internet.  mpv is a CLI program, but there are a few GUI front-ends for it. smplayer is one.  Not my taste, but lots of people seem to like it.

> **ahumanerror said:**
> Can anybody help with this?

I don't know if I've been any help or just confusing. Sorry. Perhaps someone better at helping new people will come along and post.

---

### Post by ian-weisser on 2023-12-17
The term we generally use for problems too minor to fret about is "papercut"

However, freezes and failures like you describe are not papercuts.
They are real, valid support questions.

> **ahumanerror said:**
> The more frustrating issue recently is with Firefox. When attempting to watch YouTube videos it simply doesn't play them, it constantly buffers and fails to start.

Unable to duplicate. On my desktop systems, Firefox plays YouTube solidly.

Check that you have enough RAM and a stable network connection.

---

### Post by ahumanerror on 2023-12-17
> **TheFu said:**
> I'm not good at helping people really new to Linux, but I'll try.  'niggles' is a new term for me. Looked it up. Probably due to my location in the Southern USA, that term has a derogatory meaning that isn't politically correct here, though it isn't a "bad" word.  Lots of excellent words get effectively removed from our speech so that nobody feels slightly.



This is likely a hardware issue that MS-Windows ignores.  Unix/Linux isn't as forgiving and will choke on issues.  Check your system logs.  For any error, always check the system logs first.  Google "ubuntu logs" to learn how.

I hate to say this, but if your computer has an nvidia GPU, nvidia hasn't been a good friend to Linux. Their drivers have a problem of breaking systems, especially video playback, but a few times in the last few years, installing nvidia drivers has actually broken network drivers on Linux systems.  That's crazy, right?  Without networking, Linux is fairly useless.  After all, _the network is the computer._



Yes, Firefox is problematic both due to Mozilla pushing non-production code AND Canonical forcing noobs to use a snap package for it.  Snap packages have added, mandatory, constraints that often break things.  So, what can you do about it?  Or ... what have I done about it, might be a better question.  I've purged my desktops of all snap packages.  By removing the snap subsystem, less RAM gets wasted, less CPU gets wasted. 

There are downsides. Snaps provide constraints to protect other programs and the system from poorly behaved programs or programs that have been hacked by outside people. If you are reasonably careful, this isn't an issue, but if you install software outside the approved Canonical repos, all bets are off.  As a noob, you shouldn't be downloading packages outside the package manager and probably shouldn't be using unknown PPAs.  If you have already downloaded and  install .deb files directly, you've screwed your system.

Ok, with that said, Mozilla makes a stable, enterprise, version of Firefox.  It is called Firefox ESR.  You can find reputable steps to install it, using the Mozilla PPA.  It provides an older version of firefox and isn't a snap package.  Anyway, that's something to consider.  



I don't know if I've been any help or just confusing. Sorry. Perhaps someone better at helping new people will come along and post.

Not sure how to quote specific parts of your reply so you'll have to make do with a slab of text.

'Niggles' just seemed to fit. I wouldn't really consider them big enough to be a problem, nor an issue. I suppose language is subjective.

The way I'm thinking is that if it was a hardware issue then wouldn't it be freezing much more consistently rather than random? I done a hardware scan from the BIOS and everything seems to pass OK.

You're right that I do have an nVidia GPU (I think it's the 1080 GTX), but with it being a laptop it defaults to the UHD Graphics, unless you're gaming.

The Firefox thing has touched a nerve with me because I like to watch a lot of YouTube. Your resolution of removing snap packages is over my head really since I've only been using Linux for a few months, but I expected more people to have experienced the same - or similar - thing, after searching around that doesn't seem to be the case.

> **ian-weisser said:**
> The term we generally use for problems too minor to fret about is "papercut"

However, freezes and failures like you describe are not papercuts.
They are real, valid support questions.



Unable to duplicate. On my desktop systems, Firefox plays YouTube solidly.

Check that you have enough RAM and a stable network connection.

The specs are pretty decent on my laptop and after checking the System Monitor it says I have 14.1GB free of memory so I don't think it's an issue.

^ With that being said I thought i'd check the networking activity via System Monitor while it buffers a YouTube video to see if it's actually sending/receiving data and of course it's randomly started working fine. It now suddenly, and randomly, plays just fine (??)

I must admit that I probably would jump to Ubuntu full time if only it was a bit more stable. I mean it just seems a little temperamental, but I completely get the appeal. Even on the face of it it uses much less resources than Windows, and thus runs cooler, and longer on battery... not to mention the privacy concerns in Windows. The downside of course is these *niggles* in the short time I've been using it, but somehow I imagine that it would run a little better on desktop.

---

### Post by pantazi on 2023-12-17
I am currently using Ubuntu 20.04 and have been playing with 22.04.03 in KVM virtual machine manager just to see if it's worth upgrading. I don't have Firefox in my  OS and when trying out 22.04 I came across this article, which is self explanatory.
A simple exercise that may help you.

[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by TheFu on 2023-12-17
> **ahumanerror said:**
>  
^ With that being said I thought i'd check the networking activity via System Monitor while it buffers a YouTube video to see if it's actually sending/receiving data and of course it's randomly started working fine. It now suddenly, and randomly, plays just fine (??)

I must admit that I probably would jump to Ubuntu full time if only it was a bit more stable. I mean it just seems a little temperamental, but I completely get the appeal. Even on the face of it it uses much less resources than Windows, and thus runs cooler, and longer on battery... not to mention the privacy concerns in Windows. The downside of course is these *niggles* in the short time I've been using it, but somehow I imagine that it would run a little better on desktop.

I can assure you that my Ubuntu systems are very stable, assuming there aren't hardware issues.  I'd show you some uptimes, which are typically 2-3 weeks for all my systems, but I patched Saturday and rebooted. Also, my systems do get busy and sometimes have days of heavy processing, so they aren't just sitting there, idle.

One system is very busy right now.  And stable.
```
$ uptime 
 16:33:36 up  8:32,  1 user,  load average: **10.72, 10.02, 6.60**

```

---

### Post by ian-weisser on 2023-12-17
> **ahumanerror said:**
> I expected more people to have experienced the same - or similar - thing, after searching around that doesn't seem to be the case.

An accurate assessment. Millions of installs. A relative trickle (not flood) of reported problems.
Your experience is unusual.

> **ahumanerror said:**
> The specs are pretty decent on my laptop and after checking the System Monitor it says I have 14.1GB free of memory so I don't think it's an issue.

Starting and stopping YouTube video streams tends to cause CPU spikes. Look for those, too.

> **ahumanerror said:**
> I must admit that I probably would jump to Ubuntu full time if only it was a bit more stable.

If you are comfortable being a *customer*, then don't jump. Your statement leans that direction. Ubuntu is not a drop-in replacement for Windows. It is different, and requires different skills.
If, instead, you want to be a *participant* and to learn, then jump.

---


---
title: "What Updates To Install?"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by johnsmoke on 2011-09-11
There seems to be many updates available when the Update Manager icon appears in the launcher. Which do you guys usually install? All of them? Or just some necessary security updates? I just don't want to bloat my PC with tons of things. I always turned off the Automatic Updates when I was Windows.

---

### Post by cgroza on 2011-09-11
You should install all of them. The update will only provide fixes for software you already have installed. It will not install new software.

---

### Post by MG&amp;TL on 2011-09-11
Typically you do not HAVE to install anything at all. Stuff will not be as up-to-date as it could be, and it may not be terribly secure if you're running, say, a server.

I usually install everything, because it's easy and I like to be up-to-date, but 'security updates' won't improve security massively.

All the programs are typically just patches that won't take up much more room (if any at all) than the original.

And if you upgrade your Ubuntu at any point, you will get these updates anyway, therefore you are not really cluttering anything up as such.

BUT, like cgroza said, it's good practice.

---

### Post by aeronutt on 2011-09-11
I'll take a quick visual scan of the updates, but 99.9% of the time, I install all. Certainly if there's any doubt, I default to install. One exception may be if you have 'show new distrobution releases' turned on. I always turn that off.

---

### Post by Paqman on 2011-09-11
> **johnsmoke said:**
> I just don't want to bloat my PC with tons of things.

Most of the updates you get sent are just new versions of things you already have. The amount of extra space taken will be very small, and the new versions might even be slimmer than the old ones.

The exception to this is new kernels, which are big and will take up space. However, you can safely remove old kernels that you don't use.

You can also empty the package manager's cache with the following command:
```

sudo apt-get autoclean

```
This will get rid of any old packages left over from previous updates. It will keep a copy of the latest package for everything you have on your system, so that you can reinstall without having to download it again, should you need to.

---

### Post by Rex Bouwense on 2011-09-11
You already have some good advice in the previous four posts.  I too typically look at the updates and then proceed to install them all.  The biggies usually replace biggies on your hard drive so you seldom get bloated.  :popcorn:

---

### Post by candtalan on 2011-09-11
Ubuntu and the like are not going to try to make money from you, like some other PC systems, so it is unlikely that updates will cause you any regret, only advantage. I have never found cause to hold back Ubuntu updates.

---

### Post by 3rdalbum on 2011-09-11
[IMG]http://troll.me/images/x-all-the-things/x-all-the-things.jpg[/IMG]

**Apply ALL the updates!**

---

### Post by madjr on 2011-09-11
u sum it up well :p

---

### Post by alphacrucis2 on 2011-09-11
Even in the Windows case. Install the updates. Leaving a windows workstation unpatched is asking for trouble.

---

### Post by madjr on 2011-09-12
> **alphacrucis2 said:**
> Even in the Windows case. Install the updates. Leaving a windows workstation unpatched is asking for trouble.

specially windows

---

### Post by 3rdalbum on 2011-09-12
> **madjr said:**
> specially windows

To be fair, not especially Windows. Who can forget that bug in (I think it was) Ubuntu 8.10 where you'd eject a CD and it would immediately suck the disc back in again? That was fixed in a post-release update. For a while afterward people were still reporting the problem on the forum because they hadn't run the updates.

---

### Post by madjr on 2011-09-12
> **3rdalbum said:**
> To be fair, not especially Windows. Who can forget that bug in (I think it was) Ubuntu 8.10 where you'd eject a CD and it would immediately suck the disc back in again? That was fixed in a post-release update. For a while afterward people were still reporting the problem on the forum because they hadn't run the updates.

i was referring to windows specially for security reasons.

as for ubuntu there are always bugs after release, which eventually get fixed, but would be better if they would avoid most of them all together if they made [some changes]("http://netsplit.com/2011/09/08/new-ubuntu-release-process/")

---

### Post by 3rdalbum on 2011-09-12
> **madjr said:**
> i was referring to windows specially for security reasons.

as for ubuntu there are always bugs after release, which eventually get fixed, but would be better if they would avoid most of them all together if they made [some changes]("http://netsplit.com/2011/09/08/new-ubuntu-release-process/")

Interesting idea, but it sounds like developers will have even less time to work on the things that they're developing. How much time will it take to manage an alpha branch, beta branch, and release branch? Who would use the beta branch when releases are only a month apart? I'm not sure I would, and I love booting up and finding new features :-)

I think just getting rid of the "this feature MUST land in this version" attitude would be enough to fix the problem. Also, I think UDS could be streamlined a bit so it doesn't take so much time and get everyone so worn out.

I'm no developer, my biggest contributions to Ubuntu are bug reports and help on the forums, but I can't quite see how "release once a month" will cause fewer problems than "release every two years" or "release every six months".

---

### Post by madjr on 2011-09-12
> **3rdalbum said:**
> Interesting idea, but it sounds like developers will have even less time to work on the things that they're developing. How much time will it take to manage an alpha branch, beta branch, and release branch? Who would use the beta branch when releases are only a month apart? I'm not sure I would, and I love booting up and finding new features :-)

I think just getting rid of the "this feature MUST land in this version" attitude would be enough to fix the problem. Also, I think UDS could be streamlined a bit so it doesn't take so much time and get everyone so worn out.

I'm no developer, my biggest contributions to Ubuntu are bug reports and help on the forums, but I can't quite see how "release once a month" will cause fewer problems than "release every two years" or "release every six months".

not totally sure either but the person proposing it is a developer and involved with canonical, so he should know more than most if it would work better than what we have now.

Still they need to look at all the other pros/cons and fine tune it. But at least is good to see they have identified and are working on this problem (which might or might not be the exact proposal).

---

### Post by JKyleOKC on 2011-09-13
> **johnsmoke said:**
> There seems to be many updates available when the Update Manager icon appears in the launcher. Which do you guys usually install? All of them? Or just some necessary security updates? I just don't want to bloat my PC with tons of things. I always turned off the Automatic Updates when I was Windows.You've received lots of good advice, but there's one point everyone seems to have overlooked. My copy of Update Manager has two different icons that can appear: one is the orange arrow and the other, also orange, looks like a gear wheel to some extent. The arrow indicates critical security updates are available; the gear tells me that updates are available but are only recommended, not security-related.

I always scroll through the list of updates, for either icon. It's divided into two categories, "security" and "recommended," but only one groups might be present; it all depends on what's in that batch. Almost always I'll install all of the security updates. For the recommended group, I may hold off a bit, especially if I'm working on a project that can't afford much down time in case the update farkles something it needs.

If there's a new kernel, I may wait a day or two to see if it has any major bugs -- or even wait until I can spend a day or so customizing it if need be. But I usually do install them all, eventually,

---

### Post by oscarivera9 on 2011-09-13
Install, install, install.... I also read through to see what I'm updating but usually I go for everything.  Even if it does end up taking too much space, when a new release comes out (like next month for example), your system will be renewed anyway.  What I mean by that is that when you upgrade to say Ubuntu 11.10 (Oneiric Ocelot), part of the upgrading process will involve getting rid of stuff you don't need.  All of this will be done automatically, while you're either away from the computer or working on the computer on whatever else you want, just like any other update.

---


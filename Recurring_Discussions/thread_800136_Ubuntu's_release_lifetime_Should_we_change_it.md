---
title: "Ubuntu's release lifetime: Should we change it?"
date: 2008-05-19
forum: Recurring Discussions
---

### Post by Luke has no name on 2008-05-19
[[IMG]http://brainstorm.ubuntu.com/idea/8831/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/8831/)

**Introduction:**

As it stands, Ubuntu/Canonical is supporting FOUR releases of Ubuntu at a time, plus developing a new release (Plus managing desktop/server related development separately). 

[img]http://www.ubuntu.com/files/server/LifeCycle.png[/img]

**Question:**

Should we consider, for the sake of focus, limiting official support to the "current" release, plus active LTS releases?

**Implementation:**

**Edit:** The following paragraph is a concise, altered version of my proposal.

*What I am suggesting might well be getting rid of the set releases altogether, adnd move to a rolling release for all but LTS. Every 2-3 years, an LTS will come out that is stable, and will have quarterly updates for its lifetime. Meanwhile, development will be nonstop on the rolling release, until a time (2 months?) before an LTS, at which point all focus goes to clean-up, stability, error-reporting, etc.*

-Keep the current scheme/timeframe of LTS. Have point releases every 3 - 6 months. LTS releases will get more attention, and will be updated quarterly/semi-annually with necessary security/stability updates.

-Support a standard release only as long as it is the latest release. For example, we wouldn't be supporting 7.10 anymore, if this were the case. Of course, the repos would still be available, but official updates would cease. 

List of active releases (**[color=blue]Blue [/color]** = As per this proposal,  **[color=blue]Blue [/color]** +  **[color=red]Red[/color]** = Current schedule):

Current (May 2008 )
- [color=blue]6.06 LTS[/color]
- [color=red]7.04[/color]
- [color=red]7.10[/color]
- [color=blue]8.04 LTS[/color]
- [color=blue]Development (8.10)[/color]

January 2009 (8.10 has been released)
- [color=blue]6.06 LTS[/color]
- [color=red]7.10[/color]
- [color=blue]8.04 LTS[/color]
- [color=blue]8.10[/color]
- [color=blue]Development (9.04)[/color]

May 2009 (9.04 has been released)
- [color=blue]6.06 LTS[/color]
- [color=red]7.10[/color]
- [color=blue]8.04 LTS[/color]
- [color=red]8.10[/color]
- [color=blue]9.04[/color]
- [color=blue]Development (9.10)[/color]

As you can see, this would trim down the workload by one, if not two, release cycles.

**Effects:**

# Developers would have less to deal with, as there are 20-50% fewer software versions to maintain.

# Ubuntu would shift to more of a rolling release with stable snapshots. this would allow more focus on deevlopment and error-correction (aka bug eradication) while maintaining the high quality and stability of the LTS releases.

**Conclusion:**

Ubuntu and its users would benefit from trimming down the release support list by having a decreased workload and increased focus on stability of LTS and development of upcoming releases.

---

### Post by madjr on 2008-05-19
**Not a bad idea**. We all want the workload the go down and i would like LTS to be similar to a rolling release.

hmm, i didn't understand too much the blue and red text.

am no expert on releases, so someone should point out which flaws this strategy might have (all strategies always have some kind of flaw).


**anyway, the best thing we can do is create a [COLOR="RoyalBlue"]fail-proof[/COLOR] [COLOR="DarkOrange"]upgrade/test method[/COLOR], that allows [COLOR="Sienna"]reverting back[/COLOR] if there's some kind of problem.** (similar to unetbootin)

if we want to cut back on older releases, then we need to make sure people have upgraded easily and trouble-free.

---

### Post by ice60 on 2008-05-19
i think ubuntu should stay as it is, but there should be a new version - **[size=4][color=#13355F]Ubuntu Rolling Release[/color][/size]**

i'm totally serious, i don't use ubuntu, and the thing i dislike most about it is the 6 month release cycle! i don't know what the best solution could be, (but i don't agree with only supporting the current release!) could a rolling release be as stable as the default ubuntu? i think someone should do Ubuntu Rolling Release!

**[color=#135F3A]EDIT:[/color]** i can't believe madjr mentioned a rolling release too! lol it's something i've been thinking about for a few weeks. has it been mentioned before?

---

### Post by Thirtysixway on 2008-05-19
Well don't we want older versions [7.10 isn't that old] to be supported?  Some users can't switch or don't have a need to.  Let's not leave them out in the cold just because 4 releases seems like a lot.

---

### Post by jrusso2 on 2008-05-19
I think the best thing to do is only have LTS releases.  Those would be done the same as they are now.

In between would be the beta's for the next LTS release so people could run those if they wanted bleeding edge.  The beta's for the LTS release would be a rolling release until the code is locked to being the process of final testing for the LTS release.

So you would have a choice.  LTS release where you just ran that and it was stable and updated during the period until the next LTS release.

Or the beta rolling release for those that like the new stuff and new features being evaulated for the next LTS. release.

This would provide two things.

A larger group of beta testers and a longer period of testing to work out bugs and give the developers a longer time to fix things.

A year before the LTS release you would lock the code and just work on bug fixes and stability for that year.

---

### Post by SunnyRabbiera on 2008-05-19
Yes, as ubuntu has just been too experimental as of late.
Its actually put the mental in experimental

---

### Post by madjr on 2008-05-19
> **jrusso2 said:**
> I think the best thing to do is only have LTS releases.  Those would be done the same as they are now.

In between would be the beta's for the next LTS release so people could run those if they wanted bleeding edge.  The beta's for the LTS release would be a rolling release until the code is locked to being the process of final testing for the LTS release.

So you would have a choice.  LTS release where you just ran that and it was stable and updated during the period until the next LTS release.

Or the beta rolling release for those that like the new stuff and new features being evaulated for the next LTS. release.

This would provide two things.

A larger group of beta testers and a longer period of testing to work out bugs and give the developers a longer time to fix things.

A year before the LTS release you would lock the code and just work on bug fixes and stability for that year.

+1

sounds good. **an LTS (+ service packs) and a beta rolling release** :)

we shouldn't force hardware vendors to upgrade the OS every 6 months either.

As Ubuntu becomes more mainstream, people will stick with really old versions (they got it pre-installed and things work, no need to upgrade).

i.e.: in the year **2014** some people or companies might still be using Hardy **8.04** instead of upgrading to **14.04**

---

### Post by LaRoza on 2008-05-19
> **madjr said:**
> 
we shouldn't force hardware vendors to upgrade the OS every 6 months either.

They aren't forced. They can stick with LTS and go every three years if they wish. That is the point of LTS, for those that don't want to upgrade every 6 months.

Ubuntu's release schedule is a recurring topic. Most schemes have their benefits and draw backs. Use what you want.

---

### Post by Kinst on 2008-05-19
This is ubuntu. Ubuntu exists as a fork of Debian testing, polished and ubuntu styled every 6 months.

There's no way ubuntu could do rolling snapshots of debian, nor is there a point to it.

If you really want a rolling ubuntu, well, that's what debian testing is I guess.

---

### Post by ice60 on 2008-05-19
> **Kinst said:**
> This is ubuntu. Ubuntu exists as a fork of Debian testing, polished and ubuntu styled every 6 months.

There's no way ubuntu could do rolling snapshots of debian, nor is there a point to it.

If you really want a rolling ubuntu, well, that's what debian testing is I guess.
i hadn't thought about ubuntu's relationship with debian when i thought of a rolling release, i suppose i'll have to use debian or arch then!

---

### Post by madjr on 2008-05-19
> **Kinst said:**
> This is ubuntu. Ubuntu exists as a fork of Debian testing, polished and ubuntu styled every 6 months.

There's no way ubuntu could do rolling snapshots of debian, nor is there a point to it.

If you really want a rolling ubuntu, well, that's what debian testing is I guess.

Ubuntu is ahead of debian and has more software in the repos.

Ubuntu could make it's own rolling release, it doesn't need debians permission or approval.

the point is to cut back on supported versions.

the 6 months cycle could be used for upgrade/service packs for the LTS. Ubuntu would get the same press and decrease bugs at same time.

---

### Post by cardinals_fan on 2008-05-19
I think that there should only be two (well... sort of three) releases at a given time - RELEASE, CURRENT, SNAPSHOT.  RELEASE is for enterprise/stability-minded users, with only the most thoroughly tested software.  CURRENT provides more up-to-date software, with a few bugs.  And SNAPSHOT would be the latest of everything (probably continually broken to some extent).

The nice thing about this is that the releases build on one another.  Once apps are tested in SNAPSHOT, they move to CURRENT, then to RELEASE.  All three could be rolling release - just at different places along the curve.

---

### Post by Jon Monreal on 2008-05-19
I think that Ubuntu's release cycle is very good as it is. It is nice that users can upgrade every 6 months to a new release. I do, however, agree that it would be better to minimize the amount of versions that developers have to maintain.

And it would also benefit Ubuntu to have releases with few bugs for new users getting used to Ubuntu. If it doesn't just work, they are more liable to switch back to what they were using before, even if the problem would be easy to fix. At the same time, I think it should be considered that if the current release that many people would use were to fall behind compared to other operating systems and distributions, this could be a problem. However, I don't think this would be too much of a concern with one release every year.

Users who want bleeding-edge software should also be able to easily perform an update. At the same time, there should be something in place to make sure the users who would not benefit from this do not end up with one of these releases accidentally.

If we are really serious about being Linux for Human Beings, a distribution that everyone can use, I think that we should take this idea into serious consideration. Doing so would lessen the work that developers have to do, allow them to concentrate on eliminating bugs in the code, and therefore be even more polished before the user ever touches it.

---

### Post by Kinst on 2008-05-20
> **madjr said:**
> Ubuntu is ahead of debian and has more software in the repos.

Ubuntu could make it's own rolling release, it doesn't need debians permission or approval.

Yeah, but when they make a new ubuntu, they don't make it out of the old ubuntu, they recreate it from scratch using debian. 

So if they had a rolling version, all of it would just be discarded anyways every 6 months, and that's not really rolling yeah?

---

### Post by aysiu on 2008-05-20
> **cardinals_fan said:**
> I think that there should only be two (well... sort of three) releases at a given time - RELEASE, CURRENT, SNAPSHOT.  RELEASE is for enterprise/stability-minded users, with only the most thoroughly tested software.  CURRENT provides more up-to-date software, with a few bugs.  And SNAPSHOT would be the latest of everything (probably continually broken to some extent). How is this proposal different from what Debian currently does with Stable, Testing, Unstable, Experimental?

---

### Post by cardinals_fan on 2008-05-20
> **aysiu said:**
> How is this proposal different from what Debian currently does with Stable, Testing, Unstable, Experimental?
It's not.  Anything wrong with that?

---

### Post by aysiu on 2008-05-20
> **cardinals_fan said:**
> It's not.  Anything wrong with that?
Yeah, it means not having a new release for four or five years at a time sometimes.

I kind of like Ubuntu's regular release cycles.

---

### Post by Luke has no name on 2008-05-21
> **aysiu said:**
> Yeah, it means not having a new release for four or five years at a time sometimes.

I kind of like Ubuntu's regular release cycles.

No, my proposal doe NOT adjust the release schedule, it adjusts the SUPPORT LIFETIME in such a way as to utilize the regular releases more like a "work in progress", and the LTS for those who want more stability. Let me say it again:

**Releases will still be regular, development would be at the same pace. LTS would get point releases quarterly, regular releases would lose support once the next release comes out.**

> **Jon Monreal said:**
> And it would also benefit Ubuntu to have releases with few bugs for new users getting used to Ubuntu. 

That's how good software should be released, not just for those who dno't know as much. Errors in software should be eradicated to the greatest extent possible, and I don't think Ubuntu is devoting enough resources to doing this.

---

### Post by 23meg on 2008-05-22
[QUOTE=madjr]Ubuntu is ahead of debian and has more software in the repos.

Ubuntu could make it's own rolling release, it doesn't need debians permission or approval.[/QUOTE]

And you don't need Ubuntu's permission or approval to do a "rolling Ubuntu". If you think it's a good idea, just do it. Having a crude implementation is usually a good way to see if something is *actually* a good idea.

---

### Post by Jon Monreal on 2008-05-25
> That's how good software should be released, not just for those who dno't know as much. Errors in software should be eradicated to the greatest extent possible, and I don't think Ubuntu is devoting enough resources to doing this.

I agree completely. I think that many things about Ubuntu have helped to make up for this by keeping it ahead of the pack, and that's why I say that experienced users will tolerate it. But you are ultimately right, more time and resources should be spent on eliminating bugs, and a plan like this could help free up those resources.

---

### Post by dfwlinuxguy on 2008-08-04
No changes please. 8.04 is a mess. I can't believe it was released as a LTS. I had to give up and go back to 7.10. I hope they get it all worked out soon. I do have sympathy for the developers, but unless you can give me something that works just as good or better than the previous release, I argue that updating the previous version on the current schedule is absolutely necessary.

---


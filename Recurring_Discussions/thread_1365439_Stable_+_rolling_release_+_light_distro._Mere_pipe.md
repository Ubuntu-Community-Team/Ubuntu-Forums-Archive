---
title: "Stable + rolling release + light distro. Mere pipe-dream?"
date: 2009-12-27
forum: Recurring Discussions
---

### Post by etnlIcarus on 2009-12-27
I'm all ears, if anyone's got any recommendations.

I was eager to move to Arch, until I installed it. It's incredibly fast, light on RAM usage and Pacman proved to be a decidedly pleasant package manager (although it *really* needs autocompletion) - it's just the sheer instability/brokenness of the OS that put me off.

Similarly, I've gone the Debian Unstable/Sid route before and while less broken than Arch, the never-knowing-if-it's-going-to-boot nature of the OS really doesn't make it ideal, now that I actually need my PC to do something productive. Plus performance-wise, it's as sluggish as Ubuntu.

Someone recently recommended to me Sidux which looked promising at first: based on Debian Sid but obviously somewhat less bleeding edge; optimised for 686+ processors. Only problem is it's by no means light: there's no base install option, you either install a heavily-packed Xfce or KDE desktop.

Also need to disclaim that Debian Testing is not what I'm looking for, either, since it's not really a rolling release; routinely going into feature-freezes and eventually 'upgrading' itself to Stable.

So, does a minimal, (reasonably) stable, rolling-release distro with a decent package manager actually exist, or am I hoping for too much?

Cheers in advance.

---

### Post by gnomeuser on 2009-12-27
You can look at Foresight, it has the rolling part down to an art at least but I don't think I'l use the words stable nor "light" (even if it does have low RAM usage, because when Conary is running nothing else happens)

---

### Post by AllRadioisDead on 2009-12-27
Sidux?

---

### Post by SuperSonic4 on 2009-12-27
Stable and Rolling Release are largely incompatible. PCLOS may work

---

### Post by ynnhoj on 2009-12-27
gentoo?

what sorts of problems were you having with arch, anyhow? i've been using it fairly extensively for a few years now with no stability issues. but maybe my computing needs are different (less demanding) than yours?

---

### Post by pwnst*r on 2009-12-27
> **ihermit said:**
> Sidux?

lol. drink your coffee.

---

### Post by markp1989 on 2009-12-27
> **ynnhoj said:**
> gentoo?

what sorts of problems were you having with arch, anyhow? i've been using it fairly extensively for a few years now with no stability issues. but maybe my computing needs are different (less demanding) than yours?

the op might be having the same problem as me right now , xserver randomly crashing after a update/fresh instal, should be fixed soon i hope 

op: you may want to check you slitaz it has an eee specific version , and two releases, one rolling, and one stable

---

### Post by etnlIcarus on 2009-12-27
> **SuperSonic4 said:**
> Stable and Rolling Release are largely incompatible. PCLOS may work
Well there's no reason why they're mutually exclusive, the release model just tends to be informed by the goals of the project. Debian Testing would prove the point, were it's existence not solely for the purpose of creating a static release.

> what sorts of problems were you having with arch, anyhow? i've been using it fairly extensively for a few years now with no stability issues. but maybe my computing needs are different (less demanding) than yours?
Ugh, lets see. 

The installed base system was broken (fstab, I think).
Grub is half-broken (seems to ignore half of it's own menu.lst settings).
DRI for my RV350 is broken, even after attempting to disable (none of the arch wiki instructions for disabling KMS worked; ended up finding the answer on launchpad, oddly enough) KMS a myriad of ways (meaning no Compiz or video overlays).
Qt4 was half broken (would crap-out when using half of it's engines, incl. Gtk).
Gtk was buggy, with GtkMenus behaving like basic xlib menus; having to hold-down the mouse button to keep them open.
Policykit didn't seem to be entirely all-there.
Useradd and usermod weren't adding my users to groups properly. 

Phew, this is going back a couple of months, now. There were probably other things I'm forgetting. Oh yeah, couldn't get ALSA working; at some point after I gave up trying, it then decided to start working all by itself. Go figure.

---

### Post by cascade9 on 2009-12-27
> **etnlIcarus said:**
> Also need to disclaim that Debian Testing is not what I'm looking for, either, since it's not really a rolling release; routinely going into feature-freezes and eventually 'upgrading' itself to Stable.

I _think_ that you can change the repos from (currently) 'squeeze' to 'testing' and then you dont get the 'my testing just became stable' problem, but that is not going to help with the freezing. As for why its just 'think', I'm never bothered trying, mainly because once the freeze is over, I can just d/l the newer version of debian testing and reinstall. 

I dont think its a pipe dream, to be honest. There isnt any reason why someone cant make a rolling release that is stable. Just nobody I know of has done it yet. All the rolling release distros I know of concentrate far more on being 'bleeding edge' and dont worry so much, if at all, about stability. 

I'm sure that there are many other people who have similar ideas to you.....if such a distro was built, then the users would come, IMO. I'd like to have a go at something like that myself.

---

### Post by Xbehave on 2009-12-27
> Well there's no reason why they're mutually exclusive, the release model just tends to be informed by the goals of the project.
Yes they are.
stable(doesn't crash) == Lots of testing of a give package combination == stable(unchanging) packages
rolling release == unstable(changing) packages

If you care more about stability than currentness, then try:
Fedora with backports enabled
Ubuntu with the relevant ppas
Debian testing + pull in relevant sid packages when you want them (e.g latest firefox,ect)

If you care more about currentness than stablity, then AFAIK arch is the most current distro

Personally I recommend ubuntu+ppas, because I'm running a fairly current system (2.6.32.0+xorg 7.6 with very recent mesa/drm/drivers+kde4.4beta2) and I've had no serious problems due to it and no it seams like a lot less hassle than the same setup on arch/gentoo

---

### Post by meho_r on 2009-12-27
If you want the best what can be given from "stability" + "rolling release", I'm afraid you'll end up with Gentoo.

---

### Post by mickie.kext on 2009-12-27
> **etnlIcarus said:**
> 
Qt4 was half broken (would crap-out when using half of it's engines, incl. Gtk).


Did you used KDEmod or classic KDE? KDEmod is somewhat better:).

---

### Post by etnlIcarus on 2009-12-27
> **Xbehave said:**
> Yes they are.
stable(doesn't crash) == Lots of testing of a give package combination == stable(unchanging) packages
rolling release == unstable(changing) packagesThat's just fundamentally wrong.

> If you care more about stability than currentness, then try:
Fedora with backports enabled
Ubuntu with the relevant ppasI've already got a few PPAs enabled on 9.04 and it starts to get messy. Besides most of them not having seen a single update since Karmic's release, ones like the Xfce 4.6.1 PPA have actually gone dead. You do run into the odd conflict, also.

> **mickie.kext said:**
> Did you used KDEmod or classic KDE? KDEmod is somewhat better:).I didn't use KDE at all. I use VLC and VirtualBox. For them, I need the Qt4 base libs.

---

### Post by snowpine on 2009-12-27
Arch sounds exactly like what you're looking for... next time, try harder. ;)

Seriously, though, "stable" and "rolling release" are, by definition, mutually exclusive. You can't have both. 

The closest would be something like MEPIS: Debian Stable with rolling applications (like Firefox). Have you tried it?

Oh yes, and then there is UBUNTU... it is not rolling release, but it is a wonderful, relatively up-to-date, stable, user-friendly distro... check it out if you haven't taken it for a test drive yet. :)

---

### Post by etnlIcarus on 2009-12-27
> Seriously, though, "stable" and "rolling release" are, by definition, mutually exclusive.If only cursory fact-checking and facepalming weren't mutually exclusive...

---

### Post by snowpine on 2009-12-27
> **etnlIcarus said:**
> If only cursory fact-checking and facepalming weren't mutually exclusive...

'Scuse me? Rolling release is *by definition* unstable. A stone that is "rolling" down a hill is, by definition, "not stable." See?

In other words, to answer the original question, "Yes, it is a mere pipe dream."

---

### Post by SmittyJensen on 2009-12-27
> **snowpine said:**
> 'Scuse me? Rolling release is *by definition* unstable.

**In other words, to answer the original question, "Yes, it is a mere pipe dream."**
No it's not.

PCLINUXOS! try it you might like it. rolling release but only when it's ready

---

### Post by Xbehave on 2009-12-27
> **etnlIcarus said:**
> That's just fundamentally wrong.
Care to explain? How am I wrong? They **are** mutually exclusive because a stable system has to be stable (unchanging), being a dick to those who disagree with doesn't change that, you will fit better in with a certain arch user though.

---

### Post by sertse on 2009-12-27
Ubuntu with backports enabled + ppas + getdeb. (Though I think this is your current setup :P )

Aside from Arch's aur "repo", I think Ubuntu's ppa system has the largest collection of packages for finding an updated version of whatever you want. The level of "rolling" is limited to the applications the PPAd you enabled offers. The rest is left "stable".

---

### Post by snowpine on 2009-12-27
> **Xbehave said:**
> Care to explain? How am I wrong? They **are** mutually exclusive because a stable system has to be stable (unchanging), being a dick to those who disagree with doesn't change that, you will fit better in with a certain arch user though.

+1; the OP has had a whole bunch of good suggestions (Foresight, Sidux, PCLinuxOS, Gentoo, Ubuntu, Mepis, SliTaz, Debian Testing, Arch) and not a single response except to insult the people trying to help. :(

---

### Post by Uncle Spellbinder on 2009-12-27
> **sertse said:**
> Ubuntu with backports enabled + ppas + getdeb...

+1

This is my Karmic setup, and I'm VERY happy.

---

### Post by markp1989 on 2009-12-27
ubuntu isnt really all that light though, even minimal install is still heavy when compared to arch etc,

---

### Post by Hallvor on 2009-12-27
> **etnlIcarus said:**
> I'm all ears, if anyone's got any recommendations.

I was eager to move to Arch, until I installed it. It's incredibly fast, light on RAM usage and Pacman proved to be a decidedly pleasant package manager (although it *really* needs autocompletion) - it's just the sheer instability/brokenness of the OS that put me off.

Similarly, I've gone the Debian Unstable/Sid route before and while less broken than Arch, the never-knowing-if-it's-going-to-boot nature of the OS really doesn't make it ideal, now that I actually need my PC to do something productive. Plus performance-wise, it's as sluggish as Ubuntu.

Someone recently recommended to me Sidux which looked promising at first: based on Debian Sid but obviously somewhat less bleeding edge; optimised for 686+ processors. Only problem is it's by no means light: there's no base install option, you either install a heavily-packed Xfce or KDE desktop.

Also need to disclaim that Debian Testing is not what I'm looking for, either, since it's not really a rolling release; routinely going into feature-freezes and eventually 'upgrading' itself to Stable.

So, does a minimal, (reasonably) stable, rolling-release distro with a decent package manager actually exist, or am I hoping for too much?

Cheers in advance.


Perhaps PCLXDE would be your best bet.
-It uses LXDE and is quite light.
-Rolling release.
-Nice compromise between stable and bleeding edge.
-You use apt and Synaptic.
-Easy to use.

---

### Post by ~sHyLoCk~ on 2009-12-27
Slackware-current -> Stable +rolling+light

whatddya' they do exist!:)

Seriously -current branch is more stable than those rolling distros which claim to be stable. 
Light-> That doesn't depend on a distro imho, but onyour DE/WM. Using fluxbox and musca atm, I like having options, so have KDE, Xfce, blackbox,windowmaker, etc.. installed as well, I switch when I want to.

---

### Post by Zoot7 on 2009-12-27
> **~sHyLoCk~ said:**
> Slackware-current -> Stable +rolling+light

whatddya' they do exist!:)

Seriously -current branch is more stable than those rolling distros which claim to be stable. 
Light-> That doesn't depend on a distro imho, but onyour DE/WM. Using fluxbox and musca atm, I like having options, so have KDE, Xfce, blackbox,windowmaker, etc.. installed as well, I switch when I want to.
+1 for Slackware. I've it set up with Xfce 4 at the moment, and it's a good bit lighter and nippier than Ubuntu IMO.
Also it's very stable, the only downside is having to compile most stuff from source which is a bit time consuming at times.

Gentoo is another one to consider, very stable and very quick/light (in my experience) but ***very*** time consuming.

---

### Post by etnlIcarus on 2009-12-27
> **snowpine said:**
> 'Scuse me? Rolling release is *by definition* unstable.Unless you're actually prepared to claim an Etymological fallacy, which would be almost ridiculous, *no it is not*.

> A stone that is "rolling" down a hill is, by definition, "not stable." See?You seem to be confusing *allegory* with, "definition". Stable refers to software that has been reasonably tested; not static release cycles and certainly not, "stones". There is absolutely nothing in the rolling release model that precludes an experimental/testing branch or repo, with changes fed-back into the stable branch/repos, as the developers are confident that there isn't going to be major breakage. In fact, Arch, the belle of the rolling-release ball, already has something like this; they're just not as cautious about feeding changes back into the main sync databases, as they could be.

> **Xbehave said:**
> Care to explain? How am I wrong?Your reasoning in no way established exclusivity; rather, it was just a false dilemma.

> **snowpine said:**
> +1; the OP has had a whole bunch of good suggestions (Foresight, Sidux, PCLinuxOS, Gentoo, Ubuntu, Mepis, SliTaz, Debian Testing, Arch) and not a single response except to insult the people trying to help. :(
Insult? Really? Well there goes your high ground.

Anyway, I think I've got a few more ideas about where to look now. Thanks again, folks. Now can someone lock this thread before someone accuses me of killing puppies? :p

---

### Post by Pogeymanz on 2009-12-27
Looks like you are looking for SimplyMEPIS and PCLinuxOS.

Sorry you had such a crappy time on Arch. Some of the problems you listed sound like installation mistakes, but some of them just sound bizarre. Anyway, good luck.

---

### Post by ~sHyLoCk~ on 2009-12-27
> **snowpine said:**
> 'Scuse me? Rolling release is *by definition* unstable. A stone that is "rolling" down a hill is, by definition, "not stable." See?

In other words, to answer the original question, "Yes, it is a mere pipe dream."

Not really. Rolling doesn't mean it will be unstable, it's the development teams' fault for not testing the softwares well enough. Gentoo -stable branch is quite stable, plus it's rolling. There are many. Slackware -current is also very stable.

---

### Post by samjh on 2009-12-27
Yet again, we have a definition problem.

From a life-cycle point of view, "stable" tends to mean limited change: changes are limited to security fixes and critical bug fixes.  From a systems engineering point of view, "stable" means predictable reliability: failures are unlikely, and likely failure cases have been tested thoroughly enough to be mitigated.

For general usage, I much prefer to use the term "reliable" to mean software that has been thoroughly tested and patched for bugs, and is unlikely to crash.

The OP means "stable" as in "reliable".

As for stable (reliable) + rolling release + light distro being a pipe dream, it isn't so.  Gentoo, PCLinuxOS, Sidux, Arch, and some others are reasonably reliable despite being rolling-releases.  The differences lie in convenience and size.  Arch is perhaps the lightest and most transparent of them all, while PCLinuxOS is the heaviest and most opaque.  Gentoo requires a lot of fiddling, such as self-compilation of all software packages.  Sidux tends to have its high and low points in terms of software reliability -- it's a somewhat tamed Debian Sid, and like Arch, one should be prepared to face problems.

I use Arch, and have found it quite reliable.  I've suffered only one of the problems mentioned by the OP, which is the xserver crash, but have since fixed it.  The OP seems to suffer a lot of unique problems not faced by any other Arch user, so with all due respect to the OP, it seems at least some of those faults are his own making.

---

### Post by unknownPoster on 2009-12-27
> **samjh said:**
> 

I use Arch, and have found it quite reliable.  I've suffered only one of the problems mentioned by the OP, which is the xserver crash, but have since fixed it.  The OP seems to suffer a lot of unique problems not faced by any other Arch user, so with all due respect to the OP, it seems at least some of those faults are his own making.

I definitely agree. I have used Arch regularly for the past year or so, the past 6 months of which I have run the [testing] repository. 

During this time, I've only encountered one issue, a Xorg problem when the issue with device hot plugging came up.

Honestly, I've found Arch to be more reliable than most other "regular" release distributions, including Ubuntu, Fedora, and openSUSE.

---

### Post by etnlIcarus on 2009-12-28
> The OP seems to suffer a lot of unique problems not faced by any other Arch userI wouldn't say that. Where the wiki fell short, there appeared to be just as much information on the forums, from people with similar issues.

> so with all due respect to the OP, it seems at least some of those faults are his own making.I wouldn't rule out the possibility, although I'm a pretty well-versed user, who's dealt with base and unstable installs before. There's no good reason why I should have had 3/4 of the problems I did. You want to be careful, here: Ubuntu users seem to struggle equally with the concept of 'results may vary'.

---

### Post by Twitch6000 on 2009-12-28
I would go with Debain Testing Or PCLOS.

They are probably the most stable rolling release distros I have used.

Now OpenSuse isn't exactly a rolling release,but it does have a 8 month release cycle.

---

### Post by ~sHyLoCk~ on 2009-12-28
> Now OpenSuse isn't exactly a rolling release,but it does have a 8 month release cycle.

To be more fair, any distro can be used on rolling basis. In Suse use Factory repos, in Mandriva use cooker, in Fedora use rawhide etc.  Obviously stability is out ofquestion.

---

### Post by snowpine on 2009-12-28
> **etnlIcarus said:**
> Unless you're actually prepared to claim an Etymological fallacy, which would be almost ridiculous, *no it is not*.

You seem to be confusing *allegory* with, "definition". Stable refers to software that has been reasonably tested; not static release cycles and certainly not, "stones". There is absolutely nothing in the rolling release model that precludes an experimental/testing branch or repo, with changes fed-back into the stable branch/repos, as the developers are confident that there isn't going to be major breakage. In fact, Arch, the belle of the rolling-release ball, already has something like this; they're just not as cautious about feeding changes back into the main sync databases, as they could be.


I think the word you're looking for is "reliable." A well-designed "unstable" (aka "rolling release") distro might be more "reliable" than a poorly-designed "stable" distro. But, the reversal is not true: No matter how "reliable" Debian Sid may become, it would be incorrect to call it a "stable" distro. As rolling release, it is inherently "unstable" and therefore called "Debian Unstable" instead of "Debian Stable."

---

### Post by etnlIcarus on 2009-12-28
Ugh, now you're just blatantly conflating different terms. Why do I never remember to bookmark facepalm.jpg. I must've uploaded it a good half-dozen times by now...

---

### Post by Tibuda on 2009-12-29
It depends on how you define "stable".

If "stable" means "freezed" (the packages versions are stable), then a "stable" distro can't be rolling-release by definition.

If "stable" means "reliable" (the packages are tested before released), there's no trade-off. I think this is etnlIcarus dream.

---

### Post by saulgoode on 2009-12-29
> **danielrmt said:**
> If "stable" means "reliable" (the packages are tested before released), there's no trade-off. I think this is etnlIcarus dream.
All other things being equal, there is no way that packages of a rolling distro can be as thoroughly tested as those based upon stable releases. A stable-release distro only needs to check one version of a particular package for interoperability with one particular version of each of the other related packages in that release. To attain the same level of confidence with a rolling-based distro, every combination of versions of interrelated packages would need to be tested against each other to the same degree.

---

### Post by etnlIcarus on 2009-12-29
> every combination of versions of interrelated packages would need to be testedI trust you're exaggerating. You would surely have a cut-off point, at which compatibility becomes a non-issue: a current release of package A would not need to be tested against interdependent package releases anymore than 6 months obsolete, at the most. I think you also need to have a closer look at the amount of work that goes into refining distros like Debian, or projects like the linux kernel, itself. You seem to be under the impression that 'no one could be bothered, if we actually had standards for releases'.

Seriously, some of the generic objections being raised: the uninitiated could easily be led to believe that the rolling release model as a whole were untenable - unstable, stable, or otherwise.

Anyway, I'm un-subscribing from this thread. At least someone had the good judgement to throw it in *Recurring*. Toodles.

---

### Post by saulgoode on 2009-12-29
> **etnlIcarus said:**
> I trust you're exaggerating. You would surely have a cut-off point, at which compatibility becomes a non-issue: a current release of package A would not need to be tested against interdependent package releases anymore than 6 months obsolete, at the most. 

So if the current release of package A isn't tested against last year's version (2.1) of library X -- instead it is expected that X is updated to the latest version (2.2) -- then what about package B which is interdependent with X but has no recent version available updated and tested against X 2.2? Either new package A is not tested against X 2.1 being on the system, or package B is not tested against new package X 2.2 being on the system.

---

### Post by Tibuda on 2009-12-29
> **saulgoode said:**
> So if the current release of package A isn't tested against last year's version (2.1) of library X -- instead it is expected that X is updated to the latest version (2.2) -- then what about package B which is interdependent with X but has no recent version available updated and tested against X 2.2? Either new package A is not tested against X 2.1 being on the system, or package B is not tested against new package X 2.2 being on the system.

Now think about your example in a freezed distro. Both packages A and B depends on library X, but in april (lucid release) only A is updated to use a new X version. The distro developers plans needs package A to be in the last versions, but there's no one interested in patching B. What to do? Remove B from the repositories?

---

### Post by snowpine on 2009-12-29
> **etnlIcarus said:**
> Ugh, now you're just blatantly conflating different terms. Why do I never remember to bookmark facepalm.jpg. I must've uploaded it a good half-dozen times by now...

Whose definition of the word "stable" should I believe, yours or the Debian developers? I'll agree with you when Debian Stable converts to rolling release, until then...

It's interesting you are unsubscribing from the thread you started instead of following the excellent advice you've been given. "Oh wow, Slackware, that's a good suggestion, thanks guys!" for example.

---

### Post by Tibuda on 2009-12-29
> **snowpine said:**
> Whose definition of the word "stable" should I believe, yours or the Debian developers? I'll agree with you when Debian Stable converts to rolling release, until then...

I suppose you trust Debian developers that "Debian Testing" is not unstable too, because it is not the same distro as "Debian Unstable".

---

### Post by snowpine on 2009-12-29
> **danielrmt said:**
> I suppose you trust Debian developers that "Debian Testing" is not unstable too, because it is not the same distro as "Debian Unstable".

I "trust" that Debian Testing is the testing ground for the next stable release (as its name would indicate).

---

### Post by ~sHyLoCk~ on 2009-12-29
I've heard Debian Testing is more stable than Unstable, is this true?

---

### Post by Zoot7 on 2009-12-29
> **~sHyLoCk~ said:**
> I've heard Debian Testing is more stable than Unstable, is this true?
I found it to be so in my experience. Debian Unstable is pretty cutting edge but true to its name it is quite unstable, I gave it shot for a few weeks, but having the OS not boot on me after batches of updates fairly often was a bit of a doozy.
Debian Testing I found to be fairly solid bar the odd few glitches here and there. I used it pretty much as my main OS for the 3 months before Debian Etch.

---

### Post by saulgoode on 2009-12-29
> **danielrmt said:**
> Now think about your example in a freezed distro. Both packages A and B depends on library X, but in april (lucid release) only A is updated to use a new X version. The distro developers plans needs package A to be in the last versions, but there's no one interested in patching B. What to do? Remove B from the repositories?
The two distros most recognized for their stability would not consider releasing "in April" if the release were not ready "in April". 

Nonetheless, if truly no one was willing to patch B and B did not work with the latest library then, yes, there seems little alternative for a distro that "needs package A" than to not ship package B -- by what reasoning would it make sense to ship a package that is known not to work?

---

### Post by snowpine on 2009-12-29
> **~sHyLoCk~ said:**
> I've heard Debian Testing is more stable than Unstable, is this true?

It is true, for part of the development cycle. Early in the cycle, Testing is fully rolling-release. But at a certain point (several months before planned release), Testing gets "frozen" so everyone can test for the next stable release. If you set your sources to "squeeze" you'll transition nicely into the stable release; if you set them to "testing" you'll go back to rolling release after the release date. Does that make sense?

Just to complicate things a bit, if by "stable" you mean "reliable", many Debian users feel that Unstable can be more reliable than Testing (for an everyday desktop user) *because* it is more unstable, therefore new packages that solve bugs or security issues arrive sooner. Many Debian users run a mixed testing/unstable system as a compromise. 

This is exactly why I'm a stickler for correct use of the word "stable." I want to make it clear there's no direct correlation between "rolling release/stable release" vs. "reliable/buggy." A well-designed "unstable" distro can be more "reliable" than a poorly-designed "stable" distro (and vice versa). Obviously I understand that "stable" may have a different definition in layman's terms. :)

---

### Post by ~sHyLoCk~ on 2009-12-29
Thanks snowpine and Zoot7 for the clarification.

Regards

---

### Post by Ylon on 2009-12-29
> **etnlIcarus said:**
> I'm all ears, if anyone's got any recommendations.


Ubuntu Karmic (updated) then:


```
apt-get install jwm menu
cp /usr/share/jwm/xsessions/Jwm.desktop /usr/share/xsessions/

```

Then try log in with the Jwm's WM


But you must be adult cos'.. it will be obscenely fast! :guitar::lolflag:

---

### Post by anticapitalista on 2009-12-29
If the OP is still around why not try antiX (or antiX-base)?
Debian Testing and MEPIS and a rolling release using icewm and fluxbox.

---

### Post by nrs on 2009-12-29
Yes. Old software is == stable software. That's why everyone is clamouring to use KDE 4.0 instead of 4.3/4.

---

### Post by kevCast on 2009-12-29
> **nrs said:**
> Yes. Old software is == stable software. That's why everyone is clamouring to use KDE 4.0 instead of 4.3/4.

?

4.0 was a development release of a new series in the KDE lineage.

A more appropriate analogy would be "That's why everyone is clamouring to use KDE 3.5 instead of 4.x." But that kind of contradicts the statement you were trying to make, so I can see why you avoided saying it.

---


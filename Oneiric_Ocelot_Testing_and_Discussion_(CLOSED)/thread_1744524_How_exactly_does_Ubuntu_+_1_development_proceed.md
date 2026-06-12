---
title: "How exactly does Ubuntu + 1 development proceed?"
date: 2011-04-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by manzdagratiano on 2011-04-30
I have no idea whatsoever how the development cycle commences. With Debian, the new Testing is forked from the current release, and then packages filter in from Sid once the freeze is lifted.

And I know that people say Sid breaks a lot, but I have now been using it for about eight months without any major issue - thanks to the 'apt-listbugs' there, which saves your tail before you upgrade if there are serious issues.

Yet, I somehow have been given the impression, mostly from lurking around the Development sub-forum, that people who have installed Ubuntu + 1 Alphas have been in for many great woes - many more breakages than Sid. Maybe it is partly because there is no hierarchy like Experimental > Sid > Testing > Stable in terms of instability? Which means that breakable software directly installs to the Alpha/Beta release?

I am wondering - I know the idea of Ubuntu being a rolling release has been brought up countless times and I do concur that with the model Ubuntu has, this is not feasible. However, is it not reasonable to adapt the Debian model? Maybe with just three layers - unstable, testing and stable? Stable is for people who want, well, stable. Testing for those who want to see what's up, and Unstable for the dev's themselves.

I mean, Debian manages to offer both a stable release and a rolling release through its paradigms, and I know a 'Testing' for Ubuntu has been proposed in the past. So why not the same paradigm, since we do derive from Debian? Maybe it will also decrease the number of people who come whining on with breakages, and complain how bad Ubuntu has been to them.

Just a thought.

---

### Post by PaulW2U on 2011-04-30
> **manzdagratiano said:**
> I have no idea whatsoever how the development cycle commences.

[https://wiki.ubuntu.com/OneiricReleaseSchedule](https://wiki.ubuntu.com/OneiricReleaseSchedule) shows how the development of Oneiric progresses week by week leading up to a release on 13th October.

---

### Post by manzdagratiano on 2011-04-30
Thanks... I had looked at that page in the past, but never bothered to expand the first few items to see what they exactly meant.

My concern is mostly with breakage. I know that new software always breaks first - one gets that experience after trying to modify relatively trivial code to suit a new end - but it seems that the Debian model is able to 'shield' the very rough ones. With Ubuntu, is there good reason to avoid that model - say lack of mostly time resources to manage another avatar of the forthcoming release? (There's already Stable, and the Ubuntu + 1 development release seems like a*Experimental + b*Sid + c*Testing, a + b + c = 1; 0 < a, b, c, < 1)

---

### Post by cariboo on 2011-04-30
> **manzdagratiano said:**
> Thanks... I had looked at that page in the past, but never bothered to expand the first few items to see what they exactly meant.

My concern is mostly with breakage. I know that new software always breaks first - one gets that experience after trying to modify relatively trivial code to suit a new end - but it seems that the Debian model is able to 'shield' the very rough ones. With Ubuntu, is there good reason to avoid that model - say lack of mostly time resources to manage another avatar of the forthcoming release? (There's already Stable, and the Ubuntu + 1 development release seems like a*Experimental + b*Sid + c*Testing, a + b + c = 1; 0 < a, b, c, < 1)

There will always be breakage during a releases cycle, that's why we recommend you not use the dev version as your main desktop, you should always have a previous version installed, just in case the dev version becomes unusable.

---

### Post by manzdagratiano on 2011-04-30
Hehe indeed... I guess what I was really asking for was the possibility of a 'rolling release' variant of Ubuntu like Testing/Sid are for Debian. But then again, just as in their case, one may imagine Ubuntu itself as not TOO far from a rolling release, since all you do at the end of one cycle - mostly and if you're not unlucky - is to just go through a really BIG upgrade. Even Testing and Sid get really big upgrades sometimes, and Testing itself is not rolling in the true sense of the term, like Sid, Gentoo and Arch are, since it does get frozen for some time.

---

### Post by Harry33 on 2011-05-01
> **manzdagratiano said:**
> Hehe indeed... I guess what I was really asking for was the possibility of a 'rolling release' variant of Ubuntu like Testing/Sid are for Debian. But then again, just as in their case, one may imagine Ubuntu itself as not TOO far from a rolling release, since all you do at the end of one cycle - mostly and if you're not unlucky - is to just go through a really BIG upgrade. Even Testing and Sid get really big upgrades sometimes, and Testing itself is not rolling in the true sense of the term, like Sid, Gentoo and Arch are, since it does get frozen for some time.

Ubuntu is far from being a rolling release (Debian, Arch-linux).
You may of course use cycle alfa=>beta=>rc=release=>alfa ...
But as you see the stability starts in every cycle from bottom and changes into the stable.
Full rolling release is stable all the time.
That would mean among others things, that Natty should be using now gcc4.6, python3.2 and linux 2.6.39 as soon it gets released.

---

### Post by tghe-retford on 2011-05-01
Breakage can vary - from mild annoyance to a main component not starting (in the past, X tends to be the problem child) to data loss (I've personally seen a Ubuntu Beta delete data from another partition once) to critical hardware failure (very rare, if ever, but I have seen warnings posted that a component in a development version could do damage to a computer).

If you wish to test, the best thing I would suggest anyone does is to have a separate testing computer to your production one. Even a separate partition with a stable release on a production computer could be affected by the development release (I know, been there, done that).

But it is at your own risk. I'm not as cautious as I warn others to be, but that's on my head, and with some common sense, I haven't had a major problem since Karmic (data loss across another partition). You can take some precautions, subscribing to the development mailing lists which warn of forthcoming breakage, reading this forum prior to upgrading and using [FONT="Courier New"]sudo aptitude safe-upgrade[/FONT] instead of [FONT="Courier New"]sudo aptitude dist-upgrade[/FONT] or [FONT="Courier New"]sudo apt-get upgrade[/FONT].

---

### Post by seeker5528 on 2011-05-02
> **manzdagratiano said:**
> I have no idea whatsoever how the development cycle commences. With Debian, the new Testing is forked from the current release, and then packages filter in from Sid once the freeze is lifted.

When there is a release, a new set of repositories is created that is a mirror of the release with a new release name, which then gets the new stuff.

That part of the equation is not really different between Debian and Ubuntu.

The differences are not having an equivalent to the "testing" symlink that always points to the release that is currently in development and not having anything equivalent to sid/unstable feeding into testing.

When you have a long development cycle like Debian has then unstable makes sense, it makes less sense for Ubuntu with it's 6 month cycles. 

For stuff that is not Ubuntu specific...

During non-LTS release packages are primarily synced with Debian unstable, with some packages from experimental, and other stuff pulled directly from upstream sources. 

For LTS releases Debian testing becomes the primary source when syncing with Debian, with packages Ubuntu goes upstream for still come from those upstreams, and some stuff still synced with Debian testing and experimental.  

How exactly things are handled in the Ubuntu to Debian direction when Ubuntu has the newer stuff, I don't know, seems like it's not as good as it could be, but better than it used to be.

If the Debian rolling idea takes off, that might give Ubuntu devs reason to rethink where they pull from and when, but I don't think it gives reason to change the way that Ubuntu repositories are handled relative to having testing and unstable sets of repositories versus having a single set of repositories for testing/development. There *are* PPAs for more experimental/controversial things.
 
[http://raphaelhertzog.com/2011/04/27/towards-debian-rolling-my-own-debian-cut-manifesto/](http://raphaelhertzog.com/2011/04/27/towards-debian-rolling-my-own-debian-cut-manifesto/)

[http://raphaelhertzog.com/2011/04/28/no-freeze-of-debian-development-what-does-it-entail/](http://raphaelhertzog.com/2011/04/28/no-freeze-of-debian-development-what-does-it-entail/)

[http://raphaelhertzog.com/2011/04/29/do-we-need-project-wide-support-for-debian-rolling/](http://raphaelhertzog.com/2011/04/29/do-we-need-project-wide-support-for-debian-rolling/)

[http://www.lucas-nussbaum.net/blog/?p=659](http://www.lucas-nussbaum.net/blog/?p=659)

[http://lists.debian.org/debian-devel/2011/04/threads.html#00602](http://lists.debian.org/debian-devel/2011/04/threads.html#00602)

Later, Seeker

---

### Post by manzdagratiano on 2011-05-02
I don't yet see how the proposed Constantly Usable Testing would be very different from Testing in Debian, since Testing it pretty much constantly usable - if anything they should just make Testing become Constantly Usable and keep breakage things only for Sid.

People say "Arch is not as stable as Ubuntu", which probably stems from the fact that Arch is rolling and Ubuntu is not, and may be generalized to "rolling releases are more unstable than ones that are not" - I have not found that to be the case so far - all updates have been pretty solid, and moreover, Arch itself has a testing, yet they constantly manage to keep up their rolling release. I know that the 2.6.38 kernel in Arch took longer to filter to the main repo than it did in Ubuntu - it was there in Natty beta.

With Ubuntu, when I was about to upgrade to Karmic RC, I was under the naive impression that Karmic will be "at least as stable" as Jaunty, which was pretty solid for me. It turned out that many things broke - like the powermizer bug in nvidia and how gdm would not fall back onto the default vesa in the event of nvidia breaking and constantly respawn itself making logging in impossible.

I would actually think this - if a release is rolling, sure, things would break many a time, since you keep changing stuff constantly. I see that everyday with code. However, they would also break one at a time, or, to properly say, a few at a time. With major releases like with Ubuntu, you have changed many many things, so if things break, there might be many things that break as well. I have not had a **single** problem with Lucid and Maverick, and whatever problems I had in Natty beta are not there in the Natty release, so I cannot really complain - it just goes to say how awesome a job the devs have been doing. However, I did have issues with Karmic, and it was about a month after which Karmic was mostly stable for me to install.

What I am elucidating is this: Debian can offer a rolling release as well as a stable release within its model, so is it not possible to do so for Ubuntu? - Just because Ubuntu is derived from Sid does not mean that a second layer like "Experimental" may not be possible to add above the main, i.e., create Ubuntu from Debian Sid, and then create an Experimental branch where Ubuntu specific modifications start taking place. Once they are stable for ten days, let them filter to Ubuntu - just like Experimental to Debian Sid. It would facilitate people who wish to test bleeding edge software on their systems, but not something as radical as what the devs would start with themselves - for instance, I am crazy enough to run Sid on my machine, which I do, but not crazy enough to run software from Experimental on my system in Sid. I would accept it if the answer is that this is not feasible within the constraints of time and space that the devs have, or if there is some technological point that I am missing to see here. But otherwise, the stance I hold is that a rolling version of Ubuntu which would naturally be more unstable is something to consider - even though this is a cliched idea brought up many times.

---

### Post by Harry33 on 2011-05-03
Let me put it this way.
1. To have a rolling release has nothing to with the dev cycle.
2. Rolling release is just as stable as the release version of the dev cycle.

Ubuntu is simply not a rolling release now.
However, I do support the idea to stop publishing release versions every 6 months. Instead a true rolling release Ubuntu ought to be created.

---

### Post by seeker5528 on 2011-05-04
> **manzdagratiano said:**
> I don't yet see how the proposed Constantly Usable Testing would be very different from Testing in Debian, since Testing it pretty much constantly usable - if anything they should just make Testing become Constantly Usable and keep breakage things only for Sid.

There are two separate primary issues lumped into the 'rolling' discussion.

One: How to improve the way testing is handle, so it could be supported in a more offical capacity for users who do or wish to use it as a rolling release.

Two: What to do when it's time to freeze things for the next release.

There was some mention of making unstable rolling, then testing could be frozen as normal, but then how do you get testing on things before they go into rolling.

There's other stuff that comes up from there, a bunch just seems like white noise, some should become their own separate discussions, some have become their own separate discussions.

Later, Seeker

---

### Post by Johnsie on 2011-05-05
to me it doesn't really make sense re-installing off of ones packages every 6 months just to stay almost up-to-date. Personally I would prefer it if developers had more control over when their applications would be rolled out.

---

### Post by manzdagratiano on 2011-05-05
> **seeker5528 said:**
> 
There was some mention of making unstable rolling, then testing could be frozen as normal, but then how do you get testing on things before they go into rolling.
Later, Seeker
It would be nice if unstable was truly rolling, but maybe that would defeat the point of having an 'unstable' distribution from Debian's point of view - a test bed for all new stuff. They themselves advise one to run stable, and use unstable at their own peril ("if it breaks you get to keep all the pieces"). So far unstable has proved to work well for me; if I see a perilous update which will remove many packages, or if apt-listbugs shows a whole bunch of serious errors, I do not upgrade until these issues have been resolved. If Ubuntu could offer such a thing alongside its stable release, which does not get frozen just like Sid does not, it would be all too awesome.

In Slackware there is a way to save your system template and then  install that template instead of the usual full distribution - I find  that to be extremely invaluable; not that I have had to reinstall my  Slackware yet since I use -current, but if I had to, it would be a pain  to manually select all the packages I want my system yet again.

Is it possible to do such a thing with Ubuntu? I realize potential problems with it - if gnome2 is to be replaced by gnome3, then there might be problems, but then again, naming the metapackage appropriately could deal with that. Similarly, in case of things like rhythmbox -> banshee, one could be advised which one one wants to keep, and in the case of packages that have been removed, one should be told that such and such a package is no longer available, etc. I mean, it should be possible with a sufficient number of cases covered. Then people who do reinstall, have an easier way out.

The policy indeed is that users ***should*** be able to upgrade as opposed to reinstalling every six months - it has worked for me so far from Lucid to Natty. But, if the incremental changes were usually small, as in the case of rolling releases, then the possibility of breaking the system with the next release cycle would also be reduced.

---

### Post by cariboo on 2011-05-05
> **manzdagratiano said:**
> It would be nice if unstable was truly rolling, but maybe that would defeat the point of having an 'unstable' distribution from Debian's point of view - a test bed for all new stuff. They themselves advise one to run stable, and use unstable at their own peril ("if it breaks you get to keep all the pieces"). So far unstable has proved to work well for me; if I see a perilous update which will remove many packages, or if apt-listbugs shows a whole bunch of serious errors, I do not upgrade until these issues have been resolved. If Ubuntu could offer such a thing alongside its stable release, which does not get frozen just like Sid does not, it would be all too awesome.

In Slackware there is a way to save your system template and then  install that template instead of the usual full distribution - I find  that to be extremely invaluable; not that I have had to reinstall my  Slackware yet since I use -current, but if I had to, it would be a pain  to manually select all the packages I want my system yet again.

Is it possible to do such a thing with Ubuntu? I realize potential problems with it - if gnome2 is to be replaced by gnome3, then there might be problems, but then again, naming the metapackage appropriately could deal with that. Similarly, in case of things like rhythmbox -> banshee, one could be advised which one one wants to keep, and in the case of packages that have been removed, one should be told that such and such a package is no longer available, etc. I mean, it should be possible with a sufficient number of cases covered. Then people who do reinstall, have an easier way out.

The policy indeed is that users ***should*** be able to upgrade as opposed to reinstalling every six months - it has worked for me so far from Lucid to Natty. But, if the incremental changes were usually small, as in the case of rolling releases, then the possibility of breaking the system with the next release cycle would also be reduced.

There is work afoot to make a rolling Debian repository, have a look [here]("http://raphaelhertzog.com/2011/05/03/my-debian-activities-in-april-2011/").

As far as having to indivually select tthe packages you want to install after a fresh update, I use the following commands to create a list of installed applications, and then install them in the background:

```
dpkg --get-selections > installed-software
```

To install the packages from the list:

```
dpkg --set-selections < installed-software
```

followed by:

```
sudo dselect
```

**Note**: you need to install dselect from the repositories.

---

### Post by snowpine on 2011-05-05
Debian has 3 branches (excluding experimental of course): Stable, Testing, Unstable

Ubuntu also has 3 branches: Long Term Support (currently 10.04), current (11.04), development (11.10)

Ubuntu and Debian have more in common than different.

---

### Post by seeker5528 on 2011-05-05
> **snowpine said:**
> Debian has 3 branches (excluding experimental of course): Stable, Testing, Unstable

Ubuntu also has 3 branches: Long Term Support (currently 10.04), current (11.04), development (11.10)

If you are going to consider the most current LTS release and the most current non-LTS release as two different branches, then you have to consider every release that is still supported a different branch.

Later, Seeker

---

### Post by seeker5528 on 2011-05-05
> **manzdagratiano said:**
> It would be nice if unstable was truly rolling, but maybe that would defeat the point of having an 'unstable' distribution from Debian's point of view - a test bed for all new stuff.

If testing is renamed and promoted as a rolling suite that has some amount of official support, unstable would be rolling too, since it feeds testing.

If unstable is made rolling instead of testing, I can't really see what the benefits would be for either users or developers. 

> In Slackware there is a way to save your system template and then  install that template instead of the usual full distribution - I find  that to be extremely invaluable; not that I have had to reinstall my  Slackware yet since I use -current, but if I had to, it would be a pain  to manually select all the packages I want my system yet again.

If you install Synaptic, on the file menu there are options for 'Read Markings', 'Save Markings', and 'Save Markings As'.

These markings files that synaptic creates/reads should be the same as if you did it at the command line with 'dpkg --get-selections > installed-software'.

Personally when using the command line to install from the list I would do

 ```
dpkg --clear-selections
dpkg --set-selections < installed-software
apt-get dselect-upgrade
```

Assuming the list was created on the same version of Ubuntu and you want software that's not on the list to be removed. 

If you don't want to remove anything that's already installed or the list is from an older version of Ubuntu you don't do the 'dpkg --clear-selections', but you might still want to use apt-get instead of dselect.

Later, Seeker

---

### Post by manzdagratiano on 2011-05-06
> **cariboo907 said:**
> There is work afoot to make a rolling Debian repository, have a look [here]("http://raphaelhertzog.com/2011/05/03/my-debian-activities-in-april-2011/").

As far as having to indivually select tthe packages you want to install after a fresh update, I use the following commands to create a list of installed applications, and then install them in the background:

```
dpkg --get-selections > installed-software
```To install the packages from the list:

```
dpkg --set-selections < installed-software
```followed by:

```
sudo dselect
```**Note**: you need to install dselect from the repositories.

> **seeker5528 said:**
> If testing is renamed and promoted as a rolling suite that has some amount of official support, unstable would be rolling too, since it feeds testing.

If unstable is made rolling instead of testing, I can't really see what the benefits would be for either users or developers. 



If you install Synaptic, on the file menu there are options for 'Read Markings', 'Save Markings', and 'Save Markings As'.

These markings files that synaptic creates/reads should be the same as if you did it at the command line with 'dpkg --get-selections > installed-software'.

Personally when using the command line to install from the list I would do

 ```
dpkg --clear-selections
dpkg --set-selections < installed-software
apt-get dselect-upgrade
```Assuming the list was created on the same version of Ubuntu and you want software that's not on the list to be removed. 

If you don't want to remove anything that's already installed or the list is from an older version of Ubuntu you don't do the 'dpkg --clear-selections', but you might still want to use apt-get instead of dselect.

Later, Seeker

Holy Mackerel!!! This is excellent! Such neat little tricks buried in the dpkg man pages unknown yet to me! This really is a Slackware template equivalent independent of version number - and is going to be a must do for me from now on! Ah the importance of fully reading the manuals!

Thank you Herren Cariboo and Seeker!

I shall keep following closely Debian news regarding rolling. I guess I am still going to stick to Debian Sid though. What would be cool is if Ubuntu gets a rolling intermediate as well.

---


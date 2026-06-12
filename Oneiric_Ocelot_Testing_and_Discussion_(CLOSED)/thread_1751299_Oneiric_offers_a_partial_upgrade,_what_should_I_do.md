---
title: "Oneiric offers a partial upgrade, what should I do?"
date: 2010-12-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-12-09
During the past few Ubuntu development cycles, we've been flooded with threads asking for assistance related to issues caused by careless usage of the **"Partial Upgrade"** feature of Update Manager, which hinted to a poor understanding of package management and the way updates happen in the development branch. 

In an effort to help with this situation, this document aims to clarify what a **"Partial Upgrade"** is, and why, **in most cases, you'll want to avoid it**.


[SIZE="4"]**Summary**[/SIZE]
or **"I don't really care if I keep messing things up and wasting my and others' time with preventable problems, and you have 30 seconds to convince me to care!"**

If you use Update Manager to upgrade your packages, and it offers to do a **"Partial Upgrade"**, do not accept it without thoroughly checking what packages it offers to remove, upgrade and install. If you do, you will most likely end up removing packages that shouldn't be removed, and waste time and effort repairing your testing installation and asking for assistance. 

Most **"Partial Upgrade"** situations occur due to package archive inconsistencies, which will typically be resolved within a few hours. If your package manager is confused, and so are you, **simply wait** and hold off the updates until things settle down. 


[SIZE="4"]**Short Version**[/SIZE]
or **"Hmm, so I shouldn't blindly do "Partial Upgrade"s and dist-upgrade? I didn't know that..."**

Due to the fact that uploads to the repositories of the active development branch are asynchronous and uncoordinated, dependencies of certain packages may arrive later than the dependent package. This causes package management tools such as Update Manager, which are mainly meant to be used with stable releases of Ubuntu where the package archive is always consistent, to interpret the situation as requiring a dist-upgrade to install new packages and/or repair packages in a "reqreinst" (requires reinstallation) state. What Update Manager performs when doing a **"Partial Upgrade"** is a dist-upgrade.

When testing development releases, most of the time, a **"Partial Upgrade"** is undesired. The situations where it's needed are limited to new packages obsoleting old ones (as in the case of the software-center package replacing software-store) and package removals from the archive.

Do not assume that since you're running a development release, a **"Partial Upgrade"** is necessarily warranted.


**[SIZE="4"]Long Version[/SIZE]**
or **"I want to be a better tester! I care! Tell me more!"**

In its normal operating mode, Update Manager will not offer to remove packages. This is the equivalent of "apt-get upgrade"ing your existing packages. In "Partial Upgrade" mode, it can. Sometimes, the removal is warranted, such as when a package is obsoloted by a new one. Other times, it will not be, and a **"Partial Upgrade"** can offer to remove important packages due to missing dependencies.

Now, the key question: 

"**How do I know whether a package is actually meant to be replaced or removed?**"

There's more than one way:

[list][*] Check the changelog of the package in question. You can do this via "Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or by going to [packages.ubuntu.com]("http://packages.ubuntu.com") and clicking "Ubuntu changelog" for the package you're curious about, or visiting the URL 

[https://launchpad.net/ubuntu/+source/](https://launchpad.net/ubuntu/+source/)[COLOR="DarkRed"]package_name[/COLOR]/+changelog

where [COLOR="DarkRed"]package_name[/COLOR] is the name of the source package you're curious about. The most recent changelog entry will indicate the reason for the removal or replacement, if there is one.


[*] Keep an eye on the changes mailing list or RSS feed for the active development release. The current ones are the [Oneiric-changes mailing list]("https://lists.ubuntu.com/mailman/listinfo/Oneiric-changes").

For an example scenario of using the list of recent changes to determine whether a package removal and "Partial Upgrade" is safe, refer to [the next post]("http://ubuntuforums.org/showpost.php?p=8423549&postcount=2").


[*] Check the [build status information page]("https://launchpad.net/ubuntu/+builds") for Ubuntu on Launchpad to see if those mysterious missing dependencies are coming down the pipes, or there are problems preventing them from being built.


[*] Do a forum search, or [join the #ubuntu+1 channel on irc.freenode.net]("https://help.ubuntu.com/community/InternetRelayChat") and ask around to see whether other people are having problems with the same package(s).


[*] If you're still confused, simply **wait** and see if things are magically fixed within a few hours. If not, start a new thread or post to an existing one on the same issue to check with others.[/list]

A typical interaction with a package manager involves the following three steps:

[list] [*] You select some packages to be installed / removed / upgraded


[*] The package manager resolves your intention according to its package management logic, the available software sources, and the priorities you've indicated (as in APT pinning), if any, to a set of actions it has to perform, and outputs a list of those actions


[*] You check this list, confirm it if you're happy with it, or cancel it and refine your selection until you're happy with it.[/list]

If you skip the third step, assuming that simply updating your package information and hitting "Apply" or pressing "Enter" when the prompt comes up will give you the latest changes, and/or that since you're running a development release, any kind of package conflict / removal / replacement, even those that seem to intentionally remove lots of packages, are to be expected, you'll keep breaking your installation unnecessarily. **Don't do that. Review that list of changes.**

While asking for and providing assistance regarding testing is one of the main functions of this forum, learning [the basics of using development releases]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") is a prerequisite for doing useful testing, and if lots of people keep messing up their testing installations due to being unfamiliar with those basics, the forum will get flooded with duplicate threads and quicky become much less useful to everyone. 

Please take some time to learn the basics, and if you need help with that, don't hesitate to ask!

**With thanks to 23meg**

---

### Post by cariboo on 2010-12-09
** This Is Just An Example**

Here's a typical scenario in which I figured out whether it was fine to let Synaptic remove *gstreamer0.10-schroedinger*, a package I knew nothing about previously, using one of the methods I suggested in the first post. This could have been any other package manager, such as Update Manager offering a "Partial Upgrade" to remove that package.

[list=1][*] Synaptic offered to remove the package *gstreamer0.10-schroedinger*. At this point I did not know whether Synaptic was offering to remove it due to temporary archive flux, or it was actually meant to be removed.

[[IMG]http://img16.imageshack.us/img16/2705/67492748.png[/IMG]](http://img16.imageshack.us/my.php?image=67492748.png)


[*] To figure out, I decided to check the karmic-changes mailing list **(don't be confused; this is an old example - the current one is [Maverick-changes]("https://lists.ubuntu.com/mailman/listinfo/Maverick-changes"))**. Since I'm subscribed to it, I actually did this **much faster** in my mail client, but for the sake of illustrating how it could have been done without being subscribed (by the way: **subscribing is very beneficial if you're serious about testing** - there's also [an RSS feed]("http://feeds.ubuntu-nl.org/MaverickChanges") if you don't want mail), and even only vaguely remembering the location of it, I'll pretend I browsed it at the web archives.


[*] At [https://lists.ubuntu.com/mailman/listinfo/Karmic-changes](https://lists.ubuntu.com/mailman/listinfo/Karmic-changes) (at which I may have arrived with a web search, or through [https://lists.ubuntu.com](https://lists.ubuntu.com)), I clicked the link leading to the archives.

[IMG]http://img140.imageshack.us/img140/9418/65689993.png[/IMG]


[*] I then clicked the "Date" link for the current month, since I was looking for what's probably a recent change, and I wanted the changes ordered by date.

[[IMG]http://img8.imageshack.us/img8/4152/74695720.png[/IMG]](http://img8.imageshack.us/my.php?image=74695720.png)


[*] I hit "Ctrl + F" in Firefox to search for the word "schroedinger", which is part of the package name, among the list of recent changes. I only typed the first few letters.

[[IMG]http://img12.imageshack.us/img12/2108/48677299.png[/IMG]](http://img12.imageshack.us/my.php?image=48677299.png)


[*] That highlighted what looked like a relevant change! I clicked on it to see the changelog.

[[IMG]http://img14.imageshack.us/img14/4971/85014317.png[/IMG]](http://img14.imageshack.us/my.php?image=85014317.png)


[*] I scanned through [the changelog]("https://lists.ubuntu.com/archives/karmic-changes/2009-October/010163.html") for a hint of whether this package is actually being removed. Searching the page for the words "remove", "drop" or "deprecate" was practical at this point, since I was looking to see if one of those things had happened to the suspected package.


[*] And there it was!
> debian/gstreamer0.10-schroedinger.install:
      - Dropped GStreamer plugin, it's now in gstreamer0.10-plugins-bad.


[[IMG]http://img8.imageshack.us/img8/4224/48655391.png[/IMG]](http://img8.imageshack.us/my.php?image=48655391.png)



[*] OK, it seems the GStreamer plugin for Schroedinger is being merged into the  *gstreamer0.10-plugins-bad* package, and the old package *gstreamer0.10-schroedinger* is being deprecated. So it should be fine to remove it.


[*] Just to make sure, and to satisfy my detective urge, I went back to archive page, and this time, searched for "plugins-bad", which led me to [a change entry for *gstreamer0.10-plugins-bad*]("https://lists.ubuntu.com/archives/karmic-changes/2009-October/011527.html").


[*] I looked for "schro..", and there we go:

>      + debian/gstreamer-plugins-bad.install:
       - Add new asfmux, frei0r, kate and schroedinger plugins.

[/list]

Now I know what's going on, and can comfortably let *any* package manager remove the suspected package. It's fine to accept a "Partial Upgrade" that wants to remove it.

**Thanks 23meg**

---

### Post by mörgæs on 2011-06-25
Jarry, please limit your posting spree to a few exact and well-researched answers and read the previous posts thoroughly.

---


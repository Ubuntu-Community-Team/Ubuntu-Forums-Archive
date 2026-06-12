---
title: "Really Fix It!"
date: 2008-03-06
forum: Packaging and Compiling Programs
---

### Post by dholbach on 2008-03-06
I wrote a script that sets up this list of bugs: **[http://daniel.holba.ch/really-fix-it/](http://daniel.holba.ch/really-fix-it/)**

As you might gather from the name of the page: these are bugs that are 'almost' fixed and just have to be fixed for real:
[LIST]
[*] Bugs fixed elsewhere (upstream or in a different Distro)
[*] Bugs have a patch attached
[*] Bugs that are in the Sponsoring Queue
[/LIST]

It'd be nice to get as many of these fixed as possible for release.

Please, if you touch any of the packages on the list, try to look at the other open bugs - you might be able to fix them with the same upload.

This is a great way to get started (and excellent fodder for **5 a day** ([https://wiki.ubuntu.com/5-A-Day](https://wiki.ubuntu.com/5-A-Day))):

[LIST]
[*] Confirm if the issue still exists,
[*] transform patch into a debdiff ([https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff](https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff)),
[*] see if if fixes the issue,
[*] get it in the sponsoring queue ([https://wiki.ubuntu.com/SponsorshipProcess](https://wiki.ubuntu.com/SponsorshipProcess)).
[/LIST]

Let's make Hardy ROCK and let's get those bugs fixed once for all!

--
My 5 today: #182571 (samba), #198907 (texinfo), #132191 (bzr-gtk), #156451 (labyrinth), #145019 (bzr-builddeb)
Do 5 a day - every day! [https://wiki.ubuntu.com/5-A-Day](https://wiki.ubuntu.com/5-A-Day)

---

### Post by andrewsomething on 2008-09-09
**[SIZE="4"]Harvest[/SIZE]**
*(from Daniel's blog: [http://daniel.holba.ch/blog/?p=139](http://daniel.holba.ch/blog/?p=139))*

**The very short version:**

Go to [http://daniel.holba.ch/harvest/](http://daniel.holba.ch/harvest/) - find low-hanging fruit, it will make your life (and Ubuntu) better.
**_______________________________**

**The short version:**

Check out [http://daniel.holba.ch/harvest/](http://daniel.holba.ch/harvest/) - it’s the successor to “really-fix-it”, much more improved, more extensible, just a lot better.

Its aims are:

    * Make finding opportunities among all packages easy.
    * Figure out which packages are in a good shape and which are not. (Notice the “Score“.)
    * Easily extensible.
    * Lots of different views (planned).
    * One place to get information of lists that are scattered around right now.
**______________________________**

**The long version:**

Visit [http://daniel.holba.ch/harvest/](http://daniel.holba.ch/harvest/) - it’s good for you.

I’ve always been obsessed with the idea of having one place where to get all kinds of information of the state of our packages in Ubuntu. I’ve lost count of how often I tried to find our RC Bugs tracker, the CD Generation problems, patches in Fedora/SuSE/<other distro>, etc etc etc. and I’ve always been annoyed with the discoverability of those lists. It just sucked.

Another problem that irked me a lot is that I have no idea which of our 248576425 packages are in a good shape and which aren’t. There’s simply not metric for it. How can individuals or teams figure out what needs working on?

really-fix-it (stopped and now redirects to harvest) was the first attempt to get the ball rolling to fix those problems. It was nice to see an overview of all kind of packages and what needs doing. It was a big success, lots of bugs were fixed.

It had a lot of shortcomings too:

   1. It took ages for it to run.
   2. It wasn’t very extensible, you needed to dive down into the code and figure out why a certain bug showed up on the list, etc.
   3. I got a lot of feature requests and ideas for improvements and I attempted to fix them, what happened was: I grew more and more data structures that exactly replicated what _[Launchpad Bugs]("https://bugs.launchpad.net/")_ already does.
      Stuff in a database -> screenscrape from HTML/Text pages -> Store in a database with similar data structures: bad idea!
   4. Lots of new ideas for other data sources came up and suddenly I had to invent things like “Debian Bug”, “FTBFS entry”, etc. - the concept of really-fix-it was near its end.
   5. I’m not a HTML person.

After thinking about the whole thing for several days, talking to _[Michael Vogt]("http://mvogt.wordpress.com/")_ about it and sleeping over it for several more days the solution to the problem evolved quite naturally.

Step 1: get rid of complicated data structures. There’s only one thing we care about: opportunities. If they are a patch from another distro, a bitesize bug or a piuparts problem in some log - it shouldn’t matter to us.

Step 2: make it distributed. Harvest does not care about where an opportunity comes from. It will just download a CSV (comma-separated values) file, parse opportunities (source package, URL to opportunity, short description) and put that into the database. It will check for new CSV files every now and then and download them if they changed. Opportunities that don’t show up any more, will not be displayed in the HTML pages.

Step 3: add “clues” - similar to opportunities clues are stored in CSV files, but provide information about package quality. Let’s say there’s a clue list for source packages that are uninstallable, this will give the package a score of -500. Another list will say “50% of the bugs are triaged and have been forward upstream”, this should give the source package a +200.

Step 4: make it open-source.

I simply love it how a solution becomes obvious once you’re clear about the problems in your current approach.

Find out more in the _[HACKING guide]("http://daniel.holba.ch/harvest/doc/index.html")_.
**___________________________________**
[B]
Future plans:[/B]

    * Move to _[qa.ubuntu.com]("http://qa.ubuntu.com/")_.
    * Fix _[bugs]("https://bugs.launchpad.net/harvest")_.
    * More views, split up opportunities into categories.
    * More opportunity lists.
    * More clue lists.

Here’s a call for contributors: if you wrote a script that generates fancy HTML output of opportunities already, please consider extending it so that it generates a CSV file too and get it added to _[harvest-data]("https://code.launchpad.net/harvest-data")_.

I’d like to thank a few people who helped me in getting harvest to the point it is now:

    * Colin Watson for the fantastic name.
    * Michael Vogt for enduring countless phone calls about it.
    * Emmet Hikory and Henrik Omma for reviewing it.
    * Jono Bacon and Jorge Castro for discussions about it and the encouragment I got from them.
    * Lots and lots of testers.
    * Canonical for giving me the time to work on something I deeply believed in.

**Go Wild! The Harvest Season has begun! Make Ubuntu better!**

---

### Post by dholbach on 2011-01-06
**Harvest moved to [http://harvest.ubuntu.com/](http://harvest.ubuntu.com/)**

---


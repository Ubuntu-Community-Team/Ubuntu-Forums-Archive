---
title: "Gnome Shell, App search causes 100% cpu"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by professor76 on 2011-10-01
I am running Gnome Shell on Ubuntu 11.10 Beta 2 (up-to-date). When I enter any key in the "type to search" text box on the right hand side, (you will see this when you click on Activities Button), it immediately causes 100% CPU. I have a quad core Sony Vaio laptop, I could run top from the console (ctrl+alt+f1) and could see Gnome shell causing 100% CPU.

This has been the situation for a long time. I didn't see this initially, search used to work then. Mine is an upgraded system from 11.04, not a fresh install. I didn't use Gnome 3 in 11.04 though.

Any known workarounds ?

I have reported the issue in launchpad, #864206. The tracker automatically put the bug under zeitgeist category. I guess its a wrong category since Shell apparently doesn't use zeitgeist.

---

### Post by VinDSL on 2011-10-01
> **professor76 said:**
> I have reported the issue in launchpad, #864206. The tracker automatically put the bug under zeitgeist category. I guess its a wrong category since Shell apparently doesn't use zeitgeist.
Interesting!

When I do an App Search in GS, my desktop simply freezes - end of story - requires a reboot.

As soon as I type the first letter into the search box, BOOM!

> Shell apparently doesn't use zeitgeist.

Are you sure about this?!?!?  :)

AFAIK, Zeitgeist has been integrated into Gnome 3.0.

---

### Post by sgage on 2011-10-01
Seems to be working normally for me. 32-bits, latest GS.

---

### Post by VinDSL on 2011-10-01
> **professor76 said:**
> Shell apparently doesn't use zeitgeist.
Just did a quick Google Search...


SOURCE: [http://mail.gnome.org/archives/gnome-shell-list/2011-April/msg00144.html](http://mail.gnome.org/archives/gnome-shell-list/2011-April/msg00144.html)

> Hi, all,

As many of you know, there is a project called Zeitgeist that is somehow
being integrated into Gnome-shell.  In this mail I intend to paint a
picture of what we want to do.

* What is Zeitgeist?

Zeitgeist is ~/.recently-used on steroids.  It is a service that keeps a
time-ordered log of things that happen during your session.  In
Zeitgeist's terminology, each of those things is an Event.  An event has
various properties:

	timestamp - when did this happen?
	actor - what application caused this to happen?
	subject - what is being referred to (e.g. a URI or a file)?

(There are other properties, but in this mail we'll only care about
those three.  For example, there are other properties that let you say,
"this file came from an attachment to a mail in Evolution".)

Various things log events into Zeitgeist.  We monitor your recently-used
list and feed Zeitgeist with events created from the data in that list.
There are extensions or plugins or patches for apps to log their actions
into Zeitgeist.  (All of this happens through D-Bus.)

Zeitgeist thus stores a log of things like

	- What files have I visited? (recently-used)
	- What web pages have I visited? (Firefox extension)
	- What Tomboy notes have I visited? (Tomboy add-in)
	- What IM conversations have I had? (Telepathy extension)
	- What music have I listened to? (Banshee plugin)
	- What applications have I launched? (GIO magic)
	- What pushes have I done? (bzr plugin)

That's the logging part.  But the interesting thing is how you can query
that log.

Zeitgeist provides a D-Bus API for querying the log in various
interesting ways:

- Give me the files that I visited within this time range.

- Give me the files that I've used most frequently with this app.

- Give me the files that I've opened close in time to this other file.

- Give me the apps that I use most frequently.

Etc.  This is done with a clever API based on providing an "event
template" with various wildcards.  This is not only for files, but for
any kind of subject you can put in an event, of course - thus it also
works for Tomboy notes or Banshee songs.

In terms of implementation, Zeitgeist has an "engine" daemon which
exports a D-Bus interface for adding or querying events.  All
communication with the engine is via D-Bus.  The engine stores its
database of events in an SQlite database.

There is also a separate daemon which monitors your
~/.recently-used.xbel and feeds events to the engine.  It also monitors
apps that get launched and creates events for those.  I'm not very happy
that this is a separate daemon, but it's a tiny amount of code that
could very well be folded into the main engine daemon.

* What gnome-shell wants to do

Two things:  a journal of the user's work, and jumplists.

The journal is very well explained in
[http://live.gnome.org/GnomeShell/Design/Whiteboards/FindingAndReminding](http://live.gnome.org/GnomeShell/Design/Whiteboards/FindingAndReminding) 

Jumplists are not as well defined; the meatiest discussion I've found is
in [https://bugzilla.gnome.org/show_bug.cgi?id=609114](https://bugzilla.gnome.org/show_bug.cgi?id=609114)

* Code

There is a 'zeitgeist' branch in gnome-shell's usual repository at
git.gnome.org.  This makes gnome-shell not use GtkRecent* to display
recent documents when searching, but rather to use Zeitgeist instead.
It also makes the right-click menus for application icons display
recently- and frequently-used files that you used with each app.  These
are minimal jumplists; the "let apps add their own commands to their
shell's menus" is out of the scope of Zeitgeist.

Based on that 'zeitgeist' branch, there is a 'journal' branch here:
[https://gitorious.org/~federicomenaquintero/gnome-shell/gnome-shell-federico/commits/journal](https://gitorious.org/~federicomenaquintero/gnome-shell/gnome-shell-federico/commits/journal)

That branch adds a third item besides the Windows and Applications in
the shell's overview - a "Recent Activities" item that displays a
time-based journal, similar to the one in the FindingAndReminding wiki
page.  This is what Seif blogged about:

[http://seilo.geekyogre.com/2011/04/zeitgeist-work-towards-gnome-3-2/](http://seilo.geekyogre.com/2011/04/zeitgeist-work-towards-gnome-3-2/)

Why is the journal branch not in git.gnome.org?  Because until a few
days ago, this was very early code.  We played with different rough
implementations of the journal and settled on the current one.  I will
personally take care of cleaning this up for hosting it in git.gnome.org
so that it is closer to the mainline work.

Sidebar:  I think having the journal as a third item in the overview is
not the best place for it.  I think you should be able to access the
journal directly from the desktop - think of having a "Journal" button
next to "Activities", or something as direct as that.  But that's a
discussion that we should not have right now, but rather later, when we
get a feel for how the journal behaves and for just how fluently you
need to access it.

* Can't you do this with Tracker?

Honestly, I don't know.

The following is my very biased and not thoroughly informed opinion, but
I know a thing or two.

Tracker has been advertised as a search/indexing engine ("google for
your files"), a metadata storage engine ("put RDF triplets here and
query them with a nice language"), and a database for storing anything
because you can store anything in a database ("Nokia stores contacts or
something there").

It does sound like you could implement something like the Zeitgeist
service - a time-based log of events - by using Tracker in some way.  I
mean, if you can index documents and also store contacts and store RDF,
sure, it sounds like you can implement *that*.

The point is that Zeitgeist is written already, to do what we've been
talking about since GUADEC 2008 (a time-based view of files, which
turned out to have more interesting implications).  Its database is
optimized for that kind of usage.  It's there and it works.

* But FindingAndReminding is more than a journal of stuff you did

Yes, indeed!

Of particular interest to me are the scheduling capabilities of a
journal-like view.  You want to drop a PDF in a future date to remind
you to read it, and you may want to see deadlines displayed in the
journal's timeline.  This doesn't even have mockups yet, but we should
indeed investigate it in the near future.

(Scheduling is *probably* not entirely Zeitgeist's job.  The obvious
thing is to start by showing to-do items from Evolution in the journal.
But let's talk about that later, when we have the journal working for
its originally-intended purpose.)

* Is that all?

For now, yes.  Thanks for reading.

  Federico

---

### Post by professor76 on 2011-10-01
Well, you can see the bug history from launchpad. Although the tracker auto reported on zeitgeist, the bug was moved to invalid with the following comments.

> The bug is not related to zeitgeist since shell DOES NOT use zeitgeist...


> GNOME Shell does not use Zeitgeist... I repeat it DOES NOT use Zeitgeist

Rightnow, its with Gnome-Shell.

Yes, Identical behavior. Typing a single letter into App search box freezes the box.

64-bit here.

---

### Post by Quackers on 2011-10-01
Hmm, fully updated 64 bit gnome-shell here and App search is working fine.
No ridiculous cpu figures and the search comes up with the possible Apps.

---

### Post by fillmont on 2011-10-01
I've found that with the Gnome Shell App Search, if I type quite slowly, it will search normally. But when I type with any real-world speed, it will freeze up and require a hard reboot. Running on 64 bit.

---

### Post by professor76 on 2011-10-01
I just tried the slow typing and it didn't help. Just after the first letter, UI froze. I could get into console (ctrl-alt-1) and could see the processes. Gnome Shell is 100% CPU. needed a reboot.

---

### Post by VinDSL on 2011-10-01
> **professor76 said:**
> Well, you can see the bug history from launchpad [...] the bug was moved to invalid [...]
It's easy enough to check...  ;)

I logged into GS, and would swear that Zeitgeist is chewing up cycles.

PS & Conky are both reporting it, running in the background:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-1-oct-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-oct-2011.png")[/INDENT]


Am I missing something here?!?!?

---

### Post by effenberg0x0 on 2011-10-01
@Vin

I don't use gnome shell. Is it possible this zeitgeist is a zombie or a parallel, still open, unity session?

Regards,
Effenberg

---

### Post by VinDSL on 2011-10-01
> **effenberg0x0 said:**
> @Vin

I don't use gnome shell. Is it possible this zeitgeist is a zombie or a parallel, still open, unity session?

Regards,
Effenberg
Yes, possible.  I was *thinking* the same.

Queries, in both DEs, suggest Zeitgeist is active but (mostly) sleeping.

I was hoping that Activity Journal would offer a clue, but it's broken(again).  LoL!

I don't normally use GS.  I'm just dabbling in it - seeing how Unity integrates with it, and so forth, and so on.

I don't *know* if Zeitgeist is actually tracking Gnome Shell activites, or not.

Maybe one of the GS fanbois will pop in here...   ;)

---

### Post by VinDSL on 2011-10-01
Speak of the devil...

Gnome Shell update just hit the ricotz/testing PPA:

```
3.2.0+git20110930.a7442cd0-0ubuntu1~11.10~ricotz0)
```

I'll perform the update, do a cold boot into GS and see if Zeitgeist is running, or not.

EDIT

I cold booted into GS.  Did an htop...

Htop showed zeitgeist-daemon running merrily along.

Tried AJ - still doesn't work.

Tried doing an App Search.  As soon as I typed the first letter, it said, "Searching..." and the desktop locked up.

Same old, same old...  :)

---

### Post by sanderd17 on 2011-10-04
I'm having the same issue on Arch 32-bit.

I'm able to go in tty and kill gnome-shell with the command '9'. '15' doesn't work.

For me it does work when I type very fast. If I hit the super key and type 'fir' followed by an enter, as fast as I can, than firefox opens without a problem. But if I wait until I see something, it doesn't work.

Oh, and I have zeitgeist as one of my search providers.

---

### Post by professor76 on 2011-10-04
I tried with latest updates again, and I could see the same issue. The launchpad issue is still in unassigned. 

Any others see this ?

---

### Post by xgt001 on 2011-10-04
interestingly i suffered the issue everytime untill i reverted back to the default adwaita theme and icon set....

---

### Post by sanderd17 on 2011-10-04
> **xgt001 said:**
> interestingly i suffered the issue everytime untill i reverted back to the default adwaita theme and icon set....

Yes, this is it.

Not the icon set, but the shell theme.

Probably it wasn't able to load something in the theme. That's why I could type fast (it would launch the app before the interface was called), but not slow.

---

### Post by professor76 on 2011-10-04
Yes, I confirm. I don't see the issue with adwaita (default) theme

I was using Faince ...

Thanks a lot for the help

---

### Post by sanderd17 on 2011-10-05
I'm making a list of the themes that cause this issue: [http://ubuntuforums.org/showthread.php?p=11312189#post11312189](http://ubuntuforums.org/showthread.php?p=11312189#post11312189)

If you have any themes, please share them.

---


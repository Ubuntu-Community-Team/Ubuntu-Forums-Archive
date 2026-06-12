---
title: "Gnome-PackageKit landed in repos"
date: 2011-06-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-06-18
A brand new package landed in OO repos: gnome-packagekit-3.0.3-1ubuntu1

Graphical distribution neutral software management tools
 
PackageKit allows performing simple software management tasks over a DBus
interface  e.g. refreshing the cache, updating, installing and removing
software packages or searching for multimedia codecs and file handlers.

This package contains a set of GTK+ based applications for PackageKit:
 - Status icon for PackageKit transactions (gpk-update-icon)
 - System update tool (gpk-update-viewer)
 - Software installation and removal tool (gpk-applications)
 - Repository editor (gpk-repo)
 - Several small helpers and prototype implementations

[[IMG]http://dl.dropbox.com/u/1338581/varie/gpk/pgk1s.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/gpk/pgk1.png") [[IMG]http://dl.dropbox.com/u/1338581/varie/gpk/pgk2s.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/gpk/pgk2.png") [[IMG]http://dl.dropbox.com/u/1338581/varie/gpk/pgk3s.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/gpk/pgk3.png")
[[IMG]http://dl.dropbox.com/u/1338581/varie/gpk/pgk4s.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/gpk/pgk4.png") [[IMG]http://dl.dropbox.com/u/1338581/varie/gpk/pgk5s.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/gpk/pgk5.png")

There is also a tool for creating servicepacks of installed software
I've installed a couple of apps and seems to work well  :)
(as usual sorry for ita lang in the screenshots!)

---

### Post by ronacc on 2011-06-18
thanks for the heads up, installing now to have a look . don't worry about the language in the SS this is an international forum even if it is conducted in English .

---

### Post by lucazade on 2011-06-18
> **ronacc said:**
> thanks for the heads up, installing now to have a look . don't worry about the language in the SS this is an international forum even if it is conducted in English .

comment appreciated :)
happy playing with gpk!

---

### Post by ronacc on 2011-06-18
all I have as of now is gnome-packagekit-data available for amd64 .

---

### Post by ronacc on 2011-06-18
the 64bit pkg isn't built yet , I booted over to my lubuntu install which is 32bit and its there .

---

### Post by lucazade on 2011-06-18
> **ronacc said:**
> the 64bit pkg isn't built yet , I booted over to my lubuntu install which is 32bit and its there .

there is no time to wait for packages building...ehhehe

---

### Post by Starks on 2011-06-18
I recall hearing that the Software Center would transition to the packagekit backend.

Is this the beginning of it?

---

### Post by buzzmandt on 2011-06-18
> **Starks said:**
> I recall hearing that the Software Center would transition to the packagekit backend.

Is this the beginning of it?
If this is so would this be the start of software center coming to kubuntu with a kpackagekit backend?

---

### Post by seeker5528 on 2011-06-18
> **Starks said:**
> I recall hearing that the Software Center would transition to the packagekit backend.

We've heard that before.
I'll believe it when I see it.

But maybe there *is* more reason to believe this time around.

[http://swarm.cs.pub.ro/~alexef/gsoc/proposal.html](http://swarm.cs.pub.ro/~alexef/gsoc/proposal.html)

Later, Seeker

---

### Post by ronacc on 2011-06-18
> **lucazade said:**
> there is no time to wait for packages building...ehhehe

back in the 90's when I tried caldera open linux (1.0) it took 2+ weeks of my 486dx4/100 grinding away 24/7 to get a working desktop :lolflag:

---

### Post by silex89 on 2011-06-18
It reminds me of Sulfur the GUI package manager for Sabayon. Looks great though.


:)

---

### Post by beew on 2011-06-18
Why do we need this? Synaptic is perfect as it is. I hope it is not a slow annoying piece of crap like the kpackagekit in kde. I played with Kubuntu and Fedora kde. The first chance I ran Kpackagekit in Kubuntu I installed Synaptic and forgot about it, in Fedora I only used it to install yumex.

---

### Post by seeker5528 on 2011-06-18
> **beew said:**
> Why do we need this? Synaptic is perfect as it is. 

I use Synaptic 90%+ of the time, calling it perfect is a bit of a stretch. 

Package kit wasn't designed to allow the advanced capabilities that something like Synaptic provides so you can't really compare any of the front ends to Synaptic.

Later, Seeker

---

### Post by seeker5528 on 2011-06-18
> **ronacc said:**
> back in the 90's when I tried caldera open linux (1.0) it took 2+ weeks of my 486dx4/100 grinding away 24/7 to get a working desktop :lolflag:

Keeping the phone line busy for that long wasn't an option for me when I first installed Linux, lucky for me Slackware was available as sets of floppies so you could download a floppy image here, a floppy image there, and eventually get what you needed.

Or did you mean that the installation took that long. :P

Later, Seeker

---

### Post by Starks on 2011-06-18
are gnome-packagekit and packagekit-gnome the same thing?

---

### Post by dext on 2011-06-19
> **beew said:**
> Why do we need this? Synaptic is perfect as it is. I hope it is not a slow annoying piece of crap like the kpackagekit in kde. I played with Kubuntu and Fedora kde. The first chance I ran Kpackagekit in Kubuntu I installed Synaptic and forgot about it, in Fedora I only used it to install yumex.
PackageKit uses the same Mirrors as Synaptic does, Just Because PackageKit is being introduced into Ubuntu doesnt mean you'll be forced to use it [http://www.packagekit.org/pk-intro.html](http://www.packagekit.org/pk-intro.html)  [http://www.packagekit.org/](http://www.packagekit.org/)

---

### Post by dino99 on 2011-06-19
never had good experience with packagekit :(

once again this package badly fails with: Gtk-Message: Failed to load module "pk-gtk-module"

so as the others *packagekit* i've purged it :)

---

### Post by lucazade on 2011-06-19
> **dino99 said:**
> never had good experience with packagekit :(

once again this package badly fails with: Gtk-Message: Failed to load module "pk-gtk-module"

so as the others *packagekit* i've purged it :)

I get this message only when I launch synaptic, but it doesn't brake things here.
Both Synaptic and GnomePackagekit continue to work.

One thing I didn't like of packagekit was the speed, now it seems a bit faster during operations. 

@Starks
gnome-packagekit is the correct one (gtk3), the other one is old gtk2 interface.
Dunno if it will become the default backend for SoftwareCenter or not.. nice thing is to have another great tool for managing packages/repos.

Synaptic is the state of the art of package manager (at least for pro-users), unfortunately it is so old that needs a revamp/rewrite/..
[https://code.launchpad.net/~mathieu-tl/synaptic/gtk3](https://code.launchpad.net/~mathieu-tl/synaptic/gtk3) :P

---

### Post by lucazade on 2011-06-19
> **seeker5528 said:**
> Keeping the phone line busy for that long wasn't an option for me when I first installed Linux, lucky for me Slackware was available as sets of floppies so you could download a floppy image here, a floppy image there, and eventually get what you needed.

Or did you mean that the installation took that long. :P

Later, Seeker

Keeping the phone line busy reminds me when I run a BBS on Amiga.
My family telephone was always dedicated to a 2400baud modem from night till the day after when I went to school :)
ok stop nostaglia!

---

### Post by kvv_1986 on 2011-06-19
> **beew said:**
> Why do we need this? Synaptic is perfect as it is. 

I agree with this. I thought Synaptic and USC covered everything. What is the purpose of this, if ever shipped in Ubuntu.

---

### Post by lucazade on 2011-06-19
> **kvv_1986 said:**
> I agree with this. I thought Synaptic and USC covered everything. What is the purpose of this, if ever shipped in Ubuntu.

If PackageKit will be the default backend of Ubuntu Software Center, this will allow the adoption of USC itself in all the major distros.
[http://www.webupd8.org/2011/01/cross-distro-unified-installer-is-on.html](http://www.webupd8.org/2011/01/cross-distro-unified-installer-is-on.html)

"Basically the plan is to unify the meta data for all installable packages, this way we can have a standard way of allowing all developers to put their most important data into the standard desktop files and not have to expect them to fill out debian and rpm package information. PackageKit is being used alongside a de-branded Ubuntu Software Center in a project called AppStream

As soon as the debian-packagekit integration is perfect, I'm sure Ubuntu can ship it."

Gnome-PackageKit is only a frontend, is not strictly necessary for the adoption of the backend.. just another GUI if you like to use it.

---

### Post by el_koraco on 2011-06-19
> **buzzmandt said:**
> If this is so would this be the start of software center coming to kubuntu with a kpackagekit backend?

Kubuntu Oneiric will use Muon as a PM, and the Muon store as a USC clone. They both use aptdaemon as a backend.

---

### Post by ronacc on 2011-06-19
> **seeker5528 said:**
> Keeping the phone line busy for that long wasn't an option for me when I first installed Linux, lucky for me Slackware was available as sets of floppies so you could download a floppy image here, a floppy image there, and eventually get what you needed.

Or did you mean that the installation took that long. :P

Later, Seeker

I cheated I bought the caldera floppies mail order ! what you got there was a boot floppy with the kernel and some libs to get you a cmd line and several floppies of sorces .

> ok stop nostaglia! us geezers can't turn it off that easy:lolflag:

---

### Post by buzzmandt on 2011-06-19
> **el_koraco said:**
> Kubuntu Oneiric will use Muon as a PM, and the Muon store as a USC clone. They both use aptdaemon as a backend.

thanks for that, just installed and tried muon, i think i might like it, actually has a lock at current version function.

---

### Post by dino99 on 2011-06-20
> **buzzmandt said:**
> thanks for that, just installed and tried muon, i think i might like it, actually has a lock at current version function.

i've tried it and its very close to synaptic but i've had a bad experience with it:

when you install a package which want to remove other packages it does not warn with a package(s) list dialog box when it will remove/unistall something (have happened on kubuntu: one package have uninstalled nvidia-current, without warning, then wanting to reinstall it, more than 150 packages were removed :( :( thats scary :(

---

### Post by el_koraco on 2011-06-20
> **dino99 said:**
> i've tried it and its very close to synaptic but i've had a bad experience with it:

when you install a package which want to remove other packages it does not warn with a package(s) list dialog box when it will remove/unistall something (have happened on kubuntu: one package have uninstalled nvidia-current, without warning, then wanting to reinstall it, more than 150 packages were removed :( :( thats scary :(

It has a "preview changes" box in the upper left corner.

---

### Post by dino99 on 2011-06-20
> **el_koraco said:**
> It has a "preview changes" box in the upper left corner.

enough emotion right now :(
thanks for the info, but have not seen it (maybe that font too small too, cant set it as i like or not found how to)

So i've filled a report  Bug #799618  , its too scary without popup warning dialog box

---

### Post by bmbaker on 2011-06-20
> **ronacc said:**
> I cheated I bought the caldera floppies mail order ! what you got there was a boot floppy with the kernel and some libs to get you a cmd line and several floppies of sorces .

 us geezers can't turn it off that easy:lolflag:

wow !! thank the dreaming heavens for usb sticks :-) :-)

---

### Post by mick8985 on 2011-06-21
Has this still not hit the repos for 64bit, or is my mirror behind the times?

---

### Post by xebian on 2011-06-21
> **buzzmandt said:**
> thanks for that, just installed and tried muon, i think i might like it, actually has a lock at current version function.

muon has the look and feel of synaptic.

But nothing beats apt-get and/or aptitude.

USC is already at version 5 and it's front-end is still too primitive for my taste compared to the brand new muon which has much better front.

---

### Post by Harry33 on 2011-06-21
> **mick8985 said:**
> Has this still not hit the repos for 64bit, or is my mirror behind the times?

You should look for the "packagekit" from the official repos.
It is there.
However, packagekit is a simple tool, not a replacement for synaptic, which is an advanced tool.

---

### Post by dext on 2011-06-22
try an do a **PackageKit** its case sensitive which is probably why your not finding it

---

### Post by cariboo on 2011-06-22
> **dext said:**
> try an do a **PackageKit** its case sensitive which is probably why your not finding it

If you are going to offer help, please give Ubuntu relevant help, packagekit is all lower case in the repositories. Typing **packagekit** in the synaptic quick search box, finds it with no problems.

---


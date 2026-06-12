---
title: "Packages from the default repository of Ubuntu consists of what?"
date: 2015-03-31
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-03-31
Sorry for poorly-worded title. 2 questions:

[FONT=verdana]1. In general, how much of a delay is there between when the latest stable version of programs direct from upstream is released and when Ubuntu packages it for the default repository (where it is deemed stable)? I understand that more popular packages tend to have less of a delay but I want to know whether it's worth switching to something like Arch Linux if I want the latest stable program.

2. How is that latest stable version from upstream different from the package available from Ubuntu default repository besides the fact that it is made to be guaranteed to work for a user that uses only default repositories (in terms of potential dependency-related conflicts)? I read that it gets "optimized/faster" or "made to work better" but this is quite vague and doesn't help me understand what packaging for a distro entails other than what was previous mentioned.

Thanks![/FONT]

---

### Post by grahammechanical on 2015-03-31
Latest and stable are not compatible terms, in my opinion. We get a new release of Ubuntu every 26 weeks and it is in these new releases that we get newer versions of applications. The exception to this are Firefox and Libreoffice which get updated during the support period of the version of Ubuntu we are using. There maybe one or two other applications that this applies to but I am not aware of them.

As I understand it Arch will give you the latest, but not necessary the latest stable packages. The Arch wiki says this

> [FONT=sans-serif]Based on a rolling-release model, Arch strives to stay bleeding edge, and typically offers the latest stable versions of most software.[/FONT]

Keep in mind that sometimes the "bleeding edge" has blood on it. That is why it is called the "bleeding edge."

> [FONT=sans-serif]**Arch Linux targets and accommodates competent GNU/Linux users by giving them complete control and *responsibility* over the system.**[/FONT]
[FONT=sans-serif]Arch Linux users fully manage the system on their own. The system itself will offer little assistance, except for a simple set of maintenance tools that are designed to perfectly relay the user's commands to the system. Arch developers do not expend energy re-inventing GUI system tools; Arch is founded upon sensible design and excellent documentation.[/FONT]
[FONT=sans-serif]This user-centric design necessarily implies a certain "do-it-yourself" approach to using the Arch distribution. Rather than pursuing assistance or requesting a new feature to be implemented by developers, Arch Linux users have a tendency to solve problems themselves and generously share the results with the community and development team – a "do first, then ask" philosophy. This is especially true for user-contributed packages found in the Arch User Repository – the official Arch Linux repository for community-maintained packages.[/FONT]


> [FONT=sans-serif]The Arch Linux system places precedence upon elegance of design as well as clean, correct, simple code, rather than unnecessary patching, automation, eye candy or "newbie-friendliness." Software patches are therefore kept to an absolute minimum; ideally, never. Simple design and implementation shall always trump simple user interface.[/FONT]

Whether Arch is for you is for you decide. It is not for me.

Keep also in mind that different software projects have different development schedules. For example, Gnome has just released Gnome 3.16 but it will not be in Ubuntu 15.04 because Ubuntu's Feature Freeze deadline has already past. So, do not expect Ubuntu Gnome to have Gnome shell 3.16 until the release of Ubuntu Gnome 15.10 or even 16.04. There are only so many hours in a day and even developers have a life to experience.

Regards.

---

### Post by ian-weisser on 2015-03-31
> **garycheng12 said:**
> 1. In general, how much of a delay is there between when the latest stable version of programs direct from upstream is released and when Ubuntu packages it for the default repository (where it is deemed stable)?

Difficult to provide a single, simple answer.

Let's say an upstream project releases on January 1.
Let's assume the Debian volunteer maintainer finds out the same day...but has their own busy life, and gets around to packaging the new release around January 15...but it could easily be March 15 or July 15.
The package goes to Debian Unstable, and a couple testers try it out and discover some bugs. The maintainer patches the bugs around January 30...or perhaps February 15.
More testing, and the package migrates to Debian Testing, eligible for import into Ubuntu, around February 18.
Oops. Ubuntu's deadline (Debian Import Freeze) was February 17th. The new release missed the April Ubuntu release. It will be in Ubuntu's October release.

How long it takes an upstream release takes depends upon, among many other factors:
- When during the year the upstream release takes place.
- Whether it's imported from Debian or uploaded directly.
- How long it takes to get packaged and tested by Debian volunteers


> **garycheng12 said:**
> 2. How is that latest stable version from upstream different from the  package available from Ubuntu default repository besides the fact that  it is made to be guaranteed to work for a user that uses only default  repositories (in terms of potential dependency-related conflicts)?

Also many possible answers. Package maintainers do a *lot* of work.

Let's use one of my favorite games as an example.
- The user data directory does not use an expected name
- One source file is copyrighted, not properly licensed, and therefore non-distributable.
- The upstream source lacks a .desktop file
- The upstream source lacks a manpage for one shell command
The packager fixes all of those problems, ranging from trivial to tough, so the software works the way you expect it to work.

Feel free to install a bunch of upstream binaries directly for a while, and you will discover lots of rough edges that the package managers smooth over.

---


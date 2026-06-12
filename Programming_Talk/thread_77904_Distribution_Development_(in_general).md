---
title: "Distribution Development (in general)"
date: 2005-10-17
forum: Programming Talk
---

### Post by felly on 2005-10-17
To further appreciate what the Ubuntu developers do, I'd be interested in hearing the details about what's really involved in making this distribution, and perhaps distributions in general.

I know that the packages basically come from the open source world at large, but I also know that there's much more to a distribution than just a bunch of packages, I'm just a bit hazy on those details.

So here's a preliminary list of what is involved.  Please fill in details and corrections to this list:
[LIST]
[*]package management : creating .deb packages and checking dependencies?
[*]installer
[*]initialization scripts
[*]adding new packages
[*]coming up with good default settings for packages
[/LIST]

anything else?

Thanks

---

### Post by UbuWu on 2005-10-19
* Translations
* Lots of bugfixing

---

### Post by felly on 2005-10-19
what sort of bug fixes?  bug fixes to the source packages? isn't that the job of whoever's maintaining the source?

for instance, are you saying that if there were a bug in libgtk, the ubuntu developers are fixing it?  if so, is it the fix merged back into the libgtk source control system?  or is it a specialized version just for ubuntu?

if not, what programs are the ubuntu developers bug-bashing?

---

### Post by UbuWu on 2005-10-20
[QUOTE=felly]what sort of bug fixes?  bug fixes to the source packages? isn't that the job of whoever's maintaining the source?
[/QUOTE]

Both that and problems specific to ubuntu. Also they add a lot of small improvements.

> 
for instance, are you saying that if there were a bug in libgtk, the ubuntu developers are fixing it?  if so, is it the fix merged back into the libgtk source control system?  or is it a specialized version just for ubuntu?


Yes, they do that, and often the patches are sent upstream to debian and the developers of the application if they are not ubuntu-specific.

Have a look around in [Bugzilla]("http://bugzilla.ubuntu.com") if you like to get an idea about what bugs keep the ubuntu developers busy.

---

### Post by az on 2005-10-20
Launchpad.net

Bugzilla is no longer used.  Malone is the bug-tracking system now and you can find it on launchpad.net.

---

### Post by UbuWu on 2005-10-20
[QUOTE=azz]
Bugzilla is no longer used.  Malone is the bug-tracking system now and you can find it on launchpad.net.[/QUOTE]

That is a little premature statement, the switch to launchpad/malone hasn't been made yet. At the moment, bugzilla is still in use, although it probably won't take long anymore...

---

### Post by az on 2005-10-21
For Hoary, everything in universe used Malone amd main still used bugzilla.  For Breezy, everythying now uses Malone.  This has been stated several time on the mailing lists.

Quote launchpad.net:

"Most Active Projects
 The Ubuntu Distribution [View]

Ubuntu is a Linux distribution that emphasises ease of use and free global distribution. The project uses the Launchpad for all translation and bug tracking. 
"

---

### Post by UbuWu on 2005-10-23
[QUOTE=azz]For Hoary, everything in universe used Malone amd main still used bugzilla.  For Breezy, everythying now uses Malone.  This has been stated several time on the mailing lists.
[/QUOTE]

Everything will use malone, but the transition hasn't happened yet (although it is now possible to file bugs against packages from main in malone). First, all bugs from bugzilla need to be transferred to malone.

[http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012065.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012065.html)

---

### Post by UbuWu on 2005-10-23
#ubuntu-motu 23/10:
> 06:27	LaserJock	is bugzilla still being used or is it completely replaced by Malone?
06:28	moyogo	LaserJock: bugzilla is still being used
06:28	moyogo	LaserJock: but new bugs only go to malone, i think
06:29	Lathiat	the idea is to phase bugzilla out in dapper
06:29	Lathiat	i think
06:29	Amaranth	afaik bugzilla is still the place to go for main bugs right now
06:30	Amaranth	i haven't seen a mail to the lists about using malone

---

### Post by az on 2005-10-24
[QUOTE=UbuWu]Everything will use malone, but the transition hasn't happened yet (although it is now possible to file bugs against packages from main in malone). First, all bugs from bugzilla need to be transferred to malone.

[QUOTE]

You are right.  As well, the "report a bug" tool in Breezy brings you to Bugzilla.

My bad.

---


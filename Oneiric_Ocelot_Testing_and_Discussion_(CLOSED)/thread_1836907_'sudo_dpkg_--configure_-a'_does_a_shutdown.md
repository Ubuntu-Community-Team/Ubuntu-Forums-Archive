---
title: "'sudo dpkg --configure -a' does a shutdown?"
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-08-31
Did an apt-get update on Oneiric install a couple days old and was updated O.K. yesterday.  Today:

sudo apt-get update
........blah blah
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a'

So I do:

sudo dpkg --configure -a

which promptly shuts down Oneiric.  Three times.  Then recovery mode hits the same problem.

?

Jerry

---

### Post by garvinrick4 on 2011-09-01
What happens when you run it from another install in chroot to /mnt with /dev/ /dev/pts/ /sys/ /proc/ bound and with internet connection?
Will it complete the dpkg --configure -a  and can go on to update and upgrade.
Just a thought.

---

### Post by jerrylamos on 2011-09-01
> **garvinrick4 said:**
> What happens when you run it from another install in chroot to /mnt with /dev/ /dev/pts/ /sys/ /proc/ bound and with internet connection?
Will it complete the dpkg --configure -a  and can go on to update and upgrade.
Just a thought.

Thanks, I'll mull it over.  I've done a little chroot from one pc to another over the net when compiz killed xorg and the keyboard, but the kernel was still running.

I'll try an install since I do those  frequently with unstable software.

Jerry

---

### Post by garvinrick4 on 2011-09-01
> I'll try an install since I do those  frequently with unstable software.
That will cure what ails you for sure. Have a nice day.

---

### Post by jerrylamos on 2011-09-02
Installed Beta 1 no recurrence of Title problem.  That was with a 23 August kernel which Daily Build has just updated this week.

Beta 1 had couple of the usual Oneiric bug failures which wouldn't report because of "downlevel packages"(!), so I booted in recovery mode, did "fix broken packages" which got a whole pile of updates(!), rebooted and only got one of the usual bugs that's been around for weeks.

My fast 3.33 mHz Intel tower gets the most Oneiric bugs.  After all Oneiric is unstable at this point.  Stable Narwhal, Meerkat, Lynx run just fine.  Zoom.

My 1.6 gHz AMD notebook has less Oneiric bugs. I haven't tried 64 bit on it lately after a forum post was not favorable, either more memory or more disk space or both I forget which. Haven't tried "proprietary drivers" on it after some trouble getting them to install on Oneiric a while ago.

I'll try Oneiric on this Acer Aspire netbook again later.  It'll run Unity-3D but I usually run Unity-2D because of all the Compiz overhead even when I'm running full screen applications like I usually do on this small screen.  

What Compiz is doing in the background escapes me because all the shading, transparency, fancy effects are not even visible.  If in full screen application mode Compiz should shut off.  Period.  Usual Microsoft solution is to require ever faster and faster hardware and more and more memory.

Anyway having fun and learning linux with the unstable Oneiric.  What's the next unstable release called?

Jerry

---

### Post by jerrylamos on 2011-09-13
Updated yesterday as usual like all week.

Update message said:

sudo dpkg --configure -a

pc powered down.  Compaq Presario 3.33 gHz Intel Celeron D.

Booted up in recovery mode, tried fix broken packages.

Repeat from Update above.

Tried again today.  Repeat from Updae above.

zsync daily build today & re-install.

Jerry

---


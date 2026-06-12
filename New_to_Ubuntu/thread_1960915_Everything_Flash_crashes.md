---
title: "Everything Flash crashes"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by PopPops on 2012-04-18
Hello Friends

I have a problem that Adobe Flash always crashes, whether in Chromium, Firefox or other programs like HMRC's "Basic PAYE Tools" etc.  The last time PAYE Tools worked was 01 April 2012, there has been a Flash update since.

Only Chromium gives an error message "The following plug-in has crashed: Shockwave Flash", the others just crash and disappear.  The problem seemed to start with one of the recent updates to Firefox, which became very unstable, but the recent update to Flash stopped everything working.

I have uninstalled and reinstalled Flash many times and using different methods, the last using the Flash-Aid add-on.

I am very much a beginner with Linux and now do not know where to look for diagnostics, or what I could reinstall or purge to try to solve this.  Unfortunately I do need to use the tax software to keep my Company running, so I have had to resort to borrowing my wife's Vista laptop.

I am using Ubuntu 10.04 and Adobe Reader 9.4.

Thanks in advance.

---

### Post by dzponce11 on 2012-04-18
Hi!
Actually, your problem is that the newest flash plugins are for the newer releases. Why not try upgrading and see if it works.

~~~~dzponce11

---

### Post by PopPops on 2012-04-18
Thanks !  This is where my lack of knowledge shows.  I'm surprised that Update Manager allowed the install of a non compatible version.

Could I not downgrade Flash as the tax tools have a known problem with the Unity desktop?

Regards.

---

### Post by dzponce11 on 2012-04-18
Very welcome.

~~~~dzponce11

---

### Post by tmaranets on 2012-04-18
The upgrade manager allowed the download because 10.04 is LTS and it works with some new packages.

---

### Post by PopPops on 2012-04-18
Thinking about this, this is crazy.  10.04 is LTS.  So what's the purpose of the Update Manager if you can't install updates in case they are for later versions?

How do I know what updates I can safely install?  LTS surely means Long Term Support?

Can I be the only one who has installed the updates to Firefox and Flash considered essential by Update Manager.

Now very confused, and not a little disillusioned....

Regards.

---

### Post by Andrew_P on 2012-04-18
> **PopPops said:**
> Now very confused, and not a little disillusioned...

Macromedia/Adobe Flash has been a "problem child" since Macromedia acquired it and started tinkering with it 17 years ago.  I've regularly dealt with "upgrades" that break my system, both on Windows and Linux.  Nine times out of ten, or more frequently, when Firefox or SeaMonkey crashes, it's caused by the Flash plugin.  The solution in most cases, I have found, is to downgrade to the last version of Flash known to work, be it a month ago or six months ago, and then refuse "updates" from Adobe for several months or until Web sites start complaining that my version of Flash is too old.

Around the end of March Adobe pushed out a version of Flash that didn't crash, but no site that used Flash would display any Flash content whatsoever.  The place where the content was supposed to be was just a blank spot on the screen.  This was a big problem for me, because I need to access some Web services that (stupidly) have been designed around Flash.  I rummaged around on my hard drive and found an earlier version of the Flash plugin (libflashplayer.so), from mid-February 2012, and replaced the latest version with the earlier version.  Instantly, Flash content was working as before.

Incidentally, after Flash Player 11.2 (February 2012), Adobe has dropped support for Linux via the Netscape Plugin (NPAPI).  All they'll provide for the next five (5) years is security patches.  Google will still have flash in Chrome via the newer Pepper Plugin (PPAPI), but Mozilla has not and apparently refuses to go that route for Firefox and SeaMonkey.  Since Adobe seems to hate Linux (or is at least indifferent toward it), we shouldn't expect any meaningful support from them anymore.  Besides, if they've been trying to fix the bugs and memory leaks in Flash for nearly two decades without success, it's obvious that they never will.  For more, see [http://www.tuxgarage.com/2012/02/adobe-drops-support-of-flash-for.html]("http://www.tuxgarage.com/2012/02/adobe-drops-support-of-flash-for.html").

---


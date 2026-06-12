---
title: "[SOLVED] Install from source: Conky. Did it work?"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by HavocXphere on 2008-10-11
Hi

I'm trying to do my first install from source, and I *think* it went through OK...but I'm not sure.

What I did:
[LIST=5]
[*]Installed conky via adept...some old version
[*]Grabed conky source of sourceforge
[*]Removed old conky via adept
[*]Installed all the stuff that ./configure said is missing
[*]Ran sudo make install
[*]Ran clean install...this didn't fly
[/LIST]

Now if I type conky into the run box, it launches.

**The problem is**, I can't figure out whether this is the one I installed, or still a fragment of the old one. Still looks the same and there is no version number. I didn't see a conclusive "Install went OK" message. Worse still, adept says conky isn't installed...but it clearly is cause it runs.:confused:

Is there some sort of flush command I need to execute to be 100% certain that an app is really uninstalled?

I've attached the konsole session which I used when installing...I don't know which parts you guys need so everything is in there. I'd guess the important bit is at the end though. Some of the libs were installed via adept though...I've also got a list of everything I installed if that helps.

btw, whats up with the crazy filesize restriction on .txt files? I ended up compressing it.

Thanks

---

### Post by Asham on 2008-10-11
I think if you compile applications yourself they don't show as installed in adept or the equivalent package manager. You also don't get security updates unless *you* keep uptodate with the application. 

There are pros and cons of installing from source. If only there were a package manager that installs from source and optimizes the compiler during the process!

---

### Post by HavocXphere on 2008-10-11
I've figured out the conky settings...and its definitely the installed-from-source one.\\:D/

> **Asham said:**
> I think if you compile applications yourself they don't show as installed in adept or the equivalent package manager.
:( That kinda sucks..but I guess its understandable.

Thanks

---


---
title: "anyone know how to write a gaim plugin?"
date: 2006-01-01
forum: Programming Talk
---

### Post by earobinson on 2006-01-01
anyone got a good tutorial on writing gaim plugins? Im a good programer just havent writen many plugins and would like to write one for gaim, that emails all my convos to an email.

Note: havent done any forum searching for this yet feeling lazy sorry, did a bit of googling however only a bit.

---

### Post by Hanj on 2006-01-02
Here's a small tutorial on how to write plugin in C: [http://gaim.utcr.org/c-howto.html](http://gaim.utcr.org/c-howto.html)
There are also tutorials for Perl and TCL.

---

### Post by earobinson on 2006-01-02
thanks... ill look into it

---

### Post by earobinson on 2006-02-26
any ideas how to do this in python?

---

### Post by majikstreet on 2006-02-26
[QUOTE=earobinson]any ideas how to do this in python?[/QUOTE]
*wonders same*

anyway, I vaguely remember something about gaim and python *looks it up*
[http://pygaim.sourceforge.net/](http://pygaim.sourceforge.net/)
i think it was made during google's summer of code

---

### Post by celloandy on 2006-02-26
I'm not sure about Python, and I don't think that the Gaim project, itself, has ever released an official Python plugin system, but just FYI, I know that Gaim 2, once it's out, will have a rewritten Perl plugin system, as well as a loader for plugins written using Mono (and, in theory, I guess, IronPython).  They're also, as I recall, replacing the old gaim-remote system with a new set of DBus interfaces, so it may be possible to write a separate program using the Python DBus bindings, and have it manipulate Gaim over the bus, rather than writing a plugin.  I'm not really sure what you're trying to do, exactly...

Andrew

---

### Post by earobinson on 2006-02-26
Intresting hey did you guys know you can [only send 500 emails a day via gmail ]("http://earobinson.blogspot.com/2006/02/gmail-email-limit.html")

---

### Post by earobinson on 2006-02-27
So I wrote a first stab at a program to go through the logs dir and email them to me, eventual ill write one for C++ and it will be a real gaim plugin.

ne ways check it out give me some feedback [http://earobinson.blogspot.com/2006/02/email-chat-history-parser-beta-real.html](http://earobinson.blogspot.com/2006/02/email-chat-history-parser-beta-real.html)

---

### Post by majikstreet on 2006-02-28
*posted a comment on that blog post*

---

### Post by torf on 2006-05-28
I started to check out how to write gaim plugins in perl with this:
[http://gaim.sourceforge.net/api/perl-howto.html](http://gaim.sourceforge.net/api/perl-howto.html)

I hit a bump in the road with just the first code example. After creating the file, "perltest.pl" I moved it into /usr/lib/gaim.  However, when I start gaim it isn't available as a plugin.  I ran gaim with the debug flag, and saw that it probed perltest.pl as a possible plugin.  Any ideas?

Update: Is perl support disabled? If so, can it be enabled when I'm using the standard ubuntu pacakge?
[http://sourceforge.net/mailarchive/forum.php?thread_id=6290972&forum_id=9587](http://sourceforge.net/mailarchive/forum.php?thread_id=6290972&forum_id=9587)

---


---
title: "Thinking of Starting a Free Source Code Hosting Provider for Ubuntu/Linux Developers"
date: 2007-08-09
forum: Programming Talk
---

### Post by samb0057 on 2007-08-09
I'm thinking of starting a website that provides free hosting to linux developers who need an svn/cvs server to store their code. Like a small-scale version of sourceforge.

I don't know too much about SVN, can anyone tell me what kind of tools I'll need, and how to integrate them? What would you look for in a source code hosting provider?

---

### Post by CptPicard on 2007-08-09
How much resources do you have to dedicate to this? Do you have nuke-proof filesystems? Can you RTFM about SVN and become a total guru about it, so that I'd trust my precious code to your project, instead of using something established and trustworthy such as sourceforge?

---

### Post by Jessehk on 2007-08-09
google code project hosting has a nice simple system that is great if you don't need the features of sourceforge. 

[http://code.google.com/hosting/](http://code.google.com/hosting/) :)

---

### Post by strider1551 on 2007-08-09
Well, I for one have learned a ton of stuff by doing projects that never amounted to anything and were way over my head.  As long as you're not putting all your hopes and dreams into having a site as famous as Sourceforge, I say good for you!

> I don't know too much about SVN, can anyone tell me what kind of tools I'll need, and how to integrate them?
The only package you will need to install is "subversion".  Of course, the server will need to be accessible, so that means either a static ip address or a service like dyndns.com (I assume you know that, though).  Other than that, do some Google searches and learn how to use svn yourself.

> What would you look for in a source code hosting provider?
Stability.  I want to know that it is always available and has reliable backups.  If you loose my code in a freak accident I will hunt you down and unleash my wrath.  Also, you personally need to be available.  I shouldn't have to wait more than a day to get a response on something, nor should changes (down time, etc) be done without plenty of forewarning.  Other than those two, letting other people browse the repository through a web browser is always a plus.

As was recently mentioned somewhere else on this forum, open source projects are best started to do something you personally need.  It keeps you motivated and keeps you exposed to your own work like the other users.  If you really want to try this, use your server for your own stuff, and maybe convince others you know personally to use it (even as a backup!).

---

### Post by CptPicard on 2007-08-09
I for one can't fathom why someone would want to tie themselves up with something that requires this much availability, stability and commitment.

Isn't this just a huge load of work, with the risk that a LOT of people will hate you if you let them down?

---

### Post by AlexThomson_NZ on 2007-08-09
What I would find useful is not so much a version control system, but a simple site where I can upload my projects/source as a simple .tar.gz, where I can point people to who want to try it out.

This would be quite handy I image for smaller (probably one-man) projects

---

### Post by CptPicard on 2007-08-09
Wouldn't running a static html site suffice?

---

### Post by pmasiar on 2007-08-09
> **AlexThomson_NZ said:**
> a simple site where I can upload my projects/source as a simple .tar.gz, where I can point people to who want to try it out.
get a free wiki at pbwiki.com. you can create mini-docs, upload files, etc. Perfect for 1-man projects IMHO

---

### Post by AlexThomson_NZ on 2007-08-09
Hey that sounds like just the ticket!  Cheers for the pointer :)

---


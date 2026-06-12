---
title: "Eclipse PDT + Local Apache Config"
date: 2012-12-12
forum: Programming Talk
---

### Post by svtguy88 on 2012-12-12
Hey everyone --

I've done a lot of reading online, but I can't get my development environment set up quite the way I'd like.  I'm trying to configure local PHP debugging via Eclipse PDT/xdebug.

Right now, apache has an "available-site" entry that points to "/home/user/workspace/eclipseProjectName" and this does work -- I can launch projects and step through PHP code using Eclipse.  However, this approach requires me to make a new "available-site" entry for each Eclipse project that I want to debug.

Typically, I'm only working on one or two projects, so this isn't a really big deal, but I'd like to instead have one "available-site" that points to "/home/user/www" (or wherever I put it), and then have Eclipse map each project to that folder when I debug.

I've played with the "Path Mapping" settings in Eclipse's PHP server config, but I can't get it to work -- trying to launch a debug session always results in a file not found error.

Maybe someone here can shed some light?  It took a LONG time to get PDT working correctly -- the documentation is less than stellar.  Getting this path mapping to work is the last thing I need to tweak in my dev environment.

---

### Post by svtguy88 on 2012-12-14
No one?

There's got to be someone out there doing PHP work via Eclipse/PDT...

---

### Post by svtguy88 on 2013-01-10
Bueller...?

---


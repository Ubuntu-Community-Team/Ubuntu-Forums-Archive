---
title: "Bluefish search and replace question"
date: 2006-07-11
forum: Programming Talk
---

### Post by Peepsalot on 2006-07-11
I'm doing a search and replace, with a prompt before replace.  I find it really annoying that the prompt moves every time you click it.  Is there a way to get it to stay in one damn spot?

---

### Post by oldmanstan on 2006-07-12
i tried it out myself and the way the box moves would seem to suggest that it is moving because another child window is being created (notice that if you imagine none of them disappearing they would be cascaded).

this is probably a problem in the bluefish code, try the bluefish web site (bluefish.openoffice.nl) to post a bug report or at least a request for them to change it

---

### Post by Peepsalot on 2006-07-12
Well, i found out that this issue is fixed in the latest version 1.0.5.  
> Fixes the moving replace dialog. Closes Bluefish bug #323183.
Unfortunately the version I have is 1.0.4.  I think it was installed via Automatix.  
I can't find binaries for 1.0.5 anywhere, I guess I'll have to build it from source?   I have a feeling dependencies are goin to kill me.  Or maybe ask the Automatix admins to update the repos.:-k

---

### Post by ifokkema on 2006-07-12
> **Peepsalot said:**
> I have a feeling dependencies are goin to kill me.
Not necessarily. Have you ever compiled stuff before? You may need lots of *-dev packages, but it's usually quite easy to find out which ones you need. Mostly just running ./configure, reading the error messages, installing the necessary *-dev package to make that error go away, and run ./configure again.

It the new version of Bluefish is much better, they might release it through backports, though.

---


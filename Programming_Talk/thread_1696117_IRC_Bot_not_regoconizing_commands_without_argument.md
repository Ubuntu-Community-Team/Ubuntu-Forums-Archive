---
title: "IRC Bot not regoconizing commands without arguments"
date: 2011-02-26
forum: Programming Talk
---

### Post by gluxon on 2011-02-26
I'm working on a PHP bot for my IRC channel. It works extremely well, but I have one problem that I just can't figure out. For commands that don't take arguments, gluxonbot doesn't recognize them. For example, in the code below, entering ".time" in the channel won't work, however ".time bob" works fine.

[http://gluxon.pastebin.com/fwQNmrCp](http://gluxon.pastebin.com/fwQNmrCp)

I've been scratching my head for days trying to figure out what the problem is. If any of you could look at it, thanks.

---

### Post by gmargo on 2011-02-27
Your input lines coming from the IRC server are terminated with CR-LF.  Those are not stripped by the **fgets()**.  That's why ".time " (.time followed by a space) works but ".time" does not - it's because the string is really ".time\r\n".

---

### Post by gmargo on 2011-03-02
Interested in IRC bots?  There is an Ubuntu Developer Week presentation on "Developing IRC bots", today at 19:00 UTC, or about 3 hours from now.

[https://wiki.ubuntu.com/UbuntuDeveloperWeek](https://wiki.ubuntu.com/UbuntuDeveloperWeek)

---


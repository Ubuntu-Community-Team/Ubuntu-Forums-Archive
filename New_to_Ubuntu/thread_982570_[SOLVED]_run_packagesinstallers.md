---
title: "[SOLVED] run packages/installers"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by LinuxFox on 2008-11-14
Sorry for the pointless question, but where can I read about the .run package format?  I used a .run package to install a small game today, and I wanted to learn more about the format.  Please tell me where I can read more about it.

I tried to Google it, but it assumes I want to "run a package" literally. :P

---

### Post by bswilson on 2008-11-14
Well, in your case the .run file extension has no meaning.  Unlike in Windows, the file extension doesn't really mean anything to the computer.  It's a fabrication that humans use to help identify files.

Let me guess, you ran a command like `sh ./install_this_game.run`, right?  If so, you're just executing a shell script, and the .run doesn't mean anything.

---

### Post by cariboo on 2008-11-14
For more in fon on .run files look here:

[http://filext.com/file-extension/RUN](http://filext.com/file-extension/RUN)

There should be enough info to keep you busy for a while.

Jim

---

### Post by LinuxFox on 2008-11-14
> **cariboo907 said:**
> For more in fon on .run files look here:

[http://filext.com/file-extension/RUN](http://filext.com/file-extension/RUN)

There should be enough info to keep you busy for a while.

JimThanks, I'll take time to look through it.

bswilson, actually it was a file I double-clicked and it opened up an installer.  An installer kind of like a Windows one, except for Linux.

Edit: I read through the link and it is a shell script that's a self-extractable archive.  Thanks

---


---
title: "Update with no name nor tech details?"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by Barkester on 2013-08-29
Software Updater has for two days now been prompting me to update. Its asking for permission now. Its 40 kb with absolutely no other info. I'm not running a bank, but security does concern me. I need it's name and technical details before I can install it. 
   Anybody else get this? What is it or how else might I trace it?
   Is Software Updater so secure that I can happilly take their word for it or could it be a vehicle for "things" if not monitored?

   Perhaps my previous life as a Windows user (death by blue screen) is making me over careful. Probly someone forgot the lables is all.

   Thanks for any replies.

---

### Post by Ginz on 2013-08-29
I noticed blanks in the Software Updater as well. I have no idea why it happens, but if you want to see what is to be installed you can use this in the terminal:

```

sudo apt-get update
sudo apt-get -s upgrade

```

This will simulate an upgrade of packets without actually modifying anything. If you want to proceed and install the updates you can just drop the -s from the commands above.

---

### Post by Barkester on 2013-08-30
Thanx a bunch. Shoulda known the shell'd have the answer.

---

### Post by newb85 on 2013-08-30
The same happened to me.  I waited a day and the details showed up in the Updater again.  Minor glitch, I guess.  It was only an update for Google Chrome.

---

### Post by Jonathan Precise on 2013-08-30
If the situation got solved, the mark it as solved, so people know that the problem is over.

---


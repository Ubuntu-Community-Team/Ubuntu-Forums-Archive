---
title: "Question with apt-get remove of my DEB package."
date: 2010-10-31
forum: Packaging and Compiling Programs
---

### Post by hakermania on 2010-10-31
Debian policy says to keep our files at /usr/share/ and then copy them to $HOME directory at first application run. I have made a DEB of my application that does exactly this.
The problem is that when I'm running apt-get remove to remove my DEB it does remove the files in /usr/share/ but it does not remove the files that have been copied to the $HOME folder (specificaly in ~/.config/) I think this is not normal. If it isn't normal, how do I remove all files that have been stored to home folder by unistalling the DEB?:confused:

---

### Post by mc4man on 2010-11-02
> If it isn't normal
I'd say it's normal behaviour

---


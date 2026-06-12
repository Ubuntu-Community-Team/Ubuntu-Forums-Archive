---
title: "Log in page"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by susanpenter on 2008-10-23
something very strange has been happening over the last couple of days, I have now opened flock and it has auto logged me in straight away and yet when I come to the forum in Firefox the name box is stuck solid saying username and isn't editable, the password box works as you would expect a form field to work.

Any ideas?

Susan

---

### Post by billgoldberg on 2008-10-23
> **susanpenter said:**
> something very strange has been happening over the last couple of days, I have now opened flock and it has auto logged me in straight away and yet when I come to the forum in Firefox the name box is stuck solid saying username and isn't editable, the password box works as you would expect a form field to work.

Any ideas?

Susan

Hmm, back up your passwords/bookmarks!

And reinstall firefox.

Open up a terminal (applications -> accessories -> terminal) and copy/paste this code

```
sudo apt-get autoremove firefox --purge && sudo apt-get install firefox
```

If it still happens do the same for flock. But I'm not sure flock is in the repo.

If you installed it from a .deb file or something, remove the flock folder in /home/username/.flock (.flock is a hidden folder, in the home folder press "ctrl + h" to see it) and use synaptic (system -> administration -> synaptic package manager) to remove flock.

Then install it as you did the first time.

---

### Post by susanpenter on 2008-10-23
Before I do this can I double check that it will definately give me the up to date Firefox 3 and also can I back up all my extensions or will I have to make a note of them and redo them all again.

Flock is working fine so I see no need to re-install it, FF is working fine except for in this one site.

Cheers

---


---
title: "Can I override a repository warning?"
date: 2018-11-30
forum: New to Ubuntu
---

### Post by cybervigilante on 2018-11-30
I sometimes get a warning like this for a repository that has been well-used and I am sure is okay, such as one that was allowed in Mint but not here, previously - although it is now. I think it was Safeeyes. Is there any way to override this?

E: The repository *** does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.

I tried --allow-unauthenticated but that wasn't recognized by the add-apt-repository command.

---

### Post by oldos2er on 2018-12-01
If you're sure your sources are all in order, try ```
sudo rm /var/lib/apt/lists/*

sudo apt update
```

---


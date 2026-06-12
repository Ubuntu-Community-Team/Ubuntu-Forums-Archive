---
title: "Skype on Ubuntu 12.10"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by JerryGomez on 2013-04-12
:confused: Extremely newbie! Need assist on why I can't load Skype on Ubuntu 12.10, it wont load up the program string on the command propt?

---

### Post by tsukiyomi on 2013-04-12
How did you installed skype? Did use used Software Center?

---

### Post by Routhinator on 2013-04-12
More info is needed here, however lets try something simple. We'll clear all the files off from skype and do a fresh reinstall.

```

sudo apt-get autoremove --purge skype
rm -R ~/.skype
sudo apt-get install skype

```

This will remove skype, any packages that were required by it, and their config files. This will also remove the skype settings in your home directory in case they are corrupt. And then it will reinstall skype, along with the packages you removed, and their fresh config files from the repos.

This should resolve any issues. If there is still and issue, open a terminal and run 'skype' and paste the output here so we can see any error.

---


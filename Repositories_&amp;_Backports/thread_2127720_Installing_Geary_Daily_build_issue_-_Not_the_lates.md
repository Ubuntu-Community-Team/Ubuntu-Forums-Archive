---
title: "Installing Geary Daily build issue - Not the latest version."
date: 2013-03-20
forum: Repositories &amp; Backports
---

### Post by epikvision on 2013-03-20
Hello, 

I've been having trouble lately with installing the daily build from geary.  First of all, I did the following on my terminal, which would get me the latest daily build.
```

sudo apt-add-repository ppa:valateam/ppa sudo apt-add-repository ppa:yorba/ppa sudo apt-get update && sudo apt-get geary

```

Recently, Yorba has released Geary 0.3.  But when I installed Geary, the About window shows me 0.2.2+ trunk when it should show 0.3. Perhaps, there is an issue with the package management. I ran this on Ubuntu 13.04 daily build, which updates fine.

I thought by uninstalling geary and installing from scratch would fix the problem, but it doesn't seem that straightforward.
```

sudo apt-get purge geary && apt-get autoremove

``` 
The code removes the app, but doesn't remove any configuration whatsoever.  For instance, on a fresh install, my 4 email accounts that I set up were still there.

I really wish to run the daily build on my computer, and I don't want to be stuck with what really isn't 0.2.2+ trunk.  How can I troubleshoot this issue and install the daily build?  One solution I have is to reinstall the Ubuntu daily build, but I think it's unnecessary.

---


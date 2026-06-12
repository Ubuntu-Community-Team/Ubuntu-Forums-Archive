---
title: "Failure to lock"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by jmghist on 2008-08-03
I am fairly new to Ubuntu and have really liked it so far, but have encountered a very annoying problem.  I installed version 7 on my computer.  Installation went fine.  Upgraded all the packages (210+) and that went fine.  Downloaded and tried to install hplip-2.8.7.run and it goes for awhile and then gives me a "failed to lock" error message.  Have tried all the suggestions in the forums I have found.  removing the lock file from dpkg and such, but no luck.  Thought of upgrading to 8.04 using the update manager and again get "failed to lock /var/cache/apt/archives/lock".  Have reinstalled Ubuntu several times, always encountering the same problems.  Know that nothing else is running.  Very frustrated.:(  Any suggestions?:confused:

---

### Post by hansdown on 2008-08-03
Hi jmghist. Is this what you are looking for? [http://www.google.ca/search?q=hplip-2.8.7.run+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=hplip-2.8.7.run+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)
There is an hplip in the repos that will automatically install. Also it will be updated if you have automatic updates turned on.
Go to system> administration> synaptic package manager.you can use the search bar to find hplip. The hplip toolbox is handy too. Don't forget to mark for upgrade any packages you select.Hope this helps.
Python-qt3 is something you probably need also for printing.

---


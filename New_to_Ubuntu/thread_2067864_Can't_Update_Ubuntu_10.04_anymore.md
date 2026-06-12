---
title: "Can't Update Ubuntu 10.04 anymore"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by Whippersnapper on 2012-10-07
Hello: I'm using Ubuntu 10.04 through Win XP thru WUBI, and have recently had problems updating through the update manager. I receive the following reply:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old :used instead.

Is their any fix, or time to update to the latest version 12.10?

Thanks

---

### Post by Bucky Ball on 2012-10-07
That appears to be a problem with the server as you're not the first person having issues with that repo. Maybe give it a couple of days or dig on their site for any clues.

---

### Post by jerrrys on 2012-10-07
Just uncheck it and you should be good to go

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Edit:  Or wait a couple of days  :)

---

### Post by Gone fishing on 2012-10-07
It's stalling on a non standard repository [http://ppa.launchpad.net/mozillateam](http://ppa.launchpad.net/mozillateam) just remove it from your repository list. I usually do this by hand or from synaptic (apt-get install synaptic), but I think if you type repository in dash a gui app to change repositories will appear.

Sorry working on a Windows box (ughh) at the moment.

---

### Post by Whippersnapper on 2012-10-09
Great! I got into software sources "other sources" and unchecked the offending source. Ran update manager, and I'm back in business. Consider this "SOLVED", but I don't know how to complete the process. Thank you to all who replied!

---

### Post by jerrrys on 2012-10-09
Good show  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Edit:  oops you figured it out

---

### Post by DuckHook on 2012-10-09
> **Whippersnapper said:**
> ...but I don't know how to complete the process.

Open Update Manager.
Navigate to "Settings>Other Software".
Highlight the PPA that you want to remove.
Click on the "remove" button.

---


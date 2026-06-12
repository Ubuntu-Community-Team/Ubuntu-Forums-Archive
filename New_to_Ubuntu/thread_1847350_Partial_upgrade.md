---
title: "Partial upgrade??"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by huggs on 2011-09-20
Ubuntu 10.10
Wubi install


I went into Update Manager, and there were some packages that could be updated.
I clicked the 'Install Updates' button, and a pop-up type window appeared telling me that
only a partial upgrade was possible, and that 2 packages would have to be removed.
The 2 packages are CompizPluginsExtra and xscreensaver.

There are quite a few packages that are to be updated. 

My question is, will I be able to reinstall xscreensaver and my compiz plugins after I
update, or would I be forever without them?

Also, I have always updated whenever Update Manager has popped up in the past telling me that I had updates available, and updating has resulted in an unbootable system a couple of times before, even on a fresh install. Since I have things set up pretty well how I like them now, how bad an idea would it be to just never use Update
Manager again? Would the older, outdated software I have now end up being incompatible with software I install say a year or two from now?

Mostly I guess I'd just like to know if I should go ahead with the partial upgrade, and if I'll be able to reinstall my compiz plugins and xscreensaver afterwards. Maybe too what if anything I can do to keep from having this happen to me again in the future??

TIA and sorry for a kinda unnecessarily long post   :wink:

---

### Post by wildmanne39 on 2011-09-20
Hi, it is best to wait until you can do an complete upgrade, often times a partial upgrade breaks things like update manager.

It is probably an issue that will be resolved in the servers in a short time.
Thank you

---

### Post by Crayz9000 on 2011-09-23
I've had this pop up twice now. The first time was after installing both gnome-session and gnome-shell, the update manager wanted to run a partial upgrade to remove gnome-session. I allowed it to remove those since I wasn't using them, and everything was OK.

The second time was after doing a manual install of the Canon drivers (cndrvcups-common and cndrvcups-ufr2), which I had to manually override the gs-esl dependency, since the package was renamed. I'm currently using those drivers for a Canon copier.

If I run aptitude from the command line, this is its output:

The following packages have unmet dependencies:
  cndrvcups-common: Depends: gs-esp which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     cndrvcups-common            
2)     cndrvcups-ufr2-uk

So it appears that if you manually override and install any packages that have "unmet dependencies", the updater prompts to do a partial upgrade to remove the offending packages.

---

### Post by wildmanne39 on 2011-09-23
Hi, here is a link that talks about partial upgrades and the risks.
[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)
Thank you

---


---
title: "Eclipse Issues (installing/uninstalling)"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by damonjablons on 2008-06-25
Hey Forumers,

I tried installing eclipse and had some issues with it.  I wasn't able to install updates from the PHPEclipse site.  So in order to fix this, I tried uninstalling Eclipse via Synaptic (complete removal), and completely removing any other files that said, "eclipse" on them.

Then I went and removed ~/workspace/ and all of its sub-folders.  I also removed the ~/.eclipse folder.

Now after reinstalling (via synaptic), the program won't even let me go to the update portion in the Help menu, instead it gives me this error:

```
Requested operation cannot be performed because it would invalidate the current configuration.  See details for more information.

(DETAILS)
Requested operation cannot be performed because it would invalidate the current configuration. See details for more information.  Platform configuration has been modified outside this program. A restart is recommended.
```

Even after several attempted restarts it still doesn't work.  Anyone got any ideas?  I appreciate the help.

Thanks in Advance,
Damon J.

---

### Post by Diabolis on 2008-07-14
It could be caused by a conflict between the java that comes installed by default in ubuntu and eclipse. Install the JDK directly from sun's page and choose it to be used instead of the default one.

```
sudo update-alternatives --config java
```

[there is a bug report about this]("https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/82422")

---


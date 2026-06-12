---
title: "attempted upgrade to Dapper wrecked synaptic?"
date: 2006-07-26
forum: Repositories &amp; Backports
---

### Post by spetey on 2006-07-26
Hi folks,

First, thanks for the awesome Ubuntu support!

Here's my deal:  I tried to upgrade to Dapper from Breezy on my home computer using the "new distribution release" option on the upgrade manager.  But each time I try it, I get a weird error message that flashes so quickly I can't see it.  (The distro upgrade worked fine on my office computer.)  The option remains in the upgrade manager, but I get the same quick error flash each time.

Meanwhile, in what I suspect is a related story, each time I try to upgrade or install packages, I get an error message (quoted below) in a separate window.

Any hints?

Also, I notice they're offering to upgrade my firefox to 1.0.8.  I've already followed the great forum directions to upgrade to 1.5.  So do I ignore the upgrade option?  How do I make the option go away?

Thanks again!
spetey

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


---

### Post by cilynx on 2006-07-26
What do you get if you do:
```

$ sudo apt-get update

```

---

### Post by spetey on 2006-07-26
Hi cilynx, thanks for the prompt response!

> **cilynx said:**
> What do you get if you do:```
$ sudo apt-get update
```

Huh, I don't know that option to apt-get, but I've attached the output of two successive runs.  (I'm relatively new to apt-get, having been a RedHat / Fedora person until recently, and though I'm a pretty long-time user, I was never much of a linux expert.)

After running that command twice, I tried the distro-update option in the update GUI again again.  Once again, it looks like it's downloading for a bit, then there's a quick splash of something and it's all over, with no update.

Thanks again for any thoughts!
spetey

---


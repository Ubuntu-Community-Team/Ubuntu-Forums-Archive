---
title: "Issue with MonoDevelop"
date: 2010-01-27
forum: Programming Talk
---

### Post by matthew.ball on 2010-01-27
Hey guys,

I have a rather annoying problem with MonoDevelop - the menu bar has gone MIA.

I had the version in the repos (not sure what numbers though, 2.1 perhaps?) when I lost the menu bar.
I thought it could have been an issue with that version, so I found the PPA for 2.2 beta or wherever it is at now, and updated.

Alas, the problem still remains.

I am running globalmenu so it could perhaps be a conflict with that, though even without globalmenu the menu bar doesn't come back. I am unable to find any other application which is affected the same way, which makes the issue even stranger I think.

When running monodevelop via console there are no errors regarding a menu bar.

I have tried sudo apt-get install --reinstall monodevelop - but I don't think that does entirely what I had hoped it does.
I think (re: hope!) a possible solution is to just completely purge it (which is what I thought the above command would do), and then re-install it, but I'm not entirely sure what commands would/should be used for that.

---

### Post by matmatmat on 2010-01-30
I had the same problem with globalmenu, the only way (it seems) to get the menu bar back is to uninstall globalmenu.

---


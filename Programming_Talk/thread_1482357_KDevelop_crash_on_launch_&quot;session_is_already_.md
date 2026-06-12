---
title: "KDevelop crash on launch: &quot;session is already active in another running instance&quot;"
date: 2010-05-13
forum: Programming Talk
---

### Post by 10101011 on 2010-05-13
When upgrading to Lucid (10.04), I added the backports repository and installed KDevelop.

On trying to launch KDevelop, I got the following error in a message box: "This session is already active in another running instance"

I looked around on the net and didn't instantly find a solution, so I wanted to note down the simple fix:

Change ownership of the .kde folder back your user, like so:
> sudo chown -R myusername:myusername .kde

For some reason, root was the owner.

---


---
title: "Missing Icon from my launcher"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by Colinvansmith on 2013-10-27
I just opened my computer and for some reason the dashboard icon has disappeared from my launcher. How do i open the dshaboard and how to i get it back on my launcher

thanks in advance

col

---

### Post by apollothethird on 2013-10-27
> **Colinvansmith said:**
> I just opened my computer and for some reason the dashboard icon has disappeared from my launcher. How do i open the dshaboard and how to i get it back on my launcher

thanks in advance

col

I can't tell you directly how to get your launcher back.  Someone else will chime in on that.  I have the same problem on one of my computers.  What I did for an immediate fix (workaround) was to install cairo-dock.  I also use cairo-dock on my computers where the launcher actual works.

More direct to your question, you might consider trying to reset your Unity back to it's defaults.  Try backing up your "~/.config/dconf/user" file then issue the command:

```

rm ~/.config/dconf/user

```

You'll probably have to logout and log back in for the user file to be rebuilt.

You can find other tips here:
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---


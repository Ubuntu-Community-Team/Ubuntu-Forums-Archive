---
title: "Eclipse in Edgy"
date: 2006-10-27
forum: Programming Talk
---

### Post by MrEricSir on 2006-10-27
If you're getting the "Error notifying a preference change listener" every time you try and launch Eclipse in Edgy, I have the solution for you.

Go into your workspace folder and delete (or rename) the .metadata folder.  This seems to do the trick.

Note: You have to do this EVERY TIME you want to run Eclipse.  This means re-creating your workspace from scratch.

Hope this helps y'all. :KS

---

### Post by ChrisHolt on 2006-11-09
This was not a problem until the most recent official release of edgy.  Is there a better fix?

---

### Post by Twiggy794 on 2006-11-13
Any news on a real fix for this?

---

### Post by Troels on 2006-11-21
Well, do not know I direct solution yet... At least if you are using CDT. Problem looks like being caused by CDT 3.0.1 is installed with Eclipse 3.2, but is only compatible with versions up until 3.1.

So, one solution is to delete/move all the org.eclipse.cdt* in your plugins directory (/usr/lib/eclipse/plugins)

---

### Post by Ramses de Norre on 2006-11-21
I had this already once and needed to reconfigure all preferences.. pretty annoying if you've got work to do.

---

### Post by Troels on 2006-11-21
There is a bug report on this issue as well:
[https://launchpad.net/distros/ubuntu/+source/eclipse-cdt/+bug/68661]("https://launchpad.net/distros/ubuntu/+source/eclipse-cdt/+bug/68661")

---

### Post by Twiggy794 on 2006-11-21
Blackdown Java fixes the issue.  However, for any Java developers that need Java 5 this isn't a fix.

---

### Post by Troels on 2006-11-24
As mentioned under the bug report there is a workaround...  An quite obvious one ;-)
For me I already had the problem with CDT, so I sudo moved the org.eclipse.cdt* away from the /usr/lib/eclipse/plugins/ directory. Afterwards installed the extension again through the eclipse update system. 

Now it works perfectly :-)

---


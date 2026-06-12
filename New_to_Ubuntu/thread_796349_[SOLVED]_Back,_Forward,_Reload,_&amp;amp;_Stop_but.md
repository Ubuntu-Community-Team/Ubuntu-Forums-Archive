---
title: "[SOLVED] Back, Forward, Reload, &amp;amp; Stop buttons disabled in FF3 beta"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by neurostu on 2008-05-16
I just did a clean install of Hardy heron and for some reason my FF buttons are grayed out and I can't use them.  I open up the error console and I get:
```

Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 740"  data: no]

```

Does anybody know how to fix this?

---

### Post by bumanie on 2008-05-16
Had a similar experience, although mine happened spontaneously after having worked fine for a couple of weeks. What I did was  type about:config into to the firefox address bar and then type buttons into the filter. 2 lines appeared. One said 'no buttons boolean true' (or something similar - can't remember exact wording). I toggled the true to false and then everything worked again and has done so ever since. No guarantee that this will work for you, try it if you wish. Otherwise, reinstall and hope everything goes OK the second time around.

---

### Post by neurostu on 2008-05-16
so when I type in buttons in the filter line of about:config I get:
```

extensions.hideInstallButton
browser.tabs.closeButtons

```
when I toggle either of them it doesn't do anything... thanks anyway

---

### Post by bumanie on 2008-05-16
Try right clicking on the second line and see if allows you to toggle from true to false. As I said, I couldn't remember the syntax of the line at all, but after seeing your post, I think the second line looks familiar.

PS: Right click will give a drop box that should have 'toggle' on it; left click toggle in the drop box.

---

### Post by neurostu on 2008-05-16
So thanks again but that didn't fix the issue.

I've posted a screen shot of the problem, also I can;t select "File" "Edit" "View" etc..

---

### Post by gustl on 2008-05-18
Hi 
[this]("http://ubuntuforums.org/showthread.php?p=4985384") describes a similar problem if not the same. 
Also my bookmarks were all gone.
I created a new user via firefox -ProfileManager and import my old bookmarks.
I am not sure yet, if everything is working fine again, at least the buttons and bookmarks do.

---

### Post by neurostu on 2008-05-19
Anybody know where I can post this problem to get higher visability? Possibly a mozilla forum somewhere?

---

### Post by Inxsible on 2008-05-19
You can try one of two things.
1) Go to your home folder, and delete the preferences for your mozilla firefox. i think its under .mozilla. Try restarting FF after you delete the prefs.


2)If that doesn't work how about removing firefox completely and then re-installing it?
After removing it, go to your home folder and make sure that the prefs folder for firefox has been deleted. Then install FF3 again.

---

### Post by neurostu on 2008-05-19
So I'll try that, but you'll have to forgive me for being skeptical as this is a clean install straight off of the live CD, and I'm not sure how the default prefs could cause this problem.

---

### Post by neurostu on 2008-05-22
Ok so it worked! Thanks!

---


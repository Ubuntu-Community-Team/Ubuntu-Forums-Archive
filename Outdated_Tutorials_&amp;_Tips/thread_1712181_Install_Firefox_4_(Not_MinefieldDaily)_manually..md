---
title: "Install Firefox 4 (Not Minefield/Daily) manually."
date: 2011-03-22
forum: Outdated Tutorials &amp; Tips
---

### Post by kaldor on 2011-03-22
Should work for any distro, really.

_Step 1_

Make sure you always back up your firefox settings before altering anything. Make a backup of your .mozilla folder or .mozilla/firefox folder. 

_Step 2_

Download Firefox 4 for Linux in your language [_here_]("http://www.mozilla.com/en-US/firefox/all.html")

_Step 3_

Extract the tar.bz2 that you downloaded.

_Step 4_

You should have a folder called "firefox" that came out of the tar.bz2 archive that you downloaded. You need to move this to */opt*. To do so, cd to the directory that "firefox" is located, and then run:
```
sudo mv firefox /opt/firefox
```

For example, if you saved the file to "Desktop", type *cd Desktop* before running the above command.

_Step 5_

Rename the old Firefox binary just in case:

```
sudo mv /usr/bin/firefox /usr/bin/firefox3-backup
```

_Step 6_

Use a symbolic link to point to Firefox 4:

```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

---

That should be all there is to it. If you try the new Firefox menu bar (I believe it's on by default) the "Firefox" menu button may be on the right-hand side of the browser. This is due to a conflict with older Firefox profiles. 

Fix this by creating a new profile and importing all your bookmarks, etc, into that.

Hope this helps a bit.

Edit:

A Firefox 4 ppa has been released. However, the tutorial above will apply to any release of Firefox without needing a PPA (worked on Fedora as well). 

_PPA_

Apply PPA:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

Update to Firefox 4:
```
sudo apt-get install firefox
```

---

### Post by zaivala on 2011-03-23
I haven't seen these steps elsewhere. I actually was missing Steps 4 and 5. It works now. Thank you!

---

### Post by kaldor on 2011-03-23
Glad I helped :)

---

### Post by jfgencarnacao on 2011-04-07
Thank you very much!

---


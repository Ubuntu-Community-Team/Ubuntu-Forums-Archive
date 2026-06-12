---
title: "SunBird Sync: Requires Additioanl Items"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by spotteddog on 2008-05-10
Has anyone found I fix for this yet?  :)

Hardy, SunBird 0.7 (from Synaptic Package Manager), Provider For Google Calendar 0.3 or 0.3.1 Add-on.

Error message: Requires Additional Items

Tried all last evening to install SunBird 0.8 from the tar.gz file from Mozilla. I just can't get it to install. So, I'm stuck with 0.7.

Any help is appreciated. I'm stuck.

Thanks

Spot

---

### Post by hongleong on 2008-06-16
[LIST=1]
[*]Download v0.8 tarball from [http://mozilla.mtk.nao.ac.jp/pub/mozilla.org//calendar/sunbird/releases/0.8/linux-i686/en-US/sunbird-0.8.en-US.linux-i686.tar.gz](http://mozilla.mtk.nao.ac.jp/pub/mozilla.org//calendar/sunbird/releases/0.8/linux-i686/en-US/sunbird-0.8.en-US.linux-i686.tar.gz)


[*]Sudo unpack the tarball. The directory "sunbird" will be created.


[*]Move "sunbird" into /usr/local/


[*]Create menu entry for binary "/usr/local/sunbird/sunbird" under "Office" (System > Preferences > Main Menu)


[*]Run Sunbird from the menu using your non-root user account. Your user profile will be created in "~/.mozilla/sunbird"
[/LIST]

Hope this helps. :)

---

### Post by issueperson on 2008-08-13
I followed those steps but had to add one:
open Synaptic and install libstdc++5.  

Now the latest version of Provider will work (0.4) and I can edit my google calendar from sunbird.

sweet.

---


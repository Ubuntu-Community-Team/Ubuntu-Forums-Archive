---
title: "firefox in hardy"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by shacamin on 2008-05-04
I recently install the new version of Ubuntu, and was not satisfied with the new version of Firefox that was automatically installed (3b5). I decided to switch back to version 2(.0.0.14), but I am now unable to install, uninstall or change any preferences in any of my firefox addons.

This is the weird part. I went into synaptic, did a complete removal. I reinstalled to find that my preferences had been saved. So, I went to the properties menu of the firefox-2 package, and took a look at every folder/file related to firefox, and went through and did an rm -rf removal of all of them. I then reinstalled firefox-2, to find that my preferences had still been kept, but non of the addons worked.

Is there something I'm missing? I really want my addons back...Plus, 3b5 is a CPU hog.

---

### Post by aheckler on 2008-05-04
IIRC, you need to delete your whole ~/.mozilla/firefox profile before FF2 will work. Obviously you should save your bookmarks, etc. before you do so.

---

### Post by Joeb454 on 2008-05-04
May I just ask what was the issue (or issues) you were having with FF3 Beta 5?

---


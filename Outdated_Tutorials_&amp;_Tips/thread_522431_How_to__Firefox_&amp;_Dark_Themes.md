---
title: "How to : Firefox &amp; Dark Themes"
date: 2007-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by finchair on 2007-08-10
On Firefox the auto-complete drop down has a dark text on a dark background, which makes it unreadable.

The fix for this issue is:

goto your
.mozilla/firefox/xxxx.default/chrome directory where xxxx is a random block of numbers and letters and modify your "userChrome.css" file with following entry.

/* Change the url auto-complete text color */
.autocomplete-tree {
color: #ffffff !important;
}

If your menus are dark you can also add the userChrome.css options from this post by xl_cheese:

[http://ubuntuforums.org/showthread.php?t=503508&highlight=firefox+dare+menu](http://ubuntuforums.org/showthread.php?t=503508&highlight=firefox+dare+menu)

Note: If there is not a "userChrome.css" file make a copy of the "userChrome-example.css" file and rename it to "userChrome.css" and then do the edit. Also, at this point you are not restricted to just using white, you could change it to any color you want.

---

### Post by bodhi.zazen on 2007-08-10
Thread re-named and moved. It is not a request for support and IMO does not belong in ABT.

---

### Post by finchair on 2007-08-10
Ok. Thanks.  I appreciate the correction. :-)

---


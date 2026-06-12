---
title: "[SOLVED] How to edit proxy server configuration in wine IE?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by bhadotia on 2008-08-26
To access the net we have to use our University's proxy server. Now , how do I edit these settings in the wine IE - as it completely bereft any gui configuration (not even an address bar). I think changing the settings for IE will apply on all other wine apps (as in windoze)- if not how to make these settings universal for all wine apps?
Many thanx.

---

### Post by Odd-rationale on 2008-08-27
Are you using ies4linux?

Your problem sounds similar to one I had. My IE window looked like this: [http://ubuntuforums.org/attachment.php?attachmentid=56509&stc=1&thumb=1&d=1200378155](http://ubuntuforums.org/attachment.php?attachmentid=56509&stc=1&thumb=1&d=1200378155)

I solved this issue by folloing this: [http://ubuntuforums.org/showpost.php?p=4158076&postcount=17](http://ubuntuforums.org/showpost.php?p=4158076&postcount=17)

To change your proxy settings, go under Tool --> Internet Options --> Connection

---

### Post by bhadotia on 2008-08-27
> **Odd-rationale said:**
> Are you using ies4linux?

Your problem sounds similar to one I had. My IE window looked like this: [http://ubuntuforums.org/attachment.php?attachmentid=56509&stc=1&thumb=1&d=1200378155](http://ubuntuforums.org/attachment.php?attachmentid=56509&stc=1&thumb=1&d=1200378155)

I solved this issue by folloing this: [http://ubuntuforums.org/showpost.php?p=4158076&postcount=17](http://ubuntuforums.org/showpost.php?p=4158076&postcount=17)

To change your proxy settings, go under Tool --> Internet Options --> Connection
I'm not using ies4linux and my problem is not related to the interface. I want where are the settings for the proxy server to use by the IE in wine stored and how to edit them.

---

### Post by bhadotia on 2008-09-19
Bump!

---

### Post by bhadotia on 2008-09-21
Bump!

---

### Post by bhadotia on 2008-11-30
The solution is on the [wiki]("http://wiki.jswindle.com/index.php/Wine_Registry#Proxy_Server"). I recommend using the built-in regedit to edit the registry so as to avoid any errors.

---


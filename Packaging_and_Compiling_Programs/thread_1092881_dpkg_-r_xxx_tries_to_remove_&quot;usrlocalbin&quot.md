---
title: "dpkg -r xxx tries to remove &quot;/usr/local/bin&quot;"
date: 2009-03-10
forum: Packaging and Compiling Programs
---

### Post by chcolemanjr on 2009-03-10
I've put together a deb package and it installs fine. The problem is when I try to remove the package I receive a warning message like so:

dpkg - warning: while removing xxx, directory `/usr/local/bin' not empty so not removed.

I only have one file that goes in /usr/local/bin. All my other files are in the subdirectory /usr/local/xxx. All those are being removed with no problems.

When Googleing the problem I only many saw complaints of various packages causing this warning during removal. Sadly, I saw no resolutions.

Anyone have any ideas?

---

### Post by chcolemanjr on 2009-03-17
Bump

---

### Post by cdizzle on 2011-06-17
I had this same problem with attempted removal of /usr/local/bin. Additionally, when I made a package which installed in /opt, it tries to remove /opt upon removal! What's going on here?

---

### Post by howefield on 2011-06-17
> **cdizzle said:**
> I had this same problem with attempted removal of /usr/local/bin. Additionally, when I made a package which installed in /opt, it tries to remove /opt upon removal! What's going on here?

Please create a new thread, you're more likely to get help that way, rather than tagging on to a 2 year old thread.

---


---
title: "How do I access a .xul file using a chrome:// URL ?"
date: 2009-05-05
forum: Programming Talk
---

### Post by akudewan on 2009-05-05
I have placed a chrome.manifest file under ~/.mozilla/firefox/xxxx.dev/chrome/ which looks like this:

```

content findfile findfile/content/
skin findfile classic/1.0 findfile/skin/
locale findfile en-US findfile/locale/

```

The findfile directory is placed in the same location. The skin/ and locale/ directories are currently empty. The content/ directory has a findfile.xul file

I can access the .xul file using a file:// URL, but not using chrome://findfile/content/findfile.xul. The browser shows nothing in the latter case.

Why is this not working? Do I need an install.rdf file as well?

---

### Post by biblonchk on 2009-06-23
Hi

I've the same problem with the same tutorial found at MDC
[https://developer.mozilla.org/en/XUL_Tutorial](https://developer.mozilla.org/en/XUL_Tutorial)

Trying to run this example from ~/.mozilla/firefox/xxxxx.dev/chrome dosen't works. Sothat I moved the content related to 'findfile' example into the firefox install location at /usr/lib/firefox-3.0.xx/chrome and tryied again.

The later works !!!

My question:

What is the right way to register xul application into the user's chrome chrome directory. I.e at ~/.mozilla/firefox/xxxx.dev/chrome ???

Many thanks in advance for your tips
Kindest regards

---


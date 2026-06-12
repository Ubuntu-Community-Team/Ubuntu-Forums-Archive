---
title: "[SOLVED] Downloading a website - help needed"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-10-15
Can someone tell me where this command will download the site to?

wget -r -l0 --no-parent [http://urltodownload](http://urltodownload)

I have found and used httrack but think that this command **may** be easier to use :-k

---

### Post by iaculallad on 2008-10-15
That command line will download the website to your current working directory.

---

### Post by tahitiwibble on 2008-10-15
> **iaculallad said:**
> That command line will download the website to your current working directory.

So if I create a new folder in my "home" folder and then navigate to it in a terminal and then go for "wget", then all the files will download to that same folder? This is regardless of what I'm doing in the GUI?

---

### Post by t0p on 2008-10-15
> **tahitiwibble said:**
> So if I create a new folder in my "home" folder and then navigate to it in a terminal and then go for "wget", then all the files will download to that same folder? This is regardless of what I'm doing in the GUI?

Absolutely.

---

### Post by iaculallad on 2008-10-15
> **tahitiwibble said:**
> So if I create a new folder in my "home" folder and then navigate to it in a terminal and then go for "wget", then all the files will download to that same folder? This is regardless of what I'm doing in the GUI?

Yes, wget utility will create a folder (Name basing it on the website you want to grab) and download the files on your current working directory.

---

### Post by tahitiwibble on 2008-10-15
Thanks guys.

---


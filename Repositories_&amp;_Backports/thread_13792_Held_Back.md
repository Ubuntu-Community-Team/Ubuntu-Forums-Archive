---
title: "Held Back?"
date: 2005-02-02
forum: Repositories &amp; Backports
---

### Post by Soulful93 on 2005-02-02
I believe I just upgraded to Hoary from Warty via apt-get and it removed some things clamav to be specific. Now when I try and add it again via apt-get I'm getting alot of unmet dependencies. 

Also when I do an apt-get upgrade I'm running into alot of packages that are kept back and when I try to download them I recieve unmet dependencies. Is there something I'm missing in the sources.list file? Yes, I've already done the apt-get update. Here's what I have. Any help will be greatly appreciated.  :confused: 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

---

### Post by mendicant on 2005-02-03
main and restricted for hoary:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe

---


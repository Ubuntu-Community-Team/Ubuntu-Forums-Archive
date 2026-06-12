---
title: "Just installed Ubuntu Desktop and have an issue with FireFox spell checker"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by Executioner on 2014-03-05
I did a fresh install of Ubuntu 12.4 (latest version) and it installed with no problems on my old Dell E1705 laptop with a SSD hard drive. While I was typing in some information in another web forum, I noticed that the spell checker in FF does not work. I went into options and verified that the option was checked. I thought I had fixed it when I noticed the US English dictionary was not installed so I got that completed, but still no spell checking is happening. Since I'm new to Ubuntu, not sure what else to try. Oh, I did add the Add-on dictionary for FF, but that did not solve the problem either. It's using the latest version of FF, and all updates have been installed.

---

### Post by Impavidus on 2014-03-05
Which US-english dictionary? ispell, aspell, myspell, hunspell? For most programs, including Firefox I believe, you need the hunspell dictionary (hunspell-en-us). Otherwise, type **about:config** in the address bar, search for **spell** and set the appropriate options. But maybe you did that already.

---

### Post by Vladlenin5000 on 2014-03-05
... but you need to restart Firefox after installing a new dictionary.

---

### Post by Executioner on 2014-03-05
Went here: [https://addons.mozilla.org/en-US/firefox/addon/united-states-english-spellche/](https://addons.mozilla.org/en-US/firefox/addon/united-states-english-spellche/) and now it works.

---

### Post by Linuxratty on 2014-03-05
This has happened to me as well. But only on one website. What's interesting is that Chrome's spell checker also does not work on the same website.
 You can try contacting Fire Fox and see if they can help. I have complained about this as well to them.
 I tried that link some time ago and still have the problem. 

[https://input.mozilla.org/en-US/feedback#1](https://input.mozilla.org/en-US/feedback#1)

---

### Post by Impavidus on 2014-03-06
Firefox and Chrome use the same spell checker, as do Chromium, Opera, Safari, LibreOffice, OpenOffice, gedit, ... Why do do same work twice and all invent your own spell checker?

Maybe the site on which it doesn't work has a non-standard text field.

---


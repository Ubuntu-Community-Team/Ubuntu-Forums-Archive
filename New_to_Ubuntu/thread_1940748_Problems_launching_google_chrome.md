---
title: "Problems launching google chrome"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by ElianaH on 2012-03-14
Hi, I'm from Argentina, sorry if I have any writing mistakes.


My problem is that every time I launch google chrome, it automatically searches this phrase: **xn--enable-plugins-f82h/**, instead of showing google's home page or a new tab page. My PC has 2 OS, windows and ubuntu 10.04, but this only happens with Ubuntu. I think I once used that phrase or command in the terminal,I'm not sure. I have tried changing the options within google chrome; also tried to uninstall it with synpatic and deleting any folder that is related to the browser, but nothing works. I only want it to show google's home page, help! :(

---

### Post by ubudog on 2012-03-14
If you don't mind losing your bookmarks (which you can backup if you'd like to keep them), then you can remove Chrome's configuration to 'reset' it.  This way, you can set your homepage again and all should be well.

To backup bookmarks: 
Click on the wrench icon>Bookmarks>Bookmark Manager>Organize>Export Bookmarks to HTML file.

Save this file into your home directory.

Then, close Chrome and open a terminal.  Run this: 
```
mv .config/google-chrome .config/google-chromebak
```

This should remove (actually just moving it, in case you need to go back) all your settings (and extensions), and get you back to default the next time you run Chrome.

---

### Post by ElianaH on 2012-03-22
I could remove the settings but the problem continues. I followed your advise and it worked but when a I chose Google as the main  search engine for chrome (among these options google, ask, or another one), it automatically searched the same phrase, it's very strange...

---

### Post by ElianaH on 2012-04-14
Does anybody know how to solve this? pleeeease:)

---

### Post by Curtis6767 on 2012-04-14
I have Chromium and I think it's the same as Chrome

Click on the wrench in the top right corner.

Select  Settings 

In that window you'll have options to change your homepage and manage search engines.

The phrase that is being searched for may be in there.

---


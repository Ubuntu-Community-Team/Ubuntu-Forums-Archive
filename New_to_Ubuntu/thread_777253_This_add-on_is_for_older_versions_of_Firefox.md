---
title: "This add-on is for older versions of Firefox"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by brucewagner on 2008-05-01
Every cool Firefox add-on I want to RE-add-on again... since upgrading to Ubuntu 8.04 (which comes with Firefox 3.05b), says...  "This add-on is for older versions of Firefox"

:(

What can I do to get my beloved add-ons back?

I can't live without "Reload Every", "Delicious Bookmarks 1.5.44", etc.

---

### Post by thiebaude on 2008-05-01
Go back to Firefox 2 until firefox 3 is finally released sometime in June.

---

### Post by Paqman on 2008-05-01
> **brucewagner said:**
> 
What can I do to get my beloved add-ons back?


Install the Nightly Testing Tools add-on. It'll allow you to disable the compatibility check for the add-ons. That'll let you install FF2 add-ons in FF3, but there's no guarantee they'll work.

If that doesn't work, then use FF2 like thiebaude said.

---

### Post by skymera on 2008-05-01
Unfortunately Ubuntu 7.04 ships with Firefox 3, god knows why.

I installed Firefox 2 to get my addons back. Worked better and restarted less.

You can try Paqman suggestion first if you like then install Firefox 2 if that doesn't work.

---

### Post by doorknob60 on 2008-05-01
Yeah, just install Firefox 2:
```
sudo apt-get install firefox-2 && sudo apt-get remove firefox
```

---

### Post by chewearn on 2008-05-01
> **brucewagner said:**
> 
I can't live without "Reload Every"

I'm using "Reload Every" add-on in Firefox3b5.  Install it from here:
[http://reloadevery.mozdev.org/](http://reloadevery.mozdev.org/)

---

### Post by DarKnyht on 2008-05-01
8.04 Ships with both Firefox 3 Beta 5 (the default on the top bar), and Firefox 2 as web browsers.  To use Firefox 2, just locate it in the Application menu under Internet.

If you prefer Firefox 2 over Firefox 3 Beta, just remove Firefox 3 from the top bar and drag Firefox 2 to it.

---

### Post by brucewagner on 2008-05-01
> **DarKnyht said:**
> 8.04 Ships with both Firefox 3 Beta 5 (the default on the top bar), and Firefox 2 as web browsers.  To use Firefox 2, just locate it in the Application menu under Internet.

If you prefer Firefox 2 over Firefox 3 Beta, just remove Firefox 3 from the top bar and drag Firefox 2 to it.

When I go to Applications-->Internet-->Firefox Web Browser...  It launches the same Firefox 3.0b5

> **AstalaVista said:**
> I'm using "Reload Every" add-on in Firefox3b5.  Install it from here:
[http://reloadevery.mozdev.org/](http://reloadevery.mozdev.org/)

Yes!

That's the answer!   Thanks.  Installing that newer version of Reload Every did the trick!   Works perfectly.

I wonder why they haven't updated it on the Firefox Add-ons Website ( [https://addons.mozilla.org/en-US/firefox/addon/115](https://addons.mozilla.org/en-US/firefox/addon/115) ) yet...

---


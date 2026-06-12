---
title: "Cache in 12.04 Please?"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by lyni on 2013-01-03
Could someone please let me know where to find the cache in Ubuntu 12.04 and how to clear it.
I used to find it easy enough in Ubuntu 10.04 so I would clear it out regularly. but its not so easy to find in 12.04.
thanks
lyn

---

### Post by vasa1 on 2013-01-03
What cache are you concerned about? The system cache or the browser cache?

There's one cache here: ~/.cache. To see it you need to enable viewing hidden files and folders in your file manager. Usually, it's done by toggling Control+H. In the terminal, you can see it by entering ls -a (to view hidden files). I've never interfered with that cache.

Then there's the browser's cache. For Firefox and Chrome you can bring up a screen by pressing control+alt+del together.

---

### Post by lyni on 2013-01-03
> **vasa1 said:**
> What cache are you concerned about? The system cache or the browser cache?

There's one cache here: ~/.cache. To see it you need to enable viewing hidden files and folders in your file manager. Usually, it's done by toggling Control+H. In the terminal, you can see it by entering ls -a (to view hidden files). I've never interfered with that cache.

Then there's the browser's cache. For Firefox and Chrome you can bring up a screen by pressing control+alt+del together.

thanks Vasa1 for your reply. its the Firefox cache I was talking about. in Ubuntu 10.04 it used to be in the Hidden Files.
lyn

---

### Post by vasa1 on 2013-01-03
> **lyni said:**
> thanks Vasa1 for your reply. its the Firefox cache I was talking about. in Ubuntu 10.04 it used to be in the Hidden Files.
lyn
Look over here:
```
/home/your_name/.mozilla/firefox/********.default/Cache
```
where ******** is a string of letters and numbers that varies from user profile to user profile.

---

### Post by mcduck on 2013-01-03
> **vasa1 said:**
> Look over here:
```
/home/your_name/.mozilla/firefox/********.default/Cache
```
where ******** is a string of letters and numbers that varies from user profile to user profile.

...or you can go to Tools->Clear Recent History, set time range to "Everything" and make sure "Cache" is marked & click the "Clear Now"-button. ;)

---

### Post by lyni on 2013-01-03
> **mcduck said:**
> ...or you can go to Tools->Clear Recent History, set time range to "Everything" and make sure "Cache" is marked & click the "Clear Now"-button. ;)

thank you mcduck. I didn't know about that. when I looked at it, as well as Cache being ticked it also has several other things ticked - Browsing & Download History, Form & Search History, Cache, Active Logins.
is it okay to delete all those?
thanks
lyn

---

### Post by vasa1 on 2013-01-03
> **lyni said:**
> thank you mcduck. I didn't know about that. when I looked at it, as well as Cache being ticked it also has several other things ticked - Browsing & Download History, Form & Search History, Cache, Active Logins.
is it okay to delete all those?
thanks
lyn The screen you get is the same one I described in the first answer. In other words, clicking with the mouse on the Tools option in the menu bar and then clicking on Clear Recent History gives you the exact same screen as you would get by pressing Control+Shift+Delete simultaneously.

What you choose to retain or delete is entirely your personal decision. If you like your browser to prompt you with suggestions of what you've entered or visited in the past, then you wouldn't want to delete Browsing History and Form and Search History, etc.

If you "value privacy", there are experts who excel in such matters and they will surely assist you if you start a new thread titled like "Is XYZ tracking my every move on the internet?" ;)

---

### Post by lyni on 2013-01-04
thank you both for your replies. I really appreciated them.
I have marked this thread Solved.
thanks again
lyn

---


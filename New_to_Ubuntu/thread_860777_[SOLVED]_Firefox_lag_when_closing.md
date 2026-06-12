---
title: "[SOLVED] Firefox lag when closing"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by keiichidono on 2008-07-15
When i close Firefox is always lags for a little while before closing and the "Do you want to kill or wait for the application Firefox?" dialog always appears. I never had this kind of lag when using beta 5 but now i get this lag with the latest Firefox 3. It happens to me on my other machine with Linux Mint too. I don't have a crap load of tabs open, even if i only have one website open it still lags when closing. Any ideas? :confused:

---

### Post by aysiu on 2008-07-15
I don't know, but have you tried ```
firefox --profilemanager
``` creating a new (test) profile and seeing if that test profile has the same thing happen?

---

### Post by keiichidono on 2008-07-15
I just did that and the closing lag went away. The only addon i have is Adblock plus and i use the default theme, i have attached a screen shot of all of the plugins that are in use.

---

### Post by aysiu on 2008-07-16
I don't know how your profile became corrupt, but it is corrupt, and it may be your extensions (I don't know, since I don't use Adblock Plus). I would export your bookmarks and use a fresh profile with the exported bookmarks imported.

---

### Post by keiichidono on 2008-07-16
Darn, I'll loose all my cookies and cache. Thanks for the help, I'll give it a shot and hope for the best.

---

### Post by aysiu on 2008-07-16
You could also try disabling Adblock Plus and seeing if that affects the closing behavior.

---

### Post by keiichidono on 2008-07-16
I can't live without ABP but i will try and see if that is the cause.

---


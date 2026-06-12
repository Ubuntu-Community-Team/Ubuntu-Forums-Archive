---
title: "[SOLVED] Browsing History"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by webbdawg on 2008-06-03
Ubuntu 8.04 (hardy)
gnome 2.22.2
Mozilla 3 beta 5

Why, when I delete all cookies, cache and browsing history and close FF down does my browsing history remain after I restart the FF browser?

---

### Post by hovzio on 2008-06-03
Do you have google toolbar installed or somthing of the likes? The browser setting may not effect these type of things.

---

### Post by philinux on 2008-06-03
> **webbdawg said:**
> Ubuntu 8.04 (hardy)
gnome 2.22.2
Mozilla 3 beta 5

Why, when I delete all cookies, cache and browsing history and close FF down does my browsing history remain after I restart the FF browser?

If you mean what comes up when you type something in the address bar, it's just searching your own bookmarks.

---

### Post by webbdawg on 2008-06-03
> **hovzio said:**
> Do you have google toolbar installed or somthing of the likes? The browser setting may not effect these type of things.

There is the search field that is there by default. I have added nothing to the browser. I only have tried changing settings.

I am talking about the list that drops down when I click the down arrow on the address bar. I shows every site I have typed in. I do not seem to be able to clear it.

---

### Post by hovzio on 2008-06-03
Sorry in advance if you already have this setup properly.. Do you have your privacy setting setup properly under preferences? Check out the example  in the screen shot.

---

### Post by oilchangeguy on 2008-06-03
> **webbdawg said:**
> Ubuntu 8.04 (hardy)
gnome 2.22.2
Mozilla 3 beta 5

Why, when I delete all cookies, cache and browsing history and close FF down does my browsing history remain after I restart the FF browser?

sounds like you've set fire fox to start from the previous session. deselect this option.

---

### Post by hovzio on 2008-06-03
Sorry for making a seperate post. I forgot about the picture. :(

---

### Post by ajgreeny on 2008-06-03
In FF type **about:config**, accept the warning about being careful and then in the filter, type **browser.urlbar.maxRichResults** and edit the entry to 0(zero) by right clicking and chosing "modify".  Now when you enter addresses no auto suggestions will drop down.

---

### Post by webbdawg on 2008-06-03
> **oilchangeguy said:**
> sounds like you've set fire fox to start from the previous session. deselect this option.
I could not find this setting. But when FF asks because of an abnormal exit I always start a new session.

> **ajgreeny said:**
> In FF type **about:config**, accept the warning about being careful and then in the filter, type **browser.urlbar.maxRichResults** and edit the entry to 0(zero) by right clicking and chosing "modify".  Now when you enter addresses no auto suggestions will drop down.
I did this as suggested and nothing drops down ever.

I figured That FF should at least behave as the FF I installed on my XP machine.

I should be able to see sites I have typed in my address bar during my session. When I close FF down and delete my history it should not show up in the next session. The Ubuntu FF does not act this way.

---

### Post by ajgreeny on 2008-06-04
> "I should be able to see sites I have typed in my address bar during my session. When I close FF down and delete my history it should not show up in the next session. The Ubuntu FF does not act this way."

I agree, but it's a bit of a workround if you really need it.

What we want is for just the addresses we've typed in the address bar to drop down, not all and every address we've ever visited.  That's no use at all to me, I can get those from History, as you say.

---

### Post by philinux on 2008-06-04
What happens using tools - clear private data. Does your history go?

---

### Post by ajgreeny on 2008-06-05
Yes, history does go but the drop down of addresses in the address bar does not.  Weird or what?

---

### Post by ajgreeny on 2008-06-05
OK, I've found it by a case of using logic.
As the config edit I suggested did not quite work as I wanted, I looked further in the filter results from "browser.urlbar.*****" and found matchOnlyTyped.  Double clicking that changed it to true, and all is where I wanted it to be.

It seems odd that the default is for everything you've ever visited to appear here; not what most people want, surely?

---


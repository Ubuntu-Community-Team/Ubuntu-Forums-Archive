---
title: "Need to change network setting by just one click"
date: 2023-04-06
forum: New to Ubuntu
---

### Post by desatir73162 on 2023-04-06
Hi there.
I installed tor and set the firefox to use tor's setting (check attachment).
Some times I need to disable this setting for certain websites but its boring to go to firefox's menu -> setting -> scroll down -> network setting -> and finally enable or disable what I want to.

Is there any easier approach to to that. For example disable the setting per browser's tab and also enable/disable the setting from toolbar by just one click?

Thanks in advanced.

---

### Post by TheFu on 2023-04-06
If you use the same browser for both tor and non-tor activities, you will be uncovered.  This is a terrible, terrible, idea.
I'd even use a different userid for tor stuff, just to keep everything separate.  Otherwise, why bother using tor?

---

### Post by ActionParsnip on 2023-04-06
Use the "no proxy for" section and add the URLs to not use the proxy

---

### Post by desatir73162 on 2023-04-06
> **ActionParsnip said:**
> Use the "no proxy for" section and add the URLs to not use the proxy

Thanks good trick!

But if there was a toggle button for on/off proxy setting, it was better!

---

### Post by desatir73162 on 2023-04-06
> **TheFu said:**
> Otherwise, why bother using tor?
Some websites in my area are not reachable when Im using tor. for example nic.ir

---

### Post by desatir73162 on 2023-04-06
I found this extension and it works just by one click. what I wanted exactly!
[(https://addons.mozilla.org/en-US/firefox/addon/proxy-toggle/)  But it would be better if worked per tab! any suggestion?"]https://addons.mozilla.org/en-US/firefox/addon/proxy-toggle/]("http://I found this extension and it works just by one click. what I wanted exactly! [https://addons.mozilla.org/en-US/firefox/addon/proxy-toggle/)

But it would be better if worked per tab! any suggestion?

---

### Post by ActionParsnip on 2023-04-06
> **desatir73162 said:**
> Thanks good trick!

But if there was a toggle button for on/off proxy setting, it was better!

How is it better? The sites you specify in the no proxy part won't use the proxy, the rest will use the proxy? How is switching the proxy off and on, manually, better than the browser knowing which sites to access via the proxy and which ones to access directly.....?

---

### Post by desatir73162 on 2023-04-09
> **ActionParsnip said:**
> How is it better? The sites you specify in the no proxy part won't use the proxy, the rest will use the proxy? How is switching the proxy off and on, manually, better than the browser knowing which sites to access via the proxy and which ones to access directly.....?

Because the number of websites that I have to add to that list in browser's setting are too much.
I am living in the area that internal websites are not reachable via proxy (tor) and also I need to access other websites from all over the world. so for accessing global website which are out of my area, they are filtered! Something like north korea situation but in an easy mode!

---

### Post by TheFu on 2023-04-12
Be very careful using browser extensions. Many have anti-privacy features and phone home (or worse).

---


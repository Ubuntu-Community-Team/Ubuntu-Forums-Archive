---
title: "keylogging"
date: 2012-12-13
forum: Recurring Discussions
---

### Post by jfloydb on 2012-12-13
I've read in more than one place that recent versions of Ubuntu sends search information to Amazon (via keystrokes through the Unity Dashboard, or some such nonsense). My question is this: does this happen in any way with Xubuntu or Lubuntu. I'm sure the answer is no, but I just want some confirmation. Thanks.

---

### Post by ZippyUbu on 2012-12-13
Hi - As far as I'm aware, the Amazon adds are specific to the Unity shell.  

You can remove them from results:   
> Click on the Ubuntu button, search for "Privacy" and then turn off "Include online results"You can also uninstall if you wish:
```
sudo apt-get remove unity-lens-shopping
```Log off/on and you are good to go...

--
Zu

---

### Post by cariboo on 2012-12-13
This is getting ridiculous, your keystrokes aren't logged, the same way a keylogger does, when you do a search in the dash with the shopping lens enabled, the query is first sent to Canonical's servers, where it is anonymized, then the query is sent on to Amazon. If this is considered key logging, then any search you do through Google or any other search engine should be considered key logging too.

---

### Post by Hungry Man on 2012-12-13
What you enter into the "Dash" is sent to Canonical (the company that packages the Ubuntu operating system). Canonical sends it to Amazon. Amazon sends it back to Canonical, and Canonical sends it to you. It's important to understand that, because they're proxying this information, it's only Canonical who really sees your searches.

You can easily disable this by typing "privacy" and limiting searches to local.

None of the other *buntu's contain this code - it's specific to Unity. Nothign outside of the Dash is logged.

---

### Post by ehraaron on 2012-12-14
Ubuntu is free, right.. They need to make a profit somewhere to keep motivated, so I don't feel like this is an issue. They are sharing what people search for -- anonymously -- through a proxy as well. Nothing to be concerned about, but you can always disable it if you are paranoid.

---

### Post by cprofitt on 2012-12-14
I am with cariboo on this...

Sending your search terms, anonymized and encrypted, to an Ubuntu intermediate server... then sending cleansed terms to Amazon and returning results to your dash is not key logging.

---

### Post by nothingspecial on 2012-12-14
> **jfloydb said:**
>  My question is this: does this happen in any way with Xubuntu or Lubuntu. I'm sure the answer is no, but I just want some confirmation. Thanks.

*Thread moved to **Recurring Discussions**.*

Xubuntu and Lubuntu do not include this feature, although you can install it if you wish.

This has been discussed at length already, we do not need another thread about it.

Closed.

---


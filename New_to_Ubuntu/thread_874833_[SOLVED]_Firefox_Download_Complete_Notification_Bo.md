---
title: "[SOLVED] Firefox Download Complete Notification Box Position"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by XCan on 2008-07-30
Ever since I started using the multiple desktop feature more and more I have at the same time been more and more annoyed with firefox' download complete notification. This box covers the desktop switch bar and I haven't been able to figure out how to move/disable it.

So, does anyone know how to move/disable the download complete notification box in firefox?

---

### Post by Inxsible on 2008-07-30
I am not sure if you can move the download complete notification, but you can definitely move the pager to a different location.

Maybe to the left of the bottom panel instead of the right. Or you can also have it in the top panel if you like.

I am not sure, if you want to go that route, however.

---

### Post by linux6994 on 2008-07-30
Look at the settings under preferences, main and deselect download notification box. The download status will go to the bottom bar.

---

### Post by t0p on 2008-07-30
> **XCan said:**
> 
So, does anyone know how to move/disable the download complete notification box in firefox?

If you click on it, the notification box goes away

---

### Post by sydbat on 2008-07-30
In Firefox...Edit > Preferences > Main...Uncheck "Show the Downloads window..."

See if that works. If not, I am not sure if the completed Downloads window can be removed. It goes away after a few seconds anyway.

---

### Post by randomnote1 on 2008-07-30
in the address bar type in:

about:config

in the search bar search for:

browser.download.manager.showAlertOnComplete

Set that value to false and it should disable the alert.

---

### Post by ibuclaw on 2008-07-30
type in:
```
about:config
```
in the firefox menu, and paste into the filter
```
browser.download.manager.showAlertOnComplete
```
Then set that value to false.

I believe that will stop it.

Regards
Iain

---

### Post by XCan on 2008-07-30
> **randomnote1 said:**
> in the address bar type in:

about:config

in the search bar search for:

browser.download.manager.showAlertOnComplete

Set that value to false and it should disable the alert.

> **tinivole said:**
> type in:
```
about:config
```
in the firefox menu, and paste into the filter
```
browser.download.manager.showAlertOnComplete
```
Then set that value to false.

I believe that will stop it.

Regards
Iain

Thanks! That did the trick!

---


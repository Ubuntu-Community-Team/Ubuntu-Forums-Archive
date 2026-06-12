---
title: "Oneiric with firefox 3.6"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by atno on 2011-09-06
Hi,

I've just installed Oneiric which updated firefox to 7 and that caused loads of firefox addons to break. Is there a way to downgrade to the natty firefox version?

Thanks.

---

### Post by mikewhatever on 2011-09-06
You can download the 32bit binaries of 3.6.x from
[ftp://63.245.208.138/pub/mozilla.org/firefox/releases/](ftp://63.245.208.138/pub/mozilla.org/firefox/releases/)

---

### Post by atno on 2011-09-06
> **mikewhatever said:**
> You can download the 32bit binaries of 3.6.x from
[ftp://63.245.208.138/pub/mozilla.org/firefox/releases/](ftp://63.245.208.138/pub/mozilla.org/firefox/releases/)
i could but binaries dont integrate in ubuntu menus and overall system.

---

### Post by dino99 on 2011-09-06
why would you want to use that oldish ?

---

### Post by jou770d on 2011-09-06
> **dino99 said:**
> why would you want to use that oldish ?

For this reason I suppose:
> **atno said:**
> 
<snip> 
caused loads of firefox addons to break.
<snip> 


If that's all there is to it, then you might want to check out this:
[Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/")

> About this Add-on

After installing the Add-on Compatibility Reporter, your incompatible extensions will become enabled for you to test whether they still work with the version of Firefox or Thunderbird that you're using. If you notice that one of your add-ons doesn't seem to be working the same way it did in previous versions of the application, just open the Add-ons Manager and click Compatibility next to that add-on to send a report to Mozilla.

Even if your add-ons all work fine, if they're marked incompatible, please let us know that they work fine by submitting a success report so we can encourage the add-on developer to update their compatibility information.

We'll collect all of the reports and let add-on developers know what users are having problems with, or if their add-ons seem to work just fine in future versions of the product.

If you encounter problems and want to disable your incompatible add-ons again, uninstalling the Add-on Compatibility Reporter should revert to your previous compatibility checking settings.

If you're an add-on developer trying to find reports submitted for your extension, head over to the Report Viewer here: [https://addons.mozilla.org/compatibility/reporter](https://addons.mozilla.org/compatibility/reporter)


---

### Post by dino99 on 2011-09-06
some addons fails to update automaticaly, saying : not compatible with your version, but in fact most of them can be upgraded manually via tools -> addons database

on my system i'm using 7 b4 and about 10 addons are running on it (mostly the top security hit)

---

### Post by atno on 2011-09-06
> **Amarus said:**
> For this reason I suppose:


If that's all there is to it, then you might want to check out this:
[Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/add-on-compatibility-reporter/")


Thank you Amarus everything run ok for now.

---


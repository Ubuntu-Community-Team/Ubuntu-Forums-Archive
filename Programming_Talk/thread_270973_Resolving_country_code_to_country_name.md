---
title: "Resolving country code to country name"
date: 2006-10-04
forum: Programming Talk
---

### Post by linux2512 on 2006-10-04
I need to resolve a country code (US,GB,etc..) to the appropriate country name (United States, Great Britain, etc..), is there a country database I could access via C, C++?  I've been sifting through header files and can't seem to find anything.

Thanks

---

### Post by asimon on 2006-10-04
KDE's [	KLocale::twoAlphaToCountryName](http://developer.kde.org/documentation/library/3.5-api/kdelibs-apidocs/kdecore/html/classKLocale.html#a90) function does that. But if you don't do any KDE application, than kdelibs comes probably with too much overhead.

---

### Post by linux2512 on 2006-10-04
> **asimon said:**
> KDE's [	KLocale::twoAlphaToCountryName](http://developer.kde.org/documentation/library/3.5-api/kdelibs-apidocs/kdecore/html/classKLocale.html#a90) function does that. But if you don't do any KDE application, than kdelibs comes probably with too much overhead.

Thanks, I appreciate your reply, but my app is written in GTK.

---

### Post by toojays on 2006-10-05
There is a package called iso-codes which contains a table of country code to name mappings. You can either parse the XML file /usr/share/xml/iso-codes/iso_3166.xml, or use the tab-delimited /usr/share/iso-codes/iso_3166.tab.

This package also provides gettext files to translate the country names from English into various other languages.

---

### Post by linux2512 on 2006-10-05
> **toojays said:**
> There is a package called iso-codes which contains a table of country code to name mappings. You can either parse the XML file /usr/share/xml/iso-codes/iso_3166.xml, or use the tab-delimited /usr/share/iso-codes/iso_3166.tab.

This package also provides gettext files to translate the country names from English into various other languages.

Just what I was looking for! Thanks toojays!

---

### Post by BalochDude on 2008-06-06
I found this page with country codes, its a ms sql server script, but i am sure you can modify it to anything you want, it will give you a list of all the countries and their codes:

[http://www.chapterzero.co.uk/articles/download-list-of-countries-codes.aspx](http://www.chapterzero.co.uk/articles/download-list-of-countries-codes.aspx)

---


---
title: "How to set Swiftfox to work in Kubuntu as default browser"
date: 2007-02-27
forum: Outdated Tutorials &amp; Tips
---

### Post by in_flu_ence on 2007-02-27
Hi,

    Many of those who installed swiftfox via Automatix may find that they cannot use it as the default browser even after setting it at the KDE system settings.

    Here is what you should do:

```

sudo update-alternatives --install /usr/bin/x-www-browser x-www-browser /opt/swiftfox/firefox 90
update-alternatives --set x-www-browser /opt/swiftfox/firefox
```

   I think this is especially crucial for those using the 64bit Kubuntu since we try to have the best browsing experience under the 64bit platform.

   Comment if there is any better way. :)

   Hope it helps.

---

### Post by wireddad on 2007-02-27
I have had no problems using SYSTEM SETTINGS>DEFAULT APPS to change the default web browser.  Is the problem only on 64bit (alternative) Kubuntu?

---

### Post by in_flu_ence on 2007-02-27
I am not sure if it is particularly meant for 64bit

but apparently people have problems with Swiftfox that is installed via automatix.

I suppose if Firefox is installed via Adept. there should not be a problem.

There isn't an option in x-www-browser in the Swiftfox case. Thus, the tip as given.

Hope it will help a little :)

---

### Post by kasimir on 2007-03-02
Thanks, those commands worked for me.

---


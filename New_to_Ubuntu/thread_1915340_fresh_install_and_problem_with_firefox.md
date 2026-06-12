---
title: "fresh install and problem with firefox"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by werty2010 on 2012-01-26
just did a reinstall (ubuntu 11.10) and having a problem with firefox:
every time i try to install an add on from the [official site of firefox]("https://addons.mozilla.org/en-US/firefox/extensions/") it gives me the "pop up" that supposedly downloads but just stays there at 0 bytes...

since i use a lot of extensions,i would appreciate it, if you help me...?

---

### Post by robgraves on 2012-01-26
you could just open a terminal and type:
```
sudo apt-get install firefox
```

---

### Post by claracc on 2012-01-26
I am using firefox 3.6.24, when I want to install an addon in firefox, I go to Tools menu, addons and obtain addons, in the window appearing I can search for the addon I want, then I click on it and clik on "add to firefox".

For firefox 9.0 the method would be similar.

This is the ordinary way

---

### Post by lovinglinux on 2012-01-28
> **werty2010 said:**
> just did a reinstall (ubuntu 11.10) and having a problem with firefox:
every time i try to install an add on from the [official site of firefox]("https://addons.mozilla.org/en-US/firefox/extensions/") it gives me the "pop up" that supposedly downloads but just stays there at 0 bytes...

since i use a lot of extensions,i would appreciate it, if you help me...?

If it doesn't want to download, right-click on the green installation button on Mozilla site, select "Save link as" and save the xpi file somewhere. To install the add-on, drag the downloaded xpi file to a Firefox window.

You could also try to fix the problem. Most likely that is an ipv6 issue. 

[LIST]
[*]Type **about:config** in the address bar, press Enter.
[*]Find **network.dns.disableIPv6** in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---


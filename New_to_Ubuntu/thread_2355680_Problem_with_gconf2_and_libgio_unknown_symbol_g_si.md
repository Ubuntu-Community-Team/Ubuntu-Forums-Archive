---
title: "Problem with gconf2 and libgio: unknown symbol g_signal_accumulator_first_wins"
date: 2017-03-15
forum: New to Ubuntu
---

### Post by rabb.it on 2017-03-15
Hey everyone,

I am pretty new to ubuntu and administrating a server system running on ubuntu.
Since i started there are warnings about a not fully installed package "gconf2"
I tried various levers to solve the problem (install/remove gconf2, upgrade, full-upgrade, dist-upgrade...) but didn't get any results on this problem.

Today i tried a ```
apt-get purge gconf2
``` and reinstall it, but it broke with the following error, which since then appears on any apt(-get) install/upgrade and when trying to use some applications like vim.

German: (Original)
```
gconf2 (3.2.6-0ubuntu2) wird eingerichtet ...gconf-merge-tree: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0: undefined symbol: g_signal_accumulator_first_wins
dpkg: Fehler beim Bearbeiten des Paketes gconf2 (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 127 zurück
Fehler traten auf beim Bearbeiten von:
 gconf2

```
English (Google Translation)
```
Setting up gconf2 (3.2.6-0ubuntu2) ...gconf-merge-tree: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0: undefined symbol: g_signal_accumulator_first_wins
dpkg: Error processing package gconf2 (--configure):
  Subprocess installed post-installation script returned error 127
Errors occurred while editing:
  gconf2

```

I read various roughly similar troubleshooting i found in the web and got from there that it's possibly a problem with an older version of glib, but don't really know how to resolve this.

Hope you may help me.

Greetings
Maik

PS: Hope my englisch is not that bad and you get everything. I am very sorry for any grammar mistakes.

---

### Post by steeldriver on 2017-03-15
Hello and welcome to the forums

Can you run the following command and post the results (preferably within ```
 tags again)

[CODE]
LANGUAGE=en_US:en apt-cache policy gconf2 libglib2.0-0

```

What version of Ubuntu are you using?

---


---
title: "HOWTO: Gwenview with renaming of files option"
date: 2005-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by GoldBuggie on 2005-12-16
Many ppl who manage several photos or pictures want a nice way to manage and rename them. This will explain howto make **gwenview**(picture viewer) have that option together with **krename**(renaming tool).

First install the two tools.
```
sudo apt-get install gwenview krename
``` [LIST=1]
[*]Open up *gwenview* and goto[B]
Settings->Configure External Tools[/B]
[*]Press the **Add** button.
[*]Enter some **Name:** for example *rename file(s)*
[*]As **Command:** enter **krename %U**
[*]Press the big "?" and choose some nice icon and then *apply*.
[*]finished.[/LIST]Now when you select some file(s) you can rename them thrue *right-click->external tools->rename file(s)*

---


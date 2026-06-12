---
title: "update problems"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by Gennu on 2013-01-03
every time I do an update there is always an error occur of some index file that were not able to be downloaded because they were ignored or old ones are used instead
what can I do?
I need lots of software updates . . .

---

### Post by HernanLinux93 on 2013-01-03
> **Gennu said:**
> every time I do an update there is always an error occur of some index file that were not able to be downloaded because they were ignored or old ones are used instead
what can I do?
I need lots of software updates . . .
 
 
Hey how are you well first of all, for handling and updating packages you can use the following two commands [FONT=Courier New]sudo apt-get update[/FONT]
[FONT=Courier New]sudo apt-get upgrade[/FONT]

---

### Post by Gennu on 2013-01-03
hi everybody
I have this problem on my dell laptop that every time I do an update there is always an error occur of some index files that were not able to be downloaded because they were ignored or old ones were used instead
what can I do?

---

### Post by Pjotr123 on 2013-01-03
More details please. Which index file specifically?

---

### Post by ibjsb4 on 2013-01-03
Yes, more details please.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And post any errors.

---

### Post by Gennu on 2013-01-03
okay guys I think you've noticed that I'm a new user of Ubuntu
but I've tried the both codes and non of'em was completed

---

### Post by Gennu on 2013-01-03
I've tried almost every single similar error in this forum and non of them worked with me and was just a huge waste of time

---

### Post by Gennu on 2013-01-03
> **Pjotr123 said:**
> More details please. Which index file specifically?

I'm sure that these links are very useful but for someone who have these versions
I'm dealing with 10.10 :s

---

### Post by Gennu on 2013-01-03
> **HernanLinux93 said:**
> Hey how are you well first of all, for handling and updating packages you can use the following two commands [FONT=Courier New]sudo apt-get update[/FONT]
[FONT=Courier New]sudo apt-get upgrade[/FONT]

I've tried them thousands of times but the same error is just repeated

---

### Post by arpanaut on 2013-01-03
Maverick has passed "End of Life" those repositories no longer exist.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You can follow those instructions to get old updates and/or upgrade to a newer release.
Better yet back up your important data and re-install to a more current release.
I would suggest 12.04 as it is a LTS and will be supported until 2017.

Edit: For reference.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Gennu on 2013-01-04
> **arpanaut said:**
> Maverick has passed "End of Life" those repositories no longer exist.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You can follow those instructions to get old updates and/or upgrade to a newer release.
Better yet back up your important data and re-install to a more current release.
I would suggest 12.04 as it is a LTS and will be supported until 2017.

Edit: For reference.  [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

thank you very much these links were very useful to me till I get the new 12.04

---


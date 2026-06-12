---
title: "Wine No C drive"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by harsh_ on 2008-05-28
Hey, i used wine and i deleted the whole C: drive by mistake in 7.10 and now upgraded to 8.04... The peoblem is; i cannot open anything with wine...Infact the previous applications as well.... there is no uninstall registry key and no virtual C: drive; i remember i had deleted all of that due to some weird fonts in the utorrent application. Please help

---

### Post by Cypher on 2008-05-28
If you deleted it, then perhaps you need to re-install Wine to have it create the proper virtual drives.

So try
```

sudo apt-get autoremove wine
sudo apt-get install wine

```

---

### Post by harsh_ on 2008-05-28
I tried your solution; but again it did the same thing... when i autoremove the wine; it still shows wine in the applications menu..........

Also; when it is installed; when i configure it using the "configure wine" in the drivers section it throws me an error message "There is no C drive and which is not recommended. Do not forget to Add a drive"

---

### Post by Nythain on 2008-05-28
in a terminal

winecfg

should do the trick

---


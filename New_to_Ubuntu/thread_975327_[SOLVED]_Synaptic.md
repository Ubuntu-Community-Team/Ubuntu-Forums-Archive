---
title: "[SOLVED] Synaptic"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2008-11-08
Hi
I installed SciTE with the help of Synaptic.
I' want to run it in SUDO mode so I can save python files in a user shared directory.

I tried to locate BIN file for SciTE, using this code:
```
locate *SciTE*
```
But noting came out of the search.
I tried in all possible case:
```
sudo SciTE
```


I tried gksudo, and filled the run editbox with  SciTE
but still can't save my python file in usr/.

What am I doing wrong ?

---

### Post by Pierrot Lafouine on 2008-11-08
any idea ?
Thanks

---

### Post by drs305 on 2008-11-08
You may need to update the database before running locate:
```
sudo updatedb
```

Additionally, depending on how you installed it, you may be able to find out information about the run command, icon locatations, etc by viewing the applicable file in the /usr/share/menu/ folder.

You can also usually determine the run command with the following, if you already know the app's system name:
```

which *packagename*

```
Example: which gimp

You can also run a case-insensitive search of your system for a file/folder with the following:
```

sudo find / -iname *scite*

```

---

### Post by Pierrot Lafouine on 2008-11-08
aaaaahhhh what a relief
Something is working now
updatedb is a new concept to me.

Thank you drs305

---


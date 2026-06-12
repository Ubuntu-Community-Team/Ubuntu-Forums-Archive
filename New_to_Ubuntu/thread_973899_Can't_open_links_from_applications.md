---
title: "Can't open links from applications"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by FlintZA on 2008-11-07
Hi, I am running Hardy Heron with the latest updates on everything including firefox 3. When I click on links from applications (such as NetBeans), an error pops up that /usr/bin/friefox was not found. The standard shortcut to firefox in the top bar does successfully run firefox, and it's target is set to /usr/bin/firefox, so I don't understand what the problem might be.
Any help would be appreciated, thanks :)

---

### Post by Sealbhach on 2008-11-07
> **FlintZA said:**
> Hi, I am running Hardy Heron with the latest updates on everything including firefox 3. When I click on links from applications (such as NetBeans), an error pops up that /usr/bin/friefox was not found. The standard shortcut to firefox in the top bar does successfully run firefox, and it's target is set to /usr/bin/firefox, so I don't understand what the problem might be.
Any help would be appreciated, thanks :)

Could be, that the path in the shortcut:

/usr/bin/firefox

is not correct.  

Type

```
locate firefox
```

in the terminal and paste the results here.


.

---

### Post by FlintZA on 2008-11-10
Thanks for the reply. The machine does not have an internet connection, I'll have to run the command and copy the contents to a memory stick when I get a chance.
For interest sake, what am I looking for? Is /usr/bin/firefox some kind of shortcut file, or is it a symbolic link that can be changed with a command? If I know what it is you want to look for in the locate output, perhaps I can fix it myself ;)

---


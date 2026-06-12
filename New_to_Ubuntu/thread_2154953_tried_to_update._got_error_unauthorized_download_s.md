---
title: "tried to update. got error unauthorized download site"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by rccharles on 2013-06-16
I tried to update my 12.4 Ubuntu.  Got error message about downloading from unauthorized site.

[ATTACH=CONFIG]243875[/ATTACH]

Robert

---

### Post by Frogs Hair on 2013-06-16
Close the update manager and reload/refresh the update information from the terminal. ```
sudo apt-get update && sudo apt-get upgrade  
``` The second part of command will install updates.

---


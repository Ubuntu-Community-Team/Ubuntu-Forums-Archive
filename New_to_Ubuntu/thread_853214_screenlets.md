---
title: "screenlets"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by lucky.developer on 2008-07-08
i downloaded screenlets 0.0.7 from compiz web site.
And i installed it by sudo make install command

then, i wrote the following command to start the screenlets daemon

$screenletsd start

it said...

Session-file /home/lakshmanan/.config/Screenlets/screenletsd.ses not found (will be created automatically).

when i tried to add Clock screenlet(by screenletsd add Clock), it said

Error: Screenlets-Backend (screenletsd) not found.


How can i resolve this... please help

---

### Post by tjwoosta on 2008-07-08
well...

"screenlets" is availible through the repository


so what i would do if i were you is..

```
cd /wherever/you/saved/screenlets
```

then 

```
sudo make uninstall
```  
(this is the exact opposte of make install, it will remove the screenlets that you installed)

then just delete the entire folder after doing make uninstall

then 
```
sudo apt-get install screenlets
``` 
(this will download and automatically install screenlets from the repository)

then try the screenlets again and all should be working  
(the repository is usually the best choice for downloading anything)

---


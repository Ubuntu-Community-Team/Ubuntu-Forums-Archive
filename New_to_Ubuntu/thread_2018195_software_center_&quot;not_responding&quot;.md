---
title: "software center &quot;not responding&quot;"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by casondonkersgoed on 2012-07-06
Every time I try to open the software center (clicking and using terminal) the window for it opens and after about 10 seconds it either fades to grey, or displays the loading wheel and then freezes and fades to grey. I have tried putting [COLOR="Navy"]"software-center
"[/COLOR] into the terminal and it displays this [COLOR="Navy"]"2012-07-06 01:06:07,941 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-07-06 01:06:07,947 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-07-06 01:06:08,476 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-07-06 01:06:08,682 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None."[/COLOR] please help, I will provide any additional information if needed.

---

### Post by krustenBrot on 2012-07-06
Have you tried simply reinstalling it?
 First remove it with typing  ```
sudo apt-get purge software-center
``` into a terminal. It is *apt-get purge *because you want to remove the config files as well - maybe there went something wrong. To keep the config files in future you can use *sudo apt-get remove (appname)*.

After that reinstall it typing the following:
```
sudo apt-get install software-center
```

I had various crashes and problems with the software center. Since I reinstalled it it works fine. Maybe it helps here too..

---

### Post by krustenBrot on 2012-07-06
I tried running the software-center from terminal as well - and your output seems to be just fine. I got the same here and everything is working as it should. 

And welcome to the forums by the way. ;)

---

### Post by casondonkersgoed on 2012-07-06
I uninstalled it and re-installed it using those commands and it still has the same problem. I can't figure out what the problem is because the terminal just stops without completely loading the software center. I have a feeling it might be something conflicting with it that I may need to uninstall.

---

### Post by sffvba[e0rt on 2012-07-06
Shot in the dark... in terminal run:

```
sudo apt-get update && sudo apt-get upgrade
```

Check for any errors etc. Maybe there is an issue with the sources and package cache that is causing the issue.


404

---

### Post by NikTh on 2012-07-06
Also you can try to update the catalog.. 
```
sudo update-software-center
```

---

### Post by jmfal on 2012-07-06
Or you can try this

```
 sudo apt-get install synaptic     
```

and not use the software center anymore..

---


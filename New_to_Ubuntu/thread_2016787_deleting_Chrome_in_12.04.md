---
title: "deleting Chrome in 12.04"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by TFSinclair on 2012-07-04
I'm trying to delete Google's Chrome browser from Ubuntu 12.04. The only thing I have found  to do this is from Google and is a string of commands about 3 blocks long.  Does anyone know a straight forward way to delete this obnoxious browser?

---

### Post by Paqman on 2012-07-04
Open up Ubuntu Software Centre, search for Chrome and hit the "remove" button.

---

### Post by Frogs Hair on 2012-07-04
My Chrome installation(from the website) is not listed in the software center but appears in the synaptic package manager. Chrome can be removed from there if installed. The configuration file is in home/hidden/.config. For terminal removal .```
sudo apt-get purge google-chrome
```

---

### Post by TFSinclair on 2012-07-05
Paqman and Frog's Hair, 
thank you both for your replies.  Chromium is now gone from my computer. I'd had enough of Google's tracking my every move!

---

### Post by Paqman on 2012-07-05
> **TFSinclair said:**
> Paqman and Frog's Hair, 
thank you both for your replies.  Chromium is now gone from my computer. I'd had enough of Google's tracking my every move!

[LIST=1]
[*]Google doesn't track your every move, it collects some anonymous data.
[*]What data they do collect is opt-in, so you could have just turned it off from the menu. Settings > Advanced settings > Privacy > uncheck everything.
[*]Glad you've got it sorted.
[/LIST]

---

### Post by Frogs Hair on 2012-07-05
After testing a number of the Chromium based browsers including Iron , Commando Dragon and others I found IMO none of them except possibly Commando for Windows has any real claim to enhanced privacy. Google Chrome has by far the best HTML 5 codec support at least where the Peacekeeper benchmark is concerned.

---


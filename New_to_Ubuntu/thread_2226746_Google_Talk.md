---
title: "Google Talk"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by miles5 on 2014-05-28
Hello,[INDENT]I am currently running ubuntu 14.04 LTS and whenever I run google talk (aka google voice) in google chrome it says that it could not load the google talk plugin. I have tried and it works in 
[/INDENT]
firefox, but I prefer chrome. I have also tried reinstalling it and it doesn't work. If there is any solution please tell me.

Thanks.

---

### Post by monkeybrain20122 on 2014-05-28
Remove cookies, or start with a new profile by deleting ~/.config/google-chrome. .config (notice the ".") is a hidden folder in your home directory. Open your file manager, press ctrl+h or choose "show hidden files" in menu, then locate the hidden folder .config, open it and delete the subfolder google-chrome (or rename it, in case you may want to keep something)

Edited: Make sure you close chrome before you delete/rename  ~/.config/google-chrome

---


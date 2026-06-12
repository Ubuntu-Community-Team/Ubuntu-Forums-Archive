---
title: "Ubuntu's startup sound"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by jermza on 2011-11-30
I'm using 11.10 and I noticed that, in the startup applications, "Gnome Login Sound" is checked. Ever since I've had 11.10, I've never heard a startup sound, although I hear sounds when mails arrive etc.

Is there supposed to be a login sound?

---

### Post by Frogs Hair on 2011-11-30
Yes and here is one _possible_ fix . Install the following.  ```
sudo apt-get install dconf-tools 
```
Open from dash by typing dcon . Proceed to org > gnome > desktop > sound and make sure event sounds is checked . 

Another thing to check is alert volume in sound settings.

---


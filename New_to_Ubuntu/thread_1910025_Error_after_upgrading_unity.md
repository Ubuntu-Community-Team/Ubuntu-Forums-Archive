---
title: "Error after upgrading unity"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by Pulka on 2012-01-16
Yesterday tried upgrading to unity 5.0. This are the commands i used:

```
    
sudo add-apt-repository ppa:unity-team/staging
sudo apt-get update && sudo apt-get dist-upgrade
```

But Unity 5.0 is still very buggy and decided to go back with:

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:unity-team/staging

```

After that, i only had in the login options gnome and no unity.
Installed unity by using the software installation, and unity back again. But...(there's always a but) my desktop icons are gone (but when i go through terminal they're still there) and can't browse folders. I think i don't even have nautilus or it's not working because it's installed.

Any ideas of what's wrong?

---

### Post by Fernhill Linux Project on 2012-01-16
Not sure about how to solve this. Installing gnome-shell or such from terminal would instantly give you a usable system until you get a better solution. Sorry not to be of more help.

---

### Post by Pulka on 2012-01-16
i have a usable system. I just can't browse in folders, etc. 
Example: if i click on the home icon, nothing happens

---

### Post by mcduck on 2012-01-16
Try installing the [ubuntu-desktop]("apt:ubuntu-desktop") package. That should make sure you have all the components of the default desktop setup installed.

---

### Post by Pulka on 2012-01-16
Nothing...after restarting remains the same

---

### Post by Pulka on 2012-01-16
Can't access any folder!

everything else is working fine...what happened?

---

### Post by Fernhill Linux Project on 2012-01-16
We dont know what happened, installing unstable software is a bit of a gamble to say the least. Try installing another file manager such as 'dolphin' until you get a better answer.

---


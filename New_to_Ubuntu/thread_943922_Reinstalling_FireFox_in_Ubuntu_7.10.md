---
title: "Reinstalling FireFox in Ubuntu 7.10"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-10
Ubunteros,

I use Ubuntu 7.10 64bit. I use Firefox:

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.17) Gecko/20080922 Ubuntu/7.10 (gutsy) Firefox/2.0.0.17


I have this problem. Firefox is always Stalling. Meaning pages freeze and I must wait a few minutes for things to get back to normal. Sometime the browser just closes itself down and I must re-launch it. Lucky for me I get to start where I leave off but anyway this freezing and unexpected shutdown is becoming a pain in the neck....

Maybe re-installing firefox will help? If so..... How can I do this? What are the step by step procedures for uninstalling firefox the updating to latest version?

Thanks for the feedback and suggestions....

---

### Post by AndyCooll on 2008-10-10
You can try one of two things. You can re-install Firefox as you suggest by going to System > Administration > Synaptic Package Manager. Then doing a search for Firefox, right-clicking on and selecting re-install.

Alternatively you can delete your .mozilla folder which is a hidden folder in your home directory. When in your home directory you press CTRL+H to display hidden folders. Make a backup of this before you delete it as deleting this folder deletes all your Firefox settings includig your bookmarks.

:cool:

---

### Post by shifty_powers on 2008-10-10
```
sudo apt-get purge firefox && sudo apt-get clean && sudo apt-get install firefox
```

shoudl do the trick i hope....

---


---
title: "removing extra DE"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by dtconnor on 2013-05-06
I have Ubuntu 13.04 installed and loving it.
I like Unity but my wife perferes the XP like Cinnamon.
I installed Cinnamon but it is not quite what it is on Mint in terms of configuability.

Question 1 - how can I get the same Cinnamon as Mint - I tried upgrade but it told me I had the latest version.
Second I would like to get rid of the Gnome DE so that I only the choice between Cinnamon and Unity

Question 2 - what do I purge to get rid of the Gnome DE or can I use Synaptic seach Gnome Desktop and remove all those files 
without doing damage?

---

### Post by Frogs Hair on 2013-05-06
There is a cinnamon ppa, but I can't tell you how it differs from the Ubuntu repository version and there is a risk with any ppa. If you mean classic gnome open synaptic, locate the gnome panel, enter properties with right click and look at the dependencies. I have the gnome shell and get classic as part of the package, but hesitate removing it because it was installed with the shell. Cinnamon is a modified version of the gnome shell.
 
Check this ppa at Launchpad for features   [http://linuxg.net/how-to-install-cinnamon-on-ubuntu-13-04-12-10-12-04/](http://linuxg.net/how-to-install-cinnamon-on-ubuntu-13-04-12-10-12-04/)

It looks like the Nemo  file manager is included. [https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable)

---

### Post by dtconnor on 2013-05-06
Thx - I removed the Cinnamon that I loaded from the software center and did sudo apt-get --purge autoremove to clean everything up then did a restart.
I then did apt-get install cinnamon
I still eneded up with a version of cinnamon that is not exactly the same as the version on Mint
It just not allow for the config options in set the the Mint version has - for example setting the pannel size - but a lot more.
It is OK I rather use Unity but my wife likes the Windows XPish look - I even renamed the menu botton to START for her. 
I ust don't understand it since Mint is derived from Ubuntu.

---


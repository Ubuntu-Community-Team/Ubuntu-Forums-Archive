---
title: "Installing Firefox 3 RC1?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Jaded Misanthrope on 2008-05-27
Could somebody tell me how to install Mozilla Firefox 3 RC1? I downloaded the file from the Mozilla website and extracted it with Archive Manager, but I now don't know what to do at all--any help?

---

### Post by aridus on 2008-05-27
I would like to know also!

---

### Post by CrossS on 2008-05-27
+ 1

---

### Post by philinux on 2008-05-27
[http://ubuntuforums.org/showthread.php?t=797524&highlight=firefox+rc1](http://ubuntuforums.org/showthread.php?t=797524&highlight=firefox+rc1)

---

### Post by CameO73 on 2008-05-27
There are various ways to do this.


[LIST]
[*]One of them is downloading it manually, unpacking it to a directory of choice and starting **firefox** in that directory.
[*]I've read that starting firefox using the gksu option (e.g. [Alt]-[F2] and then type **gksu firefox**) will enable the Help -> Check for Updates... option
[*]Another way (that I've been using) is described [here]("http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html"). I do recommend using another repository than the one mentioned, though. The bleeding-edge Mozilla repositories can be found [here]("https://edge.launchpad.net/%7Emozillateam/+archive"). Don't forget to select your version (e.g. Hardy Heron for the latest released one) to get the correct deb and deb-src lines. A word of caution: by adding these repositories to Synaptic, you'll be updated with (testing/preview) versions! This could mean that some stuff stops working... (that's what testing means). Oh, and you probably want to have the [Nightly Tester Tools]("https://addons.mozilla.org/en-US/firefox/addon/6543") to get some of your extensions working again in RC1 ...
[/LIST]

---


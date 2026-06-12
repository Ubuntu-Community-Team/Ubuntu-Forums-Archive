---
title: "The repository problem / Trouble with updating"
date: 2019-10-10
forum: New to Ubuntu
---

### Post by kubasienczyk on 2019-10-10
So, I have this problem while updating my Ubuntu 19.04 (Gnome  3.32.1). First off, while attempting to run the process, the message:


  "Failed to download, check your Internet connection"


  prompts. I can still carry on by clicking OK. Then Ubuntu tells me, that my repository data is out of date. Also:


  "E:The repository '[http://ppa.launchpad.net/landronimirc/clamtk/ubuntu](http://ppa.launchpad.net/landronimirc/clamtk/ubuntu)  disco Release' does not have a Release file., W:Updating from such a  repository can't be done securely, and is therefore disabled by  default., W:See apt-secure(8) manpage for repository creation and user  configuration details., E:The repository '[http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) disco Release' does not have a Release file."


  I'm sure I've messed up something simple. Please check the pics attached:


  [URL="https://i.stack.imgur.com/GlH3e.png"][IMG]https://i.stack.imgur.com/GlH3e.png[/IMG]

[/URL]

  [URL="https://i.stack.imgur.com/FlRmm.png"][IMG]https://i.stack.imgur.com/FlRmm.png[/IMG]

[/URL]

  Thanks!

---

### Post by Impavidus on 2019-10-10
The landronimirc PPA hasn't been updated in six years and has no software for disco. It's last supported release is saucy, which is long dead. Disable it. I suggest you remove any software that came from this repository.

The noobslab PPA hasn't been updated in over a year and has no software for disco. It has got packages for bionic, the latest LTS release, so if you really need it, you could modify your sources to use that, but it may not work and cause further package conflicts. I recommend you just disable it and remove any software installed from that repository.

---

### Post by cruzer001 on 2019-10-10
Please post the full output of
```
sudo apt update
```

---


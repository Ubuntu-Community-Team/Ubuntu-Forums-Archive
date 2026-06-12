---
title: "Installing additional software"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by koymackoy on 2011-11-17
[SIZE=3]Hi everyone! Good evening!

I've already installed Wubi and already explore the basics. I want to install additional software. Will it be possible for me to add software even if I only install Wubi and not Ubuntu? What about anti-virus, is it possible to install one in a Wubi environment?

Another thing is Wubi allowed to install software updates?

Thank you very much for your patience.
[/SIZE]

---

### Post by LowSky on 2011-11-17
Wubi is a software package that installs Ubuntu within Windows. Nothing more. Ubuntu then works like normal. Install whatever you want however you want.

---

### Post by Frogs Hair on 2011-11-17
Yes , you can Install programs from the software center in a Wubi installation . You may have noticed that you have access to the host / windows in the ubuntu file system . Unless you directly transfer an infected file from Ubuntu to the host (windows) in the form of a photo or something similar  you should have no virus problem . If you are uncertain about the safety of a documents , media . or photo on your computer remove it .

---

### Post by 3rdalbum on 2011-11-17
> **koymackoy said:**
> [SIZE=3]Hi everyone! Good evening!

I've already installed Wubi and already explore the basics. I want to install additional software. Will it be possible for me to add software even if I only install Wubi and not Ubuntu? What about anti-virus, is it possible to install one in a Wubi environment?

Another thing is Wubi allowed to install software updates?

Thank you very much for your patience.
[/SIZE]

Of course, you can use the Ubuntu Software Center to add more software, just like a normal install of Ubuntu (Wubi is the same as Ubuntu, just installed a little differently).

You can install an anti-virus program, although of course there are no viruses that affect Linux. You'd only need it to find viruses that affect Windows.

You can install software updates as you would with a regular Ubuntu install, but I have heard other users saying not to install kernel updates; so, in Update Manager, you should untick the updates that start with the word 'linux' (for example, "linux-headers" and "linux-image-generic").

In theory, even the kernel updates should be safe, but in practice some users have reported that they seem to cause problems when Wubi has been used, due to the way the bootloader is refreshed. I can't comment on whether this really happens, but I'm just relating what I've heard.

So, in short, install and update whatever you want; but if you want to be cautious, avoid the "linux" kernel updates. All other updates should be perfectly safe.

---

### Post by koymackoy on 2011-11-20
[SIZE=3]Good evening everyone!

Thank you so much for your time and patience. At this very moment I'm installing software - Skype. I've read an article stating that Skype is unstable when installed in Ubuntu 11.10. Anyway that's for me to find out once my installation is complete. :D



 
[/SIZE]

---

### Post by koymackoy on 2011-11-20
[SIZE=3]Hi again, the installation is complete. How can I uninstall it[/SIZE], [SIZE=3]or any program that I would want to uninstall someday, if its not on the Ubuntu Software Center? Here is the link that I used as a guide in removing an application [https://help.ubuntu.com/11.10/ubuntu-help/addremove-remove.html](https://help.ubuntu.com/11.10/ubuntu-help/addremove-remove.html)

Upon clicking the **Installed** button several sub-menus appear like Accessories, Developer Tools, Games, etc. I try to click and double click them but there is no respond. I also click the the drop-down button besides the **Installed** button and select **Canonical Partners** and **For Purchase **respectively but both display a blank page.

I also try to use the **Synaptic** to remove it but Synaptic is missing the search didn't find Synaptic. [https://help.ubuntu.com/11.10/ubuntu-help/addremove-install-synaptic.html](https://help.ubuntu.com/11.10/ubuntu-help/addremove-install-synaptic.html)

Thanks in advance
[/SIZE]

---

### Post by mike555 on 2011-11-20
I recommend installing synaptic package manager and installing using it ,because it tells you what it is installing (maybe more stuff then you want),it will also tell you what it is uninstalling, so you don't uninstall something you want or need.

  really better to do a real install to a separate partition though....

---


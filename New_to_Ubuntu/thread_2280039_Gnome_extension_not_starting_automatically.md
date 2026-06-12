---
title: "Gnome extension not starting automatically"
date: 2015-05-27
forum: New to Ubuntu
---

### Post by anbu-s on 2015-05-27
I've had the Places Status indicator extension on my ubuntu laptop and it was working fine. Lately, the extension doesn't start when I reboot or start the machine. I have to manually switch it on. Typically, when you switch the extension on, it stays on. 
Same issue for another extension - top icons.

I tried removing the places staus extension - but the remove button is not highlighted to click.

How do I solve this so that it opens up automatically whenever i start the machine?

Thanks

---

### Post by monkeybrain20122 on 2015-05-27
Well those extensions can be broken if you have an update. Many of them are unmaintained, some requires installing from git.. I don't find them very reliable. I use only 2

You can remove it and then reinstall it. Since your remove button doesn't work you have to remove manually, open the file manager (you are at your /home), press ctrl + h to show hidden files,  then go to .local/share/gnome-shell/extensions and delete the folder for the extension.


P.S. This folder structure is on my Fedora partition, I think Ubuntu-gnome should be the same.

---


---
title: "Deb package?"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by Yezinki on 2012-09-23
Hi there,

I have this BleachBit deb in downloads, how should it be opened & installed?

Thanks.

---

### Post by Lars Noodén on 2012-09-23
bleachbit seems to be in the software repositories, so the better way would be to use the Software Center, Synaptic or apt-get to install it.  That will make it easier to update, too.

See this link for one example:
[http://ubuntuforums.org/showpost.php?p=12254739&postcount=8](http://ubuntuforums.org/showpost.php?p=12254739&postcount=8)

If there is some reason you still want to work with the version you downloaded manually, then you can use [dpkg](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html) to install or uninstall it.

---

### Post by Yezinki on 2012-09-23
Thanks.

The version in the synatics is .9.1-1 & the latest is .9.1-3.....how do I update & install it?

---

### Post by Lars Noodén on 2012-09-23
If you are using Synaptic, the way to get the  new version is to wait for it to be added to the repository.  There aren't that many changes since version 0.9.2:

[http://bleachbit.sourceforge.net/news/bleachbit-093](http://bleachbit.sourceforge.net/news/bleachbit-093)

If you absolutely cannot live without the small changes in 0.9.3, then you can download the [appropriate .deb file from SourceForge](http://bleachbit.sourceforge.net/download/linux) and then use dpkg to install it.   

Overall, I'm skeptical to the usefulness of bleachbit on non-windows systems.  Other systems are not subject to 'bitrot'  nor do they tend to gather cruft.  The only thing on the system that might waste space would be the package cache and that can be cleared by 'sudo apt-get clean'.  In the user space, there are the browser caches, too, but those can either be adjusted downward or else cleared manually or both.

---

### Post by Elfy on 2012-09-23
sudo dpkg -i /path/to/package.deb

but you might need to get dependencies doing it that way, if you have gdebi installed then right click - install with gdebi

I believe in ubuntu double click will install it with USC

---


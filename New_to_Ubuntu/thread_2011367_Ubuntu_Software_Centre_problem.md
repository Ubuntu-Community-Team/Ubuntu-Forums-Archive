---
title: "Ubuntu Software Centre problem"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by falklandtim on 2012-06-27
Hi Everybody,

I've recently installed Ubuntu 12.04 onto my early MacbookPro (2006/2007)and I seem to have run into a problem while installing Dropbox via the Ubuntu's Software Centre. The Install seemed to hang, and after 20 minutes I got impatient and quit Software Centre. On restarting the Software Centre the DropBox install is still in Software Centres queue but never completes install and if I try click cancel the process just seems to do nothing. I've even left it 'cancelling' for about an hour.

Is there a way I can kill off this Dropbox installation process at the terminal, removing it from the Software Centre queue. Or just reset Software Centre some how. At the moment, because of this hung process I can't use Software Centre to install/uninstall other software.

Thanks in advance guys and girls,

Regards,

Tim

---

### Post by drpjkurian on 2012-06-27
Hi try this
```
sudo apt-get --purge remove dropbox
``` in a terminal

---

### Post by sudodus on 2012-06-27
Have a look at the following thread

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=2008883_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2008883")

---

### Post by falklandtim on 2012-06-27
Thanks for the help guys, very much appriciated.

For some reason it sorted itself out after logging in using Unity 2D. A window popped up complaining about dropbox and I was able to remove it.

---


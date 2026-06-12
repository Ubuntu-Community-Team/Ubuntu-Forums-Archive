---
title: "Grub2 submenu question"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by Planker on 2013-09-27
I'm using grub2. Most of what I've read about grub2 indicates that it should, by default, identify the different kernels and put them all into a submenu. But, on my computer, there is no submenu. Instead all the different kernels all list on the main menu with Windows below it. I'd like to enable the submenu and have the kernels automatically be listed there, but when I search for answers, all of the results show people asking how to disable the submenu instead. So, can anyone tell me what I need to do to enable the submenu and have all the kernels put into the submenu?

---

### Post by oldfred on 2013-09-27
I have not ended up with sub-menu either except for some of my new test installs.

What version of Ubuntu and grub?
fred@fred-Precise:~$ grub-install -v
grub-install (GRUB) 1.99-21ubuntu3.11
fred@fred-Precise:~$ uname -a
Linux fred-Precise 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


Actually I normally delete all but two kernels, current and one older one as backup. And I turn off os-prober and use 40_custom for any other systems I may want to boot. Part of the reason for me is I have lots of old installs and test installs and several drives, so with my standard boot and so not want all the extra versions.

---

### Post by Jonathan Precise on 2013-09-27
What ubuntu version are you using?
What grub version?
(Example: Ubuntu 12.04, grub 1.99)

Try [grub-customizer]("https://launchpad.net/~danielrichter2007/+archive/grub-customizer").

---


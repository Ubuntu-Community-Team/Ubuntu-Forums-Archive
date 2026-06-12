---
title: "Two newbie issues in need of help"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by wayne_n on 2008-10-25
I just loaded ubuntu 8.04 onto my Mac Pro (intel).  It took several tries to get it to take in VMWare Fusion, but it is running fine now.  however, i have an issue with getting vmware tools to run (I'll get help on their forum) and I can't see any files on my mac from Ubuntu or my Ubuntu files from the Mac.  I did set up a share folder in ubuntu, but it only shows me the files in the Mac finder.  When I open the shared folder in Hardy, there is nothing there.  I assume this is a permission issue.  how do i fix it. I set sharing up as directed by another article and that got me to where the ubuntu folder showed up on Mac.  But the Mac folders or the shared files don't show up on Ubuntu.  any help would be appreciated.

---

### Post by NewJack on 2008-10-25
Try following this guys tutorial for installing Ubuntu in VMWare Fusion.  If you scroll down, he details how to get the VMWare Tools running right.  Hope this helped!

---

### Post by wayne_n on 2008-10-26
Joe, there's no link.

---

### Post by Macdude-StL on 2013-04-26
Sounds like a perfect description of what I just went through, except MacOS X 10.8.3, Ubuntu 12.10 (Wheezy), and VMWare Fusion 5.0.3.

Solution: I realized that the installation wasn't complaining much when it encountered missing kernel header files, but was not completing. I entered 'kernel header' in Ubuntu Software Center and looked for a kernel version number matching what was missing. [found one, didn't fix the problem] Then I looked further and found a kernel version with the 'generic' modifier in the name. When I installed this component, the installation process went smoothly, and suddenly I could see the shared folders in /mnt/hgfs, as advertised (no restart required). I restarted anyway, and the folders were still visible (yay!). Trying this process in VirtualBox, I had found that the shared folders (added while VM was running) would not show up until the VM was restarted.

Now I get to figure out an easy way to allow myself write permissions on the files in the shares, since they are owned by a nonexistent user, with ro permission for the root group. Something similar was required in VB (vboxuser?), I just had to join the appropriate group (as stated in the documentation). Something similar is likely in this context as well.

---

### Post by wildmanne39 on 2013-04-26
Thread closed. Please do not post in old threads.

---


---
title: "Dual booting wth Windows Vista"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by varun2 on 2013-08-06
In my laptop I have 11gb unallocated space (unpartitioned)

a) Will I be able to install Ubuntu with this free space ?

b) Since this 11gb free space is not under a particular drive (like D:, E: etc) will I be able to install Ubuntu when I try to install it from CD ?

---

### Post by oldfred on 2013-08-06
Vista usually has MBR(msdos) partitioning which has a 4 primary partition limit. If you have an available primary partition and have not used Windows to create partitions which may convert to dynamic partition it should install into the unallocated space.

11GB is not a lot, but will work, it then becomes how much data you save and where you save it. You also should have a swap partition which is used if RAM runs out of room. It can be the same as your RAM if you may want to hibernate, but that is not recommended when dual booting & Ubuntu normally boots quickly. 
       [URL="https://help.ubuntu.com/community/SwapFaq"]https://help.ubuntu.com/community/SwapFaq

      [/URL]
 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)

What video card and how much RAM?
 If not a lot of RAM the lighter weight versions Xubuntu or Lubuntu work better. Full Ubuntu also needs a decent video system to run Unity but there are many other gui choices.

    [URL="https://help.ubuntu.com/community/SwapFaq"]
[/URL]

---

### Post by HeroOfCanton on 2013-08-07
a) Yes. (For a basic install)
b) Yes. Select the "Install Ubuntu along side Windows" option on setup and Ubuntu will create the new partition for you and allow you to choose between Windows and Linux when your computer starts.

Extra credit: Please back up any important data before attempting the install.

Still read oldfred's info (especially the install link), as it's good info. Just thought a simpler answer may help you get started a bit more easily.

---


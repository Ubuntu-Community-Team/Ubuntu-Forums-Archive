---
title: "Firefox won't launch"
date: 2018-12-12
forum: New to Ubuntu
---

### Post by Norm24 on 2018-12-12
As of today Firefox won't launch under Ubuntu or Ubuntu Mate 18.04.I click on the icon in panel,desktop or menu and nothing.Everything else works including Thunderbird,internet connection is good.The result is the same for either the repo build or the Mozilla build...nothing.

Had to install Chromium to just post this.Curious if anyone else has had a sudden collapse of Firefox.

Would love to get FF back...not a big fan of Chromium.

---

### Post by oldrocker99 on 2018-12-12
Did you download Firefox from their website? Try this:
```
sudo apt remove firefox
```

Then, do this:
```
sudo add-apt-repository ppa:mozillateam/ppa
sudo apt update
sudo apt install firefox-esr
```

This will make sure that Firefox stable (which is what firefox-esr is) is kept being updatable.

Any program that is not in the repositories can usually be found by Googling [name of program] ppa.

---

### Post by Impavidus on 2018-12-13
Have you tried starting firefox from a terminal?```
firefox
```It may give a useful error message.

---

### Post by ajgreeny on 2018-12-13
You may also have some configuration problem, so try renaming the hidden **.mozilla** folder in your home, and then try starting firefox again.

---

### Post by Norm24 on 2018-12-13
> **Impavidus said:**
> Have you tried starting firefox from a terminal?```
firefox
```It may give a useful error message.

This is the error message I received:
```
firefox: error while loading shared libraries: libatomic.so.1: cannot open shared object file: No such file or directory
```

---

### Post by Impavidus on 2018-12-13
libatomic is supposed to be there. What do you get from```
apt-cache policy libatomic1
```

---

### Post by Norm24 on 2018-12-13
> **Impavidus said:**
> libatomic is supposed to be there. What do you get from```
apt-cache policy libatomic1
```

I get this:
```
libatomic1:
  Installed: (none)
  Candidate: 8.2.0-1ubuntu2~18.04
  Version table:
     8.2.0-1ubuntu2~18.04 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
     8-20180414-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages
```

---

### Post by Norm24 on 2018-12-13
Thanks Impavidus,that put me on the right track.

All set will mark as solved.

---

### Post by Impavidus on 2018-12-13
Peculiar...

When checking again I see that libatomic1 is not listed as a dependency of firefox, not even indirectly, but firefox tries to load libatomic nonetheless. Anyway, you solved it.

---


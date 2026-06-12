---
title: "[SOLVED] how do i uninstall.."
date: 2008-07-05
forum: New to Ubuntu
---

### Post by ercferret18 on 2008-07-05
whenever I try to uninstall the program "kio-umountwrapper", I keep getting an error message that says "E: kio-umountwrapper: subprocess post-removal script returned error exit status 2". This happened after i had installed kubuntu and tried to remove it. I am using ubuntu 8.04.1

---

### Post by drs305 on 2008-07-06
The problem appears to be that a file is missing that is looked for during an uninstall. It doesn't really matter what's in it. So you make a file with that name, and then run the APT uninstall.

Here's how: 
```

sudo mkdir -p /usr/share/apps/d3lphin/servicemenus
sudo touch /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop
sudo apt-get remove kio-umountwrapper
```

If everything uninstalls and the created folder still exists:
```

sudo rm -R /usr/share/apps/d3lphin/servicemenus

```


[URL="https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729"]Link
[/URL]

---

### Post by ercferret18 on 2008-07-06
it worked! thanks

---


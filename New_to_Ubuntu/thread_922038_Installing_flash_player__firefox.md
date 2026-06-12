---
title: "Installing flash player / firefox"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by aeamacman on 2008-09-16
[FONT="Trebuchet MS"]Hi there,

I'm having a frustrating time trying to install adobe flash player for firefox on my 8.04 based kubuntu machine. This is what my konsole looks like when I make an attempt at running the script at ~/Desktop/flash/flashplayer-installer :

andrew@soyo:~$ cd Desktop
andrew@soyo:~/Desktop$ cd flash
andrew@soyo:~/Desktop/flash$ flashplayer-installer
bash: flashplayer-installer: command not found
andrew@soyo:~/Desktop/flash$

I also tried entering the command this way, adding ./ to flashplayer-installer :

andrew@soyo:~/Desktop/flash$ ./flashplayer-installer
bash: ./flashplayer-installer: Permission denied
andrew@soyo:~/Desktop/flash$

But it tells me permission denied. I seem to be having this problem with all shell scripts. Am I not entering the command properly? Any help would just be great![/FONT]

---

### Post by Tatty on 2008-09-16
Flashplayer 9 is in the repos.

Simply run:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by zvacet on 2008-09-17
```
sudo apt-get install kubuntu-restricted-extras
```

will install you flash and other things you need anyway

---


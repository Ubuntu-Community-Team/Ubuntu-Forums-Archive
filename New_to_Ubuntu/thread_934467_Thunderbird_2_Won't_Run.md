---
title: "Thunderbird 2 Won't Run"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by March Felloworthy on 2008-09-30
Hi, everyone. Could you help me with a problem I'm having, please?

I'm running 8.04 (regular distro) and am trying to get Thunderbird working. I've downloaded it from the repositories and a menu item has appeared for it in the Applications - Internet menu, but when I click on it an application titled "Starting Mozilla Thun..." appears in the bottom panel for a little over fifteen seconds, then disappears again.

Do you have any suggestions?

---

### Post by MusicMastaMike on 2008-09-30
Try running it in a terminal.  Go to Applications>Accessories>Terminal, and type ```
thunderbird
``` when the window appears.  Please post the output here.

---

### Post by March Felloworthy on 2008-10-01
Hi, Mike. Thanks for responding. Here's what I get:

```

/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

Hmm. So it looks like I'm missing a file. Where do I find it?

---

### Post by MusicMastaMike on 2008-10-01
Open a terminal and type:
```
sudo apt-get install libstdc++5 libstdc++6
```

That should do the trick!

---

### Post by March Felloworthy on 2008-10-01
Aha! It did indeed! Thank you very much, Mike!

---


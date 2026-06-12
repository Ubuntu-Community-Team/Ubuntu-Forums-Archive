---
title: "moving folders into theme folder."
date: 2012-08-13
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-08-13
Hello, Can someone tell me what I'm doing wrong?
I have downloaded some window themes for gnome on Ubuntu 12.04, I'm cd'ing to where the folder is - then ```
mv Mirav2 ~/.themes
```it correctly disappears from my download folder, but fails to appear in the .theme folder, neither can it be seen in gnome-tweak-tool:( I have no idea where it's going too instead. I know now would be the time to use grep, but I can't quite figure out how it works ```
grep Mirav2
```? but nothing happens, it seems to just hang - twenty mins is the max I've allowed it to just 'seem inactive'

 Thank you kindly.

---

### Post by philinux on 2012-08-13
Use this.

```
sudo updatedb

then

locate Mirav2
```

Also you could just use nautilus to move the file.

---


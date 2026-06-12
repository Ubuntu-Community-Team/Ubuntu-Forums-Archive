---
title: "Copy folders to usb drive using terminal"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by Yinepu on 2011-12-10
I tried this in the terminal and it's just giving this message for every file: "cp: cannot create symbolic link `/media/HDD/sys/class/vc/vcsa4': Operation not permitted"......

---

### Post by spiky001 on 2011-12-10
Have you tried using ```
sudo cp -v file/to/where/ever
```

---

### Post by Yinepu on 2011-12-10
Well that just makes it say "omitting directory '/media/f044be81-caad-4224-9d5d-a4e50a9dc23e'", which was the problem I had initially before writing "cp -R" instead of "cp".

---

### Post by oldos2er on 2011-12-10
Posts moved to new thread.

---


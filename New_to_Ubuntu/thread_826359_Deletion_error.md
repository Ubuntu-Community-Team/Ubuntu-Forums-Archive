---
title: "Deletion error"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Yewni on 2008-06-11
Just got an odd error while trying to empty the trash bin.  It says:

> Error removing file: Permission denied

Any idea how to get this fixed?

Thanks!

---

### Post by iaculallad on 2008-06-11
> **Yewni said:**
> Just got an odd error while trying to empty the trash bin.  It says:



Any idea how to get this fixed?

Thanks!

What about doing this:

```
sudo rm -r ~/.local/share/Trash/files/*
```

User Trash:

```
sudo rm -r /home/username/.local/share/Trash/*
```

---

### Post by Yewni on 2008-06-11
Worked like a charm!

Thanks

---

### Post by chinaski on 2008-06-20
this don't work for me

the trash (file) folder in .local etc. is empty while if I open it trhough trash desktop icon and applet I see the file

so I right click -> delete from trash and I get 

Error removing file: Permission denied

then I right click -> permissions -> read and write -> apply to enclose files and I get no error but nothing changes

????

---


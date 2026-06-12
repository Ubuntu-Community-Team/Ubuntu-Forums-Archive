---
title: "Batch Rename Extensions"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by suffer1989 on 2008-11-24
ive got about 100 lectures in Mp3 format, scattered in different folders. I took them all off a disk. However, their extension is ".mp3;1". Playing it on a pc is no issue, but is there any batch extension rrenamer so i can listen to them on my MP3 player ? it only recognises the .mp3 extension.

thanks

---

### Post by suffer1989 on 2008-11-24
no worries, GPRename worked, problem solved 

:D

---

### Post by Furat on 2008-11-24
for file in *.mp3* ; do mv $file `echo $file | sed 's/\(.*\.\)mp3\;1/\1mp3/'` ; done

---

### Post by diablo75 on 2008-11-24
> **Furat said:**
> for file in *.mp3* ; do mv $file `echo $file | sed 's/\(.*\.\)mp3\;1/\1mp3/'` ; done

I'm curious... do you just paste that into a terminal?  Or is this python or something else?  Just wondering...

---

### Post by ghostdog74 on 2008-11-25
> **Furat said:**
> for file in *.mp3* ; do mv $file `echo $file | sed 's/\(.*\.\)mp3\;1/\1mp3/'` ; done

no need to call external sed.
```

for file in *.mp3*
do
  mv $file ${file/;1/}
done

```

---

### Post by kpkeerthi on 2008-11-25
For the records... Thunar also has Bulk Rename. ```
thunar -B
```. If you use XFCE, you should already see it listed in your menu.

---


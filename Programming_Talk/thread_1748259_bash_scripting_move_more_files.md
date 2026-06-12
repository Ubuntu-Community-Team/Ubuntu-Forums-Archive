---
title: "bash scripting move more files"
date: 2011-05-03
forum: Programming Talk
---

### Post by chukchuck on 2011-05-03
```
dest="$HOME/Dropbox"
files=`zenity --file-selection --multiple --separator=' ' --title="Choose files"`
mv "${files[@]}" -t $dest

```

but i have an error because it "ignore" destination and say me that "mv cannot stat file1 file2"

---

### Post by chukchuck on 2011-05-03
solved!

---


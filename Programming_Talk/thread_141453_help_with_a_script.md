---
title: "help with a script"
date: 2006-03-08
forum: Programming Talk
---

### Post by chronusdark on 2006-03-08
im new to writing bash scripts and i need to figure out how to loop a command on every file in a directory 
and how to put the filename less the extention into a variable

---

### Post by kabus on 2006-03-08
This would put the filename of the first file in a directory into the variable $file and strip off everything after (and including) the last dot in the filename, then repeat the process with the next file until there aren't any files left :
```
for file in *; do file="${file%.*}"; echo "$file"; done
```

---

### Post by chronusdark on 2006-03-08
thank you very much

---

### Post by chronusdark on 2006-03-08
one more question how do i add one more character to the end of th $file varible?

---

### Post by hod139 on 2006-03-08
[quote=chronusdark]one more question how do i add one more character to the end of th $file varible?[/quote]

I'm not 100% sure what you are asking.  If you want to add a new file extension just type:
```

for file in *; do file="${file%.*}.foo"; echo "$file"; done 
```

---


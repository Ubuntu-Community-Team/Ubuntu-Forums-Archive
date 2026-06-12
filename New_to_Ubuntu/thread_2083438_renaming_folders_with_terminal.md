---
title: "renaming folders with terminal"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by spillage2 on 2012-11-12
Hi All,

I have been doing more and more via the terminal but come across this and it really bugs me.

If I create a folder with a space in it within terminal (some_folder_name) i always use the underscore but if i create just a new folder using the gui it will use (new file (2nd copy) not new_file_(2nd_copy)

if that makes sense.

ok so if i use mv in terminal how would i change "new file (2nd copy)" to "new_file_(2nd_copy).

terminal keeps complaining about the unexpected token `)'

i thought just cd to directory and use the "\" where a space is or am i being a bit thick and missing a vital part.

I do keep telling my family to stop using spaces but  i am doing my best to keep them away from the ms mindset...
Cheers,

Spill.

---

### Post by dannyboy79 on 2012-11-12
so your folder or filename actually has a parenthesis in it?
i think it would this
mv 'new file (2nd copy)' 'new_file_(2nd_copy)'
using a single quote around the filename BUT I would strongly suggest NOT using special characters in filenames!! Spaces aren't half as bad as special characters like parenthesis!

---

### Post by Lars Noodén on 2012-11-12
Try with single quotes or escaping the parenthesis and spaces with backslashes

```

mv 'new file (2nd copy)' 'new_file_(2nd_copy)'
# Or
mv new\ file\ \(2nd\ copy\) new_file_\(2nd_copy\)

```

---


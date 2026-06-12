---
title: "Bash help, going through subdirectories"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by tube013 on 2008-10-20
I've got a bunch of scanned single page tiffs each grouped by document in directories 0001, 0002A, 0031... etc.  I have a script that will convert the tiffs to pdf, named based on the argument past to the script.  I want to write a script that will go into every subdirectory run the script passing the name of the subdirectory it is in to the script as the argument.

This is what I've got so far.

```
for dir in $(find ./ -type d);
do
 echo "$dir"
 script.sh "$dir"
 cd ..
done
```

but it includes a "./" on the argument.. how can I remove that? or find another option to pass the subdirectory name as the argument?

Thanks!

---

### Post by PointyWombat on 2008-10-20
Hi,
If you dont need to descend into deeper directories, then this find syntax will work.

```
find . -maxdepth 1 -mindepth 1 -type d -printf %P\\n
```

---

### Post by tube013 on 2008-10-20
Thank you.

This is what I ended up using and it worked.

```
for dir in $(find . -maxdepth 1 -mindepth 1 -type d -printf %P\\n);
do
 cd "$dir"
 script.sh "$dir"
 cd ..
done
```

---


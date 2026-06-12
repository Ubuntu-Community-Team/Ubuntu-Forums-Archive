---
title: "adding newlines to ends of files"
date: 2006-12-01
forum: Programming Talk
---

### Post by cyberslayer on 2006-12-01
I have a directory that contains a large amount of C++ source code as well as subdirectories which contain more code and I would to know how to add newlines to the ends of all text/cpp/hpp/h files that don't end with newlines
so that g++ won't generate 5 million lines like "warning: no newline at end of file" when I build my code.  I don't want to do this manually because there are far too many files to add newlines to by opening them and adding a blank line to the end of each file.

Thanks

---

### Post by lloyd mcclendon on 2006-12-01
hi

you might want to check out awk it's sweet


but something like this

```
for extension in "txt cpp hpp h" ; do
    for file in `find -type f -iname "*.${extension}" ; do
        cat ${file} | awk ' { print $0 } END { print } ' > ${file}.new
    done
done
```

then you can use a similar looping technique to mv ${file} ${file%.new}

---

### Post by Jucato on 2006-12-01
I think you can safely ignore those since they are just warnings. However, I believe that a new line at the end of the file is an ISO C/C++ standard.

---

### Post by dwblas on 2006-12-04
Read the dir.  Open each file in append mode and write a "\n".  If you want to get fancy you can check the last character to see if it is a newline first.

---

### Post by ghostdog74 on 2006-12-05
```

find . \( -name "*.cpp" -o -name "*.h" -o -name "*.hpp" \) -print | xargs sed -i -e "/$/G" 

```

---

### Post by Arndt on 2006-12-05
> **ghostdog74 said:**
> ```

find . \( -name "*.cpp" -o -name "*.h" -o -name "*.hpp" \) -print | xargs sed -i -e "/$/G" 

```

sed -i -e "/$/G" adds a newline after every line. To add one only after the last line, do

```
sed -i -e '$G'
```

To add a newline only if there isn't one in place seems more difficult.

---

### Post by ghostdog74 on 2006-12-05
> **Arndt said:**
> sed -i -e "/$/G" adds a newline after every line. To add one only after the last line, do

```
sed -i -e '$G'
```

To add a newline only if there isn't one in place seems more difficult.

thanks. I have rusty brains :)

---

### Post by Ben Sprinkle on 2006-12-05
If you open a file in Gedit it auto puts a new line at end of file so just open and save. Could take longer though. :P

---


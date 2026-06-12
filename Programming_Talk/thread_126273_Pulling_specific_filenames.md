---
title: "Pulling specific filenames"
date: 2006-02-06
forum: Programming Talk
---

### Post by jaykup on 2006-02-06
I'm trying to pull only the largest resolution files out of a list of names using bash

This is a sample list of "file"

image1-800
image1-1024
image1-1280
image2-800
image3-800
image3-1024
image4-800

and I'd like it to pull out a list like this

image1-1280
image2-800
image3-1024
image4-800

The main pattern I can think to work with is pretty much filename#-size

Any ideas??

---

### Post by rydow on 2006-02-06
You could use something like this:

#slask is the file with the file names in
# may be obtained by:
# ls > slask

# get unique file names without -1280 etc.
for file in $(cat slask | sed 's/\(.*\)\(-.*\)/\1/g' | sort -u)
do
  # calculate max and print the max file name
  cat slask | grep $file | awk 'BEGIN {FS = "-"; max = 0;}{if ($2 > max) max = $2;} END {print $1 "-" max}'
done

/Jonas

---

### Post by jaykup on 2006-02-06
You amaze me with sed and awk, i am definitely going to read harder into them, thanks again, it worked great :)

---

### Post by jerome bettis on 2006-02-06
awk should not be anyones favorite language but it's really getting close to being mine.

```
BEGIN  {
    FS="-";
    i=0;
}

{
    file=substr($1, length($1));
    if (i < file)  {
        t[i++] = file;
    }
    if (nums[file] < $2)  {
        nums[file] = $2;
        names[file] = $1;
    }
}

END  {
    for (j = 0; j < i; ++j)  {
        printf("%s%c%s\n", names[t[j]], FS, nums[t[j]]);
    }
}
```

---


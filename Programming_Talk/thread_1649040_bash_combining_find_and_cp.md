---
title: "bash combining find and cp"
date: 2010-12-19
forum: Programming Talk
---

### Post by flyingsliverfin on 2010-12-19
I was wondering if it was possible to combine find and cp on the same  line using a pipe (like find `pwd` "*.png" | cp *what i found* `pwd`/pngs/)
i don't want to create a whole  script, just one line. is that possible?

---

### Post by roccivic on 2010-12-19
```
find ./source_dir -name *.png | xargs cp --target-directory=./destination_dir
```

---

### Post by CharlesA on 2010-12-19
You can use -exec with find, instead of piping the output to run the cp command.

---

### Post by roccivic on 2010-12-19
But also, why not just:

```
cd ./source_dir/
cp -rp *.png ./destination_dir
```

---

### Post by flyingsliverfin on 2010-12-19
isnt ./ for executing scripts?

---

### Post by sisco311 on 2010-12-19
> **roccivic said:**
> ```
find ./source_dir -name *.png | xargs cp --target-directory=./destination_dir
```

This will work incorrectly if there are  any  filenames  containing newlines, single or double quotes, or spaces.


```
find ./source_dir -name \*.png -print0 | xargs -0 cp -t path/to/destination
```
or
```
find ./source_dir -name \*.png -exec cp -t path/to/destination '{}' +
```should work as expected.

---

### Post by roccivic on 2010-12-19
> **flyingsliverfin said:**
> isnt ./ for executing scripts?

"." means "current working directory"

---

### Post by flyingsliverfin on 2010-12-19
thx

---

### Post by flyingsliverfin on 2010-12-19
> **roccivic said:**
> 
```
cd ./source_dir/
cp -rp *.png ./destination_dir
```

this only works if the images are mixed with other files in a single folder. mine are scattered around different folders, thats why i wanted to use find

---

### Post by roccivic on 2010-12-20
That's weird, it should work. I can't understand why the "r" switch is being ignored...

---

### Post by trent.josephsen on 2010-12-20
-r tells cp to copy directories recursively.  You didn't name any directories on the command line, and if you had, they would have been copied with all their contents -- not what you wanted.

Keep in mind *.png is expanded by your shell, not by cp.  These two command lines are equivalent (assuming apple.png orange.png banana.png are the only .png files in the current directory):
```
$ cp *.png ~/dest
$ cp apple.png orange.png banana.png ~/dest
```

(What's really annoying is accidentally hitting Enter without adding the destination folder -- in this case it would complain that 'banana.png' is not a directory, but in other circumstances it can overwrite files and have other annoying results.)

---


---
title: "Need help with a video conversion script"
date: 2007-12-26
forum: Programming Talk
---

### Post by jasonpeinko on 2007-12-26
I am new to programing in linux, i have worked with c++ for a while though.

I am trying to make a simple program to take every single movie i have in a folder and convert it using mencoder, i have it working to run the commands,

i just need to know to get a list of all the files in the directory (im asuming ls or dir) and store them to a variable probably an array

---

### Post by ghostdog74 on 2007-12-26
use the for loop
```

for files in *files_to_encode*
do
  mencoder  -<options> blah blah... $files blah blah
done

```

---


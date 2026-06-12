---
title: "Help me with a script to check broken debs please!"
date: 2009-02-25
forum: Programming Talk
---

### Post by PryGuy on 2009-02-25
Good day!
I download Ubuntu repo with apt-mirror and I found that some of my files are broken. What I want is a script that would check folder with debs for broken packages. 'dpkg -c packagename' shows broken packages, but how do I track all files in a given directory with all subfolders? Thank you!

---

### Post by geirha on 2009-02-25
The folowing will find all .deb files under /path/to/dir, recursively, and run dpkg -c on each deb file.
```
find /path/to/dir -name "*.deb" -exec dpkg -c {} \;
```

---

### Post by PryGuy on 2009-02-25
Okay, people, the script looks like this:```
#!/bin/bash

list=(`find ~/apt-mirror/ -name "*.deb"`)

#echo ${list[@]}

for filename in "${list[@]}"
do
  dpkg-deb -c $filename > /dev/null
  if [ "$?" = "2" ]; then
    echo $filename >> ~/Desktop/errors.txt
  fi
  echo $filename
done

echo "All done!" >> ~/Desktop/errors.txt

exit 0
```Thanks, geirha!

---


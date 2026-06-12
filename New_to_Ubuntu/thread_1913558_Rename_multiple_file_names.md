---
title: "Rename multiple file names?"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by rom3lol on 2012-01-22
I would like to add '00'(zeros) to the front of files with name 1.* 2.* 3.* and so on.
I'm looking at the rename command but I don't understand it much.

---

### Post by rom3lol on 2012-01-22
Ok a little more searching did the job. 

[http://stackoverflow.com/questions/3672301/linux-shell-script-to-add-leading-zeros-to-file-names](http://stackoverflow.com/questions/3672301/linux-shell-script-to-add-leading-zeros-to-file-names)

```
rename 'unless (/0+[0-9]{4}.txt/) {s/^([0-9]{1,3}\.txt)$/000$1/g;s/0*([0-9]{4}\..*)/$1/}' *

```

I changed both '{4}' to {3}, because my files where 3 digits long and '.txt' to .pdf and It worked awesome!

---


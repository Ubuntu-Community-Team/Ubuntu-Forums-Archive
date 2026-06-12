---
title: "Help with wget command"
date: 2010-10-05
forum: Programming Talk
---

### Post by white_brain13 on 2010-10-05
Guys, i need some help with wget download command. I want to download files in a web directory not in order. Example, in web directory there are files 1.jpg, 2.jpg, 3.jpg, 4.jpg, ....., 13.jpg. I want to download with 2 gap of files so i will get 1.jpg, 4.jpg, 7.jpg,...., 13.jpg. So what is the command i need to add?

---

### Post by endotherm on 2010-10-05
well, just put it in a for loop

[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)

should be something like
```

#!/bin/bash

for p in {1..20..3}
do
   wget "http://somesite/somefolder/"$p".jpg"
done

```{1..20..3} means count from one 1 to 20, incrementing by 3 with each count (1,4,7,10,13,16, 19...n)

---


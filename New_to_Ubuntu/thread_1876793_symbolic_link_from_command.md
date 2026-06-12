---
title: "symbolic link from command"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by Mount on 2011-11-06
Hi, 

I would like to make a new **symbolic link** for each file of a given **type** found in a **directory tree** and have this link saved in a folder of my choice. I can almost achieve this but the links are broken. Here's what I have so far for all .pdfs: 

```
ln -s $(find . -name '*.pdf') ./_OUT/
```

if the **-s** switch is omittrd then a **hard** link created. I do not want to do this however... as this appears to have a similar data footprint as copying the original. 

Thanks, 
g

---

### Post by papibe on 2011-11-06
Try this script:
```
#!/bin/bash

while IFS= read -r -d '' filename
do
        ln -s "$filename"  ./_OUT/

done < <(find -name '*.pdf' -print0)
```
Hope it helps,
Regards.

---

### Post by Mount on 2011-11-06
Great, that does what I need. but... 

I had to modify the output path of **ls** by 
removing the ./_OUT/ path such that the links were
created in the current working directory, otherwise
the links were not pointing to the correct place. 

Is it possible to make the links absolute rather than 
relative? 

cheers,

---

### Post by papibe on 2011-11-06
Using 'find' with an absolute path does that trick:
```
#!/bin/bash

while IFS= read -r -d '' filename
do
        ln -s "$filename" ./otherdir/

done < <(find /home/youruser/ -name '*.py' -print0)

```

EDIT: note that ./otherdir/ must exist.

Regards.

---


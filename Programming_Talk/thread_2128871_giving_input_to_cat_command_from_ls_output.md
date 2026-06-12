---
title: "giving input to cat command from ls output"
date: 2013-03-24
forum: Programming Talk
---

### Post by IAMTubby on 2013-03-24
Hi,
I am new to shell scripting.

I want to basically use cat command as, 
cat file1.txt file2.txt > output.txt

But the inputs namely file1.txt and file2.txt should come from the ls output as ls fil*.txt. 
I know I have to use pipes(|) but I'm finding it difficult to google.

Please advise.
Thanks.

---

### Post by IAMTubby on 2013-03-24
Right, got it done. I used this script.

```

#!/bin/bash


for file in fil*.txt
do
  cat "$file"
  echo
done > newfile

```

Thanks.
Unable to mark thread as solved.

---

### Post by trent.josephsen on 2013-03-24
you didn't try this?
```
cat fil*.txt >newfile
```

---

### Post by IAMTubby on 2013-03-24
> **trent.josephsen said:**
> you didn't try this?

trent.josephsen, I don't know what I was thinking.
I have been up for some time and was just not thinking right, I guess.

Thanks anyways.
Feel so stupid :)

---


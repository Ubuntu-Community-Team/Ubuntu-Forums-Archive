---
title: "Bash script"
date: 2013-05-27
forum: Programming Talk
---

### Post by UnderwaterCE on 2013-05-27
Hello,

I have a very simple script that won't seem to work.  Can someone please help.  

```

#!/bin/bash

DIR="/media"

if[ 'ls $DIR | wc -l' -eq 0 ]; then
               echo "No Drive"
else
               echo "Drive Found"
fi

```

And this is what I get when I run it.

[B]./script: line 5: syntax error near unexpected token 'then'
./script: line 5: 'if[ 'ls $DIR | wc -l' -eq 0 ]; then'[/B]


Thanks so much!

---

### Post by BioHazardTM on 2013-05-27
Between the start of if and the condition there should be a space and if you have to use a pipe (|), in the condition you have to enclose that with parenthesis and a dollar before the parenthesis.

Here is the code:
```
#!/bin/bash

DIR="/media"

if [ $(ls $DIR | wc -l) -eq 0 ]; then
    echo "No Drive"
else
    echo "Drive Found"
fi
```

I hope it helps you!

---

### Post by mörgæs on 2013-05-27
Moved and renamed.

---

### Post by ofnuts on 2013-05-28
No need to make things more complicated than need:

```

ls /media/*
if [[ $? -ne 0 ]] 
then
   echo 'No media'
    ....

```

or the terser

```

ls /media/* && { echo 'No media...' ; exit 1 ; }

```

---


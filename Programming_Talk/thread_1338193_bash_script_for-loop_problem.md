---
title: "bash script for-loop problem"
date: 2009-11-26
forum: Programming Talk
---

### Post by ko_ko_now on 2009-11-26
hello ,
i'm facing a little problem here,


after running this:
```


#!/bin/bash
for i in {1..5} 
 do 
  echo "Welcome $i times" 
done 

```I get this:
```

~$ sh name.sh
Welcome {1..5} times

```instead of this:
```


~$ Welcome 1 times
Welcome 2 times
Welcome 3 times
Welcome 4 times
Welcome 5 times

```



my bash version is :
```

~$ /bin/bash --version
**GNU bash, version 4.0.33(1)-release (i486-pc-linux-gnu)**
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

```and i'm on **Ubuntu 9.10**


can somebody help me and tell me what i'm doing wrong??

(it's not the first time that stupid problems of this kind happen to me :x)

thanks

---

### Post by mo.reina on 2009-11-26
i think you're supposed to use the seq arguement

```
for i in $(seq 1 2 20)
```

---

### Post by ghostdog74 on 2009-11-26
it works for me
```

# bash --version
GNU bash, version 4.0.16(1)-release

# ./shell.sh
Welcome 1 times
Welcome 2 times
Welcome 3 times
Welcome 4 times
Welcome 5 times


```

---

### Post by Arndt on 2009-11-26
> **ghostdog74 said:**
> it works for me
```

# bash --version
GNU bash, version 4.0.16(1)-release

# ./shell.sh
Welcome 1 times
Welcome 2 times
Welcome 3 times
Welcome 4 times
Welcome 5 times


```

The OP probably ran the script like this:

sh shell.sh

rather than

./shell.sh

---

### Post by John Bean on 2009-11-26
> **Arndt said:**
> The OP probably ran the script like this:

sh shell.sh

rather than

./shell.sh

No probably about it, that's exactly what he did - it's right there in his post for all to read.

---

### Post by Arndt on 2009-11-26
> **John Bean said:**
> No probably about it, that's exactly what he did - it's right there in his post for all to read.

I must have assumed the previous answerers took care of such details as reading what was actually written...

---

### Post by ko_ko_now on 2009-11-26
wow!!!! it works,
thanks a lot guys!!!
I'm glad for posting here,
and that you noticed that detail ... by chance i wrote the way i run the script.
:D

(i thought it's the same the "sh command" and the "./")

---

### Post by John Bean on 2009-11-26
> **ko_ko_now said:**
> (i thought it's the same the "sh command" and the "./")
No, you explicitly used "sh" to run the script in a new shell. Had you used "bash" instead it would have worked.

Not specifying will tell your current shell to use the one it finds at the top of the script, or the default shell (usually bash) otherwise.

---

### Post by John Bean on 2009-11-26
> **Arndt said:**
> I must have assumed the previous answerers took care of such details as reading what was actually written...
Fair comment, and quite right ;-)

Actually I wasn't intentionally being critical of your message and apologise if it seemed that way. My comment was on the whole thread and carries much the same implications as your reply to it.

---

### Post by Arndt on 2009-11-26
> **John Bean said:**
> Fair comment, and quite right ;-)

Actually I wasn't intentionally being critical of your message and apologise if it seemed that way. My comment was on the whole thread and carries much the same implications as your reply to it.

No problem, no need to apologise.

---


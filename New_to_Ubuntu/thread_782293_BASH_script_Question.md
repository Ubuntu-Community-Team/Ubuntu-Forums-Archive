---
title: "BASH script Question"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by DBrocks on 2008-05-04
Hey guys,

This should be very simple for many of you: How can I make a bash script that saves the contents of a text file to a variable, to be later used in the script?

Thanks!
~Dan

---

### Post by aheckler on 2008-05-04
I believe it's

```
VARIABLE=$(cat /path/to/file)
```

---

### Post by DBrocks on 2008-05-04
Amazing! Thanks! Perfect!

---

### Post by Oldsoldier2003 on 2008-05-04
```
#!/bin/bash
OUTPUT="$(cat var.txt)"
echo $OUTPUT
```

---

### Post by PeterJS on 2008-05-04
Backticks work too.
```

#!/bin/bash
OUTPUT=`cat var.txt`
echo $OUTPUT

```

---

### Post by Oldsoldier2003 on 2008-05-04
yep lots of ways to skin a cat :)

---


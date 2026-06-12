---
title: "File operations (Bash)"
date: 2010-08-05
forum: Programming Talk
---

### Post by X.Cyclop on 2010-08-05
What's wrong with this code?

```

#!/usr/bin/env bash
# File operations
 
echo "Give me a name"
read ENTRADA
 
if [ -s $ENTRADA ]; then
	echo "$ENTRADA is a file and is not empty"
		if [ -x $ENTRADA ]; then
			echo "$ENTRADA is executable"		
		fi
		if [ -r $ENTRADA ]; then
			echo "$ENTRADA is readable"
		fi
		if [ -w $ENTRADA ]; then
			echo "$ENTRADA is writable"
		fi
 
elif [ -f $ENTRADA ]; then
	echo "$ENTRADA is a file and not a folder, but it is empty"
elif [ -d $ENTRADA ]; then
	echo "$ENTRADA is a folder"
else 
	echo "$ENTRADA does not exist!"
fi

```
Whether I type a file or a folder name, I get always to the first IF, as if it would be a file (and not empty).:p

---

### Post by Arndt on 2010-08-05
> **X.Cyclop said:**
> What's wrong with this code?


Whether I type a file or a folder name, I get always to the first IF, as if it would be a file (and not empty).:p

Directories are files too.

---

### Post by X.Cyclop on 2010-08-05
Haha, i didn't know that... so is there anything to separate them?

---

### Post by Bachstelze on 2010-08-05
```
if [ -f $ENTRADA ] && [ -s $ENTRADA ]
```

---

### Post by Martin Witte on 2010-08-05
start your testing with a test for directory, then for a non-zero file.

---

### Post by X.Cyclop on 2010-08-05
Thank you so much! You two helped me.

---


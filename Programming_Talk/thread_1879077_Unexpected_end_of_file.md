---
title: "Unexpected end of file"
date: 2011-11-10
forum: Programming Talk
---

### Post by MaxRabbit on 2011-11-10
I'm having a heck of a time running a very simple script I wrote. I keep getting "line 17: syntax error: unexpected end of file." Any idea why this would be happening? It works on Red Hat, the OS my school is using that I am creating this script for, but I would really like to be able to do my "homework" at home.

Thanks,
max

```

#Command moves file to a temporary wastebasket
#Script uses first parameter as the file to be trashed.
#Script must be installed in bin directory.
#
#Step 1 - The directory named wastebasket is to be created in
#the user's home directory if it does not already exist.
#Home Directory's wastebasket
#$HOME/wastebasket
wastebasket=$HOME/wastebasket
if [ -d $wastebasket ]
 then
	echo "wastebasket exists"
 else
	echo "wastebasket does not exist"
fi

```

---

### Post by trivialpackets on 2011-11-10
I can't speak to what the problem is, the syntax looked good when I looked at it, and then it in fact did run just fine on my ubuntu system.

~ Eric

---

### Post by papibe on 2011-11-10
Is that the whole script? I don't see a line 17, it seems 15 lines long.

Try removing empty lines after the end of the code. Also, it may be a binary character you type by mistake (and hidden from the editor). Use 'cat' with the option -v to check for non-printing characters:

```
cat -v yourscrtipt.sh
```
Hope it helps.
Regards.

---

### Post by MaxRabbit on 2011-11-10
> **papibe said:**
> Is that the whole script? I don't see a line 17, it seems 15 lines long.

Try removing empty lines after the end of the code. Also, it may be a binary character you type by mistake (and hidden from the editor). Use 'cat' with the option -v to check for non-printing characters:

```
cat -v yourscrtipt.sh
```
Hope it helps.
Regards.
Thanks papibe. I see a bunch of "^M" characters :confused:

---

### Post by ju2wheels on 2011-11-11
1. ^M characters means you probably wrote/edited it on a Windows machine and transferred it to a Linux machine, its a Windows endline. Run the file through the 'dos2unix' program. Alternatively, if you had opened the file in Windows and it shows up all on one line or has 'block' characters in it for endlines, run it through 'unix2dos' so it looks right on Windows.
2. Make a habit of adding a shebang as the first line of your scripts, so add '#!/bin/sh' or '#!/bin/bash' as the first line of your script.

---

### Post by MaxRabbit on 2011-11-11
Thanks guys :) Very helpful! And yes, I did begin writing the scripts on my Dropbox on a Windows machine, so that explains everything!

---


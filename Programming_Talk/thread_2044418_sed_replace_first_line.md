---
title: "sed replace first line"
date: 2012-08-19
forum: Programming Talk
---

### Post by MikeCyber on 2012-08-19
Hi
seems easy but couldn't figure it out.
I don't know the first line of a text file, but I want to replace it with a number.
Tried things alike:

#!/bin/sh
sed '1 c\232323232' xsd1.txt 

Many thanks
Michael

---

### Post by papibe on 2012-08-19
Hi MikeCyber.

Try this:
```
sed '1s/^.*$/232323232/'  xsd1.txt
```
Tell us how it goes.
Regards.

---

### Post by MikeCyber on 2012-08-19
Thanks, but it only outputs to term but doesn't write to the file:

michael@michael-ubuntu:~/Desktop$ ./Cust*
232323232
michael@michael-ubuntu:~/Desktop$

Also later I'd prefer to give the number as parameter:
./Cust* 4343434343

For another script even two params if possible.
Thanks

---

### Post by steeldriver on 2012-08-19
I think you *can* do it with the 'c' command (as you seem to be trying to do) - but the replacement 'text' needs to go on a separate line - and if you want to have a shell variable in there you will need to use double quotes instead of single quotes

```
#!/bin/bash

replace=$(($1*11 + $2))

sed "1c \
$replace
" *file* 
```

Add the -i  (interactive) flag if you want sed to write back to the original file

```
sed -i "1c \
$replace
" file 
```

---

### Post by Odexios on 2012-08-19
Try with

```
sed '1s/.*/123/' xsd1.txt > xsd1.txt.temp; mv xsd1.txt.temp xsd1.txt
```

EDITED: ```
sed -i '1s/.*/123/' xsd1.txt
```

Of course you can write a script, give it an argument and use it as the number.

EDIT: I hate this font.

It's `sed 'ONEs'

EDIT2: Didn't know of the -i option; thanks steeldriver, there's something new to learn every day.

Modified the command accordingly.

---

### Post by MikeCyber on 2012-08-20
Thanks, getting there:

#!/bin/sh
read -p "What is your name? " name; echo "Good day, $name.  Would you like some tea?"
sed -i '1s/.*/'$name'/' cs1.txt

---

### Post by Vaphell on 2012-08-20
what will happen when you type John Smith?
sed should blow up due to undefused space. Always have variables inside double quotes (unless you need that splitting on whitespace behavior)

---


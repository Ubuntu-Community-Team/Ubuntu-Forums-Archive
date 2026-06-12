---
title: "Find command and spaces in directories"
date: 2008-09-02
forum: Programming Talk
---

### Post by kaibob on 2008-09-02
I'm new to shell scripting and have encountered a situation I don't understand. I have created a directory, /home/kaibob/temp, and within that directory I have created the subdirectories, try 1 and try 2. 

When I run the following command in a terminal window:

```
i=$(find /home/kaibob/temp -type d) ; echo "$i" >> output
```

The output file contains the following:

> /home/kaibob/temp
/home/kaibob/temp/try 2
/home/kaibob/temp/try 1

However, when I run the following commmand in a terminal window:

```
for i in $(find /home/kaibob/temp -type d) ; do echo "$i" >> output ; done
```

The output file contains the following:

> /home/kaibob/temp
/home/kaibob/temp/try
2
/home/kaibob/temp/try
1

Due to the white space within the names of the two subdirectories, I have quoted the variable $i in both commands. Why doesn't the second command give the same output as the first command? Is there any way to get the second command to output the directories correctly?

Thanks for the help!

---

### Post by ghostdog74 on 2008-09-02
use a while read loop instead
```

find /path -type f -name "blah" | while read FILE
do
 echo "$FILE"
 #do something with FILE
done

```
for short commands, you can just use -exec option.

---

### Post by kaibob on 2008-09-02
Thanks ghostdog74. I was trying to get a script to work, and the while read loop did the trick.

---


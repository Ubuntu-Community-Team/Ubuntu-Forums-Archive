---
title: "Basic scripting question"
date: 2007-10-15
forum: Programming Talk
---

### Post by Visti on 2007-10-15
Hi guys,
I was helping a friend automate some tasks through bash scripting today, which I won't be getting into. However, it involved replacing on line of text with another, so I suggest:

Working from php.ini:

```
sed s/'line no.1 = 2'/line no. = 5'/ php.ini > php.ini
```

as I know that > replaces all text from the target with output

This, however, gives me a blank php.ini. If I do

```
sed s/'line no.1 = 2'/line no. = 5'/ php.ini > php.ini.new
```

I get the file and I guess I can just mv php.ini.new php.ini, but why is it that the first solution doesn't work?

---

### Post by scruff on 2007-10-15
Check out 'sed -i' for inline editing :)

---

### Post by bigboy_pdb on 2007-10-15
The first solution doesn't work because sed is reading from the file. When you use ">" to redirect output to a file it does two things. If the file exists it, it is made into an empty file, and it writes the output to the file.

sed fails because ">" makes the file empty and it cannot read from an empty file.

To avoid this problem use:
```

sed *commands* *file1* > *file2*; mv *file2* *file1*

```

where *commands* are your sed commands, *file1* is the file that you're reading from, and *file2* is a temporary file that you write output to.

**[EDIT]**
"*command1*; *command2*" executes *command2* regardless of whether or not *command1* fails (returned an exit status that indicated that an error occurred).
**[/EDIT]**

**[EDIT]**
I forgot to mention something else. You should have a backup of your original file and you should not move the new file to the old file until you've tested your sed commands and you know that they are working.
**[/EDIT]**

---

### Post by scruff on 2007-10-15
I forgot to mention the backup thing too. But really, just use the -i switch to avoid having to mess around and copy/move files. 

Should work like this:

sed -i s/'line no.1 = 2'/line no. = 5'/ php.ini

---


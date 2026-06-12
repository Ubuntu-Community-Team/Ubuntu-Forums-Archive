---
title: "[bash] Create menu from command output"
date: 2011-01-11
forum: Programming Talk
---

### Post by eentonig on 2011-01-11
Hi all,

Greenhorn question, but I'm tired looking for a solution.

I'm probably using the wrong search terms, but I'm looking for some code that allows me to dynamically generate a menu (case or select), based on the output of a command.

I'm pretty sure this has been done a thousand times before, so there must be some reusable code existing.

I can print the user text dynamically, but I can't figure out how to create my case statement.

I.e. Put output from `hamachi list` in a variable, print out the nickname to selct from and then ssh to the selected host.

---

### Post by sisco311 on 2011-01-11
Try something like:
```

cat -n list
read -p "Select:" line
echo "Selected line is: $(sed -n "${line}p" list)"

```

---


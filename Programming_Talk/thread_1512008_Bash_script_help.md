---
title: "Bash script help"
date: 2010-06-17
forum: Programming Talk
---

### Post by Yes on 2010-06-17
Since my ACPI handler.sh script isn't working like it should, I need to write my own.  What it needs to do is test whether `acpi -a` equals "Adapter 0: on-line" or "Adapter 0: off-line".  Here's what I've tried...

```

!#/bin/sh

power_source = `acpi -a`
if [$power_source = "Adapter 0: on-line"]
then
    echo "Using AC power"
else
    echo "Using battery"
fi
```

What it does, however, is print out "Using battery" even when acpi -a says the AC adapter is on-line.  So I assume it's a problem with my if statement, right?  What's wrong with it though, I haven't been able to figure out.

So, any help would be greatly appreciated.  Thanks!

---

### Post by hannaman on 2010-06-17
> **Yes said:**
> Since my ACPI handler.sh script isn't working like it should, I need to write my own.  What it needs to do is test whether `acpi -a` equals "Adapter 0: on-line" or "Adapter 0: off-line".  Here's what I've tried...

```

!#/bin/sh

power_source = `acpi -a`
if [$power_source = "Adapter 0: on-line"]
then
    echo "Using AC power"
else
    echo "Using battery"
fi
```

What it does, however, is print out "Using battery" even when acpi -a says the AC adapter is on-line.  So I assume it's a problem with my if statement, right?  What's wrong with it though, I haven't been able to figure out.

So, any help would be greatly appreciated.  Thanks!

$power_source is most likely empty, you shouldn't put spaces around the equal sign in variable assignment.

Also, using the $power_source variable like that in the test statement doesn't preserve spaces.  You should enclose the variable in double quotes.  And also put spaces around the brackets in the test statement.

---

### Post by Yes on 2010-06-17
Ah I hadn't realized whitespace was so important in bash.  Thank you!

---


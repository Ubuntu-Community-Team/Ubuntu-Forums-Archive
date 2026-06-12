---
title: "Simple shell programming problem"
date: 2011-03-06
forum: Programming Talk
---

### Post by TheStroj on 2011-03-06
Hi everyone!

Recently I got into awk and couldn't find out how to print something from one string to another.

I don't want to print the whole line, just the content between 2 strings.

Let's say that this is the line:
```
This is ubuntuforums.org and I'm posting a new thread.
```

I want to print everything between 'is' and 'new', including those 2 words. This is the output I want:
```
is ubuntuforums.org and I'm posting a new
```

Is it possible to do this with awk? If there are easier ways, make sure to tell me ;D I would be more than glad to see if anyone could do it easier way with some other tool, just make sure it's easy to understand for a Shell programming beginner like me.

Thanks in advance :)

---

### Post by Rinzwind on 2011-03-06
What is the condition for breaking it up like that?
(assuming you need it for something else?)

The command to use for this I assume seems to be
cut



echo "This is ubuntuforums.org and I'm posting a new thread." | cut -c6-46

results in...

is ubuntuforums.org and I'm posting a new


But it is rather useless it this is all it needs to do ;)

---

### Post by TheStroj on 2011-03-06
> **Rinzwind said:**
> What is the condition for breaking it up like that?
(assuming you need it for something else?)

The command to use for this I assume seems to be
cut



echo "This is ubuntuforums.org and I'm posting a new thread." | cut -c6-46

results in...

is ubuntuforums.org and I'm posting a new


But it is rather useless it this is all it needs to do ;)

This could be used but, lets say I don't know where in text there are words 'is' and 'new' and I want to print stuff between them.

I could use something like:
```
awk '/is/,/new/' ubuntu.txt
```

But that prints the whole line, not just the words between them. What I'm looking for is a simple way to tell a program to print the words between two strings. Example:
```
my_program "is" "new" "This is ubuntuforums.org and I'm posting a new thread."
``` 

And it would return "is ubuntuforums.org and I'm posting a new". It doesn't have to be as simple as that, just something of that kind.

---

### Post by TheStroj on 2011-03-06
For anyone that will ever be searching for something like this again, here is the solution. I used simple command **grep**.

```
grep is.*new < ubuntu.txt
```

(Ubuntu.txt keeps the text mentioned above.)

Thsi is by far the easiest solution I found. '.*' just tells the program to include everything between 'is' and 'new'.

I hope that anyone else finds this useful :)

---

### Post by ibuclaw on 2011-03-06
```
awk '/is/,/new/{print}' ubuntu.txt
```

Regards

---

### Post by TheStroj on 2011-03-06
> **ibuclaw said:**
> ```
awk '/is/,/new/{print}' ubuntu.txt
```

Regards

I already posted this solution above, but the problem is that this prints the whole line, not the part between 'is' and 'new'. Re-read the thread ;)

---

### Post by ibuclaw on 2011-03-06
> **TheStroj said:**
> I already posted this solution above, but the problem is that this prints the whole line, not the part between 'is' and 'new'. Re-read the thread ;)

Re-read, and grep would print the whole line too. ;)

My awk is not too good, I must admit. But looking at the manpage, came up with this:

```

#!/usr/bin/awk -f

BEGIN {
    line = "";
    i = 0;
    j = 0;
}

/is/,/new/ {
    line = $_;
    i = match(line, /\<is\>/);
    j = match(line, /\<new\>/ - 3); # 3 is length("new");
}

END {
    print substr(line, i, j);
}

```

---

### Post by TheStroj on 2011-03-06
> **ibuclaw said:**
> Re-read, and grep would print the whole line too. ;)

My awk is not too good, I must admit. But looking at the manpage, came up with this:

```

#!/usr/bin/awk -f

BEGIN {
    line = "";
    i = 0;
    j = 0;
}

/is/,/new/ {
    line = $_;
    i = match(line, /\<is\>/);
    j = match(line, /\<new\>/ - 3); # 3 is length("new");
}

END {
    print substr(line, i, j);
}

```

Why not try the grep command? ;) Just add -o for better result.
And thanks for the code, it seems hard, but I'll try to understand it.

---

### Post by kaibob on 2011-03-07
> **TheStroj said:**
> Why not try the grep command? ;) Just add -o for better result.
And thanks for the code, it seems hard, but I'll try to understand it.

I don't know much about grep, but you may also want to consider using the -w option, which restricts matches to whole words. Otherwise, in your original example, it appears that the "is" in "this" is found and returned.

---


---
title: "Problem With Arrays in Bash Scripts"
date: 2007-05-15
forum: Programming Talk
---

### Post by munkyeetr on 2007-05-15
I have seen other threads on this problem, but I didn't find any that posted solutions...

When I create a script and try to use an array like this:

```

#!/bin/bash

names=( Jennifer Tonya Anna Sadie )

for name in ${names[@]}
do
   echo $name
done

```

I get this error: **Syntax error: "(" unexpected**

Pretty much everywhere I look regarding arrays, tells me to create them like I did in the code above.

Some of the other posts asked people to run commands and study the output (again, with no resolution posted), so I will post those here in hopes that someone can help me get to the root of the problem.

```

jon@papa-penguin:~/Desktop$ ls -l /bin/*sh
-rwxr-xr-x 1 root root 676836 2006-09-19 15:24 /bin/bash
-rwxr-xr-x 1 root root  79912 2006-07-11 12:31 /bin/dash
lrwxrwxrwx 1 root root      4 2007-05-13 09:13 /bin/rbash -> bash
lrwxrwxrwx 1 root root      4 2007-05-13 09:13 /bin/sh -> dash

```

And this is the contents of my /etc/shells file:
```

# /etc/shells: valid login shells
/bin/sh
/bin/bash

```

Any help would be appreciated. Thanks.

---

### Post by Quikee on 2007-05-15
I did my own example and "a=( a b c )" works for me.. however "a= ( a b c )" gives me an error you get. Try to execute with "bash <script name>" if in doubt which shell is used.

---

### Post by lloyd_b on 2007-05-15
With this script (on my system, named "test"):
```
#!/bin/bash

names=( Jennifer Tonya Anna Sadie )

for name in ${names[@]}
do
   echo $name
done
```
I get this result:
```
lloyd@laptop:~/stuff$ ./test
Jennifer
Tonya
Anna
Sadie
```

So I can't replicate the problem on my machine.

One possibility:  Could you cut and paste the exact error message you're getting?  One possible explanation would be if you had a space character in between the equal sign and the open parenthesis, in which case you'd get the following:
```
lloyd@laptop:~/stuff$ ./test
./test: line 3: syntax error near unexpected token `('
./test: line 3: `names= ( Jennifer Tonya Anna Sadie )'
lloyd@laptop:~/stuff$ 
```

Could you include info on which Ubuntu version you're running? 

Lloyd B.

---

### Post by munkyeetr on 2007-05-15
okay, it now works when I run it using:

```

bash <scriptname>

```

...which makes sense (now) because my link to **sh** points to the **dash shell**.

thank you everyone...

One more question:

Since I never use the dash shell, it should be safe to redirect my sh link to /bin/bash, yes or no?

---

### Post by lloyd_b on 2007-05-15
.> ..which makes sense (now) because my link to sh points to the dash shell.

thank you everyone...

One more question:

Since I never use the dash shell, it should be safe to redirect my sh link to /bin/bash, yes or no?

I would recommend against it.  Just because you don't use it directly doesn't mean that there aren't any shell scripts on your system that rely on "/bin/sh" to behave like dash rather than bash. 

This is an interesting problem, so I did a little experimentation:

From a "bash" shell (which is my default), the script works correctly if invoked as "./test", or "bash ./test", but fails if invoked as "sh ./test" or "dash ./test"

From the "dash" shell, the script STILL works correctly if invoked as "./test" or "bash ./test", and fails if invoked as "sh ./test" or "dash ./test"

From either shell, it works correctly if I invoke it as "sh -c ./test" or "dash -c ./test".

So the issue is that running a shell script as "sh {script}" or "dash {script}" bypasses the "#!/bin/bash" line, thus causing it to fail.  But it can be invoked as "sh -c {script}" or "dash -c {script}", and the "#!/bin/bash" *is* correctly handled to invoke the bash shell.

In this case, running "sh -c ./test" is downright silly - it runs a copy of sh, which then turns around and runs a copy of "bash".  Simpler to just run "./test", which works correctly regardless of your default shell, and only invokes an extra copy of "bash" if one is required.

Lloyd B.

---

### Post by munkyeetr on 2007-05-15
Thank you for the time spent experimenting, and the advice.
I will try running the script as you did when I get home from work, and see if I get the same results.

Thanks again.

---


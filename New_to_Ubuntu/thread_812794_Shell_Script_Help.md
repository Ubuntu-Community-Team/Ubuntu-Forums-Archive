---
title: "Shell Script Help"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-05-30
I am currently writing a shell script and I need some help. I need to export a variable and then have another terminal read it. I have tried the export command but that will only work in the same terminal. I am new to writing in shell script can somebody help?

---

### Post by Joeb454 on 2008-05-30
You could output it to a hidden file and have the other terminal read that file?

```
echo variable >  ~/.var
```

And in the other terminal you would read that file :)

---

### Post by Promaster91 on 2008-05-30
How would I read that variable in? (Sorry I am new to Shell Script)

---

### Post by SupaSonic on 2008-05-30
Or you can launch your script like this 
```
. script
```
instead of this 
```
./script
```

Then the variable from the first script will be exported in your current bash session, and the second script will have it set.

EDIT: I realised that you might have a different problem

---

### Post by Cypher on 2008-05-30
Joeb's method is the "right" way of transferring data from one script to another. You would follow the syntax of:
```

<variable>=<value>

```
when generating the file and then in the second script, you can use
```

if [ -f <file> ]; then
   . <file>
fi

```
Now all the variables are part of the second programs context..

---

### Post by Joeb454 on 2008-05-30
> **Promaster91 said:**
> How would I read that variable in? (Sorry I am new to Shell Script)

You would assign your variable with ```
variable = `cat ~/.var`
```

Obviously you can use different filenames and variable names ;)

---


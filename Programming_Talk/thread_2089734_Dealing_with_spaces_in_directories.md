---
title: "Dealing with spaces in directories"
date: 2012-11-30
forum: Programming Talk
---

### Post by alkal0id on 2012-11-30
Questions like this have been asked a million times but I'm having trouble finding a generic solution that I can use.  Heres a simple script I'm playing around with which is supposed to tell me about a file (i.e. if it exists or not). 

```

filedir='new test dir1'
filename='file.pdf'

file="$filedir/$filename"


if [ -f $file ];
then
   echo "File $file exists."
else
   echo "File $file does not exist."
fi

```Heres the output it gives me:
> test.sh: line 12: [: too many arguments
File new test dir1/file.pdf does not exist.
If I remove the spaces in the directory, it works fine. How do you deal with spaces in directory names? I tried adding backslashes before the spaces but that didn't work.

---

### Post by spjackson on 2012-11-30
Simply
```

if [ -f "$file" ];

```

---

### Post by alkal0id on 2012-11-30
Thanks a lot. I have to learn about quotes in bash. In PHP, "" quotes will process variables, \n and other special commands, while the '' quotes just interpret the string literally without taking any notice of characters like $ etc. I've yet to get my head around how bash uses quotes.

---

### Post by Vaphell on 2012-11-30
it's simple
" " keep things in 1 piece, but allows for expansion of $var
' ' is in one piece too but is as literal as it gets - $var stays $var

if you want to test for file existence you can use this neat construct
```
[ -f "$file" ] && echo "file exists" || echo "file doesn't exist"
```
it follows rules of boolean logic, success = TRUE and goes to && part, failure = FALSE, skips && and goes straight to || part
i don't recommend using it for anything more complicated though.

---

### Post by SeijiSensei on 2012-11-30
> **alkal0id said:**
> Thanks a lot. I have to learn about quotes in bash. In PHP, "" quotes will process variables, \n and other special commands, while the '' quotes just interpret the string literally without taking any notice of characters like $ etc. I've yet to get my head around how bash uses quotes.

Exactly the same way.  Single-quotes mean to treat a string literally; double-quotes mean replace any variables with their values and display the result.

---

### Post by for.i.am.root on 2012-11-30
You could expand on that to include:

```
[ -f $1 ] && echo "file exists" && exit 0 || echo "$0 error: file does not exist" && exit 1
```

Then run:

```
myscript /test/directory/sample_file
```

If you wanted to "separate" the directory and file you could use:

```

if [ -d $1 ] then
#directory exists, check for file
   if [ -f $2 ] then
      echo "file $2 exists in directory $1" && exit 0
   else
      echo "$0 error: file does not exist" && exit 1
   fi
else
echo "$0 error: directory does not exist" && exit 1
fi

```

The above would be run as:
```
myscript /some/random/directory some\ random\ file
```

Be careful with above code. At work on a dozer box and can't test for grammatical mistakes.

---


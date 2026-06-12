---
title: "Parse a text file and replace text"
date: 2008-12-07
forum: Programming Talk
---

### Post by arsenik on 2008-12-07
I want to parse a C file and replace the following example line:

function(x(a,**b**,c),**y**,x(d,**e**,f))

with:

function(**b**,**y**,**e**)

I have a regular expression as:

x\([^,],[^,],[^\)]) to parse the needed variables

How would I go about doing this in a bash shell script?

---

### Post by snova on 2008-12-07
Look into sed. I don't know exactly how.

Alternatively, why not use a language with regexp features built in, such as Perl?

Also, why?

---

### Post by arsenik on 2008-12-07
I stated what I needed in the first message.  I am a programmer, its for a C program I created.  I could use perl, sed, or awk.  That's why I'm here asking for help :)

---

### Post by geirha on 2008-12-07
Once you've found the proper replacement regex ...
```

$ echo 'function(x(a,b,c),y,x(d,e,f))' | sed -r 's/\<function\(\w+\(\w+,(\w+),\w+\),(\w+),\w+\(\w+,(\w+),\w+\)\)/function(\1,\2,\3)/'
function(b,y,e)

```

Run it on the file
```

sed -r 's/\<function\(\w+\(\w+,(\w+),\w+\),(\w+),\w+\(\w+,(\w+),\w+\)\)/function(\1,\2,\3)/' file.c  > newfile.c
# Alternatively add the -i option to make the replacement in place
sed -r -i~ 's/\<function\(\w+\(\w+,(\w+),\w+\),(\w+),\w+\(\w+,(\w+),\w+\)\)/function(\1,\2,\3)/' file.c

```

---

### Post by arsenik on 2008-12-07
Thanks I appreciate the help.  I understand everything  but the \w+ 's . What do they represent in regex?

---

### Post by ghostdog74 on 2008-12-07
no need regexp to complicate things, just use fields/delimiters
```

# echo "function(x(a,b,c),y,x(d,e,f))" |awk -F"," '{print "function("$2","$4","$6")"}'
function(b,y,e)


```

---

### Post by geirha on 2008-12-07
\w+ should be equivalent to [a-zA-Z0-9_]+ or something close to that. I never quite remember what exactly it matches, but in the case of source code, it should match functions and variable names nicely.

---


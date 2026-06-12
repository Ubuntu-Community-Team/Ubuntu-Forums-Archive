---
title: "RE help, matching strings ending with &quot;;&quot;"
date: 2009-06-15
forum: Programming Talk
---

### Post by matmatmat on 2009-06-15
I'm using python & i am trying to match ";" in a line:
```

for page in css:
        f = open(page, "r")
        lines = f.readlines()
        count = 1
        obcount = 0
        ebcount = 0
	probwithfile = False
        for line in lines:
		[B]if not re.match("^{$", line) or not re.match("^}$", line):
		        if not re.match(".*?;", line):
                                print "hi"[/B]


``` 
it prints out "hi" for every line

---

### Post by iponeverything on 2009-06-15
escape the ;

like so:```
 \;
```

---

### Post by matmatmat on 2009-06-15
Thanks, it is now this:
```

if not re.match(".*?\;.*", line):
    print "hi"

```
but that still doesn't work

---

### Post by myle on 2009-06-15
What about:

```

line.endswith(';')

```

---

### Post by Can+~ on 2009-06-15
Why are you trying to parse CSS?

---

### Post by ghostdog74 on 2009-06-15
if you want to match anywhere in the line, use "in" operator
```

if ";" in line:

```
if want to match at the end, use endswith(), at the start, use startwith()
No need to use regular expression for such a simple task

---

### Post by matmatmat on 2009-06-16
I've tried
both
```

if not line.endswith(";"):
    print "hi"

**and**

if not ";" in line:
    print "hi"

```
both don't work,
i am wanting to match things like:
```

    blahblahblah:#colourblahblah**;**

```

---

### Post by monraaf on 2009-06-16
maybe use line.strip().endswith(';')

---

### Post by matmatmat on 2009-06-16
Thanks, it worked

---

### Post by matmatmat on 2009-06-16
Sorry, no it doesn't!
I'm not back to where I started:
```
for page in css:
        f = open(page, "r")
        lines = f.readlines()
        count = 1
        obcount = 0
        ebcount = 0
        scount = 0
	probwithfile = False
        for line in lines:
                for match in re.finditer("}", line):
                        ebcount += 1
                for match in re.finditer("{", line):
                        obcount += 1    
                        if not re.match("[\.a-zA-Z0-9=#:\s_,]*\}.*", line):
                                if not re.match("[a-zA-Z0-9_=#:\s\.,]*\{.*",line):
                                        print "hi"
                                        if not line.strip().endswith(";"):
                                                print "#################### CSS Error ###################"
                                                print "Line does not end with ';' in file %s on line %i" % (page, count)
                                                print line
                                                scount += 1
                                                probwithfile = True

```

it doesn't print "hi"

---

### Post by Bodsda on 2009-06-16
You have an indentation error 'probwithfile = False' and also I think you are overcomplicating this, as others have said if you want to match the end of a string use ```
if string.endswith(var):
```

You are doing a lot of stuff before you even get anywhere near a print statement, try and add some print statements at each stage to see what exactly is going on.

Also, you might think about posting the rest of the code if your still having issues.

Regards,

Bodsda

---

### Post by matmatmat on 2009-06-16
i got it working

---


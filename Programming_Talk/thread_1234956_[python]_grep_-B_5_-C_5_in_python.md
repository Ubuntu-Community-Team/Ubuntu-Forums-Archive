---
title: "[python] grep -B 5 -C 5 in python"
date: 2009-08-08
forum: Programming Talk
---

### Post by starcraft2fan on 2009-08-08
```
for filename in os.listdir("."):
    for line in open(filename).xreadlines():
        if "foo" in line:
            print line
```

So this is a simple python equivalent of `cat filename | grep foo`. However, I would like the equivalent of `cat filename | grep -B 5 -C 5 foo`, how should the above code be modified?

---

### Post by unutbu on 2009-08-08
Well, one way to do it would be to loop through the file twice.
The first time, you search for "foo" and just save the line numbers where foo occurs:
[PHP]
matched_lines=[]
for line_number,line in enumerate(open(filename)):
    if "foo" in line:
        matched_lines.append(line_number)[/PHP]

Then you prepare a set of all the lines you actually want to print:
[PHP]
print_lines=set()
for line_number in matched_lines:
    for num in range(line_number-5,line_number+6):
        print_lines.add(num)[/PHP]

Then you loop through the file a second time, and print all lines whose line number is in the set print_lines:
[PHP]
for line_number,line in enumerate(open(filename)):
    if line_number in print_lines:
        print line
[/PHP]

---

### Post by slavik on 2009-08-08
why not have a list of lines as you are scrolling through the file?

an example perl code, please note that there are problems with it if the line you look for is within the last 5 lines or the first 5 lines and you read less than 11 lines.

```

# assume -A5 -B5 (Before, After)
$a = 5;
$b = 5;
$pattern = "some line";
$total = $a + $b + 1;
@lines = ();
while ($line = <STDIN>) {
  push $line, @lines;
  shift @lines if ($#lines + 1 > 11);
  print join "", @lines if ($lines[int($total / 2)] =~ /$patter/)
}

```

basically, keep a list as you are reading lines, if the line in the middle matches, then print what you have in the buffer.

of course, the code above needs to be fixed.

---

### Post by ghostdog74 on 2009-08-08
```

#!/usr/bin/env python
context=2
buffer = ["" for i in range(context)]
def append(data, x):
    '''ring buffer'''
    data.pop(0)
    data.append(x)
    return data

f=open("file")
for line in f:
    line=line.strip()
    if "match" in line:
        print '\n'.join(buffer)
        print line
        for i in range(context):
            try:
                line=f.next().strip()
            except: pass
            else:
                print line
                append(buffer,line)
    else:
        append(buffer,line)

```

output
```

# more file
line 1
line 2
line 3
line 4
match
match
line 5
line 6
line 7
line 8
line 9
# ./python.py
line 3
line 4
match
match
line 5


```

---

### Post by unutbu on 2009-08-08
I like your solution ghostdog74.

Here is a slightly modified version which checks if there is a match during the "after-context", and resets the counter when there is a match so the correct number of "after-lines" are printed:

[PHP]#!/usr/bin/env python
before=2
after=3
buffer = []
def append(size, data, x):
    '''ring buffer'''
    if len(data)>=size:
        data.pop(0)
    data.append(x)

f=open("a")
for line in f:
    line=line.strip()
    if "match" in line:
        if buffer:
            print '\n'.join(buffer)
        buffer=[]
        print line
        after_count=0
        while after_count<after:
            after_count+=1
            try:
                line=f.next().strip()
            except: pass
            else:
                print line
                if "match" in line:
                    after_count=0
    else:
        append(before,buffer,line)
[/PHP]

---


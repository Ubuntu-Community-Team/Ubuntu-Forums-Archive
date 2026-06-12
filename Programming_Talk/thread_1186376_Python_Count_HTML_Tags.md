---
title: "Python Count HTML Tags"
date: 2009-06-13
forum: Programming Talk
---

### Post by matmatmat on 2009-06-13
How would you count how many opening HTML tags there were & then closing tags in a line?
eg
```

for line in something:
    for match in re.match("*opening_regex_here*",line):
        count += 1
    for match in re.match("*closing_regex_here*",line):
        count2 += 1    

```

---

### Post by Bodsda on 2009-06-13
> **matmatmat said:**
> How would you count how many opening HTML tags there were & then closing tags in a line?
eg
```

for line in something:
    for match in re.match("*opening_regex_here*",line):
        count += 1
    for match in re.match("*closing_regex_here*",line):
        count2 += 1    

```

Just tried this out in an interpreter, dunno if its exactly what you want but here goes, this is how I would do it.

[php]
line = "<your><line><with><html><tags>"
tag_o = line.split(">")
tag_c = line.split("<")
print "%s Opening tags, %s Closing tags.\n" % ((len(tag_o) - 1 ), (len(tag_c) - 1 ) 
[/php]

For me, when i tried the list returned by the split contained 1 "", hence the -1.

Hope this helps, Regards,

Bodsda

---

### Post by benj1 on 2009-06-13
openning tag <[A-Za-z0-9=".? -]*>
closing tag </[A-Za-z0-9=".? -]*>

be careful if youre using re.match() i think that only matches the start of the line, you might be better with re.findall()

---

### Post by ghostdog74 on 2009-06-13
i think (if i am not wrong) OP wants to count matching tags....

---


---
title: "python file help"
date: 2007-07-29
forum: Programming Talk
---

### Post by crashovaride on 2007-07-29
I need some help from anyone who is familiar with python. I have a file i'm looking to read, and what i want to do is add .com, .edu, etc web extensions. This is what i have...

data_file = open('/root/Desktop/social.log', 'rb')
for line  in data_file:
	put = line
	put += ".com"
	print put
data_file.close()

but, every time i attempt to read, or write a new file, it enters the information as:

websitename
.com
.edu

Anyone have any solutions? I'm pulling my hair out and these stupid books don't help at all!!!

---

### Post by scooper on 2007-07-29
I'm assuming your indentation got messed up in the paste, so presumably all the "put" stuff is in the loop.  When you read from a text file the lines end in a line feed.  You can strip it using <string>.rstrip(), e.g.

```

data_file = open('/root/Desktop/social.log', 'rb')
for line in data_file:
    put = line.rstrip()
    put += ".com"
    print put
data_file.close()

```

HTH
Steve

---

### Post by pmasiar on 2007-07-29
... or even shorter:
```

for line in open('/root/Desktop/social.log'):
    print line.rstrip() + ".com"

```

---

### Post by crashovaride on 2007-07-29
Thanks for your help bro, it worked. I really appreciate it.

---


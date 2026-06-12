---
title: "Is appending files is SAFE ?"
date: 2010-01-15
forum: Programming Talk
---

### Post by baskar007 on 2010-01-15
Hi friends i have a small python scrip that will download a file in 5 parts, and  append all files to a single file.

this codes are used to appending files.
[PHP]
partlist = ["part1",part2,part3]   #part file paths
source = "Sourcefile.ext"          #Source file 
FF = open(source,"a")
for x in partlist:
    F = open(x,"r")
    data = F.read()
    FF.write(data)
    F.close()
FF.close()
[/PHP]

is appending two or more files is safe?

---

### Post by Zugzwang on 2010-01-15
What precisely do you mean by "safe"?

---

### Post by nvteighen on 2010-01-15
> **baskar007 said:**
> Hi friends i have a small python scrip that will download a file in 5 parts, and  append all files to a single file.

this codes are used to appending files.
[PHP]
partlist = ["part1",part2,part3]   #part file paths
source = "Sourcefile.ext"          #Source file 
FF = open(source,"a")
for x in partlist:
    F = open(x,"r")
    data = F.read()
    FF.write(data)
    F.close()
FF.close()
[/PHP]

is appending two or more files is safe?

If you mean safe in the sense of not losing data, it is as long as you don't do stupid things like moving the write cursor to the beginning and then write, e.g.

All these procedures are part of the Python core... Do you think Python would be so succesful if something as basic as opening a file in appending mode would fail? :p

---

### Post by lavinog on 2010-01-15
Are these text or binary files?

---

### Post by baskar007 on 2010-01-15
> **Zugzwang said:**
> What precisely do you mean by "safe"?
I mean losing datas

---

### Post by baskar007 on 2010-01-15
> **lavinog said:**
> Are these text or binary files?
yeah all are binary files. like images,debs, videos  (these code i auctually used in downloader application).

---

### Post by lostinxlation on 2010-01-17
Deleted...

---

### Post by c0mput3r_n3rD on 2010-01-17
Why not? appending is meant to put pieces of data together one after another on the next line.

---

### Post by phrostbyte on 2010-01-17
It is as safe as it can be.

---

### Post by baskar007 on 2010-01-18
> **phrostbyte said:**
> It is as safe as it can be.
Yeah ,Its safe there is no chance for corrupt. thanks for all who replyed.

---

### Post by phrostbyte on 2010-01-18
> **baskar007 said:**
> Yeah ,Its safe there is no chance for corrupt. thanks for all who replyed.

There is always a chance for corruption, with any filesystem. :( Blame quantum mechanics.

---

### Post by lavinog on 2010-01-18
> **phrostbyte said:**
> There is always a chance for corruption, with any filesystem. :( Blame quantum mechanics.

Classical physics is good for corruption too.

---

### Post by c0mput3r_n3rD on 2010-01-18
> **baskar007 said:**
> Hi friends i have a small python scrip that will download a file in 5 parts, and  append all files to a single file.

this codes are used to appending files.
[PHP]
partlist = ["part1",part2,part3]   #part file paths
source = "Sourcefile.ext"          #Source file 
FF = open(source,"a")
for x in partlist:
    F = open(x,"r")
    data = F.read()
    FF.write(data)
    F.close()
FF.close()
[/PHP]is appending two or more files is safe?

Easier way to open a file and appending data is just by simply writing
```

file = open("file_to_open.txt", "a")

```

---


---
title: "Editing group of files with sed"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by 1ns1d3r on 2016-01-12
Hello,

I want to know how edit group of files with sed command.

For example: I have several txt files and these files contain word "Windows", I want to replace this word by "Ubuntu".

So, main problem, I don't know how to save changes. If I write 

sed -e 's/Windows/Ubuntu/g' *.txt

then changed files display in shell but don't save. For one file there is a trick with creating temporary file and then renaming, but what do with several files?

---

### Post by steeldriver on 2016-01-12
You can use the -i (or --in-place) option

From man sed 

```

       -i[SUFFIX], --in-place[=SUFFIX]

              edit files in place (makes backup if SUFFIX supplied)


```

So for example

```

sed -i.bak -e 's/Windows/Ubuntu/g' *.txt

```

(The -e is optional, since you're only giving a single command)

Note there is also a -s option to treat each file as separate, but GNU sed applies this implicitly when you use -i

---

### Post by 1ns1d3r on 2016-01-12
Does option -i sometimes not exist on OS?

---

### Post by nerdtron on 2016-01-12
You can check on the man page of sed if the option -i exists. I'm pretty sure it exists on Ubuntu and Red Hat servers.

Another way to save your sed -e is to use redirection, > , to save your output to another file. Since you have multiple files, just run it on a loop. Also you don't need -e option for simple replacement like this.
Example:
```
 
## single files:
sed 's/Windows/Ubuntu/g' file1.txt > file1.txt.new

## several files, loop:
for i in *txt; do sed 's/Windows/Ubuntu/g' $i > $i.new ; done 
```

---


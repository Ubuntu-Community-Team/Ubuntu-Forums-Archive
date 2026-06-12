---
title: "Shell: remove all lines containing specified pattern from all files in a folder"
date: 2015-12-04
forum: Programming Talk
---

### Post by erotavlas on 2015-12-04
Hi,
I would like to remove all lines containing a specified pattern from all files in a folder. I know that the command 
```

grep -v "patternr" ./file > temp && mv temp file

```
does the first part i.e. removes all lines containing a specified pattern from a specific file. How can I achieve this for all files in a folder?
I tried something like this but it does not work.
```

grep -Rv "pattern" ./folder > temp && mv temp file

```
Do I need necessarily iterate over the files of the folder or there is a more simple way?
Thank you

---

### Post by Vaphell on 2015-12-04
what's wrong with loops?

```
shopt -s globstar
sed -r -i '/pattern/d' ./folder/**/*
```

globstar for recursiveness, if the files are directly under folder then folder/* would cut it

without globstar 

```
find ./folder -type f -exec sed -r -i /pattern/d +
```

---

### Post by erotavlas on 2015-12-04
The second solution does not work
```

find ./folder -type f -exec sed -r -i /pattern/d +
find: missing argument to `-exec'

```
I also tried to remove + and put ; without difference.

---

### Post by Vaphell on 2015-12-04
a case of brainfart

```
find ./folder -type f -exec sed -r -i '/pattern/d' {} +
```

---

### Post by erotavlas on 2015-12-04
Ok thank you

---

### Post by erotavlas on 2015-12-04
I'm sorry, but I have one more question. Now I would like to replace a string with another in each file inside a folder.
```

find ./folder -type f -exec sed -i 's/Hobbies</span></a> |/Hobbies</span></a>/g' {} +

```
I make some mistake, or have I to escape some character?
```

sed: -e expression #1, char 19: unknown option to `s'

```
Thank you

---

### Post by Lars Noodén on 2015-12-04
> **erotavlas said:**
> ```

find ./folder -type f -exec sed -i 's/Hobbies</span></a> |/Hobbies</span></a>/g' {} +

```

The slash ( / ) is a the delimiter so you can't use it in any other way without escaping it.  

```

find ./folder -type f -exec sed -i 's/Hobbies<\/span><\/a> |/Hobbies<\/span><\/a>/g' {} +

```

Alternately, you can use different delimiters like a pound sign ( # ).

```

find ./folder -type f -exec sed -i 's#Hobbies</span></a> |#Hobbies</span></a>#g' {} +

```

---


---
title: "find command"
date: 2012-01-13
forum: Programming Talk
---

### Post by achuthpnr on 2012-01-13
how to remove the ./ prefixing the name of the file found. 
```
find . -type f -name "*.bin"  -exec echo ./abc {}  \;
```this prints 
./abc ./file1.bin
./abc ./file20.bin etc..

I dont need the ./ before the file names if i am removing the echo to run "abc" on the found files.

---

### Post by CoffeeRain on 2012-01-13
This pipes the output into awk and takes away the first two characters

```

find . -type f -name "*.bin"  -exec echo {} \; | awk '{print substr($0,3)}'

```

---

### Post by achuthpnr on 2012-01-13
Thanks. This is informative, but still the problem persists. 

The problem here is to remove the ./ prefix in the file names so that the "abc" can process them. Adding the awk part removes the ./ for "abc" but keeps that of the file name.

I think I need to look in to awk now to find a solution.

---

### Post by bryanl on 2012-01-13
try the printf option
```
find . -mtime -300 -size +1G -printf "\"%f\",\"%h\",%s,\"%t\"\n" > files300days-or-newer.csv

```
this example provides a list of big files of recent vintage in a form I can pick up to play with in a spreadsheet. The "%h" printf option is the leading directories including the "./".

see man find for more on the possibilities.

As for feeding another utility, I'll often make a list with find and then use an editor to create a command list. For occasional needs, that gives me a bit more leeway if I make a mess of something.

---

### Post by CoffeeRain on 2012-01-13
You could pipe the output of awk into your command.

---

### Post by Arndt on 2012-01-13
> **achuthpnr said:**
> Thanks. This is informative, but still the problem persists. 

The problem here is to remove the ./ prefix in the file names so that the "abc" can process them. Adding the awk part removes the ./ for "abc" but keeps that of the file name.

I think I need to look in to awk now to find a solution.

Why do you need to remove the ./ prefix?

---

### Post by ofnuts on 2012-01-14
> **Arndt said:**
> Why do you need to remove the ./ prefix?
I was going to ask... :)  true Linux command usually do the right thing with the paths. The problem lies in your abc command that doesn't support full paths... that's the one I would either fix if I have the source or wrap in a script so that it behaves properly when given a full path. Actually "find" as you use it can return files in subdirectories...How will abc handle them?

---

### Post by Drenriza on 2012-01-14
just use cut, to cut away the first two characters.

---

### Post by Telengard C64 on 2012-01-14
```

#! /bin/bash

find . -type f -name "*.bin" -print |
while read -r f; do
    ./abc "${f:2}"
done

```

---

### Post by achuthpnr on 2012-01-18
abc is a simple c program, which takes up the bin file and process it. It is taking in the filename using argv[]. And as you told, it is not working correctly with full path. How can this problem be solved?

```

struct index {double x,y,z};
struct index *lastindex;

unsigned long int L,N0;
char *lastindexfile;
FILE *fp;

int main(int argc, char *argv[])
{  
    lastindexfile=argv[1];
    N0=(unsigned long int)atol(argv[2]);

    lastindex=(struct index *)calloc(N0,sizeof(struct index));
    
    fp=fopen(lastindexfile,"r");
    fread(lastindex,sizeof(struct index),N0,fp);
    fclose(fp);
   
    // rest  of the program

}


```

---

### Post by achuthpnr on 2012-01-18
> **Telengard C64 said:**
> ```

#! /bin/bash

find . -type f -name "*.bin" -print |
while read -r f; do
    ./abc "${f:2}"
done

```

Thanks. This solved the problem

---

### Post by Telengard C64 on 2012-01-18
> **achuthpnr said:**
> Thanks. This solved the problem

No it didn't. It is just a kludge until you fix your program.

---


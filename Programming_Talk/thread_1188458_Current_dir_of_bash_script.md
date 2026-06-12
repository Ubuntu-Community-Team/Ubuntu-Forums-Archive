---
title: "Current dir of bash script?"
date: 2009-06-15
forum: Programming Talk
---

### Post by afowler on 2009-06-15
Hello,


I would like to make a simple "upload" script to rsync some html files to a server for testing, etc. 

How do determine the full path current directory of the actual bash script so I can construct an rsync command that will work matter where the upload script is called from?


Thank you

---

### Post by kaibob on 2009-06-15
> **afowler said:**
> How do determine the full path current directory of the actual bash script so I can construct an rsync command that will work matter where the upload script is called from?

I don't completely understand your request, but the following will return the path of a shell script:

```
$(dirname $0)
```

or

```
${0%/*}
```

Are you looking for something else?

---

### Post by C-- on 2009-06-15
Add the path to your PATH environment variable.

---

### Post by soltanis on 2009-06-15
using the pwd command

---

### Post by afowler on 2009-06-16
> **kaibob said:**
> I don't completely understand your request, but the following will return the path of a shell script:

```
$(dirname $0)
```

or

```
${0%/*}
```

Are you looking for something else?


I think this works.  Sort of, I was wanting a full path...  but i guess this works too.

The script will upload some files that are in a subdirectory next to it via rsync.

I wanted the path to the script so I could generate a path to the files i wanted to upload.

---

### Post by Reiger on 2009-06-16
Then you'd use, as mentioned, $PWD or MY_DIR=$(pwd)

---

### Post by afowler on 2009-06-24
> **Reiger said:**
> Then you'd use, as mentioned, $PWD or MY_DIR=$(pwd)

assuming ~/scripts/path.sh

```
echo $(dirname $0)
echo $PWD

```

gives me:

```
./scripts
/home/username
```


I would like:

```
/home/username/scripts
```


I can not just concatenate them, as that would give: "/home/username./scripts".... not a valid path.  

Is there a safe way to join the values of $PWD and $(dirname $0) as a path?

---

### Post by kaibob on 2009-06-24
Post deleted by Kaibob

---


---
title: "Bash: Why are these two variables treated differently?"
date: 2011-06-28
forum: Programming Talk
---

### Post by jhonan on 2011-06-28
I'm reading a value from a text file into an environment variable, like this;

```
export CURRENT_Q=( $(< "current_q.txt") )
```Now, if I echo this, it looks right. But, there's a separate process I'm kicking off (an internal application) that tries to use this variable, and fails.

However, if I do this;

```
tmp_CURRENT_Q=( $(< "current_q.txt") )
export CURRENT_Q=$tmp_CURRENT_Q
```It works.

Does it have something to do with when the variable expression is parsed? - i.e. in my second example, the CURRENT_Q contains the 'real' value of the variable. In the first example, the file hasn't been read yet?

Slightly confused here.

---

### Post by geirha on 2011-06-28
You can't export array variables. I'm not exactly sure how bash handles **export var=( something )**, but it's pointless anyway, so don't do it. What are you actually trying to do?

For reading the content of a file into a variable or array, do
```

var=$(<"$filename")         # Entire content is stored as one long string
mapfile -t arr <"$filename" # Content stored in the array named arr, with one line per element.

```

---

### Post by jhonan on 2011-06-28
> **geirha said:**
> You can't export array variables. I'm not exactly sure how bash handles **export var=( something )**, but it's pointless anyway, so don't do it. What are you actually trying to do?
The file contains one line, a single numeric value, it's an indicator we use to identify the current financial period (e.g. 23) So it won't be read as an array, only as a single value.

From reading your suggestion, I think my problem is the use of the additional parenthesis. i.e. I'm doing var=($(<"$filename")) instead of var=$(<"$filename")

I'll try that instead. Thanks for the reply.

---

### Post by geirha on 2011-06-28
Right, then **var=$(<"$filename")** will do, though since it's just one line, you can also use read. Using read is more efficient, and I also find that "prettier".
```
read -r var < "$filename"
```

---

### Post by jhonan on 2011-06-29
> **geirha said:**
> Right, then **var=$(<"$filename")** will do, though since it's just one line, you can also use read. Using read is more efficient, and I also find that "prettier".
```
read -r var < "$filename"
```
Yup, tested **var=$(<"$filename")** and it works, thanks!

In bash, I'm always getting caught out by parentheses and quotes.

---


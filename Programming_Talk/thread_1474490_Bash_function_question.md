---
title: "Bash function question"
date: 2010-05-06
forum: Programming Talk
---

### Post by dragos2 on 2010-05-06
In the code below I want to pass some lines of text to the function to be written.
I encountered 2 problems:

1) Only "a" gets written
2) How can I write $1 to file directly in the function? Why not $1 > file ?

```

function writetofile {
 if  test ! -z "$1"
 then
    echo "$1" > file.txt # why $1 > file.txt does not work ?
 fi
}

var="a b"
writetofile $var

```

---

### Post by mobilediesel on 2010-05-06
> **dragos2 said:**
> In the code below I want to pass some lines of text to the function to be written.
I encountered 2 problems:

1) Only "a" gets written
2) How can I write $1 to file directly in the function? Why not $1 > file ?



Bash separates things into words by tabs, spaces and newlines. You can use "$@" instead of "$1" in the function and it will use the whole thing regardless of space.
```

function writetofile {
 if  test ! -z "$@"
 then
    echo "$@" > file.txt
 fi
}

var="a b"
writetofile $var

```

---

### Post by dragos2 on 2010-05-06
> **mobilediesel said:**
> Bash separates things into words by tabs, spaces and newlines. You can use "$@" instead of "$1" in the function and it will use the whole thing regardless of space.
```

function writetofile {
 if  test ! -z "$@"
 then
    echo "$@" > file.txt
 fi
}

var="a b"
writetofile $var

```

It throws an error:
```

 test: a: binary operator expected

```

when I test if the passed string is not null. 

I think this solves it partially:

```

function writetofile {
 if  test ! -z "$1" #even one character passed its still != null
 then
    echo "$@" > file.txt
 fi
}

var="a b"
writetofile $var

```

---

### Post by mobilediesel on 2010-05-06
> **dragos2 said:**
> It throws an error:
```

 test: a: binary operator expected

```

when I test if the passed string is not null. 

I think this solves it partially:

```

function writetofile {
 if  test ! -z "$1" #even one character passed its still != null
 then
    echo "$@" > file.txt
 fi
}

var="a b"
writetofile $var

```

Try this:
```
writetofile () 
{ 
    if [ ! -z "$1" ]; then
        echo "$@" > file.txt;
    fi
}
```

---

### Post by dragos2 on 2010-05-06
> **mobilediesel said:**
> Try this:
```
writetofile () 
{ 
    if [ ! -z "$1" ]; then
        echo "$@" > file.txt;
    fi
}
```

Working, thanks :)

Is was because of the [ ] ?

---

### Post by mobilediesel on 2010-05-06
> **dragos2 said:**
> Working, thanks :)

Is was because of the [ ] ?

Yeah, I can't remember why it makes a difference though. I'm getting fairly decent with Bash I'm far from being a genius, so far.

---


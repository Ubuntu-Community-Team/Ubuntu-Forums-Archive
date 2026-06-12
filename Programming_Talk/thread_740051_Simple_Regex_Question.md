---
title: "Simple Regex Question"
date: 2008-03-30
forum: Programming Talk
---

### Post by solarwind on 2008-03-30
Let's say ls outputs this:
```

JoranConfigurator$1.class 
JoranConfigurator$3.class
 JoranConfigurator$5.class
JoranConfigurator.class
JoranConfigurator$1.java
JoranConfigurator$3.java
JoranConfigurator$5.java
JoranConfigurator.java
JoranConfigurator$2.class
JoranConfigurator$4.class
JoranConfigurator$ParseAction.class
action
JoranConfigurator$2.java
JoranConfigurator$4.java
JoranConfigurator$ParseAction.java
spi
```

How do I make  a regular expression that matches all files ending with ".class" that DO NOT contain a dollar sign (4)?

I tried this:

```
ls | egrep "*[^\$].class"
```

But it didn't work.

---

### Post by WW on 2008-03-30
"^[^\$]*\.class$" works:
> 
$ ls -1
other$1.class
other$3.class
other.class
stuff
thing$1.class
thing$2.class
thing.class
this.class.no
$ ls | egrep "^[^\$]*\.class$"
other.class
thing.class
$ 

The pattern:
 [color=blue]^[/color] : Must match from the beginning of the name
 [color=blue][^\$]*[/color] : Zero or more occurrences of anything except $
[color=blue]\.class$[/color] : Must end with .class

---

### Post by cwaldbieser on 2008-03-30
```

grep -e '*.class' -v -e '\$'

```

---

### Post by solarwind on 2008-03-30
> **WW said:**
> "^[^\$]*\.class$" works:

The pattern:
 [color=blue]^[/color] : Must match from the beginning of the name
 [color=blue][^\$]*[/color] : Zero or more occurrences of anything except $
[color=blue]\.class$[/color] : Must end with .class

Thanks so much!

---

### Post by solarwind on 2008-03-30
> **cwaldbieser said:**
> ```

grep -e '*.class' -v -e '\$'

```

And what does this do?

---

### Post by cwaldbieser on 2008-03-31
> **solarwind said:**
> And what does this do?
It is a grep command that does what you asked.

```

$ ls | grep -e '*.class' -v -e '\$'

```

The first expression (-e option) matches anything that ends in ".class".  The next expression is inverted (-v), and matches a dollar sign.

---

### Post by solarwind on 2008-03-31
> **cwaldbieser said:**
> It is a grep command that does what you asked.

```

$ ls | grep -e '*.class' -v -e '\$'

```

The first expression (-e option) matches anything that ends in ".class".  The next expression is inverted (-v), and matches a dollar sign.

Thanks.

---

### Post by WW on 2008-03-31
> **cwaldbieser said:**
> It is a grep command that does what you asked.

```

$ ls | grep -e '*.class' -v -e '\$'

```

The first expression (-e option) matches anything that ends in ".class". 
Actually, it doesn't:
> 
$ [color=blue]ls -1[/color]
other$1.class
other$3.class
other.class
stuff
thing$1.class
thing$2.class
thing.class
this.class.no
$ [color=blue]ls | grep -e '*.class'[/color]
$

In a regular expression, * means 'match zero or more occurrences of the previous item'.  But there is nothing before * in the pattern '*.class'; apparently grep treats the * as a literal character in this case, and it will try to match the * character.  Also, . means 'any character'.  Finally, there is nothing in that pattern that says it  must occur at the end.  So the pattern '*.class' matches strings such as '*Xclass', '123*mclassZZZ', etc, but it doesn't match any of the file names.

---

### Post by ghostdog74 on 2008-03-31
```

# ls *class|while read -r fi
   do 
      case $fi in  
        *[$]* ) continue;; 
        *) echo $fi ;; 
     esac
   done


```
or
```

# ls *class |awk '!/\$/'

```

---


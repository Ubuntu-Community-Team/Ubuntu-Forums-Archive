---
title: "Bash: problem with single quote inside a double quote"
date: 2015-10-25
forum: Programming Talk
---

### Post by erotavlas on 2015-10-25
Hi,
I have a problem with bash command. This line works well as bash command
```
cat /etc/*-release | grep "NAME=" -m2 | tail -1 | cut -d "=" -f2  | tr -d '"' | tr '[:upper:]' '[:lower:]'
```
Whereas if I would like to assign it to a variable, it does not work
```
 name="$(cat /etc/*-release | grep "NAME=" -m2 | tail -1 | cut -d "=" -f2  | tr -d '"' | tr '[:upper:]' '[:lower:]')" 
```
I tried also this
```
 name="$(cat /etc/*-release | grep "NAME=" -m2 | tail -1 | cut -d "=" -f2  | tr -d "'"'" | tr "'[:upper:]'" "'[:lower:]'")" 
```

Thank you

---

### Post by blm-ubunet on 2015-10-25
More likely the problem would be double quote inside singles.
If was just quoting then escaping '\"' would work.

This is close..
```
name=$(echo $(cat /etc/*-release) | grep "NAME=" -m2 | tail -1 | cut -d "=" -f2 | tr -d '"' | tr '[:upper:]' '[:lower:]')
```
but the "echo" removes the newlines from the cat stdout so the remaining stuff does not wrong quite right..
It's highly likely there is a cleaner way..

---

### Post by erotavlas on 2015-10-26
> **blm-ubunet said:**
> More likely the problem would be double quote inside singles.
If was just quoting then escaping '\"' would work.

This is close..
```
name=$(echo $(cat /etc/*-release) | grep "NAME=" -m2 | tail -1 | cut -d "=" -f2 | tr -d '"' | tr '[:upper:]' '[:lower:]')
```
but the "echo" removes the newlines from the cat stdout so the remaining stuff does not wrong quite right..
It's highly likely there is a cleaner way..

Hi,
thank you for your help. Finally, I found the solution. The command worked in this way as you suggested by adding the escaping symbol \ before the double quote ".
```

name="$(cat /etc/*-release | grep "NAME=" -m2 | tail -1 | cut -d "=" -f2  | tr -d '\"' | tr '[:upper:]' '[:lower:]')"

```
There is no need of echo.

---

### Post by Vaphell on 2015-10-26
is there a reason why you are after NAME not ID?

```
$ name=$( lsb_release -si )
$ name=${name,,}
$ echo "$name"
ubuntu
```

and if you really need to mangle etc/*release

```
$ awk -F= '$1=="ID" { print $2; }' /etc/*release
ubuntu
```

---

### Post by erotavlas on 2015-10-26
> **Vaphell said:**
> is there a reason why you are after NAME not ID?

```
$ name=$( lsb_release -si )
$ name=${name,,}
$ echo "$name"
ubuntu
```

and if you really need to mangle etc/*release

```
$ awk -F= '$1=="ID" { print $2; }' /etc/*release
ubuntu
```

You are right, more compact way with single line
```

name="$(cat /etc/*-release | grep "DISTRIB_ID=" | cut -d "=" -f2 | tr '[:upper:]' '[:lower:]')" 

```

---

### Post by Vaphell on 2015-10-26
even more compact

```
$ name=$( awk -F= '/^DISTRIB_ID/ { print tolower($2); }' /etc/*release )
$ echo "$name"
ubuntu
```

1 command instead of 4.

---


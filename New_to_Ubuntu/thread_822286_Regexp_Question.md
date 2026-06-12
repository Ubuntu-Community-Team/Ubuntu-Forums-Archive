---
title: "Regexp Question"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by control_guy on 2008-06-08
I am doing the following:

```
cat xyz.tt | egrep date1.\{1,4\}value=\"\(.\{4,6\}2008\)\"
```

which outputs a line like:

    ```
<input type="hidden" name="date1" value="6-7-2008">
```

What I want is to store only *6-7-2008* to variable $var1 so that I can use it in further commands. Could someone help me?

Thanks.

---

### Post by kamaji792 on 2008-06-08
I don't know how to make egrep do what you want but you could try perl.

```
perl -n -e 'if ( m/date.+value="(\d+-\d+-2008)"/ ) { print $1 }' xyz.tt
```

**-n** makes the command loop though each line of the file.
**-e** specifies the perl commands to be run

```
perl -n -e 'if ( **m/**date.+value="(\d+-\d+-2008)"**/** ) { print $1 }' xyz.tt
```
[INDENT]match the expression between the '/.../'[/indent]

```
'if ( m/date.+value="(**\d+-\d+-2008**)"/ ) { print **$1** }'
```
[indent]print the part matched by the brackets.[/indent]

Basically if a line matches **date.+value="\d+-\d+-2008"**

it will print the match **\d+-\d+-2008**

**\d** matches a digit.
**+** means 1 or more

all the best

---

### Post by control_guy on 2008-06-08
Exactly what I needed. Also a good practical introduction to perl. Thanks a lot.

> **kamaji792 said:**
> I don't know how to make egrep do what you want but you could try perl.

```
perl -n -e 'if ( m/date.+value="(\d+-\d+-2008)"/ ) { print $1 }' xyz.tt
```

**-n** makes the command loop though each line of the file.
**-e** specifies the perl commands to be run

```
perl -n -e 'if ( **m/**date.+value="(\d+-\d+-2008)"**/** ) { print $1 }' xyz.tt
```
[INDENT]match the expression between the '/.../'[/indent]

```
'if ( m/date.+value="(**\d+-\d+-2008**)"/ ) { print **$1** }'
```
[indent]print the part matched by the brackets.[/indent]

Basically if a line matches **date.+value="\d+-\d+-2008"**

it will print the match **\d+-\d+-2008**

**\d** matches a digit.
**+** means 1 or more

all the best

---


---
title: "variable substitution within a subshell"
date: 2008-02-09
forum: Programming Talk
---

### Post by provisional_idiot on 2008-02-09
so basically i want to substitute the value of a script variable in a subshell so that it acts as a regular expression for some other  interpreter, say sed or awk. naively i want to write something like the following: 

substitute=regular_expression
variable=`ls | awk  '/$substitute/ {print $0}'`

of course this tells awk to search for “$substitute” instead of “regular_expression” which is i had intended. 

any help for producing the intended effect?

---

### Post by provisional_idiot on 2008-02-09
the only solution ive come up with so far seems unnecessarily sloppy and in fact intractable under high iteration. the trick is to create an executable file, say temp.f, and copy the syntax of the command to the file and run it:

substitute=regular_expression
1>/dir/temp.f
echo -n "ls | awk '/" 1>> /dir/temp.f
echo "$substitute/ { print \$0 }'"
/dir/temp.f

however this is unsatisfactory to me though it meets the basic parameters of the question.... looking for something less "ad hoc"

---

### Post by stroyan on 2008-02-09
The eval bash builtin will accomplish what you want.
It takes arguments and evaluates them before using them as a command.
That means that parameter expansion of values like $substitute is done.
You need to backslash quote to protect values like $0 that you want to pass to awk.
```
substitute=regular_expression
eval "variable=\$(ls | awk '/$substitute/ {print \$0}')"
```

---

### Post by ghostdog74 on 2008-02-09
> **provisional_idiot said:**
> 
substitute=regular_expression
variable=`ls | awk  '/$substitute/ {print $0}'`


```

substitute=regular_expression
variable=`ls | awk  -v s="$substitute" '$0~s {print $0}'`

```
BTW, you are not doing substitution with the above code. in Awk, use sub/gsub to substitute.
even better, for the above scenario, use ls to "get" your file pattern,eg
```

ls file*.txt |  awk '....'

```

---

### Post by stroyan on 2008-02-09
If the goal is really to match file names then 'ls' is not adding anything.
Bash parameter expansion is matching the file names passed to ls for 'ls file*.txt'.
The same result can be achieved with bash alone using ```
variable==$(for f in *.zoo ;do echo $f;done)
```

---

### Post by ghostdog74 on 2008-02-09
> **stroyan said:**
> If the goal is really to match file names then 'ls' is not adding anything.
Bash parameter expansion is matching the file names passed to ls for 'ls file*.txt'.

we really wouldn't know until OP has clarified what he's trying to do. besides, if he's trying to use awk, then there are might be other agendas. otherwise, the ls is really not needed.

> 
The same result can be achieved with bash alone using ```
variable==$(for f in *.zoo ;do echo $f;done)
```

```

variable=`echo *.zoo` #just for the above case

```

---

### Post by stroyan on 2008-02-09
variable=`echo *.zoo` won't put newlines between file names.
It will put spaces between them.
That will make for trouble handling file names that contain spaces.
Of course, file names can actually contain newlines.
That will break all sorts of attempts, including echoing each file name
or parsing ls output.

---

### Post by ghostdog74 on 2008-02-10
doesn't matter.going OT anyway

---


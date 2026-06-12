---
title: "basic script question"
date: 2007-09-05
forum: Programming Talk
---

### Post by energiya on 2007-09-05
Hi,
I'm trying to build a script to interact with mpc. The thing is I can't get \n (new line) in a variable. The output should be:
> 
Song Name
[playing] #1/12   4:13/5:22 (79%)
volume: 84%   repeat: on    random: on 

but after a
```

soutput=`mpc`
echo "$soutput"

```
I get
> 
Song Name [playing] #1/12   4:13/5:22 (79%) volume: 84%   repeat: on    random: on 

I really need a new line.

**Basically**, how do I keep new line when assigning var_name=`command` ?

Thanks.

---

### Post by eentonig on 2007-09-05
By making sure that the output of 'command' contains the '\n' newline character where you want it.

---

### Post by energiya on 2007-09-05
Yes, I know... but how do I do that? I can't control what mpc outputs. I tried to replace \n with sed to another delimiter but sed is over my mind (sed -e 's/\n/{*}/g' doesn't work).

---

### Post by cwaldbieser on 2007-09-05
Are you sure you are quoting the arguments to echo in your script?

```

$ x=$(who)
$ echo "$x"
carl     tty1         Sep  4 09:13
carl     :0           Sep  3 09:55
$ echo $x
carl tty1 Sep 4 09:13 carl :0 Sep 3 09:55

```
The newline is a legal word seperator, so echo has 11 arguments in the second example.  In the first example, echo has a single argument that includes embedded new lines.

---

### Post by tseliot on 2007-09-05
maybe you should use something like "yourcommand | cut -d".

type:
```
man cut
```

and see how it works

---


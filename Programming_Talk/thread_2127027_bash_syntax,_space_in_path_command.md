---
title: "bash syntax, space in path command"
date: 2013-03-18
forum: Programming Talk
---

### Post by sselt on 2013-03-18
```
$ pwd
$ ~/pathwith space

$ if [ $(pwd) = ~/pathwith space ]; then echo "true"; fi
$ bash: [: too many arguments
```

What is wrong? I've tried escaping the space and quotes around the path. :-k

---

### Post by Vaphell on 2013-03-19
i will use echo instead of pwd
```
$ echo "~/pathwith space"
~/pathwith space
$ [ $(echo "~/pathwith space") = ~/pathwith space ] && echo true
bash: [: too many arguments
$ [ $(echo "~/pathwith space") = [COLOR="#0000CD"]"[/COLOR]~/pathwith space[COLOR="#0000CD"]"[/COLOR] ] && echo true
bash: [: too many arguments
$ [ [COLOR="#0000CD"]"[/COLOR]$(echo "~/pathwith space")[COLOR="#0000CD"]"[/COLOR] = [COLOR="#0000CD"]"[/COLOR]~/pathwith space[COLOR="#0000CD"]"[/COLOR] ] && echo true
true
```

comparison in [] requires exactly 2 arguments for = (4 total: 'arg1', '=', 'arg2', ']' )
when you have an expression that can be reduced to [ ~/pathwith space = ~pathwith space ], [ sees:
1. ~/pathwith
2. space
3. =
4. ~/pathwith
5. space
6. ]
you have to use quotes and/or escaping to make it crystal clear what is supposed to be a single 'word', even in case of embedded commands that give space ridden output.

to showcase it let's write a small function that will use the same stuff as [ but will print the parameters it gets.
Open new terminal window and type (it will locally override the stock [ command)
```
$ [() { printf "%s\n" "$@"; }
$ [ $( echo "a b" ) = a b ]
a
b
=
a
b
]
$ [ $( echo "a b" ) = "a b" ]
a
b
=
a b
]
$ [ "$( echo "a b" )" = "a b" ]
a b
=
a b
]
```

---

### Post by kevdog on 2013-03-19
Try this

if [ "`pwd`" = "~/pathwith space" ]; then echo "true"; fi

---

### Post by Bucky Ball on 2013-03-19
*Thread moved to **Programming Talk**.*

---

### Post by sisco311 on 2013-03-19
@Vaphell and kevdog 

Tilde expansion only applies when `~' is unquoted. ;) See BashPitfalls 26 (link in my signature). 


 @OP: Check out BashFAQ 031 and 020 (link in my sig) and [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes). 

I'd use the new test command:
```
if [[ "$(pwd)" == "$HOME/dir name" ]]
then
...
fi
```

---

### Post by Vaphell on 2013-03-19
i know about ~ but too many arguments doesn't sound like a problem with tilde expansion (more like lacking in-depth knowledge how the parsing in bash works) so i ignored it.
Once the OP deals with it he can move to fixing possible issues with "~/dir" vs ~/dir vs /home/username/dir

---

### Post by sselt on 2013-03-19
Thanks @Vaphell, @kevdog, and @sisco311. I learned something today.

What was throwing me off a previous script, with no spaces, that works.

When in doubt, just quote the whole damn thing!

Haha. I know that's not true, but it might make a funny signature,
which other people would then bash. har har.

---

### Post by schragge on 2013-03-19
Just nitpicking, sorry.
> **sisco311 said:**
> 
I'd use the new test command:
```
if [[ "$(pwd)" == "$HOME/dir name" ]]
``` The first pair of double quotes may be omitted here: the new form of test ([[...]]) takes care of quoting the results of parameter expansion and command substitution (this was a big point behind introducing it into the shell in the first place):
```
[[ $(echo a b) == 'a b' ]] && echo ok
``` works the same as ```
[ "$(echo a b)" = 'a b' ] && echo ok
```

---


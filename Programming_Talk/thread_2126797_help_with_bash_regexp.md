---
title: "help with bash regexp"
date: 2013-03-18
forum: Programming Talk
---

### Post by tehcavil on 2013-03-18
> 
#!/bin/bash

filename=$1

rm -f output.ir

one=`cat $filename`
echo -e ${one//[()]/'\n'parens'\n'} >> output.ir


thats my code so far, I'm trying to make a lisp -> bash compiler. this is what i have so far for the tokenizer part of the parser written in bash unfortunately my regexp knowledge is quite weak, i need help, so far this works by changing every ( and ) into a "parens". I want to change the ( into a "start_parens'\n'" and the ) into a "'\n'end_parens" in one pass/regexp. is this possible?

edit: meanig can i do conditional substring replacement?

---

### Post by schragge on 2013-03-18
I'd use sed for this:
```
[COLOR=green]$[/COLOR] echo '(())'|sed 's/(/start_parens\n/g;s/)/end_parens\n/g'
[COLOR=green]start_parens
start_parens
end_parens
end_parens[/COLOR]

```
Applying this to your code
```

#!/bin/sh
exec sed 's/(/\nstart_parens\n/g;s/)/\nend_parens\n/g' $1 >output.ir

```

---

### Post by tehcavil on 2013-03-18
> **schragge said:**
> I'd use sed for this:
```
[COLOR=green]$[/COLOR] echo '(())'|sed 's/(/start_parens\n/g;s/)/end_parens\n/g'
[COLOR=green]start_parens
start_parens
end_parens
end_parens[/COLOR]

```
Applying this to your code
```

#!/bin/sh
exec sed 's/(/\nstart_parens\n/g;s/)/\nend_parens\n/g' $1 >output.ir

```

thanks!

---


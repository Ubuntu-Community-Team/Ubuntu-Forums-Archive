---
title: "Trouble getting until structure to work in script"
date: 2011-03-20
forum: Programming Talk
---

### Post by slashwannabe94 on 2011-03-20
Hey guys, 

I'm just playing around in bash trying to understand it better but i keep getting an error on a script i have made. 

This is the code

#!/bin/bash
x=0
until [ "$x" -ge 10 ]; then
    echo "Current value of x: $x"
    x=$(expr $x + 1)
    sleep 1
done
---------------------------------------------
This is the error i get.

until_do_done.sh: line 4: syntax error near unexpected token `then'
until_do_done.sh: line 4: `until [ "$x" -ge 10 ]; then'

obviously then is the wrong token being used, so what should i use and why not 'then'? 

Thanks

SlashWannabe94

---

### Post by johnl on 2011-03-20
> **slashwannabe94 said:**
> Hey guys, 

I'm just playing around in bash trying to understand it better but i keep getting an error on a script i have made. 

This is the code

#!/bin/bash
x=0
until [ "$x" -ge 10 ]; then
    echo "Current value of x: $x"
    x=$(expr $x + 1)
    sleep 1
done
---------------------------------------------
This is the error i get.

until_do_done.sh: line 4: syntax error near unexpected token `then'
until_do_done.sh: line 4: `until [ "$x" -ge 10 ]; then'

obviously then is the wrong token being used, so what should i use and why not 'then'? 

Thanks

SlashWannabe94

Try

```

until [ "$x" -ge 10 ]; **do**
...
done

```

**then** is only used with **if** statements.

---

### Post by slashwannabe94 on 2011-03-20
Thanks dude, that worked :)

---


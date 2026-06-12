---
title: "Chaining commands in bash script using &amp;&amp;"
date: 2014-07-21
forum: Programming Talk
---

### Post by donsy on 2014-07-21
I need to write a bash script in which every command is conditional upon the successful execution of the previous command and if any command fails no following commands will be executed. I would rather not have each statement embedded in an "if" statement. So far this is what I'm thinking about doing:
```
#!/bin/bash

comand1
[ $? ] && command2
[ $? ] && command3
[ $? ] && command4
[ $? ] && command5

```

Is this OK? Is there a better way?

---

### Post by Lars Noodén on 2014-07-21
You can connect them directly:

```
#!/bin/bash

comand1 && command2 && command3 && command4 && command5

```

If that is hard to read in your script, then you can split the line using a backslash at the end of the line.

```
#!/bin/bash

comand1 \
&& command2 \
&& command3 \
&& command4 \
&& command5

```

---

### Post by sisco311 on 2014-07-22
You can use `set -e', check out BashFAQ 105 (link in my signature).

But, I would do something like:
```

command1 || exit 1
command4 || { echo "command4 failed" >&2; exit 4; }

```

If you want to use verbose error messages you could write a little function to keep your code clean and organized:

```

#!/bin/bash

err()
{
    r="$1"
     case "$r" in
        1)  printf '%s\n' "error 1" >&2 ;;
        2)  printf '%s\n' "error 2" >&2 ;;
        4)  printf '%s\n' "error 4" >&2 ;;
        *)  printf '%s\n' "unknown error" >&2 ; exit -1 ;;
    esac
exit "$r"
}

command1 || err 1
command2 || err 2
command3 || err 4

exit 0

```

---

### Post by donsy on 2014-07-22
Thanks for all the suggestions. I think I'll go with 'set -e' as that solution seems the simplest for the commands I'll be using.

---


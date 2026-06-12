---
title: "Bash - I can't get for loops to work"
date: 2012-11-30
forum: Programming Talk
---

### Post by alkal0id on 2012-11-30
EDIT: God I feel stupid. The second I hit the submit button, the answer came to me. I was using sh script.sh to run my shell scripts. I tried bash script.sh instead and it works fine. MODS can you mark this thread as solved please.

I have bash version  4.2.24(1) so thats not the problem. When I try to do this kind of for loop:
```

for i in {0..10..2}
  do
     echo "Welcome $i times"
 done

```The output should be:
> Welcome 0 times Welcome 2 times Welcome 4 times Welcome 6 times Welcome 8 times Welcome 10 timesbut when I do it, the output is:
> Welcome {0..10..2} timesI'm new to bash programming but I'm familiar with PHP loops so I know I can do this kinda thing with while loops but I prefer to use for loops when I can.

---

### Post by sudodus on 2012-11-30
> **alkal0id said:**
> EDIT: God I feel stupid. The second I hit the submit button, the answer came to me. I was using sh script.sh to run my shell scripts. I tried bash script.sh instead and it works fine. MODS can you mark this thread as solved please.

I have bash version  4.2.24(1) so thats not the problem. When I try to do this kind of for loop:
```

for i in {0..10..2}
  do
     echo "Welcome $i times"
 done

```The output should be:
but when I do it, the output is:
I'm new to bash programming but I'm familiar with PHP loops so I know I can do this kinda thing with while loops but I prefer to use for loops when I can.

Try according to this:

```
man bash:

       for name [ in word ] ; do list ; done
              The list of words following in is expanded, generating a list of
              items.  The variable name is set to each element of this list in
              turn,  and  list is executed each time.  If the in word is omit&#8208;
              ted, the for command executes  list  once  for  each  positional
              parameter that is set (see PARAMETERS below).  The return status
              is the exit status of the last command that  executes.   If  the
              expansion of the items following in results in an empty list, no
              commands are executed, and the return status is 0.

       for (( expr1 ; expr2 ; expr3 )) ; do list ; done
              First, the arithmetic expression expr1 is evaluated according to
              the  rules  described  below  under  ARITHMETIC EVALUATION.  The
              arithmetic expression expr2 is then evaluated  repeatedly  until
              it  evaluates  to zero.  Each time expr2 evaluates to a non-zero
              value, list is executed and the arithmetic expression  expr3  is
              evaluated.   If  any  expression is omitted, it behaves as if it
              evaluates to 1.  The return value is the exit status of the last
              command in list that is executed, or false if any of the expres&#8208;
              sions is invalid.
```

*examples:*

```
for i in *.txt;do echo textfiles: $i;done

for (( i=1; i<=20 ; i++ )) ; do echo $i;done

for i in *.TXT;do mv $i ${i/\.TXT/}.txt; done  # "move *.TXT *.txt"
```

---

### Post by Vaphell on 2012-11-30
> EDIT: God I feel stupid. The second I hit the submit button, the answer came to me. I was using sh script.sh to run my shell scripts. I tried bash script.sh instead and it works fine. MODS can you mark this thread as solved please.

use hashbang line to define shell( #!/bin/bash )
make scripts executable and run them with ./script.sh - system will call proper shell based on that first line of the script file.

---


---
title: "Multiple If statements in shell script"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by hookitup on 2013-11-13
hello folks.


i just got back into writing scripts for my server, im still fairly new to writing scripts.
im trying to make a script start a server dependent on its question being answered.

so this what i have but i dont really know how to get past 1 if statment.

```
#!/bin/bash
echo "What server do you want to start (1srv-5srv):"
read server

if [ "$server" = 1srv ]; then
        echo "you picked server 1"
else
        check if its 2srv


```

so how would i get it to then check if $server is equal to 2srv and echo "you picked server 2" if not that then check if its 3srv and so on so forth?

im sure theres a more advanced way of doing this. 
anybody know?

---

### Post by steeldriver on 2013-11-13
You could use elif - however a case...esac construction might be more natural than a big stack of elifs

```

case "$server" in

  "1srv") echo "Doing something"
  ;;

  "2srv") echo "Doing something else"
  ;;

  # and so on up to 5srv

  *) echo "Oops"
  ;;

esac

```

You can type 'help if' and/or 'help case' at the bash prompt for more info - there's also a 'select' statement in bash that allows you to enter a number to choose from a list

```
$ select server in srv1 srv2 srv3 srv4 srv5; do echo "You selected $server"; break; done
1) srv1
2) srv2
3) srv3
4) srv4
5) srv5
#? 2
You selected srv2

```

---

### Post by hookitup on 2013-11-13
Thanks for the quick reply steeldriver.

so in the case statement if im reading correctly. it checks if the variable $server is already defined (1srv-5srv)  if so it runs the echo command or any other command if not echos "Oops" ???

---


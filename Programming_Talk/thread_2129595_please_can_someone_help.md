---
title: "please can someone help"
date: 2013-03-26
forum: Programming Talk
---

### Post by mario00 on 2013-03-26
[COLOR=#000000]hi i'm new to this and i was wondering if anyone could help me. i want to make a menu style shell script that will let me backup, restore and quit and i have no idea how to even start. I've read many tutorials but it goes over my head [/COLOR]:sad:[COLOR=#000000] hope someone can help. i really haven't a clue what to do to even start writing this and would love to learn. surely someone knows how to make one like this[/COLOR]

---

### Post by Vaphell on 2013-03-26
menu can be done with *select*

```
select choice in "backup" "restore" "quit"
do
  echo "you selected '$choice'"
  case $choice in
    backup)  echo do backup things here
             ;;
    restore) echo do restore things here
             ;;
    quit)    echo quit
             exit 0
             ;;
  esac
  break  # jump out of the otherwise infinite select loop.
done
```

how it would look like:
```
1) backup
2) restore
3) quit
#? 1
you selected 'backup'
do backup things here

```

and when it comes to backing up, look at *rsync* command

---


---
title: "Bash script: problem with IF and WHILE"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by daniel3ub on 2008-10-25
Hi, people!

I am trying to learn bash script, and the best way is try to DO something, right? ;)

So, I wrote this in a backup script:

```

1 while read line
2 do
3	if [ ! -e $origem ]
4		then echo "ERRO: $origem não existe."
5			notify-send "ERRO: $origem não existe."
6			done < "$params"
7	fi
(some other commands)
done < "$params"

```

The idea is:
Read the parameters for this script from a file $params. This is ok.
If the dir $origem doen't exist, read the next line of file $params, ignoring the (some other commands).

The problem is that I get an error in line 6: "./backup.daniel02.sh: line 6: Erreur de syntaxe près du symbole inattendu « done »" or something like "syntax error next the unattended symbol « done »"

What's wrong?

Thanks!

---

### Post by ghostdog74 on 2008-10-25
use the "continue" keyword
```

if [ ! -e $dir ];then
  ...
   continue
fi

```

---


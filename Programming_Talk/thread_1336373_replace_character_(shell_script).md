---
title: "replace character (shell script)"
date: 2009-11-24
forum: Programming Talk
---

### Post by razzer on 2009-11-24
Hello

Im making a shell script wich is adding users from a file where each user is sepearetd liked this 

Kajsa;svensson
Tomas;börjesson

and so on, the script is in a while loop until it has done all users in the file. What i wonder is, how can i check for each time it ads a user if there is any swedish characters like "åäö" and replace them if found? for example åä should be replaced with "a" and ö with "o"

---

### Post by diesch on 2009-11-24
```

$ echo "öåä" |sed 'y/åäö/aao/' 
oaa

```

---

### Post by stylishpants on 2009-11-25
Try uni2ascii.  

```

bob@cob:~$ cat /tmp/test 
Kajsa;svensson
Tomas;börjesson

bob@cob:~$  uni2ascii -Bq /tmp/test 
Kajsa;svensson
Tomas;borjesson

```

---


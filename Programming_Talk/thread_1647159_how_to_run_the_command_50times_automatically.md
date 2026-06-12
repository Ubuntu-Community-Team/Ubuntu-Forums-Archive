---
title: "how to run the command 50times automatically?"
date: 2010-12-16
forum: Programming Talk
---

### Post by niejieqiang on 2010-12-16
hi,all,i need to handle a text file with the follow command :
 perl -pi -e 's/([a-z]+)( [^\x00-\x7f]+)( [^\x00-\x7f].*)/\1\2\n\1\3/g' 1.txt
 
i don't know how to run the command  50 times or more in once. could you help me ? thanks in advance .

---

### Post by ksprasad on 2010-12-16
Hi,
 
 Use for loop in a shell script
 
Regards,
ksprasad

---

### Post by daqron on 2010-12-16
You want to run the command 50 times on the same target file? 
```
for i in `seq 50` ; do perl -pi -e 's/[COLOR="Red"][regex stuff][/COLOR]/g' 1.txt ; done

```
Or you want to run the command once on files 1.txt through 50.txt?
```
perl -pi -e 's/[COLOR="Red"][regex stuff][/COLOR]' {1..50}.txt

```

---

### Post by niejieqiang on 2010-12-17
:D thank you ~~~

---


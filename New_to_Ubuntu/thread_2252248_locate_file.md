---
title: "locate file"
date: 2014-11-10
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-11-10
Hi all, 

I've installed todo-indicator and it created todo.txt file. 
I'm trying to find it using command: 

$ locate todo.txt

but it doesn't return any result. 

So my questions are: 

1) where does todo-indicator place its todo.txt file? 

2) why locate command doesn't return results? do I need to run some indexing command for future usage?  

Lubuntu 14.04.1 LTS 

Thanks ahead.

---

### Post by nerdtron on 2014-11-10
1. not sure about that.
2. From the man page:
>         locate  reads one or more databases prepared by updatedb(8) and writes
       file names matching at least one of the PATTERNs to  standard  output,
       one per line.



So you should run "sudo updatedb" first. Then try the locate command again.

For me, I rarely use the locate command. I usually use the find command when I try to locate things.
```
find / -iname "todo.txt"
```

---

### Post by marchello_lippi2 on 2014-11-10
nerdtron, thanks

---

### Post by whitesmith on 2014-11-10
+1 to @nerdtron for bringing up eternal problems with locate. (OK, they just feel eternal.) locate works off a database, and only the Great Spirit in the Sky knowss when it's updated--daily, I presume, but when? On the other hand, find gives realish time responses, at the cost of being pokey. Don't even think of running locate on a large system with a multiplicity of large computers (say, maybe, the one at the Argonne National Laboratory)--**unless** you limit its scope, which can be done without hair-pulling. Do as nerdtron suggests and you should be OK. Cheers!

---


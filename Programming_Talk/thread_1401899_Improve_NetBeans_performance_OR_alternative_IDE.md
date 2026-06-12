---
title: "Improve NetBeans performance OR alternative IDE?"
date: 2010-02-08
forum: Programming Talk
---

### Post by Enk on 2010-02-08
Hi

I've got a HP Compaq presario, upgraded to 4GB RAM but only 2GHz CPU. But NetBeans is just too slow. I've used NetBeans on worse computers, so I can't understand why it is so bleeding slow.

Autocomplete is really slow, and alt-tabbing to/from NetBeans is dreadfull. Really interferes with my productivity :P

Can this be improved? Using netbeans 6.7.1.

Anyway, if there are any other smaller IDEs, please let me know!

---

### Post by Reiger on 2010-02-08
That is odd. Perhaps it is indexing/task-checking/w-ever? Let that finish; afterwards it should be nippy.

Alternatively you might want to upgrade to Netbeans 6.8 anyway.

---

### Post by doas777 on 2010-02-08
are you sure your java configuration is optimal? you've installed sun jdk and updated your alternatives, right?

there have been some tips on eclipse optimization that may work as well for you, if you search a little.

---

### Post by Axos on 2010-02-08
Works fine on my notebook (2 years old, 2 GB RAM). Be sure to close projects you are no longer working on (right click on them in the projects list and click close). Every project you have there is using memory. Once you get near the JVM's memory limit (which is configurable), the JVM will start to bog down due to frequent garbage collection.

---

### Post by Enk on 2010-02-08
Found a solution (I think).

Specifying max/min memory size with:

```
netbeans -J-Xms512m -J-Xmx1024m
```

Certainly better than the 80MB it used before :D

Thanks for all replies.

---

### Post by Axos on 2010-02-08
Wow, the default mx for mine is 401m. I wonder why it was set so low for yours. Garbage collection thrash-o-rama!

To change this "permanently", you can edit etc/netbeans.conf in the NetBeans installation directory.

---

### Post by lwhitmore on 2010-05-01
Well - I've moved to netbeans because Aptana dumped PHP.  I like the IDE, but it did seem sluggish (even compared to Aptana / Eclipse).

I've found a solution:

[LIST]Find and open your netbeans.conf file in your favourite text editor[/LIST]
[LIST]Edit the *netbeans_default_options* (which changes the start up parameters used each time netbeans is run[/LIST]
[LIST]Mine is currently set as below, and it's running nice and fast.  YMMV - have a go and see.[/LIST]
```
netbeans_default_options="-J-client -J-Xverify:none -J-Xss2m -J-Xms512m -J-XX:PermSize=32m -J-XX:MaxPermSize=200m -J-Dapple.laf.useScreenMenuBar=true -J-Dsun.java2d.noddraw=false -Dsun.java2d.opengl=true"
```

---

### Post by margemoosh on 2010-09-04
> **lwhitmore said:**
> Well - I've moved to netbeans because Aptana dumped PHP.  I like the IDE, but it did seem sluggish (even compared to Aptana / Eclipse).

I've found a solution:

[LIST]
[*]Find and open your netbeans.conf file in your favourite text editor
[/LIST]

[LIST]
[*]Edit the *netbeans_default_options* (which changes the start up parameters used each time netbeans is run
[/LIST]

[LIST]
[*]Mine is currently set as below, and it's running nice and fast.  YMMV - have a go and see.
[/LIST]
```
netbeans_default_options="-J-client -J-Xverify:none -J-Xss2m -J-Xms512m -J-XX:PermSize=32m -J-XX:MaxPermSize=200m -J-Dapple.laf.useScreenMenuBar=true -J-Dsun.java2d.noddraw=false -Dsun.java2d.opengl=true"
```

i have exactly same problem but when i use your options i get:
```
Unknown option -Dsun.java2d.opengl=true
```can you tell me which packages should i install to fix this problem?

---


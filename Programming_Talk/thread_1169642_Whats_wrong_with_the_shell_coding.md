---
title: "Whats wrong with the shell coding"
date: 2009-05-25
forum: Programming Talk
---

### Post by H.om on 2009-05-25
#!/bin/sh
count=0
d=expr $count + 2


I want 'd' to have a value=3. But it gives an error.
./test: 3: 0: not found

Suggest me a method.

---

### Post by H.om on 2009-05-25
#!/bin/sh
count=0
d=expr $count + 2


I want 'd' to have a value=3. But it gives an error.
./test: 3: 0: not found

Please correct me.or suggest any other method

---

### Post by lloyd_b on 2009-05-25
> **H.om said:**
> #!/bin/sh
count=0
d=expr $count + 2


I want 'd' to have a value=3. But it gives an error.
./test: 3: 0: not found

Suggest me a method.

Well, first off, 0 + 2 = 2, not 3 :)

Second, if you want to use expr for that calculation, try wrapping the command with backtics:```
#!/bin/sh
count=1
d=`expr $count + 2`
echo $d
```

Alternately, I believe```
d=$((count + 2))
``` will work with "sh".

Lloyd B.

---

### Post by darthmob on 2009-05-25
that's a simple one! :)
if you want to assign something to a variable which has to be executed put it in $ and brackets. it works like this:

```
#!/bin/sh
count=0
d=$(expr $count + 2)
```

PS: 0+2 = 2 != 3


// edit:
> Second, if you want to use expr for that calculation, try wrapping the command with backticsyou mixed something up there. the text in backtics is assigned literally without interpreting the commands in it.

// edit2:
I mixed something up there. your version works fine. it's these ' thingies which do what I said (they look all the same..).

---

### Post by nikhilbhardwaj on 2009-05-25
backticks work just fine
there's nothing wrong with using them with expr

---

### Post by H.om on 2009-05-26
Thankyou so much

---


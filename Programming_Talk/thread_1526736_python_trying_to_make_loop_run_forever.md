---
title: "python trying to make loop run forever"
date: 2010-07-08
forum: Programming Talk
---

### Post by leahk on 2010-07-08
i want this loop to keep on checking the number of files that are in the current working directory and every time one is added... print it out with cat. it stops running after a few seconds. also i dont understand how to use continue correctly. :p thank for ur help 
```
while True:
        while (x==t):
                time.sleep(0.5)
                x = filecount(os.getcwd())

        else:
                x = filecount(os.getcwd())
                g = commands.getoutput('ls -ct1 | head -1')
                if g.endswith('pyc')==True:
                        g = g[:-1]
                print ('printing out', g)
                c = 'cat' 
                x = c + ' ' + g
                os.system(x)
                x = t
```

---

### Post by leahk on 2010-07-08
i tried putting the whole thing in a while True loop but when i try to add a file it just keeps printing the latest file out over and over again

---

### Post by Tony Flury on 2010-07-08
When posting code - especially python - use the CODE or PHP tags - in order to maintain the indentations.
As you are probably aware indentations are important in python.

---

### Post by DaithiF on 2010-07-08
Hi,
This is your third thread on this topic in the last couple of days.  Could you explain what you are trying to accomplish and why, as it sounds rather like a programming homework assignment to me that you're attempting to complete without really making an effort to learn how.

For what its worth, heres the documentation for the while loop -- it explains continue fairly clearly I think:
[http://docs.python.org/reference/compound_stmts.html#while](http://docs.python.org/reference/compound_stmts.html#while)

---

### Post by wmcbrine on 2010-07-08
"continue" is like "break", except that, instead of ending the loop at that point, it loops back to the beginning -- so the rest of the loop won't be executed in that iteration, but the loop itself will continue.

---


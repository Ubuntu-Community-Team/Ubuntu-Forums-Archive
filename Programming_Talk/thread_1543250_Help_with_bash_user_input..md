---
title: "Help with bash user input."
date: 2010-07-31
forum: Programming Talk
---

### Post by d3vi1dog562 on 2010-07-31
Im writing a script to help automate some tasks and i can get a the user input 1 2 or 3 to execute different things. I can't figure out how to get the read value to work in the if then statement. Please help here is a layout of the problem.

```

#!/bin/bash 

echo """ Input your selection
1) KillAll, enable script!
2) Ooops error.
3) Doh.
"""

read mine

if mine=1 
then 
    echo " Your select will begin shortly:"
elif mine=2
    echo "Bad choice since the program isn't finished"
else
    echo "DOOOOOOOH"

fi
sleep 15
exit

```please help me with my problem

---

### Post by GlazedDonut on 2010-07-31
You need to put $ in front of variables, [ $var -eq <num> ] for the if comparisons, and a then after the elif:
```
#!/bin/bash 

echo """ Input your selection
1) KillAll, enable script!
2) Ooops error.
3) Doh.
"""

read mine

if [ $mine -eq 1 ] 
then 
    echo " Your select will begin shortly:"
elif [ $mine -eq 2 ]
then
    echo "Bad choice since the program isn't finished"
else
    echo "DOOOOOOOH"

fi
sleep 15
exit
```

---

### Post by d3vi1dog562 on 2010-07-31
Opps i found out after a couple hours of googling and playing  :P Thanks tho that is exactly what i was looking for  +1  for you!

---


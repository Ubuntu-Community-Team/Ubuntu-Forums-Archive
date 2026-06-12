---
title: "Strange bash script behavior"
date: 2010-12-26
forum: Packaging and Compiling Programs
---

### Post by my_abousamra on 2010-12-26
Dear All,

I was writing this script (test.sh)

#!/bin/bash

         if [ $1 != "minutes" -o $1 != "hours" -o $1 != "days" -o $1 != "weeks" ]
        # if [ $1 != "weeks" ]
        then
                echo "Error: wrong time format"
                exit 1
        fi
        echo $1

 and I had this strange problem, when running this script like that 

./test.sh weeks            
Error: wrong time format

although the condition should not match but when I use the hashed if condition instead of the first one it works fine

./test.sh weeks            
weeks

any suggestions!

---

### Post by MadCow108 on 2010-12-26
it evaluates weeks != minutes
which is true and it aborts

you want and (-a ) not or

---

### Post by my_abousamra on 2010-12-26
solved!
Thank U

---


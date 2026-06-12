---
title: "Shell script not working"
date: 2010-05-09
forum: Programming Talk
---

### Post by @rizz on 2010-05-09
Hi all i have a problem....
  

   I am trying to learn bash but i cant find a way do do the arithmetic stuff

 eg: Here is what i wrote in the file.sh

  #!/bin/sh
 echo "$[2+2]"

Now when i run the script from the command line i am supposed to get 4 bu t what i get is

 ```
$ $[2+2]
``` The same happens when i try the expr, instead of evaluating it prints the literals.....???

  Need help plz:confused:

---

### Post by kerry_s on 2010-05-09
change-> #!/bin/sh
to-> #!/bin/bash

in ubuntu sh is linked to dash not bash, so if you need bash specific put bash.

---

### Post by @rizz on 2010-05-09
Thumbs up!!!

It works like a charm......

Thanks again!!!

---


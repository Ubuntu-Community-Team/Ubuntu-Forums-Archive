---
title: "Basic grep script wont work"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by smackheid on 2012-05-23
Hi all,

I can't seem to get the below script to work, yet I can do it line by line. When I run the script, it prompts for the input and upon entering the input, returns to the command line.

I've also chmod 777 to directory and files, but no luck.

Any suggestions?

============
#!/bin/bash

echo "Enter Nominal"
read $ID
fgrep -i $ID DeadCell????????????????.csv
============

( I've tried using variants formats with wildcards * and ?, but have had no luck.)

---

### Post by steeldriver on 2012-05-23
```
read $ID
```should be

```
read ID
```(you only need the $ when you are expanding the value not when you are assigning it)

rookie mistake, we've all done it ;)

---

### Post by smackheid on 2012-05-23
Aw schoolboy error!!! How embarrassing!!!

Thank you once again steeldriver.


Regards
Smackheid

---


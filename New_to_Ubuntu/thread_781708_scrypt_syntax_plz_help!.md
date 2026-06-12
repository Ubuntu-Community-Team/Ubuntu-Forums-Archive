---
title: "scrypt syntax plz help!"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by -random on 2008-05-04
To put it simply, how do i pass a bash variable to a function argument?


i have a little prob with:
-
#!/bin/bash
echo Enter the year plz
read YEAR
cd /media/sdb1/recovered/jpg/$YEAR/
mkdir 01

find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR01*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/01/
-

and according to the debug:
-
bash -x ./myscript.sh

+ find /media/sdb1/recovered/jpg/2001/ -name '*.*'
+ xargs -i mv '{}' /media/sdb1/recovered/jpg/2001/01/
-

the "$YEAR01*.*" is simply read as '*.*' instead of, say '200401*.*'

what am i doing wrong?:confused:

---

### Post by -random on 2008-05-04
i typed:

 info |
> d
info: Writing node (dir)Top...
info: Done.
bash: d: command not found

What happened? whaaa!

---

### Post by girishv on 2008-05-04
Hi,

where have you defined $YEAR01 ?? I do not see it defined in the script.
Either set it up inside the program as
YEAR01=200401 # no $
or if you are passing year as argument, change $YEAR to $1

Also, if you are going to move each file individually, you can use -exec flag of find itself

find /media/sdb1/recovered/jpg/2001/ -name '*.*' -exec mv {} /media/sdb1/recovered/jpg/2001/01/ \;

No linebreak

Girish

---

### Post by -random on 2008-05-04
> **girishv said:**
> where have you defined $YEAR01 ?? I do not see it defined in the script.

forgot to put the top bit in soz! it's in now

---


---
title: "Bash Scripting Question  need to run $mybashscript variable and have variable set"
date: 2007-03-19
forum: Programming Talk
---

### Post by statictonic on 2007-03-19
Basically I'm looking to see if there is a way to have it so you would run $bashscriptfile dothis

do this would be set as a variable for example while the bash script was run.  similar to how cat would work when using it to read a text file $cat textfile

Anyone know if there's a way?

---

### Post by amd-64 on 2007-03-19
Here is an example of a code I use to reduce size and rename images. The script uses convert which is part of imagemagick  

The code in myscript is as follows
```

#! /bin/tcsh

for img in $1
do
  convert -sample 45%x45% -quality 80 $img web-$img
done

```

make sure myscript is executable 

```

$ chmod a+x myscript
```

You can then run this to loop on any number of images, using a wild card 

```
 $ sh myscript image*.jpg 
```

---

### Post by statictonic on 2007-03-19
> **amd-64 said:**
> Here is an example of a code I use to reduce size and rename images. The script uses convert which is part of imagemagick  

The code in myscript is as follows
```

#! /bin/tcsh

for img in $1
do
  convert -sample 45%x45% -quality 80 $img web-$img
done

```

make sure myscript is executable 

```

$ chmod a+x myscript
```

You can then run this to loop on any number of images, using a wild card 

```
 $ sh myscript image*.jpg 
```

ah that was actually really nice and simple, thanks for the help!

---


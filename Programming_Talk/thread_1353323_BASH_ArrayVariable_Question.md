---
title: "BASH Array/Variable Question"
date: 2009-12-12
forum: Programming Talk
---

### Post by cubeist on 2009-12-12
Hi,
I am having trouble solving a problem that seems really simple.  I need to select multiple image names and have each selection stored in a different variable, array, text file, etc. so I can recall it at a later time.

Here is what am talking about
```
echo "Enter Number of image groups:"
read selection
for (( x=0 ; x < $selection ; x++ ))
do
zenity --file-selection --multiple --text="Select Image Files" --separator=" "
done
```
So lets say I want to select four groups of multiple images each, the output is such: (I shortened the file paths for readabilty)
```
$
Select Number of image groups:
4
/home/Downloads/PC080174.JPG /home/Downloads/PC080181.JPG
/home/Downloads/PC080198.JPG /home/Downloads/PC080203.JPG
/home/Downloads/PC080175.JPG /home/Downloads/PC080181.JPG /home/Downloads/PC080198.JPG
/home/Downloads/PC080174.JPG /home/Downloads/PC080181.JPG /home/Downloads/test/PC080198.JPG /home/Downloads/PC080203.JPG

```

So how can I store each line of selected images into a unique variable?!

Any thoughts or ideas are appreciated... I have been shell scripting for ages, but I cannot wrap my head around this one!

---

### Post by mo.reina on 2009-12-12
```
echo "Enter Number of image groups:"
read selection
for (( x=0 ; x < $selection ; x++ ))
do
**VAR=($(**zenity --file-selection --multiple --text="Select Image Files" --separator=" "**))**
done
```

that will put the results into array VAR.  you can check the results with

```
echo ${VAR[@]}
```

---

### Post by cubeist on 2009-12-12
> **mo.reina said:**
> ```
echo "Enter Number of image groups:"
read selection
for (( x=0 ; x < $selection ; x++ ))
do
**VAR=($(**zenity --file-selection --multiple --text="Select Image Files" --separator=" "**))**
done
```

that will put the results into array VAR.  you can check the results with

```
echo ${VAR[@]}
```

Thanks! Unfortunately I tried that... it only puts the last selection into that variable.  I need to put each selection into a different variable.

---

### Post by Rany Albeg on 2009-12-12
Hi,

Just change to VAR**+**= instead of VAR=

Have a nice day.

---

### Post by cubeist on 2009-12-12
> **Rany Albeg said:**
> Hi,

Just change to VAR**+**= instead of VAR=

Have a nice day.

Thanks Rany, that is really close, unfortunately that puts each individual image into a spot in the array... I need each array to hold all the images per selection... but just as you were posting your reply I found an ideal solution...just double checking now...

---

### Post by kaibob on 2009-12-12
I didn't understand the OP's request originally (my fault) but think I do now. My suggestion:

```
#!/bin/bash

echo "Enter Number of image groups:"
read selection

for (( x=0 ; x < $selection ; x++ )) ; do
   VAR=$(zenity --file-selection --multiple \
      --text="Select Image Files" --separator=" ")
   ARRAY+=( "$VAR" )
done
```

If there are two "image groups" then two array elements would be created.

---

### Post by cubeist on 2009-12-12
OK, found the solution, hopefully useful to others in the future.  You need to use the command mapfile, like so!

```

echo "Select Number of image groups:"
read selection
for (( $x ; x < $selection ; x++ ))
do
zenity --file-selection --multiple --text="Select Image Files" --separator=" " >> /tmp/zenner
mapfile -t newArray < /tmp/zen
done
echo "There are '${#newArray[@]}' elements in the array"
echo ${newArray[0]}
echo ${newArray[1]}
```

This outputs the following:

```
$
Select Number of image groups:
2
There are '2' elements in the array
/home/Downloads/PC080174.JPG /home/Downloads/PC080175.JPG
/home/Downloads/PC080181.JPG /home/Downloads/PC080182.JPG

```

Now, I can work on image groups selectively at different parts of my whole script!

PS - Here is where I saw the reference to mapfile ([http://mywiki.wooledge.org/BashFAQ/005](http://mywiki.wooledge.org/BashFAQ/005))

---

### Post by cubeist on 2009-12-12
> **kaibob said:**
> I didn't understand the OP's request originally (my fault) but think I do now. My suggestion:

```
#!/bin/bash

echo "Enter Number of image groups:"
read selection

for (( x=0 ; x < $selection ; x++ )) ; do
   VAR=$(zenity --file-selection --multiple \
      --text="Select Image Files" --separator=" ")
   ARRAY+=( "$VAR" )
done
```

If there are two "image groups" then two array elements would be created.

Thank You Kaibob, your solution is much cleaner than mine!

---

### Post by Oishikawa on 2011-03-28
Thank You.. This too help me to solv my script,  SO.. Muchhh

---


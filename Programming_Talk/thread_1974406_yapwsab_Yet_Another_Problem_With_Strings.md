---
title: "yapwsab Yet Another Problem With Strings"
date: 2012-05-06
forum: Programming Talk
---

### Post by hakermania on 2012-05-06
At Bash :D

I've made a script-fu (gimp script) that rounds the corners of images and can be called through the command line.

But, no matter what, I cannot make it work!
```

#!/bin/bash
path=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
path=${path%?}
gimp -i -f -d -b '(round_the_corners "$path")' -b "(gimp-quit 0)"

```If I give in a terminal:
```

gimp -i -f -d -b '(round_the_corners "1.png")' -b "(gimp-quit 0)"

```it works just fine, but I don't know what is the correct way to pass the variable inside the single quotes that the -b arguments needs :(

---

### Post by codemaniac on 2012-05-06
try passing the individual .png files to gimp with a foreach loop .
something like below .
```

for i in `ls *.png`
do 
    gimp -i -f -d -b '(round_the_corners $i)' -b "(gimp-quit 0)"
done

```

---

### Post by hakermania on 2012-05-06
> **codemaniac said:**
> try passing the individual .png files to gimp with a foreach loop .
something like below .
```

for i in `ls *.png`
do 
    gimp -i -f -d -b '(round_the_corners $i)' -b "(gimp-quit 0)"
done

```
Hello and thanks for the help. I disagree with many points in your answer:
a) using ` ` inside commands so as to take the output is old technique, the new one is to place it between $()

b) Also, one should not use this inside a for loop. It should be
```

for i in *.png

```

c) I don't want to take every single png image in a directory and alter it. The code I provided will run from a nautilus-script, placed under ~/.gnome2/nautilus-scripts/ so as to be available under the right click menu, when I click on a png file, for example. The variable NAUTILUS_SCRIPT_SELECTED_FILE_PATHS contains the path of the file I have used the script through the right-click menu....

---

### Post by codemaniac on 2012-05-06
> **hakermania said:**
> Hello and thanks for the help. I disagree with many points in your answer:
a) using ` ` inside commands so as to take the output is old technique, the new one is to place it between $()

b) Also, one should not use this inside a for loop. It should be
```

for i in *.png

```

c) I don't want to take every single png image in a directory and alter it. The code I provided will run from a nautilus-script, placed under ~/.gnome2/nautilus-scripts/ so as to be available under the right click menu, when I click on a png file, for example. The variable NAUTILUS_SCRIPT_SELECTED_FILE_PATHS contains the path of the file I have used the script through the right-click menu....

Forgive my old coding styles , The idea was to call gimp on iteration .

---

### Post by Bachstelze on 2012-05-06
What are the contents of $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS?

---

### Post by hakermania on 2012-05-06
> **Bachstelze said:**
> What are the contents of $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS?
If I add an echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > ~/Desktop/asdf
then cat ~/Desktop/asdf, gives:
```

/home/alex/Desktop/1.png

```

---

### Post by Bachstelze on 2012-05-06
Then why are you removing the last character?

---

### Post by codemaniac on 2012-05-06
```
path=${path%?}
```
Are you sure you want the above in your script ?

---

### Post by hakermania on 2012-05-06
> **Bachstelze said:**
> Then why are you removing the last character?
+@codemaniac

When 'Round Corners' script contains:
```

#!/bin/bash
path=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
echo $path > ~/Desktop/asdf
path=${path%?}
echo $path >> ~/Desktop/asdf
gimp -i -f -d -b \'(round_the_corners "$path")\' -b "(gimp-quit 0)" 2> /home/alex/Desktop/asdf

```
then
/home/alex/Desktop/asdf contains:
```

/home/alex/Desktop/1.png
/home/alex/Desktop/1.png

```
I had a problem if I didn't remove the last characer, it's like a \n or something, not sure what.
It doesn't change the string in any 'physical' way...

---

### Post by Bachstelze on 2012-05-06
Maybe there's something else, then. Do a hexdump of your text file to make sure you don't have other invisible characters in there.

---

### Post by hakermania on 2012-05-06
```

alex@MaD-pc:~/Desktop$ hexdump asdf
0000000 682f 6d6f 2f65 6c61 7865 442f 7365 746b
0000010 706f 312f 702e 676e 2f0a 6f68 656d 612f
0000020 656c 2f78 6544 6b73 6f74 2f70 2e31 6e70
0000030 0a67                                   
0000032
alex@MaD-pc:~/Desktop$ cat asdf
/home/alex/Desktop/1.png
/home/alex/Desktop/1.png

```

Thanks again.

---

### Post by Bachstelze on 2012-05-06
Looks like it oes not change the string in *any* way, because the two strings are the same...

---

### Post by hakermania on 2012-05-06
Ok then.
Anyway, the path is correct, what the real problem in the script is that I cannot use '$' for variables inside the single quote that is needed....
```

#doesn't work:
gimp -i -f -d -b '(round_the_corners "$path")' -b "(gimp-quit 0)"
#works:
gimp -i -f -d -b '(round_the_corners /home/alex/Desktop/1.png)' -b "(gimp-quit 0)"

```

---

### Post by codemaniac on 2012-05-06
> **hakermania said:**
> Ok then.
Anyway, the path is correct, what the real problem in the script is that I cannot use '$' for variables inside the single quote that is needed....
```

#doesn't work:
gimp -i -f -d -b '(round_the_corners "$path")' -b "(gimp-quit 0)"
#works:
gimp -i -f -d -b '(round_the_corners /home/alex/Desktop/1.png)' -b "(gimp-quit 0)"

```

Single quote is making bash blind about your path variable , it is being treated as literal and bash cannot substitute with the actual  $path value .Can you try double quotes instead of single ones .

---

### Post by hakermania on 2012-05-07
> **codemaniac said:**
> Single quote is making bash blind about your path variable , it is being treated as literal and bash cannot substitute with the actual  $path value .Can you try double quotes instead of single ones .

I've tried it, it doesn't work :(

---

### Post by Arndt on 2012-05-07
> **hakermania said:**
> I've tried it, it doesn't work :(

What does your attempt look like?

---

### Post by hakermania on 2012-05-07
> **Arndt said:**
> What does your attempt look like?
Here you go:
[http://i.imgur.com/ssXY9.png](http://i.imgur.com/ssXY9.png)

---

### Post by Arndt on 2012-05-07
> **hakermania said:**
> Here you go:
[http://i.imgur.com/ssXY9.png](http://i.imgur.com/ssXY9.png)

A string delimited with " starts at one " and ends at the next one, so a string or sequence of strings like this
```
           "abc"def"ghi"
```
does not contain
```
           abc"def"ghi
```
but instead
```
           abcdefghi
```

In order to make the middle " stay and be treated as string delimiters by the shell, you must quote them, with the \ character:
```
           "abc\"def\"ghi"
```

---

### Post by Vaphell on 2012-05-07
try switching ' and " around.
```
gimp -i -f -d -b "(round_the_corners '$path')" -b "(gimp-quit 0)"
```

gimp would see this
```
$ path=1.jpg
$ echo "(round_the_corners '$path')"
(round_the_corners '1.jpg')
```
currently with 2 pairs of double quotes you get this:
```
$ echo "(round_the_corners "$path")"
(round_the_corners 1.jpg)
```

outer "" will allow expanding $path which will be inside literal single quotes.
If that doesn't work for whatever reason, go with Arndt's advice and escape inner quotes

---

### Post by hakermania on 2012-05-07
> **Arndt said:**
> A string delimited with " starts at one " and ends at the next one, so a string or sequence of strings like this
```
           "abc"def"ghi"
```does not contain
```
           abc"def"ghi
```but instead
```
           abcdefghi
```In order to make the middle " stay and be treated as string delimiters by the shell, you must quote them, with the \ character:
```
           "abc\"def\"ghi"
```

Yep, that did it :DDDD

Few, that was a difficult, one.
The script now looks like this:
```

#!/bin/bash
path=$1
echo \"$path\"
gimp -i -f -d -b "(round_the_corners \"$path\")" -b "(gimp-quit 0)"

```Thank you very much for your help :)

Aaaand, lastly, the nautilus-script looks like this:

```

#!/bin/bash
path=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
path=${path%?}
gimp -i -f -d -b "(round_the_corners \"$path\")" -b "(gimp-quit 0)"

```
(yep, for some reason, the path=${path%?} is needed)

Please see this [http://gimpforums.com/thread-a-script-fu-rounded-corners-from-the-command-line](http://gimpforums.com/thread-a-script-fu-rounded-corners-from-the-command-line) if you are interested with the rounding corners script.

---


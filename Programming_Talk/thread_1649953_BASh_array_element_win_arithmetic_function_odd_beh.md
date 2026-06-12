---
title: "BASh: array element w/in arithmetic function odd behavior"
date: 2010-12-20
forum: Programming Talk
---

### Post by jamesisin on 2010-12-20
I am building a script to change time stamps in cue files.  I have managed to parse out the bit I need to convert from frames (ff) to milliseconds (nnn), but when I run the array element through the arithmetic function in bash I get an error.

Here is the section of script in question:

```
for (( i=0 ; i < ${#cuefind[@]} ; i++ )) ; do
   # path is cue iteration less file name
   cuefolder="${cuefind[i]%/*.*}"
   cat "${cuefind[i]}" | grep INDEX | awk -F':' '{print $3}' > /tmp/whyme2
   declare -a ff
      let ii=0
      while read ffline; do
         ff[$i]=$ffline
         echo "ffline is " $ffline
         nnn=$(( ( ffline * 1000 ) / 75 ))
         echo "nnn is " $nnn
         ((ii++))
      done < /tmp/whyme2
   done 
```

And here is the error I receive:

```
ffline is  00
")syntax error: invalid arithmetic operator (error token is "

```

Here is the script running without the variable in the equation (I just stuck in the real number 8 ) :

```
ffline is  00
nnn is  106
ffline is  38
nnn is  106
ffline is  38
nnn is  106
ffline is  56
nnn is  106
ffline is  38
nnn is  106
ffline is  38
nnn is  106
ffline is  28
nnn is  106
ffline is  38
nnn is  106
ffline is  19
nnn is  106
ffline is  13
nnn is  106
ffline is  19
nnn is  106
ffline is  19
nnn is  106
ffline is  66
nnn is  106
ffline is  00
nnn is  106
ffline is  38
nnn is  106
ffline is  38
nnn is  106
ffline is  56
nnn is  106
ffline is  00
nnn is  106
ffline is  38
nnn is  106

```

Clearly the problem is in the array somehow.  I don't have the variable quoted which I think is fine because each element is just a two digit number, so I'm confused where the equation is bumping into a quotation mark.

A little help?

---

### Post by jamesisin on 2010-12-20
Maybe this additional information will be useful:

```
$ x=1000
$ new=$(( x * 3 ))
$ echo $new
3000
$ new=$(( ( x * 3 ) / 5 ))
$ echo $new
600
$ cat /tmp/whyme2
00
38
38
56
38
38
28
38
19
13
19
19
66
00
38
38
56
00
38
$ 

```

---

### Post by jamesisin on 2010-12-21
Also, I tried including the dollar sign on the variable (even though within the double-parenthetical equations you are not supposed to) and received a slightly different error:

```
ffline is  00
 * 1000 ) / 75 ")syntax error: invalid arithmetic operator (error token is "

```

Does any of this make sense?

I don't use these mathematical functions much.

I know I have the equation correct because it works outside the script.  It's just that in the script I get this error (when using the variable—if I substitute the number 8 I get exactly the same as posted above).

---

### Post by gmargo on 2010-12-21
Your input file, /tmp/whyme2, is probably in DOS format (CR/LF line endings). Correct it to UNIX format (LF line endings) and your code works.

---

### Post by jamesisin on 2010-12-21
That seems odd.  The temp file is created from standard out (using the > in BASh) on an Ubuntu system.  Is there a systemic way to force the other type?

```
cat "${cuefind[i]}" | grep INDEX | awk -F':' '{print $3}' > /tmp/whyme2
```

---

### Post by gmargo on 2010-12-21
First check if my supposition was right.  Use **xxd** to dump your file and verify the line endings.  I'm guessed this was the problem since that's the only way I managed to generate your error.

---

### Post by jamesisin on 2010-12-22
Here's the hex-dump:

```
$ xxd /tmp/whyme2
0000000: 3030 0d0a 3338 0d0a 3338 0d0a 3536 0d0a  00..38..38..56..
0000010: 3338 0d0a 3338 0d0a 3238 0d0a 3338 0d0a  38..38..28..38..
0000020: 3139 0d0a 3133 0d0a 3139 0d0a 3139 0d0a  19..13..19..19..
0000030: 3636 0d0a 3030 0d0a 3338 0d0a 3338 0d0a  66..00..38..38..
0000040: 3536 0d0a 3030 0d0a 3338 0d0a            56..00..38..

```

So, yes, that looks like the DOS interpretation of Enter.  So how can I force standard out to print only the 0a into the file?

---

### Post by gmargo on 2010-12-22
There are many ways.  Here are three:

[LIST=1]
[*]Add this to pipeline:
```

sed 's/\r//'

```
[*]Or, add this to pipeline:
```

perl -n -e 's/[[:space:]]+\z//s; print "$_\n"'

```
[*]Or, add this to pipeline (from the **tofrodos** package):
```

fromdos

```
[/LIST]

---


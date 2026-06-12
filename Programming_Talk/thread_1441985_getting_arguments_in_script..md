---
title: "getting arguments in script."
date: 2010-03-29
forum: Programming Talk
---

### Post by piyush.neo on 2010-03-29
i have to implement find function of shell with script. So i need to take arguments like find -s 200 -m 3
I am using getopts for this...
find -n file -s 20
```

while getopts n:s:v OPTION; do

     case "$OPTION" in
        n) echo "N" ;;
        s) echo "S";;
        esac
done


$N
S
$

```
this script is working fine for selecting the arguments but as soon as i am using "set" in any of the case its not working properly then...as
```

while getopts n:s:v OPTION; do

     case "$OPTION" in
        n) echo "N";set `who` ;;
        s) echo "S";;
        esac
done


$N
$

``` 
Can u suggest some idea so that i can use getopts as well as "set" in cases

---

### Post by gmargo on 2010-03-29
I think you're confused about using 'set'.  'set' is for setting shell options, not setting variables.  Anyway, here's a bit of getopts code that will get you started:

```

USAGE="$0 [-n file] [-s num] [-v]"
N=""
S=""
V=0
while getopts n:s:v OPTION
do
    case "$OPTION" in
    n)      N="$OPTARG"
            echo "N=$N"
            ;;

    s)      S="$OPTARG"
            echo "S=$S"
            ;;

    v)      V=1
            echo "V=$V"
            ;;

    \?)     echo $USAGE
            exit 1
            ;;
    esac
done


```

---

### Post by piyush.neo on 2010-03-29
yeah..this is working fine..but i need to use "set" command in my script and as soon as i am using it in any case of getopts..its spoiling it..

---

### Post by gmargo on 2010-03-29
What do you need to use set for?  "set `who`" is obviously wrong.  What are you trying to do?

---

### Post by piyush.neo on 2010-03-29
why it is wrong..?? my script demand that...well that not point..
Point is if i can somehow use the set without spoiling getopts..though i have implemented my script other way but still is there a solution to use to "set"???

---

### Post by gmargo on 2010-03-29
Please explain what you are trying to do with 'set'?  It looks like you want to use 'set' to set the positional parameters, which is what you are parsing with getopts. So it's no wonder that the getopts loop breaks.

---

### Post by piyush.neo on 2010-03-30
i have to implement shell's find command with ls,grep,sort etc (not awk)..
i have taken the o/p of ls -R| grep ^d (to select all directories recursively) now i want to pass each dir as argument to ls command to view files of each dir(so in output i can print the whole path of file ).So
set `ls -R| grep ^d|tr '/n' ' '`
loop
{
ls $1
shift
#other stuff
}

---

### Post by gmargo on 2010-03-30
> 
set `ls -R| grep ^d|tr '/n' ' '`
Now I understand.  There are several solutions.  If you absolutely insist on using 'set' in this manner, then simply delay the 'set' until after you are finished parsing the original command line options.  But you could also iterate over the list directly, or store the list in an array or temporary file, and then iterate over each entry.  (And... suddenly this sounds like homework, so I should probably shut up now.) :cool:

---

### Post by cubeist on 2010-03-30
hmmm, this sounds like a homework assignment... no other logical reason why you *have* to use set.  Only a teacher/prof would make you solve a problem in the weirdest way possible!

---

### Post by piyush.neo on 2010-03-30
Right..its homework and i have already implemented the other way....but just for the sake it clicked my mind and want to know how to use "set" that way...it helps to understand the underlying implementation...:)
Thanks u people...

---

### Post by cubeist on 2010-03-30
[COLOR="Red"]
Edit - Removed some of my comments -- Sorry, my comments were harsher than I had intended.  #-o[/COLOR]

Next time, it would be considerate if you disclose right up front that you are working on a homework problem. Tell us why you can't solve the problem, and we will provide hints, but not solutions.

From the forum rules:
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---


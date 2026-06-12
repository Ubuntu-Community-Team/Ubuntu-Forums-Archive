---
title: "Bash scripting"
date: 2009-10-23
forum: Programming Talk
---

### Post by docetes on 2009-10-23
Hi Guys,


quick question

i have a text file:


```
<AAAAA><BBBBBBBBBB><CCCCCCCCCC><DDDDDDDDD><EEEEEEEE><FFFFFFFFf><GGGGGGGG>
<AAAAA><BBBBBBBBBB><CCCCCCCCCC><DDDDDDDDD><EEEEEEEE><FFFFFFFFf><GGGGGGGG>
<AAAAA><BBBBBBBBBB><CCCCCCCCCC><DDDDDDDDD><EEEEEEEE><FFFFFFFFf><GGGGGGGG>
```

which i feed into my script

```
#!/bin/bash
INPUT="$1"

if [ -f temp.txt ];then
rm temp.txt
fi

# the while loop, read one char at a time
while IFS= read -r -n1  c
do
	if [ "$c" = "<" ];then 
	tr '[A-Z]' '[a-z]' >> temp.txt
	fi
done < "$INPUT"
```

but I get the output


```
aaaaa><bbbbbbbbbb><cccccccccc><ddddddddd><eeeeeeee><fffffffff><gggggggg>
<aaaaa><bbbbbbbbbb><cccccccccc><ddddddddd><eeeeeeee><fffffffff><gggggggg>
<aaaaa><bbbbbbbbbb><cccccccccc><ddddddddd><eeeeeeee><fffffffff><gggggggg>
```


why am i missing the 1st "<" on the first line?

Thanks,
Dave

---

### Post by dwhitney67 on 2009-10-23
The tr utility copies the standard input to the standard output with substitution or deletion of selected characters.

Since the 'read' already has removed the '<' from standard in, the tr utility cannot see it.  Perhaps you should consider outputting the character manually, or if possible, put the character back onto the standard input stream.

---

### Post by ghostdog74 on 2009-10-23
what do you intend to do ? you want to change ALL alphabets to lower case? if yes, then just  one tr will do..
```

# tr '[A-Z]' '[a-z]' < file
<aaaaa><bbbbbbbbbb><cccccccccc><ddddddddd><eeeeeeee><fffffffff><gggggggg>
<aaaaa><bbbbbbbbbb><cccccccccc><ddddddddd><eeeeeeee><fffffffff><gggggggg>
<aaaaa><bbbbbbbbbb><cccccccccc><ddddddddd><eeeeeeee><fffffffff><gggggggg>


```

---

### Post by docetes on 2009-10-23
no I only want to change the letters between < and > to lower case. I know my script doesn't do that yet but I'm just starting :)

---

### Post by dwhitney67 on 2009-10-23
This removes the <> brackets; is that what you want?

Perhaps you should augment your example input file and show what you would expect the results to look like:

```

#!/bin/bash

INPUT=$1
OUTPUT=temp.txt

if [ -f $OUTPUT ]
then
        rm -f $OUTPUT
fi

while IFS= read -r -n1 c
do
        if [ "$c" == "<" ]
        then
                tr '[A-Z]' '[a-z]' | tr -d '[<>]' >> $OUTPUT
        fi
done < "$INPUT"

```

Or perhaps you wanted:
```


INPUT=data.txt
OUTPUT=temp.txt

if [ -f $OUTPUT ]
then
        rm -f $OUTPUT
fi

while IFS= read -r -n1 c
do
        if [ "$c" == "<" ]
        then
                echo -n "<" >> $OUTPUT
                tr '[A-Z]' '[a-z]' >> $OUTPUT
        fi
done < "$INPUT"

```

---

### Post by ghostdog74 on 2009-10-23
> no I only want to change the letters between < and > to lower case. I know my script doesn't do that yet but I'm just starting

then your input file is misleading....your input file should be similar to this
```

# more file
<AAAAA>DONT CHANGE<BBBBBBBBBB>DONT CHANGE<CCCCCCCCCC>DONT CHANGE<DDDDDDDDD>DONT CHANGE<EEEEEEEE>DONT CHANGE<FFFFFFFFf>DONT CHANGE<GGGGGGGG>
<AAAAA>DONT CHANGE<BBBBBBBBBB>DONT CHANGE<CCCCCCCCCC>DONT CHANGE<DDDDDDDDD>DONT CHANGE<EEEEEEEE>DONT CHANGE<FFFFFFFFf>DONT CHANGE<GGGGGGGG>
<AAAAA>DONT CHANGE<BBBBBBBBBB>DONT CHANGE<CCCCCCCCCC>DONT CHANGE<DDDDDDDDD>DONT CHANGE<EEEEEEEE>DONT CHANGE<FFFFFFFFf>DONT CHANGE<GGGGGGGG>


```


for text manipulation, parsing files, formatting output and etc, use awk. 
```

#!/bin/bash
awk 'BEGIN{
 FS=">"
}
{
 for(i=1;i<=NF;i++){
    match($i,"<")
    $i = substr($i,1,RSTART-1) tolower(substr($i,RSTART))
 } 
}1' OFS=">" file


```

output
```

#
# ./shell.sh
<aaaaa>DONT CHANGE<bbbbbbbbbb>DONT CHANGE<cccccccccc>DONT CHANGE<ddddddddd>DONT CHANGE<eeeeeeee>DONT CHANGE<fffffffff>DONT CHANGE<gggggggg>
<aaaaa>DONT CHANGE<bbbbbbbbbb>DONT CHANGE<cccccccccc>DONT CHANGE<ddddddddd>DONT CHANGE<eeeeeeee>DONT CHANGE<fffffffff>DONT CHANGE<gggggggg>
<aaaaa>DONT CHANGE<bbbbbbbbbb>DONT CHANGE<cccccccccc>DONT CHANGE<ddddddddd>DONT CHANGE<eeeeeeee>DONT CHANGE<fffffffff>DONT CHANGE<gggggggg>


```

---


---
title: "how should I read files LINE BY LINE"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by just_linux on 2008-08-10
ok here: 
I want to read a text file LINE BY LINE and put it in a array like :
i am here
are you there?
who is -- this 
whwhw whw whwww   w w w                               w w
...
 become :
list [0] = "i am here"
list [1] = "are you there"
...

But the issue is that I get work WORD PER WORD by looping ::lolflag:

                          ```
  dos2unix address
                                    for element in $(cat address);
				
                                       do
					i=`expr 1 + $i`
					list[$i]="$element" 
				done
```

Please help 
Thanks :guitar:

---

### Post by DGortze380 on 2008-08-10
> **just_linux said:**
> ok here: 
I want to read a text file LINE BY LINE and put it in a array like :
i am here
are you there?
who is -- this 
whwhw whw whwww   w w w                               w w
...
 become :
list [0] = "i am here"
list [1] = "are you there"
...

But the issue is that I get work WORD PER WORD by looping ::lolflag:

                          ```
  dos2unix address
                                    for element in $(cat address);
				
                                       do
					i=`expr 1 + $i`
					list[$i]="$element" 
				done
```

Please help 
Thanks :guitar:

I think you'll need to use awk for that. I haven't worked with it that much, but a quick google search should yield some good results.

There is a read command, but it is white space delimited so in your cause it would read word by word.


EDIT: This syntax is probably wrong, and there may be a more efficient way to do it. But this is a start.

```

awk '{print $1,$2,$3,$4)}'

```

So if the line is: "I Want To Read This Line"

The above code would print to the screen: "I Want To Read"

---

### Post by Pro-reason on 2008-08-10
Here is something you could adapt to your purpose:

```

#!/bin/bash

while read line
    do
        let count=$count+1
        echo "$line" > $2$count.txt
    done < "$1"

```

Save it as *read.sh*.

Then save this:

```

Hello world
Nice day today
is it not?

```

...as *input.txt*.

Then run this:

```

bash read.sh input.txt output

```

You'll get a file called "*output1.txt*" containing "*Hello World*". a file called "*output2.txt*" containing "*Nice day today*", etc.

---


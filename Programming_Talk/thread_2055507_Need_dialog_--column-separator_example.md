---
title: "Need dialog --column-separator example"
date: 2012-09-09
forum: Programming Talk
---

### Post by Nathanael Culver on 2012-09-09
While there are lots of tutorials and references to the tha man page explaining the syntax of the [FONT="Courier New"]--column-separator[/FONT] option for [FONT="Courier New"]dialog --menu,[/FONT] I can't find any examples that use it, nor can I make it work in my own code. The man page says

```
--column-separator <string>
```

but I can't figure out whether <string> should be wrapped in quotes, and where and how it should be inserted in the menu definition. This works:

```

#!/bin/bash

    dialog --title " Welcome to My Menu! " \
           --menu "" 19 40 12              \
                   "1" "Option One"        \
                   "2" "Option Two"        \
                   "3" "Option Three"      \
                   "4" "Option Four"       \
2>temp
Cancelled=$?
Choice=`cat temp` ; rm temp
if [ $Cancelled -eq 0 ] 
  then echo "You selected: $Choice"
  else echo "You cancelled!"
fi

```

But when I try to add a column separator:

```
#!/bin/bash

    dialog --title " Welcome to My Menu! " \
           --column-separator "@"          \
           --menu "" 19 40 12              \
                   "1" "Option One"        \
                   "2" "Option Two"        \
"@"                "3" "Option Three"      \
                   "4" "Option Four"       \
2>temp
Cancelled=$?
Choice=`cat temp` ; rm temp
if [ $Cancelled -eq 0 ] 
  then echo "You selected: $Choice"
  else echo "You cancelled!"
fi

```
It fails. Can someone provide me with an example? Thanks.

--Nathanael

---

### Post by conradin on 2012-09-10
--column-separator is only for radio or "check boxes" which, I believe is the same as the documented checklist boxes... so maybe that option isn't usable in the way youre attempting. 
heres a article i liked:
[http://www.linuxjournal.com/article/2807](http://www.linuxjournal.com/article/2807)

Also, when I ran the second bit of code, option one showed "nfo"
after it. I took out the floating "@"
Im not sure if nfo is some sort of error code.


```

#!/bin/bash

    dialog --title " Welcome to My Menu! " \
           --column-separator "@"          \
           --menu "" 19 40 12              \
                   "1" "Option One"        \
                   "2" "Option Two"        \
                   "3" "Option Three"      \
                   "4" "Option Four"       \
2>temp
Cancelled=$?
Choice=`cat temp` ; rm temp
if [ $Cancelled -eq 0 ] 
  then echo "You selected: $Choice"
  else echo "You cancelled!"
fi

```

---

### Post by Nathanael Culver on 2012-09-10
> **conradin said:**
> --column-separator is only for radio or "check boxes" which, I believe is the same as the documented checklist boxes... so maybe that option isn't usable in the way youre attempting. 
heres a article i liked:
[http://www.linuxjournal.com/article/2807](http://www.linuxjournal.com/article/2807)

Yes, a good article. However, it doesn't show how to use the --column-separator option.

--column-separator does work for menu as well, but as it turns out not in the way I thought. I was expecting to be able to do column breaks *between* menu items, like this:

```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Menu! &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#9474;
&#9474; &#9474;1 Option One      5 Option Five   &#9474; &#9474;
&#9474; &#9474;2 Option Two      6 Option Six    &#9474; &#9474;
&#9474; &#9474;3 Option Three    7 Option Seven  &#9474; &#9474;
&#9474; &#9474;4 Option Four     8 Option Eight  &#9474; &#9474;
&#9474; &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; &#9474;
&#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
&#9474;       <  OK  >    <Cancel>           &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

however, it turns out column-separator is for creating columns *within* items, like this:

```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Menu! &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#9474;
&#9474; &#9474;1 Option One    1-2 buckle my sho &#9474; &#9474;
&#9474; &#9474;2 Option Two    Old MacDonald had &#9474; &#9474;
&#9474; &#9474;3 Option Three  Jack and Jill wen &#9474; &#9474;
&#9474; &#9474;4 Option Four   Old King Cole was &#9474; &#9474;
&#9474; &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; &#9474;
&#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
&#9474;       <  OK  >    <Cancel>           &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

Code for the above looks like this:

```
#!/bin/bash

dialog --title " Welcome to My Menu! " \
       --column-separator "|"          \
       --menu "" 6 0 0              \
               "1" "Option One | 1-2 buckle my shoe"        \
               "2" "Option Two | Old MacDonald had a farm"        \
               "3" "Option Three | Jack and Jill went up a hill"      \
               "4" "Option Four | Old King Cole was a merry old soul"       \
2>temp
Cancelled=$?
Choice=`cat temp` ; rm temp
if [ $Cancelled -eq 0 ] 
  then echo "You selected: $Choice"
  else echo "You cancelled!"
fi
```

Not what I was after, unfortunately. But I guess the question is solved.

--Nathanael

---


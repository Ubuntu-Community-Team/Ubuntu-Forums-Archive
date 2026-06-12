---
title: "and/or function with if/else script"
date: 2013-04-09
forum: Programming Talk
---

### Post by spiritech on 2013-04-09
i have the following code

```
echo "is this correct? type Y for yes or N for no"
read correct

 if [ $correct = y ]
      then echo "you typed yes"
      
 elif [ $correct = Y ]
      then echo "you typed yes"
      else echo "you typed no"
fi
```

can i combine the y and the Y into one if statement?

```
echo "is this correct? type Y for yes or N for no"
read correct

 if [ $correct = y or Y ]
      then echo "you typed yes"
      else echo "you typed no"
fi
```

spiritech

---

### Post by papibe on 2013-04-09
Hi spiritech.

I see a couple of approaches.

First, using a logical "or":
```
#!/bin/bash
echo -n "is this correct (type Y for yes or N for no)? "
read correct

if [ "$correct" = "y" -o "$correct" = "Y" ]; then
    echo "you typed yes"
else
    echo "you typed no"
fi

```
Or lowering the case of the answer, and do one test:
```
#!/bin/bash
echo -n "is this correct (type Y for yes or N for no)? "
read var

correct="${var,,}"

if [ "$correct" = "y" ]; then
    echo "you typed yes"
else
    echo "you typed no"
fi

```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by steeldriver on 2013-04-09
in modern bash, you could also look at the regex match operator **=~** although I think that only works within the extended test syntax [[ ... ]] e.g.

```
 if [[ "$correct" =~ (y|Y) ]]
```

or (using a character range)

```
 if [[ "$correct" =~ [yY] ]]
```

You can build up more complicated expressions like

```
if [[ "$correct" =~ ^([yY]|[yY][eE][sS])$ ]]
```

which matches a single y or Y or the whole word Yes in any combination of upper and lower cases Yes YES YeS etc.

---

### Post by spiritech on 2013-04-10
> **steeldriver said:**
> in modern bash, you could also look at the regex match operator **=~** although I think that only works within the extended test syntax [[ ... ]] e.g.

You can build up more complicated expressions like

```
if [[ "$correct" =~ ^([yY]|[yY][eE][sS])$ ]]
```

which matches a single y or Y or the whole word Yes in any combination of upper and lower cases Yes YES YeS etc.

thankyou for your help this does what i need, as do the other answers. it is nice to be able to use the character classes. i tested the above code as it was, and agian without the ^ $, it worked both times. from what i understand ^ means beginning of line and $ means from end of line, why is it used in this case?

---

### Post by steeldriver on 2013-04-11
Yes you've got it, the ^ and $ match the start and end of the string respectively - the idea is that they exclude things like 'OhYes' and 'Yessir' and ONLY match the isolated word [yY][eE][sS]

---

### Post by ofnuts on 2013-04-11
There is also the more readable:
```

    echo "Answer:"
    read answer
    case $answer in
        yes|y|o|oui)
            echo "Affirmative!"
            ;;
        no|n|non)
            echo "Negative!"
            ;;
        *)
            echo "What ?"
            ;;
    esac

```

---

### Post by spiritech on 2013-04-11
> **steeldriver said:**
> Yes you've got it, the ^ and $ match the start and end of the string respectively - the idea is that they exclude things like 'OhYes' and 'Yessir' and ONLY match the isolated word [yY][eE][sS]

yes, thankyou.

---


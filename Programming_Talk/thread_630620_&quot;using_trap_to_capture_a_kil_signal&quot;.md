---
title: "&quot;using trap to capture a kil signal&quot;"
date: 2007-12-03
forum: Programming Talk
---

### Post by nickoli on 2007-12-03
I have a program that has a loop in it and also uses case. I want to somehow embed trap "" 2 so that I can hit control c while running the program without killing the program I've tried several approaches but no avail. Is there anyway to embed trap in my program so it will capture ctrl c. here is my last attemp at solving this problem.

 
bash-2.04$ more shorty
#### function
function nokill
{
        trap "" 2
}

$(nokill)
echo Choice\?
read input

while [ "$input" != "stop" ] 
do
$(nokill)
case $input
in
         [0-9]* ) echo Positive Integer
                echo input
                read input ;;

        -[0-9]* ) echo Negative Number
                 echo input
                 read input ;;
        date    ) date
                 echo input
                 read input ;;
[Ss][Tt][Oo][Pp]) exit 0 ;;
            *   ) echo "Boldly goes where no man has gone before!"
                 echo input
                 read input ;;
esac

done

---

### Post by dwhitney67 on 2007-12-04
```
#!/bin/sh

function nokill
{
  trap "" 2
}

nokill

input=runforever
while [ "$input" != "stop" ]
do
        echo -n "Choice? "
        read input

        case $input in
                [0-9]* ) echo Positive Integer inputted;;

                -[0-9]* ) echo Negative Number inputted;;

                date) date;;

                [Ss][Tt][Oo][Pp]) exit 0 ;;

                * ) echo "Boldly goes where no man has gone before!";;
        esac
done
```

P.S.  The function is not really needed; a call to trap at the beginning of the program would have sufficed.

---

### Post by nickoli on 2007-12-05
Thanks for your time and help in that matter it worked. I can hit ctrl c and it dosn't kill it thanks.:guitar:

---


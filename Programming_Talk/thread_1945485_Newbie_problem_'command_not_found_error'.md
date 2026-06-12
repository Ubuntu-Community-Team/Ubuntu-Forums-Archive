---
title: "Newbie problem: 'command not found error'"
date: 2012-03-23
forum: Programming Talk
---

### Post by DirkRenegade on 2012-03-23
I enter:
[B]
#!/bin/bash
echo "average program: enter 10 numbers for mean average" 
[/B][B]nm2=1
for i in 1 2 3 4 5 6 7 8 9 10
do
if test "$1" = "noplay"
    then 
    exit
fi
if test "$1" = "play"
    then
    echo -e "\nprint enter number $i"
    read nm
    nm2=$[nm+nm2]
    echo -e "\n$nm2 is the total"
    mean=$[nm2/10]
    echo "$mean is the mean"
fi
if test "$mean" -ge "30" | "$mean" -le "50"
    then
    echo "your mean in between 30 and 50"
elif test "$mean"  -gt "100"
    then
    echo "your mean is greater than 100"
else 
    echo "your mean is not in between 30 and 50, or greater than 100"
fi
done
[/B]
it runs as i expected but i also get this error:

**./average.sh: line 19: 0: command not found**

the '0' in the error is a representation of the mean - as the program runs it changes as the mean changes, so the error is equal to $mean.

I would very much appreciate any help as I am obviously a padwan learner in search of a jedi...please ignore the dumb nature of the program...

---

### Post by r-senior on 2012-03-23
> ```
if test "$mean" -ge "30" | "$mean" -le "50"
then
    echo "your mean in between 30 and 50"
```
You want an && in here don't you? You want the mean to be greater than 30 **and** less than 50.

You also need another 'test' before the second test, i.e. if test <expr> && test <expr>.

The calculation of the running mean is wrong, but I'm going to assume that's because you haven't been able to test it properly.

Not quite sure I understand the point of the play/noplay argument. If I didn't want to play, why would I run the program in the first place? ;)

```
./average.sh noplay
```

ps. Please use code tags (see the '#' button in the posting toolbar). These will preserve indentation.

---

### Post by DirkRenegade on 2012-03-23
Thanks for your advice r-senior. There is no point play/no play- i'm just trying out new stuff in a dumb program! This will not be a useful program ever. I'm totally new to shell scripting so i'm just a child at play really. I'm going to try out what you said and confirm whether it works or not.

---

### Post by DirkRenegade on 2012-03-23
yeah that did the trick...thanks! I'll also observe the code format rule next time...cheers.

---


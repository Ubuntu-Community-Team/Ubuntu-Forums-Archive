---
title: "Multiple ranges in one for loop in Bash"
date: 2016-06-28
forum: Programming Talk
---

### Post by motoperpetuo on 2016-06-28
I'm working through the tutorial at [http://ryanstutorials.net/bash-scripting-tutorial/bash-loops.php](http://ryanstutorials.net/bash-scripting-tutorial/bash-loops.php). As an exercise, I'm supposed to write a tic-tac-toe game in Bash. My game has the standard nine squares and looks like this:
```

me@mycomputer:~/bash/20160501/Ryans Tutorials/6$ ./tictactoe.sh

                              X X - 
                              - - - 
                              - - - 
                              
Choose a space [1-9] or q to quit: 

```
No Os yet because I haven't started coding the computer's part.

Each space's value (-,X, or O) is stored in an array, a. I'm working on this routine to tell when the human player has won. So far, it can only evaluate a win across the top row, that is, spaces 1, 2, and 3:

```

#Check if player has won
checkforplayerwin () {
threeinarow=0
for i in {1..3};do
        if [ "${a[$i]}" = "X" ]
        then
                ((threeinarow++))
        fi
done

if [ $threeinarow -eq 3 ]; then
        win=1
        fi
}

```

I could, of course, add another individual for loop for the other eight winning combinations of spaces but that seems inelegant. Does anyone know if there is some way I could check all of these ranges in one for loop, something like:
```

for i in ((1 2 3, 4 5 6, 7 8 9, 1 4 7, 2 5 8, 3 6 9, 1 5 9, 3 5 7));do

```

---

### Post by spjackson on 2016-06-29
I don't know how to do 'Multiple ranges in one for loop in Bash', however I don't see how this will help you. It may be possible to check all the lines in a single loop, though I can't think how, but I think any solution would be tortuous and 'unnatural'. The way I'd do this (in pseudo-code) is:
```

for each line in winning_lines
do
    check line
done

```
where 'check line' is essentially the loop you have already written but with parameters.

---

### Post by Habitual on 2016-06-29
I think an [array]("http://www.tldp.org/LDP/abs/html/arrays.html") may be better suited for "Multiple ranges"?
</opinion>

---


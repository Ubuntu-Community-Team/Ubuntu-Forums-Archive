---
title: "alternative to bash in tcsh"
date: 2011-10-19
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2011-10-19
Hi

I have following lines in bash, the lines are inside while
```

    if [[ "$2" == +([0-9]) ]]
    then     depth=$2
        shift
    else exit 1
    fi

```The code check wheather the $2 is a number with unless 1 digit

and I want to ask how can this be done in tcsh?

So far I tried everything that I could came up(and it was a lot of ideas) but none of it has worked.
I 've also googled a lot and find out that tcsh's "if" uses some glob-expresion when it comes to pattern, and I haven't been able to find something in the glob-expresions that would do the same stuff as that "if" above, I tried but I can't find solution on my own, so I am asking for your help.

Thanks.

---

### Post by Mr.Pytagoras on 2011-10-19
Hi again

I have solved it ;)
        ```
    if ( $i > $#argv ) then 
                exit 1
            endif
            expr "$argv[$i]" + 1 >& /dev/null
            if ($status != 0) then
                exit 1
            else
                set depth = $argv[$i]
                
            endif
```

the expr will try to add 1 to something in $argv[$i] and wheather it success or fail is stored in special shell variable $status and the first if is for the case when there is no input

---


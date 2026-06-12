---
title: "Bash shell reg expression for a number"
date: 2015-11-20
forum: Programming Talk
---

### Post by pkoukoulis-r on 2015-11-20
[COLOR=#000000][FONT=Arial]Hi[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]new to bash. Attempting to learn bash from a book I purchased "Pro Bash Programming" [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Here's the problem.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Attempting to verify a number and thought I'd use a simply regular expression, but I cannot understand why the following does not work:[/FONT][/COLOR]

```
[COLOR=#000000][FONT=Arial]$ echo $BASH_VERSION[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]4.3.42(1)-release[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ [[ 12 =~ [0-9] ]] && echo "Is a number"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Is a number[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ [[ 12a =~ [0-9] ]] && echo "Is a number"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Is a number[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]both show as a number[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If I use quotes then none of the following options results in true[/FONT][/COLOR]

```
[COLOR=#000000][FONT=Arial]$ [[ "12" =~ "[!0-9]" ]] && echo "Is a number"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ [[ "12" =~ "[0-9]" ]] && echo "Is a number"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ [[ "12a" =~ "[!0-9]" ]] && echo "Is a number"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]$ [[ "12a" =~ "[0-9]" ]] && echo "Is a number"[/FONT][/COLOR]

```
[COLOR=#000000][FONT=Arial]Could anybody explain the above behavior?[/FONT]

[/COLOR]

---

### Post by Vaphell on 2015-11-20
easy peasy

case 1 - you are asking whether there is a digit (single at that) which makes anything with a single digit pass even, things like x0xoxoxoxoxox, which can be confirmed by printing out ${BASH_REMATCH[@]} array that stores the result of the recent comparison

```
$ [[ 12 =~ [0-9] ]]; printf '%s\n' "${BASH_REMATCH[@]}"
1
$ [[ 12a =~ [0-9] ]]; printf '%s\n' "${BASH_REMATCH[@]}"
1
$ [[ x0oxoxoxoxoxooxoxo =~ [0-9] ]]; printf '%s\n' "${BASH_REMATCH[@]}"
0
```


If you want to match against the whole value, you need to use anchors ^ (start) and $ (end)

```
$ [[ 12 =~ ^[0-9]+$ ]]; printf '%s\n' "${BASH_REMATCH[@]}"
12
$ [[ 12a =~ ^[0-9]+$ ]]; printf '%s\n' "${BASH_REMATCH[@]}"
```

[0-9]+ enforces at least one (+) digit.


case 2 - by quoting the pattern you are not regexing, you are comparing against a fixed string

```

$ [[ 12 =~ "[0-9]+" ]]; printf '%s\n' "${BASH_REMATCH[@]}"

$ [[ 'aaa[0-9]+aaa' =~ "[0-9]+" ]]; printf '%s\n' "${BASH_REMATCH[@]}"
[0-9]+
```

---

### Post by pkoukoulis-r on 2015-11-20
many thanks, that makes sense....  !!

I came across the following:

#!/bin/bash


function is_integer()
case ${1#-} in
  *[!O-9]*) 1;;
  *) 0 ;;
esac




in a pdf I downloaded.
When I attempt to to test it as follows


var="12"
is_integer $var
echo $? $var 
var="12a"
is_integer $var 
echo $? $var 
 line 5: 1: command not found 127 
12
 line 5: 1: command not found 127 
12a

Could you help me understand the above?

---

### Post by Vaphell on 2015-11-20
the first thing to mention is that there are 2 flavors of pattern matching in bash. Regular expressions used only with [[ =~ ]] and globs used everywhere else, less potent than regexes (then there are extended globs that can be enabled with a shell option that are almost as good as fullblown regexes but almost nobody uses them)

case test uses globs and the code is supposed to test whether after the removal of a possible leading '-' a non-digit can be found, though the code is syntactically incorrect so it doesn't work


run this

```
#!/bin/bash

is_int_glob_1()  {
    case ${1#-} in              # ${1#-} removes leading (#) minus sign (-) from $1
        *[!0-9]*) return 1;;    # return failure if a non-digit can be found
        *) return 0;;           # return success otherwise
    esac
}

is_int_glob_2()  {
    ! [[ ${1#-} = *[!0-9]* ]]   # remove leading -, test for non-digit, negate the result with ! (glob edition)
}


is_int_regex_1()  {
    ! [[ ${1#-} =~ [^0-9] ]]    # remove leading -, test for non-digit, negate the result with ! (regex edition)
}


is_int_regex_2()  {
    [[ ${1} =~ ^-?[0-9]+$ ]]    # test directly: optional -, any non-empty sequence of digits
}


for fun in is_int_{glob,regex}_{1,2}
do
    for test in -12 12 12a 12.1
    do
         "$fun" "$test" && echo "$fun($test): True" || echo "$fun($test): False"
    done
    echo
done

```

---


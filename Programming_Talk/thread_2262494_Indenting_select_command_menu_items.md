---
title: "Indenting select command menu items?"
date: 2015-01-25
forum: Programming Talk
---

### Post by Anthony_Cunningham on 2015-01-25
Fairly new to writing scripts in Linux and I haven't been able to find out if this is possible. I would like to be able to indent the menu options
listed by the select command when building a menu.

My current test code for the select command is:-

```
PS3=$'\n\tWhich Java do you wish to use?'
    select opt in ${multiJava[@]}
    do
      if [[ -n ${opt} ]] ; then
        javaSelect=${opt}
        break
      fi
    done

```

Ideally for each menu item returned I would like to be able to choose a level of indentation such as can be accomplished with echo -e "\tSome text"
when displaying normal output from a script. 

Thanks!

---

### Post by Vaphell on 2015-01-25
your problem is that you haven't quoted $multijava[@] and as a result all the leading/trailing whitespace is stripped (unquoted **$**whatever = whitespace stripping, word splitting). Also the question is if you want the index indented too, or it's just about labels
Also, select can lay menu items out in columns, which makes 0 sense in indented menu and i don't know if you can influence its behavior. If you want full control, you may be forced to write your own solution where you print by hand just like you want it, eg

```
#!/bin/bash

menu=( $'option1'
       $'\toption 1-1'
       $'\toption 1-2'
       $'\t\toption 1-2-1'
       $'option2' )
       

while :
do
    i=0
    for m in "${menu[@]}"
    do
        printf -- '%d) %s\n' $(( ++i )) "$m"
    done

    read -p "choice: " opt
    if [[ -z $opt ]] || [[ $opt = *[^0-9]* ]] || (( opt>${#menu[@]} )) || (( opt==0 ))
    then
        printf "Improper value, try again\n\n"
        continue
    fi
    selected=${menu[opt-1]} # verbatim, with indentation
    read -r selected <<< "${menu[opt-1]}" 
    break
done

echo "selected option #$opt: '$selected'"
```

out

```
$ ./menu.bash
1) option1
2) 	option 1-1
3) 	option 1-2
4) 		option 1-2-1
5) option2
choice: a
Improper value, try again

1) option1
2) 	option 1-1
3) 	option 1-2
4) 		option 1-2-1
5) option2
choice: 0
Improper value, try again

1) option1
2) 	option 1-1
3) 	option 1-2
4) 		option 1-2-1
5) option2
choice: 4
selected option #4: 'option 1-2-1'
```

---

### Post by ofnuts on 2015-01-26
> **Vaphell said:**
>  If you want full control, you may be forced to write your own solution where you print by hand just like you want it

Methinks that if the OP gets picky about the aesthetics, he would be better inspired to use a more graphic UI (zenity, etc...). Line-mode menus are so previous millennium :)

---

### Post by Anthony_Cunningham on 2015-01-27
> **Vaphell said:**
> your problem is that you haven't quoted $multijava[@] and as a result all the leading/trailing whitespace is stripped (unquoted **$**whatever = whitespace stripping, word splitting). Also the question is if you want the index indented too, or it's just about labels
Also, select can lay menu items out in columns, which makes 0 sense in indented menu and i don't know if you can influence its behavior. If you want full control, you may be forced to write your own solution where you print by hand just like you want it, eg

```
#!/bin/bash

menu=( $'option1'
       $'\toption 1-1'
       $'\toption 1-2'
       $'\t\toption 1-2-1'
       $'option2' )
       

while :
do
    i=0
    for m in "${menu[@]}"
    do
        printf -- '%d) %s\n' $(( ++i )) "$m"
    done

    read -p "choice: " opt
    if [[ -z $opt ]] || [[ $opt = *[^0-9]* ]] || (( opt>${#menu[@]} )) || (( opt==0 ))
    then
        printf "Improper value, try again\n\n"
        continue
    fi
    selected=${menu[opt-1]} # verbatim, with indentation
    read -r selected <<< "${menu[opt-1]}" 
    break
done

echo "selected option #$opt: '$selected'"
```

out

```
$ ./menu.bash
1) option1
2)     option 1-1
3)     option 1-2
4)         option 1-2-1
5) option2
choice: a
Improper value, try again

1) option1
2)     option 1-1
3)     option 1-2
4)         option 1-2-1
5) option2
choice: 0
Improper value, try again

1) option1
2)     option 1-1
3)     option 1-2
4)         option 1-2-1
5) option2
choice: 4
selected option #4: 'option 1-2-1'
```

Thanks for the reply. I had problems when quoting the multiJava. It is build from a find command looking for possible JREs. When I quoted it in the select command it would add all elements in the array to a single item and selection in the subsequent menu. I tried many combinations and unquoted was the only way the listed each element as it's own menu item - including how I was quoting the find command. 

Great explanation on building own menu! I was wondering if I could indent each menu item from the select - for example with a tab - to align with output I had currently built. If this isn't possible with select I completely understand your sample of building a custom menu.

---

### Post by Anthony_Cunningham on 2015-01-27
> **ofnuts said:**
> Methinks that if the OP gets picky about the aesthetics, he would be better inspired to use a more graphic UI (zenity, etc...). Line-mode menus are so previous millennium :)

You spotted my OCD had kicked it ;-) Thanks for the suggestion I wasn't aware of zenity. I dont' think I need it for this project but will definitely come in handy in the future.

---

### Post by Vaphell on 2015-01-27
> Thanks for the reply. I had problems when quoting the multiJava. It is build from a find command looking for possible JREs. When I quoted it in the select command it would add all elements in the array to a single item and selection in the subsequent menu. I tried many combinations and unquoted was the only way the listed each element as it's own menu item - including how I was quoting the find command. 

any details? How are you looking for JREs and how exactly are you populating the menu?

---

### Post by Anthony_Cunningham on 2015-01-27
> **Vaphell said:**
> any details? How are you looking for JREs and how exactly are you populating the menu?

I don't access to the script right now, I'm certain what I had last as a test script was close to:-

```
multiJava=( "$(find ${javaSearchPaths} -executable -type f -name java -print 2>/dev/null | grep -i "/jre/bin")" )
oIFS=$IFS
IFS=$'\n'
PS3=$'\n\tWhich Java do you wish to use?'
  select opt in ${multiJava[@]}; do
    if [[ -n "${opt}" ]] ; then
      break
    fi
  done
  IFS=$oIFS

```

I read about using $IFS and this helped the situation. if I use a printf to show the multiJava array before the IFS it does list each element as I would expect. Other variations I tried
got tripped up on a install path with a space in it; the above helped with that too. Be gentle I'm fairly new to this :-)

---

### Post by Vaphell on 2015-01-27
another question, what is ${javaSearchPaths} because i smell word splitting here which i consider harmful. Is this something like
```
javaSearchPaths='/some/path /some/other/path'
```


quoting in select is not the problem, what you did creating your array can be reduced to
array=( "..." )
it will be a single item and not quoting it later makes word splitting kick in. The solution is not to do that, but to populate the array with proper elements.


assuming you have results on separate lines (some output example?) the most kosher way would be to use

```

# paths as proper array
javaSearchPaths=( '/some/path1/'
                  '/some/other path/no 2' )

# creating multiJava[] from the command output
readarray -t multiJava < <( find "${javaSearchPaths[@]}" -executable -type f -name java -print 2>/dev/null | grep -i "/jre/bin" )
```


example with echo instead of find:
```
$ readarray -t multiJava < <( echo $'something\n\tsomething else' )
$ printf '%s\n' "${multiJava[@]}"
something
	something else
$ select opt in "${multiJava[@]}"; do break; done
1) something
2) 	something else
#? 1
```

---

### Post by Anthony_Cunningham on 2015-01-30
> **Vaphell said:**
> another question, what is ${javaSearchPaths} because i smell word splitting here which i consider harmful. Is this something like
```
javaSearchPaths='/some/path /some/other/path'
```


quoting in select is not the problem, what you did creating your array can be reduced to
array=( "..." )
it will be a single item and not quoting it later makes word splitting kick in. The solution is not to do that, but to populate the array with proper elements.


assuming you have results on separate lines (some output example?) the most kosher way would be to use

```

# paths as proper array
javaSearchPaths=( '/some/path1/'
                  '/some/other path/no 2' )

# creating multiJava[] from the command output
readarray -t multiJava < <( find "${javaSearchPaths[@]}" -executable -type f -name java -print 2>/dev/null | grep -i "/jre/bin" )
```


example with echo instead of find:
```
$ readarray -t multiJava < <( echo $'something\n\tsomething else' )
$ printf '%s\n' "${multiJava[@]}"
something
    something else
$ select opt in "${multiJava[@]}"; do break; done
1) something
2)     something else
#? 1
```


Thank you for the guidance and input, this has been a great help, taught me a few more things and helped simply some code! All working perfectly! 

Thanks, Ant

---


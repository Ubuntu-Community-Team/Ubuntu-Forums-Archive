---
title: "sed - How to use the matched result"
date: 2014-01-26
forum: Programming Talk
---

### Post by frogwarrior on 2014-01-26
I'm making a script that will automatically start up (i.e. make the folders and files and stuff) websites for me, but the syntax is killing me. Heres the script:
```
#!/bin/bash
param['title']="Test site"
webDir="/var/www/test"
projectName="new_test_site"
projectDirName=${webDir}/${projectName}

mkdir -p $projectDirName

headvar=$(cat template.html | sed -e "s/~*~/${param
[*]}/g")
echo $headvar
```

heres template.html:
[HTML]<!DOCTYPE html>
<html>
<head>
<title>~title~</title>
<script type="text/javascript" src="//ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>[/HTML]

as you can see, ~title~ is in the HTML tag, so I need bash to replace it with param['title'], if I do this:
```
cat template.html | sed -e "s/~*~/${param['title']}/g"
```
it works (well kinda does, theres a bit of a glitch though), but I need the matched pattern to be the index of the array, but bash has a special meaning for array
[*] so I don't know how. My plan is to have loads of these ~variables~ which bash will replace with values from the params array. Whats the best way of doing this? Would I be better off using awk?

---

### Post by bluefrog on 2014-01-26
not sure i understand your logic but this might help you.
```
i=$(grep ~.*~ template.html | sed "s/.*~\(.*\)~.*/\1/")

echo $i
title

echo ${param[title]}
Test title

sed "s/\(.*\)~\(.*\)~\(.*\)/\1${param[$i]}\3/g" template.html 
<!DOCTYPE html>
<html>
<head>
<title>Test title</title>
<script type="text/javascript" src="//ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>

```

---

### Post by frogwarrior on 2014-01-27
That didn't solve my problem because it seems to have loaded a string into i, not an array. I found another forum talking about this exact problem, and heres a working solution someone came up with:
```
echo
echo "Using \${ template form and straight cvs form"
echo
OIFS=$IFS
IFS=";"
while read name val; do
    eval "tmpvars_$name=$val"
done <params.txt;
IFS=$OIFS
eval echo "\"$(cat html.txt)\""
unset ${!tmpvars_*}
```
I haven't a clue how it works yet, but it gets the job done.

---

### Post by bluefrog on 2014-01-27
an array index is a number, nothing else if not mistaken.

you have to think about what you want to achieve with what means/tools before coding

---

### Post by Vaphell on 2014-01-27
this working solution is all kinds of fugly. A rule of thumb: eval=bad

```
#!/bin/bash

declare -A param
param=( [title]=TitLe
        [abc]=AbC
        [def]=o.O )

sed -f <( [COLOR="#0000FF"]for key in ${!param[@]}; do printf 's/~%s~/%s/g\n' "$key" "${param[$key]}"; done[/COLOR] ) template.txt
```

param is declared as associative array where strings are allowed as keys, by default bash arrays are integer-indexed.
Colored part prepares a series of "s/~k~/param[k]/g" expressions that sed uses as an input file in 1 go. **<( ... )** is a pseudo-file so sed which requires files with -f param happily gobbles it and runs.

```
$ cat template.txt 
<!DOCTYPE html>
<title>[COLOR="#0000FF"]~title~[/COLOR]</title>
[COLOR="#0000FF"]~abc~[/COLOR] [COLOR="#0000FF"]~def~[/COLOR] ghi
</html>
$ ./html_template.sh 
<!DOCTYPE html>
<title>[COLOR="#0000FF"]TitLe[/COLOR]</title>
[COLOR="#0000FF"]AbC[/COLOR] [COLOR="#0000FF"]o.O[/COLOR] ghi
</html>
```

---


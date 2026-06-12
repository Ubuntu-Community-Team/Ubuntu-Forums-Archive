---
title: "rename with mv not working in script..."
date: 2014-04-12
forum: New to Ubuntu
---

### Post by Little_Nooby on 2014-04-12
Hey,

So, I can  rename a file with mv without problem in the terminal. But as I have to rename a huge amount of files, I'd like to make a script to do it. The problem is that the same command doesn't work in the script and I can't get to know why. 

Here is the script code : 
```
#!/bin/bash
n=$(echo $1|grep -o [0-9][0-9])
newn=0
let 'newn = n - 26'

newname=$(echo $1|sed 's/[0-9][0-9]/2.'$newn'/')

fullname=$(pwd)/$1
fullnewname=$(pwd)/$newname
echo $fullname
echo $fullnewname

mv $fullname $fullnewname
```

And here are the results (I added some mv command to show you it should work).

```
adrien@portable-adrien:/media/Adrien_DDE/Series/Code lyoko/Code Lyoko/Season 2$ mv -v Code\ Lyoko\ 27.ogm Code\ Lyoko\ 2.1.ogm 
`Code Lyoko 27.ogm' -> `Code Lyoko 2.1.ogm'
adrien@portable-adrien:/media/Adrien_DDE/Series/Code lyoko/Code Lyoko/Season 2$ mv -v Code\ Lyoko\ 2.1.ogm Code\ Lyoko\ 27.ogm 
`Code Lyoko 2.1.ogm' -> `Code Lyoko 27.ogm'
adrien@portable-adrien:/media/Adrien_DDE/Series/Code lyoko/Code Lyoko/Season 2$ nmchgr Code\ Lyoko\ 27.ogm 
/media/Adrien_DDE/Series/Code lyoko/Code Lyoko/Season 2/Code Lyoko 27.ogm
/media/Adrien_DDE/Series/Code lyoko/Code Lyoko/Season 2/Code Lyoko 2.1.ogm
mv: target `2.1.ogm' is not a directory
```

Any help is welcome, thank you.


P.S.: (alternatively, it is possible to use matching regexp with rename to make operation on it? Something like $rename 's/[0-9][0-9]/$MATCH-26/' Code*  #It should find the number and subtract 26.

---

### Post by sudodus on 2014-04-12
You should enclose the variables in double quotes. Otherwise it does not work with blanks in the names of files and directories

So
 
```
fullname="$(pwd)/$1"
```

and similar in the other command lines

---

### Post by Little_Nooby on 2014-04-12
Thank you, that was almost that! Enclose the result there didn't solve the problem, I had to do it a little further. Here is the script working :
#!/bin/bash
n=$(echo $1|grep -o [0-9][0-9])
newn=0
let 'newn = n - 26'

newname=$(echo $1|sed 's/[0-9][0-9]/'2.$newn'/')

mv "$1" "$newname"

---

### Post by Vaphell on 2014-04-12
> P.S.: (alternatively, it is possible to use matching regexp with rename to make operation on it? Something like $rename 's/[0-9][0-9]/$MATCH-26/' Code* #It should find the number and subtract 26. 

```
$ rename -nv 's/\d{2}/"2.".($&-26)/e' *
Code Lyoko 27.ogm renamed as Code Lyoko 2.1.ogm
```

with safeguard against numbers <= 26
```
$ rename -nv 's/\d{2}/$&>26?("2.".($&-26)):$&/e' *
Code Lyoko 27.ogm renamed as Code Lyoko 2.1.ogm
```

---


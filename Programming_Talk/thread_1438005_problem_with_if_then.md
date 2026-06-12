---
title: "problem with if then"
date: 2010-03-24
forum: Programming Talk
---

### Post by LuniTux on 2010-03-24
hello,

I am trying to create a bin bash script that will run python scripts that appear in a selected folder. the problem is that i can not seem to get the if statement to work properly.

Here is the code:

[COLOR="DarkRed"]cd[/COLOR] email/

[COLOR="#4169e1"]chkfiles[/COLOR]=`[COLOR="DarkOrchid"]test -f *.py &&[/COLOR] [COLOR="#8b0000"]echo[/COLOR] [COLOR="Magenta"]"FOUND"[/COLOR] [COLOR="DarkOrchid"]||[/COLOR] [COLOR="#8b0000"]echo[/COLOR] [COLOR="Magenta"]"NOT FOUND"[/COLOR]`
[COLOR="#8b0000"]if[/COLOR] [COLOR="#4169e1"]$chkfiles[/COLOR] = [COLOR="#ff00ff"]"FOUND"[/COLOR]
   [COLOR="#4169e1"]files[/COLOR]=`[COLOR="DarkRed"]ls[/COLOR] [COLOR="DarkOrchid"]*.py[/COLOR]`
   [COLOR="#8b0000"]if[/COLOR] [COLOR="#4169e1"]$files[/COLOR] [COLOR="#8b0000"]![/COLOR]= [COLOR="Magenta"]""[/COLOR]
      [COLOR="#8b0000"]for[/COLOR] [COLOR="#4169e1"]i[/COLOR] [COLOR="#8b0000"]in[/COLOR] [COLOR="#4169e1"]$files[/COLOR]
         [COLOR="#8b0000"]do[/COLOR]
            ./[COLOR="#4169e1"]$i[/COLOR] [COLOR="Blue"]#dont know if this part works yet[/COLOR]
      [COLOR="#8b0000"]done[/COLOR]
[COLOR="DarkRed"]fi[/COLOR]
[COLOR="#8b0000"]fi[/COLOR]

I get the error:

./Desktop/MyScript.sh: line 11: syntax error near unexpected token `fi'
./Desktop/MyScript.sh: line 11: `   fi'

and if i remove the "fi" statments:

./Desktop/MyScript.sh: line 11: syntax error: unexpected end of file

Is there something else i have to do with the if statment?

---

### Post by mIXpRo on 2010-03-24
i know tcsh scripting which will be : 

#! tcsh -f 

[COLOR=DarkRed]cd[/COLOR] email/

[COLOR=#4169e1]set chkfiles[/COLOR]=`[COLOR=DarkOrchid]test -f *.py &&[/COLOR] [COLOR=#8b0000]echo[/COLOR] [COLOR=Magenta]"FOUND"[/COLOR] [COLOR=DarkOrchid]||[/COLOR] [COLOR=#8b0000]echo[/COLOR] [COLOR=Magenta]"NOT FOUND"[/COLOR]`
[COLOR=#8b0000]if[/COLOR] ([COLOR=#4169e1]$chkfiles[/COLOR] == [COLOR=#ff00ff]"FOUND"[/COLOR]) then
   [COLOR=#4169e1]set files[/COLOR]=`[COLOR=DarkRed]ls[/COLOR] [COLOR=DarkOrchid]*.py[/COLOR]`
   [COLOR=#8b0000]if[/COLOR] [COLOR=#4169e1](${#files}[/COLOR] [COLOR=#8b0000]![/COLOR]= 0) then
      [COLOR=#8b0000]for[/COLOR]each [COLOR=#4169e1]i[/COLOR] [COLOR=#8b0000]in[/COLOR] [COLOR=#4169e1]$files[/COLOR]
            ./[COLOR=#4169e1]$i[/COLOR] [COLOR=Blue]#dont know if this part works yet[/COLOR]
      end
endif 
[COLOR=#8b0000]endif [/COLOR]

---

### Post by Johnny B on 2010-03-24
if statements are always followed by "then"
test conditions should be enclosed in square brackets

```
chkfiles=`test -f *.py && echo "FOUND" || echo "NOT FOUND"`
if [ $chkfiles = "FOUND" ] ;then
files=`ls *.py`
if [ $files != "" ] ;then
for i in $files
do
./$i #dont know if this part works yet
done
fi
fi
```

---

### Post by LuniTux on 2010-03-24
adding the then statments fixed the if problem but now i get and error on:

```
if $chkfiles = "FOUND"; then
```

./Desktop/MyScript.sh: line 3: FOUND: command not found

Is there some kind of special operator for comparing strings?

---

### Post by LuniTux on 2010-03-24
I figured it out:

```

chkfiles=`test -f *.py && echo "FOUND" || echo "NOT FOUND"`
if [ $chkfiles="FOUND" ]; then
   files=`ls *.py`
   if [ $files!="" ]; then
      for i in $files 
         do
            echo $i
      done
   fi
fi
```

I did not have the brackets for the string comparisons

---

### Post by mIXpRo on 2010-03-24
the comparison is == not =

---

### Post by rnerwein on 2010-03-24
hi
chkfiles=`test -f *.py && echo "FOUND" || echo "NOT FOUND"`

this works only if you got only 1 file with the ending .py in that directory.
if there are more .py ( *.py ) files you will get the error " test to much arguments or so "
ciao

---

### Post by LuniTux on 2010-03-25
Thanks for the tip. the problem now seems to be that i can not get the strings to compare correctly.
If there are files, the program runs but does not display anything. I check the variable [COLOR="RoyalBlue"]$chkfiles[/COLOR] and it returns "NOT_FOUND" even though there is a .py file in the location
```


chkfiles=`test -f *.py && echo "FOUND" || echo "NOT_FOUND"`
if [ [COLOR="Red"]$chkfiles=="FOUND"[/COLOR] ]; then
   files=`ls *.py`
echo $files
   if [ $files!=="" ]; then
      for i in $files 
         do
            echo $i
      done
   fi
fi


```

I forgot to add the extention to the python file when i saved it. the program works now but only for 1 file

---

### Post by mIXpRo on 2010-03-25
maybe your problem is with :

files=`ls *.py`

cause it stores just one file 
you have to make a list , something like that :

files=(`ls *.py`)

---

### Post by cubeist on 2010-03-25
Since we are offering advise, it is a good habit to stop using backticks (``) and start using double quotes.
```

chkfiles=$(test -f *.py && echo "FOUND" || echo "NOT_FOUND")
if [[ $chkfiles=="FOUND" ]]; then
   files=$(ls *.py)
echo $files
   if [[ $files!=="" ]]; then
      for i in $files 
         do
            echo $i
      done
   fi
fi
```

---

### Post by falconindy on 2010-03-25
> **mIXpRo said:**
> the comparison is == not =
Both are valid for a string comparison.

> **mIXpRo said:**
> maybe your problem is with :

files=`ls *.py`

cause it stores just one file 
you have to make a list , something like that :

files=(`ls *.py`)
Both will store the same resulting data. Storing to an array has, of course, the added advantage of easy retrieval of specific items.

---


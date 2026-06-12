---
title: "BASH: Referencing variables using variables"
date: 2011-10-27
forum: Programming Talk
---

### Post by Greeface on 2011-10-27
Not sure if I worded the title correctly.  It's easiest to explain with an example...

```

VAR="fail"
VAR1="cool"
VAR2="neat"

for i in 1 2 ;
do
echo $VAR$i
done
```

See what I'm trying to do there?  I need to combine the $VAR$i so instead of outputting "fail1" and "fail2" it outputs "cool" and "neat".

I tried various things such as $(VAR$i) but I'm just stumbling here.  Couldn't find anything on Google either.  Help a noob about?  Thanks.

---

### Post by Greeface on 2011-10-28
I think I got it.

```
$(eval "echo \$$(echo VAR${i})")
```

I don't really understand what's going on here, but oh well.

---

### Post by ofnuts on 2011-10-28
> **Greeface said:**
> Not sure if I worded the title correctly.  It's easiest to explain with an example...

```

VAR="fail"
VAR1="cool"
VAR2="neat"

for i in 1 2 ;
do
echo $VAR$i
done
```See what I'm trying to do there?  I need to combine the $VAR$i so instead of outputting "fail1" and "fail2" it outputs "cool" and "neat".

I tried various things such as $(VAR$i) but I'm just stumbling here.  Couldn't find anything on Google either.  Help a noob about?  Thanks.
Have you tried arrays?
```

>declare -A array
>array[1]='neat'
>array[2]='cool'
>echo "${array[1]} ${array[2]}"
neat cool

```

---

### Post by Vaphell on 2011-10-28
```
$ var1=value1
$ var2=value2
$ for i in 1 2; do tmp=var$i; echo $tmp **${!tmp}**; done
var1 **value1**
var2 **value2**
```

but i agree with ofnuts, arrays are more convenient because they know their size

```
$ arr=(v1 v2 v3 v4 v5)
$ for (( i=0; i<${#arr[@]}; i++ )); do echo $i ${arr[$i]}; done
0 v1
1 v2
2 v3
3 v4
4 v5
```

---

### Post by sisco311 on 2011-10-28
See: BashFAQ #006 (link in my signature). :evil:

---

### Post by Greeface on 2011-10-28
Thanks guys, some good info here.  Unfortunately these variables are being defined by HTML form info passed to the cgi script, so I can't really use an array to begin with.

If anyone cares here's what I'm doing currently:
```

NUM="0"
for FILE in $CONTENTS ;
do

let NUM++

ACTION=$(eval "echo \$$(echo FILE${NUM})")

echo "Perform $ACTION on $FILE, blah blah..."

done

```

It would be better to pass the filename through the HTML form rather than indexing them like this, but I couldn't figure out how to create the form and have it look nice.  Oh well, this works well enough.  Hacky scripting FTW.

---

### Post by Vaphell on 2011-10-28
> Thanks guys, some good info here. Unfortunately these variables are being defined by HTML form info passed to the cgi script, so I can't really use an array to begin with.

care to give a mini-example of your workflow and what your script is supposed to do? because i don't really get why the use of arrays is not possible.

either way, if you have to do a runtime evaluation, stick to ${!tmp_variable} form, at least it's cleaner than the hacky eval and it's right there in bash so you don't have call additional commands only to capture their output.

---

### Post by Greeface on 2011-10-29
Sure, I'll do my best to describe it.  This is a file management script for the file upload section on my personal server.  It uses a for loop to look at each of the files in the uploads directory and outputs an HTML table with the file listing.  This table is within a form and each file has a 'delete' and 'rename' button.  Here's the section that generates each row:

```
OUTPUT()
{
echo "<tr>"
echo "<td>`date +%D-%T -u -r $FILE`</td>"
echo "<td>$OWNER</td>"
echo "<td><a href=\"/auth/upload/$FILE\">$NAME</a></td>"
if [[ $OWNER = $REMOTE_USER ]] ;
then {
echo "<td><input type=\"submit\" name=\"FILE$NUM\" value=\"delete\" />"
echo "<input type=\"submit\" name=\"FILE$NUM\" value=\"rename\" /></td>"
}
else {
echo "<td><input type=\"submit\" name=\"FILE$NUM\" value=\"delete\" disabled />"
echo "<input type=\"submit\" name=\"FILE$NUM\" value=\"rename\" disabled /></td>"
}
fi
echo "</tr>"
}
```

Pressing a button passes the value back to the script through the variables $FILE1, $FILE2, etc.  Every time it runs my script checks to see if any of these variables are non-zero.  If it finds the value "rename" in one of them it brings up the rename dialog for that file, and same for "delete".

The use of an array isn't necessary since there's only ever one variable being passed to it.  I need a better HTML form.  If I could find a way to switch it around and pass the file number through the variable without changing the button's label then that would be ideal.  To clarify, the issue here is that the button's value is what it's labeled when you view the web page, so it wouldn't make sense to set it to the file number.  I realize now that I could just fix this by changing the buttons to images, I'll have to do that.  But this hacky solution works alright for now.

Thanks for tip on the ${!tmp_variable} thing, I'll swap that in for the time being.

---


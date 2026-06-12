---
title: "line replace using a variable in sed"
date: 2009-08-05
forum: Programming Talk
---

### Post by Glenn Jones on 2009-08-05
Hi guys,


I'm trying to replace a line in a file which I've stored to a vriable (I this case I shall call it var1) with another variable (var2). The majority of the script has been written using awk and sed in the c-shell. 

Ideally I would like to modify the original file and I've attempted to do this using the following sed command

sed -i 's/"$var1"/"$var2"/' $file

However when I try this nothing changes in the output file $file.

I have tried the command on the command line where I put $var1 and $var2 in explicitly. This does work so the problem is getting the script to read $var1 and $var2.

If anyone could help it will be much appreciated. I'm using gsed version 4.1.4 if thats any help

Thanks

---

### Post by Dill on 2009-08-05
Try enclosing the entire expression with quotation marks, like so:

```
sed -i "s/$VAR_1/VAR_2/g" $FILE
```

Cheers,
Dill

---

### Post by Glenn Jones on 2009-08-05
> **Dill said:**
> Try enclosing the entire expression with quotation marks, like so:

```
sed -i "s/$VAR_1/VAR_2/g" $FILE
```

Cheers,
Dill

Thanks Dill.

I've just given that command a go, but it gives me the following error:


```
gsed: -e expression #1, char 27: unknown option to `s'
```

and deletes $VAR_1 form $FILE

---

### Post by Dill on 2009-08-05
Hmm... the sed FAQ (Section 4.3) had another suggestion:

*For longer shell scripts, it is sometimes useful to begin with single quote marks ('), close them upon encountering the variable, enclose the variable name in double quotes ("), and resume with single quotes, closing them at the end of the sed script... *

```
sed -i 's/'"$HELLO"'/'"$WORLD"'/g'
```

See [Section 4 of the FAQ]("http://sed.sourceforge.net/sedfaq4.html") for more info.

Hope this helps... and I'm sorry that my first suggestion deleted your variable!

Cheers,
Dill

---

### Post by ghostdog74 on 2009-08-05
forget that quoting hell...
```

var1="hello"
var2="world"
awk -v var1="$var1" -v var2="$var2" '{
  gsub(var1,var2)
  print
}' file > temp
mv temp file

```

---

### Post by Glenn Jones on 2009-08-06
Unofrtunatley the sed commands don't seem to work however I do it. I have converted the script into bash to no avail. Not sure what the problem is but I get the following error 

```
gsed: -e expression #1, char 27: unknown option to `s'
```

where the sed command is 

```
gsed -i 's/'"$event"'/'"$dataPath"'/g' $file1
```

If anyone else has had this problem I'd be very interested in hearing if and how you overcame this. 

I'm now going to give the awk commands a go 

Cheers

---

### Post by uljanow on 2009-08-06
```
eval sed -i 's/$var1/$var2/' $file
```

---

### Post by ghostdog74 on 2009-08-06
> **uljanow said:**
> ```
eval sed -i 's/$var1/$var2/' $file
```

why the eval? there's no need to.

---

### Post by Dan675 on 2012-06-14
I was having the same problem, looks like mine was due to the fact that the variable I was trying to replace it with was a file path so there was extra forward slashes messing with the sed command.

```
sed "s/./$workingDirectory/"
```

I used a different delimiter

```
sed "s,.,$workingDirectory,"
```

And it worked, perhaps you where trying to do something similar.

---


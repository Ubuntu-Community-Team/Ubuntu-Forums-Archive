---
title: "Convert var1|var2|var3... to line / other?"
date: 2012-02-01
forum: Programming Talk
---

### Post by honeybear on 2012-02-01
Hi,

Into KSH, or AWK, I have a variable that contains undefined number of varX. who knows how much

```
MYVAR="var1|var2|var3..."
```

I would like to convert it to this format, that would ouput echo $mynewvariablecontent 

```
'var1','var2','var3'
```

would you have the possible solution? I have not managed :( The problem is that there is an undefined content of terms into MYVAR

Thank you very much

---

### Post by ofnuts on 2012-02-01
> **honeybear said:**
> Hi,

Into KSH, or AWK, I have a variable that contains undefined number of varX. who knows how much

```
MYVAR="var1|var2|var3..."
```I would like to convert it to this format, that would ouput echo $mynewvariablecontent 

```
'var1','var2','var3'
```would you have the possible solution? I have not managed :( The problem is that there is an undefined content of terms into MYVAR

Thank you very much

```

echo $MYVAR |  sed -e "s/^/\'/" -e "s/$/\'/" -e "s/|/\',\'/g"

```

---

### Post by sisco311 on 2012-02-01
The parameter expansion ${parameter/pattern/string} is not standard, but it seams to work in ksh:
```
printf '%s\n' \'${myvar//|/\',\'}\'
```

---

### Post by Vaphell on 2012-02-01
first two ofnuts' sed expressions can be squeezed into one
```
"s/^\|$/'/g"
"s/.*/'&'/"
```

or you can append ' in the *echo $VAR* step and skip first two entirely
```
echo \'$MYVAR\' | sed "s/|/\',\'/g"
```

---

### Post by honeybear on 2012-02-06
Thank you!!

I noticed that awk is bit more sured than sed... by experience. 

You helped.

---


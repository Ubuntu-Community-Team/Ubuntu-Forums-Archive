---
title: "Removing a block of text from a variable in a shell script"
date: 2008-11-29
forum: Programming Talk
---

### Post by SoCalChris on 2008-11-29
I have a string that I'm using in a shell script. How could I remove all text from that string that is within a set of parenthesis?

For example, in this code snippet, I would like to remove the parenthesis, and all text within the parenthesis, and return only "I want to keep this ".
```

myString="I want to keep this (But I want to remove this)"
echo $myString

```

Thanks

---

### Post by ghostdog74 on 2008-11-29
```

# str="I want to keep this (But I want to remove this)"
# echo ${str%%(*}
I want to keep this


```

---

### Post by slavik on 2008-11-29
I would do something like:

str="text (is) text (sometimes) ..."
echo $str | sed 's/\(.*\)//g'

---

### Post by ghostdog74 on 2008-11-29
> **slavik said:**
> I would do something like:

str="text (is) text (sometimes) ..."
echo $str | sed 's/\(.*\)//g'

that won't do. sed doesn't know about non-greediness.

---

### Post by SoCalChris on 2008-11-29
> **ghostdog74 said:**
> that won't do. sed doesn't know about non-greediness.

Yeah, slavik's code returns

"text ..."

How could I use the example you provided, assuming that there is still text that I want after the closing parenthesis?

Using slavik's example, I would like "text (is) text (sometimes) ..." to return "text  text  ..."

Thanks for both of your guy's help.

---

### Post by JohnFH on 2008-11-29
Try this:

```
echo $str | sed 's/([A-Z a-z]*) //g'
```

---

### Post by ghostdog74 on 2008-11-29
assuming no spaces in those brackets, you can go over each word one by one, testing each word for ( or )
```

var="text (is) text (sometimes) ..."
echo $var |awk '
{
    for(i=1;i<=NF;i++){ 
        if($i !~ /[)]/){
            print $i
        }
    }
}
'

```

other ways include using Perl/Python that uses regexp with non greedy support.

---

### Post by geirha on 2008-11-29
```
echo "$var" | sed 's/([^)]*)//g'
```

---

### Post by SoCalChris on 2008-11-30
> **geirha said:**
> ```
echo "$var" | sed 's/([^)]*)//g'
```

Thanks, this worked.

---

### Post by slavik on 2008-11-30
yes it does ...

echo "$var" | sed 's/\(.*?\)//g' #didn't have the '?' before

---

### Post by ghostdog74 on 2008-11-30
> **slavik said:**
> yes it does ...

echo "$var" | sed 's/\(.*?\)//g' #didn't have the '?' before

can you show your output, as it doesn't look right for me. I don't use sed often, but AFAIK, geirha's  solution is the way to go, at least for sed.

---

### Post by slavik on 2008-12-01
> **ghostdog74 said:**
> can you show your output, as it doesn't look right for me. I don't use sed often, but AFAIK, geirha's  solution is the way to go, at least for sed.
i fail at sed...

echo "$var" | perl -pen 's/\(.*?\)//g'

slavik@slavik-laptop:~$ echo "$var" | perl -pne 's/\(.*?\)//g'
this is  and more  elsewhere

---


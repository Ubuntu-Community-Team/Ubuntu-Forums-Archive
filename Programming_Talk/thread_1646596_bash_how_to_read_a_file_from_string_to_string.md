---
title: "bash: how to read a file from string to string?"
date: 2010-12-16
forum: Programming Talk
---

### Post by PryGuy on 2010-12-16
Good day everyone!

I have a file like this:
```
some data
%packages
the
lines
i
need
badly
%end
some data
```
Is it possible to read the lines that are between the %packages and %end tags?

Thanks in advance!

---

### Post by Arndt on 2010-12-16
> **PryGuy said:**
> Good day everyone!

I have a file like this:
```
some data
%packages
the
lines
i
need
badly
%end
some data
```
Is it possible to read the lines that are between the %packages and %end tags?

Thanks in advance!

```
sed -n '/%packages/,/%end/p'
```

That will keep the % lines, but you can get rid of them with 'grep', for example.

---

### Post by PryGuy on 2010-12-16
Thanks, pal! It's a job for sed as I expected. Thanks again!

[s]Small correction though:```
sed -n '/[COLOR="Red"]\[/COLOR]%packages/,/[COLOR="Red"]\[/COLOR]%end/p'[/s]
```
Sorry, my bad.

---

### Post by zobayer1 on 2010-12-16
cool, I was also looking for doing something like this, but didn't know about sed.
then I wrote this... which just stores the items in an array...
```

a=0
n=0
while read line
do
    if [ "$line" = "%packages" ]
    then
        a=1
    elif [ "$line" = "%end" ]
    then
        a=0
    elif [ "$a" = 1 ]
    then
        array[$n]="$line"
        n=$(($n+1))
    fi
done
echo "Final count: $n"
a=0
while [ $a -lt $n ]
do
    echo ${array[$a]}
    a=$(($a+1))
done

```

Thanks for showing the way with 'sed'

---

### Post by Arndt on 2010-12-16
> **PryGuy said:**
> Thanks, pal! It's a job for sed as I expected. Thanks again!

Small correction though:```
sed -n '/[COLOR="Red"]\[/COLOR]%packages/,/[COLOR="Red"]\[/COLOR]%end/p'
```

For me, it worked without escaping the %. What happens if you don't?

---

### Post by PryGuy on 2010-12-16
I get error.

---

### Post by Arndt on 2010-12-16
> **PryGuy said:**
> I get error.

What a wonderful answer. That much was already obvious. What error, exactly?

---

### Post by PryGuy on 2010-12-16
> **Arndt said:**
> What a wonderful answer. That much was already obvious. What error, exactly?Well, I'm sorry. I have a localized version, so I'm not sure how does it look like in English.
But the most interesting thing is that I tried to reproduce it now to see the bug and find an equivalent in English, but it worked without problems this time... ](*,)

---

### Post by Arndt on 2010-12-16
> **PryGuy said:**
> Well, I'm sorry. I have a localized version, so I'm not sure how does it look like in English.
But the most interesting thing is that I tried to reproduce it now to see the bug and find an equivalent in English, but it worked without problems this time... ](*,)

Those things happen.

---

### Post by PryGuy on 2010-12-16
Thanks again, pal! It really helped!

---


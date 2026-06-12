---
title: "Bash script"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by emp1953 on 2008-09-10
Newbie to bash scripting
Want a simple demo script that will:

At command line I want to enter  > scriptname 1    or scriptname 2    1 and 2 are parameters

 

The script should

 

If parameter $1 is 1 then echo The sky is blue

If parameter $1 is 2 then echo The sky is red

If parameter 1 is blank then echo The sky is dark. 
   (I'd rather test for the blank then have it be a default in the else) but I don't know how to test for blank)

 

Here&#8217;s what I have so far

#! /bin/bash
sel=$1
if [ $sel -eq 1  ]
then
      color=red
elif [ $sel -eq 2  ]
      color=blue
else
      color=dark
fi

echo The sky is $color
 

My unary operator &#8211;eq is not right   it is not = or ==   other unary operators are &#8211;lt &#8211;gt for less than and greater than.  With this failure I don't know if the rest is correct either
    Thanks for Any help

---

### Post by bodhi.zazen on 2008-09-10
I think you need to quote your variables :

if [ "$1" -eq "1" ]; then 
if [ "$sel" -eq "2" ]; then

Or use case :

```
case "$1" in
1 ) color=red
;;

2 ) color=blue
;;

* ) color=dark
;;
esac
```

---

### Post by emp1953 on 2008-09-10
Is -eq a valid unary operator?  I can't find a list of them.

In your suggested script what is the significance of the double ;;

Thanks

---

### Post by bodhi.zazen on 2008-09-10
Well you are asking good questions.

I hope I do not get this wrong, but your bash variable is a string and not a number.

The -eq is valid.

test has it's own syntax as does case.

Best source of information is google.

[http://www.faqs.org/docs/abs/HTML/tests.html](http://www.faqs.org/docs/abs/HTML/tests.html)

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_03.html)

---

### Post by ad_267 on 2008-09-10
= is for strings, -eq for integers. Also you were missing another "then"

Type "man test" for more details.

So you want:
```

#! /bin/bash
sel=$1
if [ "$sel" = "1" ]
then
color=red
elif [ "$sel" = "2" ]
then
color=blue
else
color=dark
fi

```

---

### Post by emp1953 on 2008-09-11
Thanks for all the help
I can expand this into what I need now.

---

### Post by ds[de] on 2008-09-11
> **emp1953 said:**
> Is -eq a valid unary operator?

I didn't see this question answered. Just to clarify, a unary operator is applied to a single operand. Since -eq (~equal) checks the difference between two operators, it certainly is **not** a unary opeartor :-)

An example for a **unary** operator would be **!** (not). "-eq" however is called a **binary** operator.


Regards,
ds[de]

---

### Post by ghostdog74 on 2008-09-11
> **emp1953 said:**
> Newbie to bash scripting
Want a simple demo script that will:

At command line I want to enter  > scriptname 1    or scriptname 2    1 and 2 are parameters

 

The script should

 

If parameter $1 is 1 then echo The sky is blue

If parameter $1 is 2 then echo The sky is red

If parameter 1 is blank then echo The sky is dark. 
   (I'd rather test for the blank then have it be a default in the else) but I don't know how to test for blank)

 

Here’s what I have so far

#! /bin/bash
sel=$1
if [ $sel -eq 1  ]
then
      color=red
elif [ $sel -eq 2  ]
      color=blue
else
      color=dark
fi

echo The sky is $color
 

My unary operator –eq is not right   it is not = or ==   other unary operators are –lt –gt for less than and greater than.  With this failure I don't know if the rest is correct either
    Thanks for Any help

you can use case/esac, its neater
```

case $sel in 
  1 ) color=red ;;
  2 ) color=blue;;
  3 ) color=dark;;
  * ) echo "Invalid";;
esac
echo "Color is $color"

```

---

### Post by ds[de] on 2008-09-11
> **ghostdog74 said:**
> you can use case/esac, its neater

So is reading the thread, bodhi.zazen already posted a solution using a case statement 7 posts above yours ;-)


Regards,
ds[de]

---


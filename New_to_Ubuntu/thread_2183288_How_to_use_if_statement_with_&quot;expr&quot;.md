---
title: "How to use if statement with &quot;expr&quot;"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by Taati_Barao on 2013-10-24
Hi everyone

Im trying to write a simple script the can calculate the price of  something, but when i run the script there is an error "expr: syntax  error". here is my script

#ex1

shirt=\$15.00
black=\$13.50


echo "Please enter how many shirt you want"
read num1
echo
echo "Please choose"
echo "1 ---> Normal Shirt"
echo "2 ---> black Shirt"
read choice
echo


if [ $choice = "1" ]; then
	answer=`expr $num1 * $shirt`
	echo "$num1 * $shirt = $answer"
elif [ $choice = "2" ]; then
	answer=`expr $num1 * $black`
	echo "$num1 - $num2 = $answer"

else 
	echo "invalid selection"

fi

Please anyone can help tell me what was missing in the script? 


Thanks

Taati

---

### Post by Lars Noodén on 2013-10-24
If you wrap the code you post in [****code][/code] tags, the result will be easier for use to read here.

You might [use $(...) instead of `...`](http://mywiki.wooledge.org/BashFAQ/082).  Among other things it will make the result easier to read.  

Lastly, "expr" is not really needed for [arithmetic expression](http://www.tldp.org/LDP/abs/html/arithexp.html).  You can use double parenthesis instead.

---

### Post by SeijiSensei on 2013-10-24
Also remember that "[" and "]" are operators in bash just like any other command and must be delimited by a space.  An entry like

```
if [$something = 1]
```

will generate a syntax error.  Make sure you use

```
if [ $something = 1 ]
```

If you wrap the comparison target with quotes, wrap the environment variable as well.  (I usually do numerical comparisons this way.)

```
if [ "$something" = "1" ]
```

Make sure you use double-quotes around $something so it will be evaluated rather than treated as a literal as '$something' would be.

---

### Post by Taati_Barao on 2013-10-24
thanks for the advice on wrap....

---

### Post by Taati_Barao on 2013-10-24
Thanks for your help

---

### Post by Taati_Barao on 2013-10-24
thanks for the link you provided is very helpful to me....

Cheers

---


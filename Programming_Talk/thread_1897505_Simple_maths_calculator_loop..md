---
title: "Simple maths calculator loop."
date: 2011-12-19
forum: Programming Talk
---

### Post by johnthebaptist92929292 on 2011-12-19
Hi, I am trying to make a maths calculator that:

1. Prompts the user for a number.
2. Prompts the user for an operation (add, subtract, divide or multiply)
3. Prompts the user for a number.
4. Prompts the user for another operation (same as above) OR the option to get the result for the equation.
5. The script should loop back if the user chooses to add another operation, and ask for another number (repeat until result)

Now, i already have the arithmetic sorted, and i know i have to add an UNTIL loop, but i'm not very good with loops as i find them hard to understand. 

Here is a copy of my code so far:

-----

echo "please enter a number"
read n1

echo "please choose an operation"
echo "1. add"
echo "2. subtract"
echo "3. divide"
echo "4. multiply"
read opr

echo "please enter a number again"
read n2

if [ $opr = "1" ]
   then
      echo $((n1+n2))
elif [ $opr = "2" ]
   then  
      echo $((n1-n2))
elif [ $opr = "3" ]
   then
      echo $((n1/n2))
elif [ $opr = "4" ]
   then
       echo $((n1*n2))

fi
exit 0

-----

Can anyone give me any pointers? I really have tried to look for solutions but this is my last hope.

---

### Post by karlson on 2011-12-19
> **johnthebaptist92929292 said:**
> Hi, I am trying to make a maths calculator that:

1. Prompts the user for a number.
2. Prompts the user for an operation (add, subtract, divide or multiply)
3. Prompts the user for a number.
4. Prompts the user for another operation (same as above) OR the option to get the result for the equation.
5. The script should loop back if the user chooses to add another operation, and ask for another number (repeat until result)

Now, i already have the arithmetic sorted, and i know i have to add an UNTIL loop, but i'm not very good with loops as i find them hard to understand. 

Here is a copy of my code so far:

-----

echo "please enter a number"
read n1

echo "please choose an operation"
echo "1. add"
echo "2. subtract"
echo "3. divide"
echo "4. multiply"
read opr

echo "please enter a number again"
read n2

if [ $opr = "1" ]
   then
      echo $((n1+n2))
elif [ $opr = "2" ]
   then  
      echo $((n1-n2))
elif [ $opr = "3" ]
   then
      echo $((n1/n2))
elif [ $opr = "4" ]
   then
       echo $((n1*n2))

fi
exit 0

-----

Can anyone give me any pointers? I really have tried to look for solutions but this is my last hope.

I have a few questions:

1.  Why are you trying to do this in Shell?
2.  What is the issue with the loop?

---

### Post by CoffeeRain on 2011-12-19
If you are looking to do stuff like this, shell is a very bulky and hard to use language. It is more suited to working with the computer. I find Python is an easy language to learn, and is suited to working with strings and data like this.

---

### Post by johnthebaptist92929292 on 2011-12-19
karlson:

1. Because it is for an assignment for university. The reason I am asking on the Internet is because I am currently on my Xmas break and I live 200 miles away from campus so seeing my tutors for help is not an option.
2. Do you know any websites (or know some yourself) that contain good examples for all sorts of loops - mostly UNTIL loops -  that are based around arithmetic? I CANNOT find any that are to do with arithmetic. 

Thankyou.

a little different from my original post i know but that's all i need.

---

### Post by johnthebaptist92929292 on 2011-12-19
> **CoffeeRain said:**
> If you are looking to do stuff like this, shell is a very bulky and hard to use language. It is more suited to working with the computer. I find Python is an easy language to learn, and is suited to working with strings and data like this.

This is for a university assignment so it must be in this.

---

### Post by CoffeeRain on 2011-12-19
Ah... Here is a link for loops, it includes a pretty good description of until loops. [http://tldp.org/LDP/abs/html/loops1.html](http://tldp.org/LDP/abs/html/loops1.html)
You would have to ask the user for input on whether or not they want to continue and then act on it. When those variables are defined, then you could introduce your loop and use the same variables.

```
echo -n "Do you want to add more operations? (y/n) "
read choice

until (($choice = "n")) ; do
code for more operations here
done
```

---

### Post by johnthebaptist92929292 on 2011-12-19
> **CoffeeRain said:**
> Ah... Here is a link for loops, it includes a pretty good description of until loops. [http://tldp.org/LDP/abs/html/loops1.html](http://tldp.org/LDP/abs/html/loops1.html)
You would have to ask the user for input on whether or not they want to continue and then act on it. When those variables are defined, then you could introduce your loop and use the same variables.

```
echo -n "Do you want to add more operations? (y/n) "
read choice

until (($choice = "n")) ; do
code for more operations here
done
```


I have managed to do something very similiar to your little code exerpt. It is allowing me to do one more calculation (i.e. 10x10x10=1000) AND I have managed to make it loop back to the options bit again UNTIL the user chooses the "result" option. HOWEVER, I cannot get it to calculate more than 3 values. Is there any way I could send you a quick copy of the script? I know I'm close to the solution but I just need that little bit more!

Thanks anyway

---

### Post by CoffeeRain on 2011-12-19
Would copying or attaching it in here not work?

---

### Post by sisco311 on 2011-12-19
From the [forum policy](http://ubuntuforums.org/index.php?page=policy):

> 
While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.


If you are looking for a good BASH guide, check out the links in my signature.

Thread Cloased.

---


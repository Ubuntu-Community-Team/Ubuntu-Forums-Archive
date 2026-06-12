---
title: "how to use loop"
date: 2013-10-29
forum: Programming Talk
---

### Post by Taati_Barao on 2013-10-29
Hi Everyone


Could anyone  help me on how to use loop  to repeat the task for 2 times, 

the code as follows


```
shirt=15
black=13.50

echo "how many shirt you want"
read num
echo
echo "Please enter a choice"
echo "1 ---> normal shirt"
echo "2 ---> black shirt"
read choice
echo

if [ $choice = "1" ]; then
    price=`expr $num1 \* $shirt`
    echo "$num1 * $shirt = $price"

elif [ $choice = "2" ]; then
    answer=$(bc <<< "scale=2;$num*$black")
    echo "$num * $black = $answer"
else
    echo "Invalid option"
fi
```

 The output code 


  ```
how many shirt you want
2

Please enter a choice
1 ---> normal shirt
2 ---> black shirt
1

2 * 15 = 30
ictadmin@ubuntu:~/Desktop$
```
 
Please anyone can tell me where to put loop inside my script, where it can repeat the task for 2 times or more.

Thanks

Taati

---

### Post by cariboo on 2013-10-29
Moved to programming talk.

---

### Post by papibe on 2013-10-29
Hi Taati_Barao.

This should point you in the right direction:
```
for i in {1..2}
do
    echo $i;
done
```
The output would be:
```
1
2
```
Regards.

---

### Post by Taati_Barao on 2013-10-30
Hi Papibe

Thanks for that hint

Taati

---


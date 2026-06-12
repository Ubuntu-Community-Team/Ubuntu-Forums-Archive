---
title: "number counter"
date: 2016-04-20
forum: New to Ubuntu
---

### Post by DGRE6133 on 2016-04-20
Hi all.
Not sure if this is posted in the right area, but I'm new to linux scripting, and working with ubuntu. 
I have a school project that requires the user to input an unknown amount of numbers, sum up those numbers, average them and display the biggest and smallest number. so far all I have is this:

```
sum=0
num=0
echo "enter an many numbers as you like or q to quit."
read num
while [ $num != q ]
do 
sum=`expr $num + $sum`
read num
done
```




And the script has to loop. 
any Ideas??
thank you in advance.

---


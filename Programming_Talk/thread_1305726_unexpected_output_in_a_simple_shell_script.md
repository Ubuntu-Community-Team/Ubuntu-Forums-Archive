---
title: "unexpected output in a simple shell script"
date: 2009-10-30
forum: Programming Talk
---

### Post by bilol on 2009-10-30
Hi friends, 
Can anybody suggest me what is wrong with the following code?

```
echo "enter no. of rows..."
read m
echo "enter no. of cols...."
read n
for (( i=1;i<=m;i++  )); do
     for (( j=1;j<=n;j++ )); do
         echo "enter the element a[$i][$j]"
         read a[$i][$j] 
         echo " the value entered is " ${a[$i][$j]}
     done
done
echo " the matrix entered is"
for (( i=1;i<=m;i++  )); do
     for (( j=1;j<=n;j++ )); do
         echo " the value of a[$i][$j] is " ${a[$i][$j]}
     done
done

```
...and the output is 
```
dhiman@dhiman-desktop:~$ bash matmul
enter no. of rows...
2
enter no. of cols....
3
enter the element a[1][1]
1
 the value entered is  1
enter the element a[1][2]
2
 the value entered is  2
enter the element a[1][3]
3
 the value entered is  3
enter the element a[2][1]
4
 the value entered is  4
enter the element a[2][2]
5
 the value entered is  5
enter the element a[2][3]
6
 the value entered is  6
 the matrix entered is
 the value of a[1][1] is  3
 the value of a[1][2] is  3
 the value of a[1][3] is  3
 the value of a[2][1] is  6
 the value of a[2][2] is  6
 the value of a[2][3] is  6

```
..I expect the output should be 1 2 3 4 5 6

Any help will be appreciated....

---

### Post by Linteg on 2009-10-30
Does bash support multi-dimensional arrays?

---

### Post by bilol on 2009-10-30
> Does bash support multi-dimensional arrays? 
Yes..because in the first segment of the code ,data are read properly in the 2D array.

---

### Post by Arndt on 2009-10-30
> **bilol said:**
> Yes..because in the first segment of the code ,data are read properly in the 2D array.

Unfortunately, that's not proof, because with the line

         read a[$i]junk 

instead of

         read a[$i][$j] 

the exact same results appear.

---

### Post by geirha on 2009-10-30
It does indeed not have support for multidimensional arrays. Make a 1d-array of size m*n instead, then a[j+i*n] to get the right element.

---

### Post by bilol on 2009-10-30
Thanks a lot geirha.

---


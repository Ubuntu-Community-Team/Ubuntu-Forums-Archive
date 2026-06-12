---
title: "can you explain this C program for me"
date: 2006-12-01
forum: Programming Talk
---

### Post by LaoLiulaoliu on 2006-12-01
#include<stdio.h>
main()
{
int c;
while(c=getchar()!=EOF)
printf("%d\n",c);
printf("%d - at EOF\n",c);
}

Can you analyze this program for me .Please tell me .ok?:KS

---

### Post by LaoLiulaoliu on 2006-12-01
when I execute it ,it show as follows:
a  /*I type a*/
1
1
0 - at EOF

---

### Post by zgornel on 2006-12-01
> **LaoLiulaoliu said:**
> #include<stdio.h>
main()
{
int c;
while(c=getchar()!=EOF)
printf("%d\n",c);
printf("%d - at EOF\n",c);
}

Can you analyze this program for me .Please tell me .ok?:KS
Check Kerrigan and Ritchie. This is one of their first examples. :D anyway, he program reproduces the hex code of the entered character (including \n) until the EOF char is encountered when it displays the last line.

---

### Post by Arndt on 2006-12-01
> **zgornel said:**
> Check Kerrigan and Ritchie. This is one of their first examples. :D anyway, he program reproduces the hex code of the entered character (including \n) until the EOF char is encountered when it displays the last line.

Interesting. Actually, that's not what the program does. Look at the sample run.

(Besides, "hex" is not what %d prints - you use %x for that.)

---

### Post by lloyd_b on 2006-12-01
There are parentheses missing in the if statement.  The line:

while(c=getchar()!=EOF)

Should be 

while ((c = getchar()) != EOF)

That why he's getting the 1's, rather than the ASCII value - It's doing a logical compare between "getchar() != EOF", and then assigning that value to "c".

Lloyd B.

---

### Post by zgornel on 2006-12-01
> **Arndt said:**
> Interesting. Actually, that's not what the program does. Look at the sample run.

(Besides, "hex" is not what %d prints - you use %x for that.) Right. My bad. I was thinking at the ascii code.

---

### Post by LaoLiulaoliu on 2006-12-02
> **lloyd_b said:**
> There are parentheses missing in the if statement.  The line:

while(c=getchar()!=EOF)

Should be 

while ((c = getchar()) != EOF)

That why he's getting the 1's, rather than the ASCII value - It's doing a logical compare between "getchar() != EOF", and then assigning that value to "c".

Lloyd B.

My original aim is 
while(c=(getchar()!=EOF))

---

### Post by lloyd_b on 2006-12-02
> My original aim is
while(c=(getchar()!=EOF))

This is exactly what the original code did.  "c = (getchar() != EOF)" will result in "c" either getting a value of 1 (if the result of getchar() is not equal to EOF), or 0 (if the result of getchar() is equal to EOF).

That is why whenever you hit a key, it printed "1", until you hit <CTRL> D, at which point it printed a "0".

My change assumes that you want "c" to receive the value of the character code, rather than the results of the boolean compare.

Lloyd B.

---


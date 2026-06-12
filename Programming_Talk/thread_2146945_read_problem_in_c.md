---
title: "read problem in c"
date: 2013-05-20
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-20
hi all;

 i have run this code and the first read and write work correctly. but and the second one is missed.
the output log is:


 freez@JALALI:~$ ./a
salam8a
okok2freez@JALALI:~$
```


 

[LIST]
[*]#include <stdio.h>
[*]
[*]int main()
[*]{
[*]write(1,"salam",5);
[*]char a[2];
[*]char b[5];
[*]read(0,a,2);
[*]if(a[0]=='8')
[*]{write(1,"ok",2);
[*]read(0,b,5);
[*]write(1,"ok2",3);
[*]}
[*]return 0;
[*]}
[/LIST]
 

```

---

### Post by spjackson on 2013-05-20
Your first read reads the 2 characters '8' and 'a'. There is a 3rd character waiting to be read, which is '\n'. Your second read reads this '\n', so your program never gives you chance to enter a second line of text.

---


---
title: "gcc - scanf capturing extra char while using printf"
date: 2014-12-25
forum: Programming Talk
---

### Post by astroa on 2014-12-25
please check the code written for gcc:

--------------------------------------------------------------

#include<stdio.h>

void main()
{
    char ch;
    
    while(1)
    {
        printf("Enter:\t");
        scanf("%c",&ch);
        printf("\t%c\n",ch);
    }
}

----------------------------------------------

output obtained:
Enter:    a
    a
Enter:        

Enter:    b
    b
Enter:        

Enter:    

---------------------------------------------------------

I think, a dummy invisible char is introduced for scanf by printf which prints an extra "Enter:" here.
Why is this happening?
Anything wrong with the code?

-------------------------------------------------------------

---

### Post by oldos2er on 2014-12-25
Moved to Programming Talk. I'm hoping this isn't homework.

---

### Post by astroa on 2014-12-25
thanks, oldos2er. ;)

---

### Post by schragge on 2014-12-25
See [here](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1352443831&id=1043284392). It's a newline character that gets inserted when you press Enter.

---

### Post by astroa on 2014-12-25
modifying

scanf("%c",&ch);

to

scanf(" %c",&ch);

works for me.

Also, i understood why the anomaly happened.

thanks to schragge and all those who helped.

until next doubt :)

---


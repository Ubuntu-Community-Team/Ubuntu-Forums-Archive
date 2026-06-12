---
title: "simple C coding for moving file from one disk (C)to another disk (D)"
date: 2012-03-29
forum: Programming Talk
---

### Post by sneha09 on 2012-03-29
I need to copy file from one disk to another Using C language only... Like from drive c to drive d. please help!!!!!

---

### Post by Zugzwang on 2012-03-29
In another post of yours, you already have some copy for copying files. Whether you copy from one disk to the other, or from one disk to the same disk doesn't make a difference in the code.

---

### Post by sneha09 on 2012-03-29
> **Zugzwang said:**
> In another post of yours, you already have some copy for copying files. Whether you copy from one disk to the other, or from one disk to the same disk doesn't make a difference in the code.
yes... now i am done with that problem.

---

### Post by sneha09 on 2012-03-29
#include <stdio.h>
   
    int main()
   {
   if ( rename("C:\\old.cpp", "D:\\new.cpp") )
    perror( NULL );
   getchar();
    return 0;
   }
By this code,my file gets moved.But not copied. I need to copy files.

---

### Post by CynicRus on 2012-03-29
Use standart windows console comand 
[COPY]("http://ss64.com/nt/copy.html").

#include <stdlib.h>

int main()
{
    system("copy c:\\hello.txt d:\\hello2.txt");
    return 0;
}

---

### Post by sneha09 on 2012-03-30
> **CynicRus said:**
> Use standart windows console comand 
[COPY]("http://ss64.com/nt/copy.html").

#include <stdlib.h>

int main()
{
    system("copy c:\\hello.txt d:\\hello2.txt");
    return 0;
}
Thanks a lot ... i really mean it. GOD bless you with everything that you desire in Life...:KS
Coming on my problem's next stage.. that is to change the extension of this file that i am copying in another drive. can you help me... like i wanna change this text file into excel.

---

### Post by CynicRus on 2012-03-30
[http://support.microsoft.com/kb/216686](http://support.microsoft.com/kb/216686)

---


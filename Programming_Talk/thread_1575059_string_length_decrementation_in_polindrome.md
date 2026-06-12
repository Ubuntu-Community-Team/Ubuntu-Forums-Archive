---
title: "string length decrementation in polindrome"
date: 2010-09-15
forum: Programming Talk
---

### Post by navaneethan on 2010-09-15
Consider this code,why we have to decrement the length by 2? for example  

```
void strPass(char *str,int len) //(start addr,4)
{
   if(str[0]==str[(len)-1])  //1st char comparision
      strPass(str+1,**len-2**);  //here why we are decrementing the length by 2 
    else
       printf("This is not polin...");

}

main()
{
  //  Get the input string     /*consider INPUT STRING=**JAVA/0***/
  len=strlen(str)-1;    //4 is calculated
  strPass(&str,len);    //(start addr, 4) passed
}
```

---

### Post by dwhitney67 on 2010-09-15
Think of your string as a V-shaped entity; as you span the string, you are comparing pairs of characters.  In this context, as in most, "pair" equals 2.

```

#     #                length = 7 (count them hash-marks!)
 #   #                 length = 5
  # #                  length = 3
   #                   length = 1

```
Does it make sense now?


P.S.  The code you posted is either awful C or C++; please post complete code when dealing with trivial applications.  Also, consider the case when the string only has one character, or none at all!

---


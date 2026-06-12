---
title: "writing printf with variable argument with pointers"
date: 2012-08-17
forum: Programming Talk
---

### Post by 681ankit on 2012-08-17
MY CODE FOR PRINTF() to print only integers and unsigned long :-

```
void printf(char *ch,void *num,...)
    {
        int i;
        va_list ptr;    //to store variable length argument list
        va_start(ptr,num); // initialise ptr
        
        
        for(i=0;ch[i]!='\0';i++)
            {
                
                
                if(ch[i]=='%')  // check for % sign in print statement
                    { i++;
                    
                        if( ch[i]=='d')
                            {  
                              int *no = (int *)va_arg(ptr,int * );
                              int value=*no;  // just used for nothing 
                              printno(value);  //print int number
                              
                            }
                        if( ch[i]=='u')
                            {
                            
                               unsigned long *no =(unsigned long *) va_arg(ptr,unsigned long *);
                               unsigned long value=*no;
                               printuno(value);  //print unsigned long
                              
                               
                            }
                    }
                else    // if not % sign then its regular character so print it
                    {
                        printchar(ch[i]);
                    }
            }
            
        
        
    
    }


/**********************************************************/
```

I am getting the some what incorrect output...

This function prints string portion correctly ..but
when printing integer or uint it shows value 425067 for all %d %u

So pls tell me how to improve it ,,...THANKS

---

### Post by ofnuts on 2012-08-17
Because you declare "num" as part of the fixed args in your function prototype. Your function should be declared as: 
```

void printf(char *ch,...)

```and the va_list initialized by:
```

va_start(ptr,ch);

```

---

### Post by 681ankit on 2012-08-17
> **ofnuts said:**
> Because you declare "num" as part of the fixed args in your function prototype. Your function should be declared as: 
```

void printf(char *ch,...)

```and the va_list initialized by:
```

va_start(ptr,ch);

```

You solved my problem ....thanks...now i find standard prototype for printf

---

### Post by dwhitney67 on 2012-08-17
> **681ankit said:**
> 
So pls tell me how to improve it ,,...THANKS

A pre-check should be added to the home-made printf() function to ensure that 'ch' actually points to a non-NULL string.  Also 'ch' should be declared as a const char*, and perhaps even renamed to something like 'format'.

Something like:
```

void printf(**const char *format**,...)
{
    int i;
    va_list ptr; //to store variable length argument list
    va_start(ptr,format); // initialise ptr

    **if (format == NULL) return;**

    ...
}

```

P.S.  In the future, please (not pls, plz, or any other spelling) post your code within CODE tags as I have done above.

---

### Post by ofnuts on 2012-08-17
Btw, when you write something like this:
```
if( ch[i]=='d') {
...
}
if( ch[i]=='u') {
...
}

```then you have a nice case for as switch statement (couldn't resist the pun...)

If you persist with the if's, that's OK, but then make them nested if/else, otherwise it will be very difficult to write the "catch the rest" code if needed.

---


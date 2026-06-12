---
title: "what's wrong with my program"
date: 2008-12-16
forum: Programming Talk
---

### Post by praneeth.k on 2008-12-16
//-------------PROGRAM:RAILFENCING---------------------
#include<stdio.h>
#include<string.h>
#include<malloc.h>
int main()
{
    char *plain;char *cipher;char *decipher;int i,j=0,k,n;
    puts("enter the plain text");
    scanf("%s",plain);
    n=strlen(plain);
    plain=(char*)malloc(n);
    cipher=(char*)malloc(n);
    decipher=(char*)malloc(n);
    puts(plain);
//---------------ENCRYPTION-----------------------------
    for(i=0;i<n;i+=2)
        cipher[j++]=plain[i];
    for(i=1;i<n;i+=2)
        cipher[j++]=plain[i];
    cipher[j]='\0';
    printf("the cipher text is %s",cipher);
//---------------DECRYPTION-----------------------------
    for(i=0,j=(n/2)+1,k=0;k<n;)
        {
            decipher[k]=cipher[i++];
            decipher[++k]=cipher[j++];
        }
   printf("\n\nthe decrypted cipher is %s",decipher);
return 0;
}

output:
enter the plain text
hello
      6054:     symbol=malloc;  lookup in file=./a.out [0]
      6054:     symbol=malloc;  lookup in file=/lib/libc.so.6 [0]
lookup 0x0000000000400000 0x00000000000002f0 -> 0x00002b303d819000 0x0000000000073d90 /1 malloc


      6054:     symbol=printf;  lookup in file=./a.out [0]
      6054:     symbol=printf;  lookup in file=/lib/libc.so.6 [0]
lookup 0x0000000000400000 0x00000000000002a8 -> 0x00002b303d819000 0x000000000004d280 /1 printf
the cipher text is 




-----please help me out ,i think its a problem with memory allocation.

---

### Post by mdurham on 2008-12-16
> char *plain;
puts("enter the plain text");
scanf("%s",plain);
Where is your input going? 'plain' should be a buffer (array of chars)
For some reason you try to allocate storage for 'plain' with malloc() after illegally using it. You must somehow allocate your storage before using it.
when you want to show some code wrap it in 'CODE' tags else it's hard to read.

---

### Post by kcode on 2008-12-16
Thats a snippet of your code where the error exists...
> **praneeth.k said:**
> //-------------PROGRAM:RAILFENCING---------------------
#include<stdio.h>
#include<string.h>
#include<malloc.h>
int main()
{
    char *plain;char *cipher;char *decipher;int i,j=0,k,n;
    puts("enter the plain text");
    scanf("%s",plain);
    n=strlen(plain);
    plain=(char*)malloc(n);

You missed ampersand (&) in scanf() function. It should be:
```

scanf("%s",&plain);

```

Right now i can only see this(there may be more), going for coffee. :-)

cheers

---

### Post by mdurham on 2008-12-16
> **kcode said:**
> Thats a snippet of your code where the error exists...

You missed ampersand (&) in scanf() function. It should be:
```

scanf("%s",&plain);

```


This is NOT correct. There is no missing & as 'plain' is (supposed to be) a pointer.

---

### Post by dwhitney67 on 2008-12-16
> **mdurham said:**
> This is NOT correct. There is no missing & as 'plain' is (supposed to be) a pointer.

+1

This is merely another case of K&R C-style programming still infecting the world.  It sure would be nice if when declaring a variable, one would also initialize it to something useful.

For example:
[php]
char plain[80] = {0};
char cipher[80] = {0};
char decipher[80]= {0};

puts("Enter the plain text: ");
fgets(plain, sizeof(plain), stdin);
...
[/php]
Alternatively,
[php]
char* plain = malloc(80);
char* cipher = malloc(80);
char* decipher = malloc(80);

puts("Enter the plain text: ");
fgets(plain, 80, stdin);
...
free(plain);
free(cipher);
free(decipher);
[/php]
Also, never use scanf() or gets() to obtain a string from stdin.  Always use fgets(); it is considered safer because it will prevent buffer overruns should the user type in too many characters at the input prompt.

---

### Post by kcode on 2008-12-16
> **mdurham said:**
> This is NOT correct. There is no missing & as 'plain' is (supposed to be) a pointer.

Sorry...didnt see it. Thanks for the correction.

---

### Post by praneeth.k on 2008-12-17
CODE tag means? will u please eloborate so that i may do it from from now on

thanks for your time.

---

### Post by Caduceus on 2008-12-17
Simple, write [ CODE ] (without the spaces) then the code, followed by [ /CODE ] (again without spaces). Ruby code for example:

```
puts("Hello, world!")
```

---

### Post by PandaGoat on 2008-12-17
You might run into problems caused by allocating only strlen(plain) bytes.  If you want it to have the standard null terminating character at the end you should allocate strlen(plain)+1 bytes.   I'm not sure if you need this or not, but I figured it is important to point out.

---

### Post by nvteighen on 2008-12-17
> **dwhitney67 said:**
> 
Also, never use scanf() or gets() to obtain a string from stdin.  Always use fgets(); it is considered safer because it will prevent buffer overruns should the user type in too many characters at the input prompt.

+1

Just a question: What happens to the data that fgets() ignores? Are they fflush()'ed automatically?

---

### Post by praneeth.k on 2008-12-17
> **PandaGoat said:**
> You might run into problems caused by allocating only strlen(plain) bytes.  If you want it to have the standard null terminating character at the end you should allocate strlen(plain)+1 bytes.   I'm not sure if you need this or not, but I figured it is important to point out.

reply--
ya thanks,ive  modified it to strlen(plain)+1,

thanks for your time

---

### Post by scourge on 2008-12-17
> **nvteighen said:**
> +1

Just a question: What happens to the data that fgets() ignores? Are they fflush()'ed automatically?

Nope, and flushing stdin results in undefined behavior. If you want to clear the buffer you can use fgetc until you reach a line break or EOF.

---

### Post by nvteighen on 2008-12-17
> **scourge said:**
> Nope, and flushing stdin results in undefined behavior. If you want to clear the buffer you can use fgetc until you reach a line break or EOF.
I was asking something else... :p Let me clarify my question:

Why does fgets() prevent the overflow effect you can appreciate with scanf()? scanf() directly reads from stdin whatever it finds there; stdin is buffered, so data will stay there until they're dumped to some variable... This is appreciable when using scanf() and overflowing variables on purpose. But fgets() doesn't: yeah, it prevents overflowing stuff to be dumped to a variable, but where does that data go?

---

### Post by scourge on 2008-12-17
> **nvteighen said:**
> I was asking something else... :p Let me clarify my question:

Why does fgets() prevent the overflow effect you can appreciate with scanf()? scanf() directly reads from stdin whatever it finds there; stdin is buffered, so data will stay there until they're dumped to some variable... This is appreciable when using scanf() and overflowing variables on purpose. But fgets() doesn't: yeah, it prevents overflowing stuff to be dumped to a variable, but where does that data go?

My understanding is that fgets and scanf read the data the same way, with the distinction that fgets stops when a specific number of characters have been read. You can still get an overflow with fgets if you tell it to read more characters than your char array can hold.

So fgets doesn't really prevent overflows, but unlike scanf it at least lets the programmer prevent them. And the data doesn't go anywhere, it stays in stdin.

---


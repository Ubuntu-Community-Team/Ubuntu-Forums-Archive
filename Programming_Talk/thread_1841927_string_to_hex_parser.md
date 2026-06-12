---
title: "string to hex parser"
date: 2011-09-10
forum: Programming Talk
---

### Post by avee137 on 2011-09-10
I need to implement a string to hex parser .

My requirement is as below :
1.get 8 characters from console input.
   say ab12de11
2. my program should store it as
   char buf5[5] = {'0xab','0x12','0xde','0x11','\0'};


any relevant suggestion would be appreciated .

---

### Post by rolandrock on 2011-09-10
First hit on google:
[http://www.daniweb.com/software-development/c/threads/49346](http://www.daniweb.com/software-development/c/threads/49346)

---

### Post by avee137 on 2011-09-10
> **rolandrock said:**
> First hit on google:
[http://www.daniweb.com/software-development/c/threads/49346](http://www.daniweb.com/software-development/c/threads/49346)


the code is flawed.it uses itoa() which is basically meant to convert an int to char.

---

### Post by ofnuts on 2011-09-10
> **avee137 said:**
> the code is flawed.it uses itoa() which is basically meant to convert an int to char.
Maybe itoa() has a reciprocal function that would be called....    hmm. maybe.

And maybe there is and adequate format specifier for the *scanf()  functions.

---

### Post by dwhitney67 on 2011-09-10
> **avee137 said:**
> 
2. my program should store it as
   char buf5[5] = {'0xab','0x12','0xde','0x11','\0'};

What you have above does not make sense.

Do you mean something like this (where unsigned values are stored)?
```

unsigned char buf[5] = {0xab, 0x12, 0xde, 0x11, 0x00};

```

or do you mean something like this (where strings are stored)?
```

char* buf[5] = {"0xab", "0x12", "0xde", "0x11", NULL};

```

---

### Post by avee137 on 2011-09-10
this code works for a 8 character string to 4byte hex parsing.

```
#include<stdio.h>
#include<string.h>
#include<stddef.h>
#include<stdlib.h>

void DBG(char *str)
{
#ifdef DEBUG
    printf("%s\n",str);
#endif
}

char toHex(char ch1 , char ch2)
{
    char hexByte ;
    ch1 = ch1 << 4 ;
    hexByte = (ch1 | ch2 );
    return hexByte ;
}
char getHexEq(char inChar)
{
    switch (inChar)
    {
    case '0' :
        return 0 ;
        break ;
    case '1' :
            return 1 ;
            break ;
    case '2' :
            return 2 ;
            break ;
    case '3' :
            return 3 ;
            break ;
    case '4' :
            return 4 ;
            break ;
    case '5' :
            return 5 ;
            break ;
    case '6' :
            return 6 ;
            break ;
    case '7' :
            return 7 ;
            break ;
    case '8' :
            return 8 ;
            break ;
    case '9' :
            return 9 ;
            break ;
    case 'a' :
            return 10 ;
            break ;
    case 'b' :
            return 11 ;
            break ;
    case 'c' :
            return 12 ;
            break ;
    case 'd' :
            return 13 ;
            break ;
    case 'e' :
            return 14 ;
            break ;
    case 'f' :
            return 15 ;
            break ;
    default:
            printf("invalid character format\n");
            break ;
    }
}

int main()

{

    int i ,j;
    char ch1 ,ch2 ,chHex;
    char buf9[9] = {'\0'};

    char hexBuf4[4] = {'\0'};

    printf ("enter the 8 character hex id\n");
    scanf("%s",buf9);

    for(i = 0,j=0 ; i < 8,j<4  ; i+=2,++j)
    {
        ch1 = getHexEq(buf9[i]);
        ch2 = getHexEq(buf9[i+1]);

        chHex = toHex(ch1 , ch2);
        hexBuf4[j] = chHex ;

    }

    for(i = 0 ; i < 4  ; ++i)
    {
    printf(" 0x%x\n ", (unsigned)(unsigned char)hexBuf4[i] );
    }
    return 0;
}
```

---

### Post by ofnuts on 2011-09-10
> **avee137 said:**
> this code works for a 8 character string to 4byte hex parsing.

<snipped code-orrhea>



Wondering why you don't use the %x format in the scanf to get your hex decoded for you? Something like "%2x%2x%2x%2x" to get 4 numbers scanned in from 2 input characters each?

---

### Post by Bachstelze on 2011-09-10
```
    scanf("%s",buf9);
```

Nice buffer overflow.

---

### Post by dwhitney67 on 2011-09-10
> **avee137 said:**
> this code works for a 8 character string to 4byte hex parsing.

I just returned home, and I must say that I enjoyed the little chuckle I got from perusing your code.

```

$ gcc hexparsing.c
hex.c: In function &#8216;main&#8217;:
hex.c:91: warning: left-hand operand of comma expression has no effect
hex.c: In function &#8216;getHexEq&#8217;:
hex.c:76: warning: control reaches end of non-void function

```
While this looks good:
```

$ ./a.out
enter the 8 character hex id
ab12de11
 0xab
  0x12
  0xde
  0x11

```
The following produces an error:
```

$ ./a.out
enter the 8 character hex id
AB12DE11
invalid character format
invalid character format
invalid character format
invalid character format
 0x99
  0x12
  0x99
  0x11

```
As does the following:
```

$ ./a.out
enter the 8 character hex id
WHOWHATWHEREWHEN
invalid character format
invalid character format
invalid character format
invalid character format
invalid character format
invalid character format
invalid character format
invalid character format
 0x99
  0x99
  0x99
  0x99
*** stack smashing detected ***: ./a.out terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x1f2390]
/lib/tls/i686/cmov/libc.so.6(+0xe233a)[0x1f233a]
./a.out[0x80486b3]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x126bd6]
./a.out[0x8048431]
======= Memory map: ========
00110000-00263000 r-xp 00000000 08:03 565023     /lib/tls/i686/cmov/libc-2.11.1.so
00263000-00264000 ---p 00153000 08:03 565023     /lib/tls/i686/cmov/libc-2.11.1.so
00264000-00266000 r--p 00153000 08:03 565023     /lib/tls/i686/cmov/libc-2.11.1.so
00266000-00267000 rw-p 00155000 08:03 565023     /lib/tls/i686/cmov/libc-2.11.1.so
00267000-0026a000 rw-p 00000000 00:00 0 
00557000-00558000 r-xp 00000000 00:00 0          [vdso]
00b8e000-00ba9000 r-xp 00000000 08:03 549778     /lib/ld-2.11.1.so
00ba9000-00baa000 r--p 0001a000 08:03 549778     /lib/ld-2.11.1.so
00baa000-00bab000 rw-p 0001b000 08:03 549778     /lib/ld-2.11.1.so
00e64000-00e81000 r-xp 00000000 08:03 551198     /lib/libgcc_s.so.1
00e81000-00e82000 r--p 0001c000 08:03 551198     /lib/libgcc_s.so.1
00e82000-00e83000 rw-p 0001d000 08:03 551198     /lib/libgcc_s.so.1
08048000-08049000 r-xp 00000000 08:02 229455     /home/user/a.out
08049000-0804a000 r--p 00000000 08:02 229455     /home/user/a.out
0804a000-0804b000 rw-p 00001000 08:02 229455     /home/user/a.out
09682000-096a3000 rw-p 00000000 00:00 0          [heap]
b7839000-b783a000 rw-p 00000000 00:00 0 
b7852000-b7856000 rw-p 00000000 00:00 0 
bfecd000-bfee3000 rw-p 00000000 00:00 0          [stack]
 Aborted

```

---

### Post by avee137 on 2011-09-15
> **dwhitney67 said:**
> I just returned home, and I must say that I enjoyed the little chuckle I got from perusing your code.

```

$ gcc hexparsing.c
hex.c: In function ‘main’:
hex.c:91: warning: left-hand operand of comma expression has no effect
hex.c: In function ‘getHexEq’:
hex.c:76: warning: control reaches end of non-void function

```While this looks good:
```

$ ./a.out
enter the 8 character hex id
ab12de11
 0xab
  0x12
  0xde
  0x11

```The following produces an error:
```

$ ./a.out
enter the 8 character hex id
AB12DE11
invalid character format
invalid character format
invalid character format
invalid character format
 0x99
  0x12
  0x99
  0x11

```As does the following:
```

$ ./a.out
enter the 8 character hex id
WHOWHATWHEREWHEN
invalid character format
invalid character format
invalid character format
invalid character format
invalid character format
invalid character format
invalid character format
invalid character format
 0x99
  0x99
  0x99
  0x99
*** stack smashing detected ***: ./a.out terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x1f2390]
/lib/tls/i686/cmov/libc.so.6(+0xe233a)[0x1f233a]
./a.out[0x80486b3]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x126bd6]
./a.out[0x8048431]
======= Memory map: ========
00110000-00263000 r-xp 00000000 08:03 565023     /lib/tls/i686/cmov/libc-2.11.1.so
00263000-00264000 ---p 00153000 08:03 565023     /lib/tls/i686/cmov/libc-2.11.1.so
00264000-00266000 r--p 00153000 08:03 565023     /lib/tls/i686/cmov/libc-2.11.1.so
00266000-00267000 rw-p 00155000 08:03 565023     /lib/tls/i686/cmov/libc-2.11.1.so
00267000-0026a000 rw-p 00000000 00:00 0 
00557000-00558000 r-xp 00000000 00:00 0          [vdso]
00b8e000-00ba9000 r-xp 00000000 08:03 549778     /lib/ld-2.11.1.so
00ba9000-00baa000 r--p 0001a000 08:03 549778     /lib/ld-2.11.1.so
00baa000-00bab000 rw-p 0001b000 08:03 549778     /lib/ld-2.11.1.so
00e64000-00e81000 r-xp 00000000 08:03 551198     /lib/libgcc_s.so.1
00e81000-00e82000 r--p 0001c000 08:03 551198     /lib/libgcc_s.so.1
00e82000-00e83000 rw-p 0001d000 08:03 551198     /lib/libgcc_s.so.1
08048000-08049000 r-xp 00000000 08:02 229455     /home/user/a.out
08049000-0804a000 r--p 00000000 08:02 229455     /home/user/a.out
0804a000-0804b000 rw-p 00001000 08:02 229455     /home/user/a.out
09682000-096a3000 rw-p 00000000 00:00 0          [heap]
b7839000-b783a000 rw-p 00000000 00:00 0 
b7852000-b7856000 rw-p 00000000 00:00 0 
bfecd000-bfee3000 rw-p 00000000 00:00 0          [stack]
 Aborted

```

you are right. this code is not perfect  . i ll try to implement better error handling .

---

### Post by ofnuts on 2011-09-15
> **avee137 said:**
> you are right. this code is not perfect  . i ll try to implement better error handling .You should be using scanf() (or another similar function) instead of reinventing the wheel.

---


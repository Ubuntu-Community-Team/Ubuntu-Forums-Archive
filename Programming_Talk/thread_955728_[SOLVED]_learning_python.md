---
title: "[SOLVED] learning python"
date: 2008-10-22
forum: Programming Talk
---

### Post by mosty friedman on 2008-10-22
hey everyone, 
i'm currently learning python because i heard good things about how a cool language it is...so i'm applying what i'm learning by solving some simple programs just for testing...so i'm trying to print a pyramid of asterisk...it worked fine but can someone tell me how to print the asterisk on the same line without having spaces between them?
here's my code
```

n = int( raw_input( 'enter n : ' ) )
for i in range( 0, n ):
    for j in range( 0,n-i ):
        print '*',
    print 

```
this gives this output
* * * * *
* * * *
* * *
* *
*
i want it to give this output
*****
****
***
**
*

---

### Post by LaRoza on 2008-10-22
I think that is just the way print works, adding spaces. 

If you don't want spaces, you should assemble the string then print it, instead of printing each character at a time.

Or:
```

n = int( raw_input( 'enter n : ' ) )
for i in range(0,n):
    print "*"*i

```

---

### Post by gomputor on 2008-10-22
```
n = int( raw_input( 'enter n : ' ) )
for i in range( 0, n ):
    print '*' * (n-i)

>>enter n : 5
*****
****
***
**
*

n = int( raw_input( 'enter n : ' ) )
for i in range( 0, n+1 ):
    print '*' * i

>>enter n : 5
*
**
***
****
*****
```

---

### Post by mosty friedman on 2008-10-22
thanks guys, doesnt even need an extra loop...am still thinking in terms of java :P

---


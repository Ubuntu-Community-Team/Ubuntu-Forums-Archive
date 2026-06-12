---
title: "converting qbasic into python"
date: 2007-11-23
forum: Programming Talk
---

### Post by shleyman on 2007-11-23
is there any way to convert a program frm qbasic to python?
```
DECLARE FUNCTION IsPrime& (p&)
DEFLNG I-Z
CLS

INPUT "enter number to test: ", n

m = 0 ' number of pairs

PRINT : PRINT n;

FOR p = 3 TO n / 2 STEP 2
IF IsPrime(p) AND IsPrime(n - p) THEN
PRINT TAB(10); "="; p; "+"; n - p
m = m + 1
END IF
NEXT

PRINT : PRINT m; "distinct representations"

FUNCTION IsPrime (p)

IF p MOD 2 = 0 THEN
IsPrime = 0
ELSE
IsPrime = 1

FOR i = 3 TO SQR(p) STEP 2
IF p MOD i = 0 THEN IsPrime = 0: EXIT FOR
NEXT
END IF

END FUNCTION
```

im wanting to be able to break this down and have a look at what it would be like in python but its written in qbasic so im abit stuck...
any help will be much appreciated

---

### Post by LaRoza on 2007-11-23
Working on it, I don't know QBasic, so I'm guess on some things ; )

I think I see logic errors, so I can't figure out what to do...

---

### Post by LaRoza on 2007-11-23
Tell me what the program is supposed to do, and I'll try to finish it.

---

### Post by ankursethi on 2007-11-23
I know this is offtopic, but if anybody wants to run this example, you can try FreeBasic from freebasic.net. It's a free, cross platform implementation of QBasic.

(I can't find it in the repos. Just get the pre-built binaries in a tar.gz or compile it on your own.)

Python code :
```
import math

def Main() :
    m = 0
    n = int(raw_input("Enter number : "))

    for p in range (3, n/2, 2) :
        if isPrime(p) and isPrime(n-p) :
            print p, " + ", n-p
            m += 1

    print m, " distinct representations."



def isPrime(num) :
    prime = True
    if num%2 == 0 :
        prime = False

    root = math.sqrt(num)
    for i in range(3, root, 2) :
        if num % i == 0 :
            prime = False

    return prime

if __name__ == "__main__" :
    Main()

```

Apparently this code finds out the prime factors of a number. Note that SQR(p) in the original code does NOT mean the square of p, but represents the *square root* of p.

---

### Post by tyoc on 2007-11-23
> [COLOR=#0000bb]def IsPrime [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]p[/COLOR][COLOR=#007700]): 
    if [/COLOR][COLOR=#0000bb]p [/COLOR][COLOR=#007700]% [/COLOR][COLOR=#0000bb]2 [/COLOR][COLOR=#007700]== [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]: 
       return [/COLOR][COLOR=#0000bb]False 
    [/COLOR][COLOR=#007700]else 
        return = [/COLOR][COLOR=#0000bb]True 
[/COLOR][COLOR=#ff8000]# The followoing isn't translated 
    [/COLOR][COLOR=#007700]FOR [/COLOR][COLOR=#0000bb]i [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]3 TO SQR[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]p[/COLOR][COLOR=#007700]) [/COLOR][COLOR=#0000bb]STEP 2 
    [/COLOR][COLOR=#007700]IF [/COLOR][COLOR=#0000bb]p MOD i [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0 THEN IsPrime [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]: EXIT FOR 
    [/COLOR][COLOR=#0000bb]NEXT 
    END [/COLOR][COLOR=#007700]IF  [/COLOR]I think that the first if else, will never let the flow continue to for loop, because is divisible of 2 or is not (return true or false).


Or forget the comment, because I have never seen before [COLOR=#007700]         return = [/COLOR][COLOR=#0000bb]True???[/COLOR] dont know exactly how this program evolve hehehe.

---

### Post by LaRoza on 2007-11-23
> **tyoc said:**
> I think that the first if else, will never let the flow continue to for loop, because is divisible of 2 or is not (return true or false).


Or forget the comment, because I have never seen before [COLOR=#007700]         return = [/COLOR][COLOR=#0000bb]True???[/COLOR] dont know exactly how this program evolve hehehe.

Sorry, I was editing it in the middle of the night and didn't come back to.

---

### Post by Martin Witte on 2007-11-23
my shot (my qbasic is a it rusty, my last basic programming dates from the eighties)
```
import math

# the pyton style guide advises to use lowercase names for functions,
# seperate words with uderbscores, see http://www.python.org/dev/peps/pep-0008/
def is_prime(p):
    """determine if p is prime by the so called brute force method"""
    prime = True
    if p%2 == 0:
        prime = False
    else:
        for i in range(3, math.ceil(math.sqrt(p/2)), 2):
            if p % i == 0:
                prime = False
                break
    return prime

if __name__ == '__main__':
    n = int(raw_input('ener number to test: '))
    m = 0 #number of pairs
    print n
    for p in range(3, n/2, 2):
        if is_prime(p) and is_prime(n-p):
            #string concatenation is preferable over adding string segments, see
            # http://wiki.python.org/moin/PythonSpeed/PerformanceTips#head-bcf69f4e2cacc9683c2f9a1f401e891cac50506f 
            print '%s = %d + %d' % (' '*10, p, n-p)
            m+=1

    print '%d distinct representations' % m

```

---

### Post by shleyman on 2007-11-24
wow thanks quys 
by the way the program is the goldbach conjecture.

---


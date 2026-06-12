---
title: "Tabular Output"
date: 2009-11-01
forum: Programming Talk
---

### Post by Dark Aspect on 2009-11-01
Hello

I am trying to get a Tabular output in Java or in simpler terms, spaced output with a simple program. My goal is to multiply 1 by 10, 100, 1000 and so on in tabs and have a output much like:

N     10*n     100*n     1000*n
1     10       100       1000
2     20       200       2000
3     30       300       3000
4     40       400       4000
5     50       500       5000
6     60       600       6000

I am pretty much lost, I know I can use /t for tab formating but %d doesn't like multiply variables for x. Do I need a separate integer for each tab? 

```
public class tabular
{
     public static void main(String[] args)
        {
          int x = 1;

          while (true)
           {
            x = x;
            x = x * 10;
            x = x * 100;
            x = x * 1000;
            System.out.printf("%d\t %d\t %d\t %d", x);
            x++;
          break;
           }
        }
}
```

---

### Post by MadCow108 on 2009-11-01
I'm no java programmer but I guess my observations should still hold:

your code seems completely wrong
with every assignment to x you assign a new value to x losing the old, you either need 4 integers each storing one result or 4 printf functions each printing the result before overwriting it, or one printf which prints the return of 4 operations on x directly.

your printf expects 4 integers and receives one (except java handles printf differently than all languages with printf I know)

your x++ will increase the last value of x (which is x*10*100*1000) resulting in x*10*100*1000+1 so it will not produce the result you seem to want.
also the loop will end after the first iteration because of your unconditional break, making the loop kind of senseless

---

### Post by Dark Aspect on 2009-11-01
> **MadCow108 said:**
> I'm no java programmer but I guess my observations should still hold:

your code seems completely wrong
with every assignment to x you assign a new value to x losing the old, you either need 4 integers each storing one result or 4 printf functions each printing the result before overwriting it, or one printf which prints the return of 4 operations on x directly.

your printf expects 4 integers and receives one (except java handles printf differently than all languages with printf I know)

your x++ will increase the last value of x (which is x*10*100*1000) resulting in x*10*100*1000+1 so it will not produce the result you seem to want.
also the loop will end after the first iteration because of your unconditional break, making the loop kind of senseless

Yep, I figured some of that out. Thanks - I think I had a brain fart :D

On the other hand heres the new code:

```
public class test
{
     public static void main(String[] args)
	{
	  int x = 1;
           System.out.println("N\t 10*N\t 100*N\t 1000*N");
	  while (x < 10)
	   {
            System.out.printf("%d\t %d\t %d\t %d \n", x, x * 10, x * 100, x * 1000);
            x++;
           }
	}
}
```

---


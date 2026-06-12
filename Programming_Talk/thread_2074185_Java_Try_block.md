---
title: "Java: Try block"
date: 2012-10-21
forum: Programming Talk
---

### Post by vikkyhacks on 2012-10-21
```
class a
{
        public static void main(String[] s)
        {
                int n1,n2,$n;
                if(s.length != 2)
                {
                        System.out.print("Invalid arguments supplied\n");
                        System.exit(0);
                } 
                try
                {
                        n1 = Integer.parseInt(s[0]);
                        n2 = Integer.parseInt(s[1]);
                }
                catch(Exception a)
                {
                        System.out.print("Stings supplied for arithematic operations !!!");
                }
                System.out.print(n1+n2);
        }
}
```



produces error .... I need to convert the string argument received to integer inside the try block and throw the respective errors and calculate the addition outside, .. help me

1. Understand why this error occurred ???
2. How can i solve this ???

---

### Post by GeneralZod on 2012-10-21
If you have an error, please, in future, actually tell us what it is :)

---

### Post by vikkyhacks on 2012-10-21
Oops tat's my mistake !!!

```
a.java:20: error: variable n1 might not have been initialized
		System.out.print(n1+n2);
		                 ^
a.java:20: error: variable n2 might not have been initialized
		System.out.print(n1+n2);
		                    ^
2 errors

```

---

### Post by spjackson on 2012-10-21
The problem is that if an error is thrown then after the catch block has been executed, you do the addition anyway. In that case, one or both of n1 and n2 are not initialised.

One option is to set both to 0 before the try block. In this case you will print the sum of 0+0 after the catch. Another option is to place a return statement in the catch block after printing the error message.

---

### Post by vikkyhacks on 2012-10-21
Thanks I understood !!! :)

---


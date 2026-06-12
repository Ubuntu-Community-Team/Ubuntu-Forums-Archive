---
title: "java error when compiling program"
date: 2006-10-02
forum: Programming Talk
---

### Post by baldy1324 on 2006-10-02
hi i just made a fibonacci sequence program in java and when i run the javac compiler it lists this error: ```
robert@Workhorse:~/sci_proj$ javac fibiterative.java
fibiterative.java:23: '}' expected
^
1 error

```
here is the source code-
```
robert@Workhorse:~/sci_proj$ cat fibiterative.java
class main
{
        public static void main(String[] args)
        {
                int n = 350;
                double first = 0;
                double second = 1;
                System.out.print(first);
                System.out.print("    ");
                System.out.print(second);
                Sysetm.out.print("    ");

                while (n--)
                        {
                                double third = first + second;
                                first = second;
                                second = third;
                                System.out.print(third);
                                System.out.print("    ");
                        }
        {
}

```
any suggestions would be appreciated

---

### Post by meng on 2006-10-02
I haven't counted the lines but you have an open brace second last line, where it should be close brace, could well be line 23 (or else line 22).

---

### Post by Ryan Marcus on 2006-10-02
Yes, that looks like the problem.

As somebody new to java, I often forget these little syntax things (mainly semi-colons), and I found that using Eclipse is incredibly useful.

---

### Post by meng on 2006-10-02
Even Jedit is good for that sort of thing.

---


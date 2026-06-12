---
title: "Java string format"
date: 2012-08-27
forum: Programming Talk
---

### Post by Drenriza on 2012-08-27
Hey guys.

I have a program where i query a MS-SQL database and returns a result set with about 150 entries, in 12 cells.

My question is, how can i format the returning result in a table format in a console program?

**See example in picture since the editor cant display as i want it. Thanks.**

I have looked at **System.out.printf** and **System.out.format** but i cant wrap my head around it ;/ So hoping someone can help me out or point me in the right direction.

Thanks in advance.
Kind regards.

---

### Post by dwhitney67 on 2012-08-27
> **Drenriza said:**
> 
**See example in picture since the editor cant display as i want it. Thanks.**

Baloney... use CODE tags to preserve output.

See if this helps:
```

public class Format
{
    public static void main(String[] args)
    {
        String[] raw = { "1", "222", "33333333", "44444", "5555", "6666666", "777777",
                         "888888", "999999", "11", "22", "3333", "444", "5555555", "666",
                         "7777777", "88888888", "9999", "111", "222", "333333", "4444444",
                         "555", "6666666", "7777777", "888888", "99999" };

        for (int i = 0; i < raw.length; ++i)
        {
            if (i % 9 == 0) System.out.println();

            System.out.format("%-8s ", raw[i]);
        }
        System.out.println();
    }
}

```
Output looks like:
```


1        222      33333333 44444    5555     6666666  777777   888888   999999   
11       22       3333     444      5555555  666      7777777  88888888 9999     
111      222      333333   4444444  555      6666666  7777777  888888   99999 

```

---


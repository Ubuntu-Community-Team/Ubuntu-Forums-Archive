---
title: "Convert Simple Java Program to C#"
date: 2009-01-08
forum: Programming Talk
---

### Post by Fosfate on 2009-01-08
Here is the Java code:

```
public class WordPlay {   
    public static void main (String[] args) {   
        String[] listVariableA = {"a","e","i","o","u"};   
        String[] listVariableB = {"b","c","d","f","g","h","j","k","l","m","n","p","r","s","t","v","x","y","z"};   
        String[] listVariableC = {"a","e","i","o","u"};   
           
        int oneLength = listVariableA.length;   
        int twoLength = listVariableB.length;   
        int threeLength = listVariableC.length;   
  
        int i;   
        for (i = 0; i < 50; i++) {   
        int rand1 = (int) (Math.random() * oneLength);   
        int rand2 = (int) (Math.random() * twoLength);   
        int rand3 = (int) (Math.random() * threeLength);   
  
        String newLogoName = listVariableA[rand1] + " " + listVariableB[rand2] + " " + listVariableC[rand3];   
           
        System.out.println(newLogoName);   
        }   
        }   
    }  
```
How would one write that in C# as a console program?

---

### Post by efexD on 2009-01-08
Could you post the output of the java? I'll be happy to translate it to C#.

---

### Post by efexD on 2009-01-08
oops sorry. forums are bugging

---

### Post by myrtle1908 on 2009-01-08
Not the way I would write it ... just a straight conversion.

[PHP]
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace Test
{
    class WordPlay
    {
        static void Main(string[] args)
        {
            String[] listVariableA = { "a", "e", "i", "o", "u" };
            String[] listVariableB = { "b", "c", "d", "f", "g", "h", "j", "k", "l", "m", "n", "p", "r", "s", "t", "v", "x", "y", "z" };
            String[] listVariableC = { "a", "e", "i", "o", "u" };

            int oneLength = listVariableA.Length;
            int twoLength = listVariableB.Length;
            int threeLength = listVariableC.Length;

            Random rand = new Random();
            int rand1, rand2, rand3;
            String newLogoName;
            for (int i = 0; i < 50; i++)
            {
                rand1 = rand.Next(oneLength);
                rand2 = rand.Next(twoLength);
                rand3 = rand.Next(threeLength);
                newLogoName = listVariableA[rand1] + " " + listVariableB[rand2] + " " + listVariableC[rand3];
                Console.WriteLine(newLogoName);
            }


        }
    }
}

[/PHP]

[PHP]Yields something like:-

a m e
a y u
o f i
...[/PHP]

---


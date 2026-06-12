---
title: "Java: Need advice on String manipulation program"
date: 2011-08-22
forum: Programming Talk
---

### Post by fallenshadow on 2011-08-22
I wrote this simple program a while back but it doesn't quite work properly.

For some reason the surname is repeated. Any ideas?

[PHP]
class StringTest
{
  public static void main(String[] args)
  {
    String str1 = new String();
    String str2 = new String();
    char initial=' ', firstletsn;
    int i=0, start=0, end=0, endstr;
  
    System.out.print("Enter your firstname followed by your surname ");
    str1 = EasyIn.getString();
    endstr = str1.length();
  
    while (i < endstr)
    {
        System.out.println(str1.charAt(i)+ " " + i);
        i++;
    }
    
    i=0;
    
        while(str1.charAt(i)== ' ')
        i++;
        start=i;
        
        initial = str1.charAt(start);
        str1 = str1.toLowerCase();
         
        while ((str1.charAt(i)>='a')&&(str1.charAt(i)<='z'))
        i++;
        
        
        while(i < endstr)
        {
            System.out.println(str1.charAt (i) + " " + i);
            i++;
        }
        end = i;
    str2 = str1.substring(start,end);
    firstletsn = str2.charAt(start);
    str2 = str2.toUpperCase();
    firstletsn = str2.charAt(0);
    str2 = str2.substring(1,str2.length());
    str2 = str2.toLowerCase();
    
    System.out.println(firstletsn+str2 + " " + initial + ".");
    
  }
}
[/PHP]

I was gonna study this for an upcoming test but since its faulty then there is no point in studying something wrong!

---

### Post by Bachstelze on 2011-08-22
What's EasyIn?

---

### Post by fallenshadow on 2011-08-22
It is just a class that takes input.. no need to worry about that. :)

Works the same as scanner.

---

### Post by Bachstelze on 2011-08-22
You'll have to tell me what kinf of input your program expects, ten. just the surname or first name + surname ?

---

### Post by fallenshadow on 2011-08-22
The program expects the first name followed by the surname. Like this:

> firstname surname

The letters are outputed one by one... except the surname gets repeated a second time.. I need to know why this happens.

It organizes the name in the correct way at the end. The end output is correct.

---

### Post by GeneralZod on 2011-08-22
> **fallenshadow said:**
> 
The letters are outputed one by one... except the surname gets repeated a second time.. I need to know why this happens.


Well ... if I'm understanding you correctly, it's because you print it out twice ;) (There are two "while" loops with 

```

System.out.println(str1.charAt (i) + " " + i)

```
 
in them; comment out the second).


> **fallenshadow said:**
> 
It organizes the name in the correct way at the end. The end output is correct.

Is the output for

```

Jebediah Bootlace

```

really supposed to be

```

Jebediah bootlace J.

```

?

---

### Post by ofnuts on 2011-08-22
In the real word, this code would be written using a regular expression... 

It is also some code which won't work outside of English-speaking countries (and even then...), and I'm not talking about the futility of the "initial" in ideographic languages, but of the test of the a-z range.

---

### Post by fallenshadow on 2011-08-23
Oh silly me... I was tired when I posted this. :lolflag:

Please forgive me for posting up such a stupid question. :D

Thanks General Zod! Your reply was very helpful! :)

---


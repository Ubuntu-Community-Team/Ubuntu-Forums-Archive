---
title: "Java If/Else Statement Question"
date: 2009-11-11
forum: Programming Talk
---

### Post by Hosmion on 2009-11-11
I am coding in Java just for fun, and I am having unknown (to me) errors that I need to fix..  Please help me resolve my problem :D
```

public class If {
    public static void main(String args[]){
        int test = 6;
            if (test == 9);
                System.out.println("Yes");
            }else{                                                                   <--Error Here
            System.out.println("This is else");
        }
    }
}
```[/code]

---

### Post by Arndt on 2009-11-11
> **Hosmion said:**
> I am coding in Java just for fun, and I am having unknown (to me) errors that I need to fix..  Please help me resolve my problem :D

public class If {
    public static void main(String args[]){
        int test = 6;
        
            if (test == 9);
                System.out.println("Yes");
            }else{                                                                   <--Error Here
            System.out.println("This is else");
        }
    }
}

What is the error message? We can help you interpret it.

---

### Post by schauerlich on 2009-11-11
There's a semicolon after the if statement.

Also, please use [code] tags.

---

### Post by Somme on 2009-11-11
```
if (this == that) {
   // do something
} else {
   // do something else
}

```

---

### Post by Hosmion on 2009-11-11
> **Arndt said:**
> What is the error message? We can help you interpret it.

```
public class If {
    public static void main(String args[]){
        int test = 6;
        {
            if (test == 9);
                System.out.println("Yes");
    }else{
            System.out.println("This is else");
        }
    }
```

That is my original codeing..  This is the Error Message..
```

Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
    Syntax error on token "else", delete this token
    Syntax error, insert "}" to complete ClassBody

    at If.main(If.java:7)
```

---

### Post by myrtle1908 on 2009-11-11
Both EDavidBurg and Somme gave you the answer.  You have a semicolon after the if statement.  This is syntactically incorrect.

---

### Post by Hosmion on 2009-11-11
```
public class If {
    public static void main(String args[]){
        int test = 6;
        {
            if (test == 9)
                System.out.println("Yes");
    }else{
            System.out.println("This is else");
        }
    }


```
That still does not work.

---

### Post by schauerlich on 2009-11-11
> **Hosmion said:**
> That still does not work.

Count your brackets. they don't match.

Make sure your editor has syntax highlighting and bracket matching. It will help you catch mistakes like these.

In vim: 
:syntax on
:set showmatch

---

### Post by LKjell on 2009-11-11
```
public class If 
{
    public static void main(String args[])
    {
        int test = 6;
        {
            if (test == 9)
            [COLOR="Red"]{[/COLOR]
                System.out.println("Yes");
            }
            else
            {
            System.out.println("This is else");
            }
        [COLOR="Red"]}[/COLOR]
    [COLOR="Red"]}[/COLOR]
}
```

---

### Post by Somme on 2009-11-11
> **Hosmion said:**
> ```
public class If {
    public static void main(String args[]){
        int test = 6;
        {
            if (test == 9)
                System.out.println("Yes");
    }else{
            System.out.println("This is else");
        }
    }


```That still does not work.

Indentation levels for the first and last line in your application shouldn't differ. As others have already pointed out, you haven't properly closed one or more if/else statements ( see my previous post ).

---

### Post by Hosmion on 2009-11-12
I fixed it..  Thanks you guys!

---


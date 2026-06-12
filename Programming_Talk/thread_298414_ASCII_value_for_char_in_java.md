---
title: "ASCII value for char in java"
date: 2006-11-12
forum: Programming Talk
---

### Post by igknighted on 2006-11-12
Is there a method in java to return the ASCII value of a char as an int?  I can't find one in the API, but I think it's just cause I'm blind

---

### Post by DaveBorealis on 2006-11-12
> **igknighted said:**
> Is there a method in java to return the ASCII value of a char as an int?

```

char somechar = ((char)in.readLine()); 
int i = Integer.parseInt(somechar); 
System.out.println(i); 

```

Hello,
Above takes a keyboard char (ASCII, I believe) and the second line does what you want.
HTH,
Dave

---

### Post by igknighted on 2006-11-12
> **DaveBorealis said:**
> ```

char somechar = ((char)in.readLine()); 
int i = Integer.parseInt(somechar); 
System.out.println(i); 

```

Hello,
Above takes a keyboard char (ASCII, I believe) and the second line does what you want.
HTH,
Dave

I'm getting a syntax error saying
```
Cannot find symbol
symbol : method parseInt(char)
location : class java.lang.Integer
```

---

### Post by igknighted on 2006-11-12
Ok, sorry to double post, but I found the answer.  All I needed was to do an explicit conversion:
```
charact = sentence.charAt(i);
ascii = (int)charact;
```

Thanks for the suggestion

---

### Post by DaveBorealis on 2006-11-12
> **igknighted said:**
> I'm getting a syntax error saying
```
Cannot find symbol
symbol : method parseInt(char)
location : class java.lang.Integer
```

My mistake.  parseInt takes a string, not a char!

There's also java.lang.getNumericValue(char ch), if you want to keep playing around, but I just looked it up and it seems to be unicode based rather than ASCII.

Glad you got it to work!
Dave

---


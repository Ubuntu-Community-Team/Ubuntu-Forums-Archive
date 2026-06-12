---
title: "C++ string literal question"
date: 2007-10-11
forum: Programming Talk
---

### Post by Houman on 2007-10-11
hello there;

I had a question regarding strings in C++, I have to write some perl code from my C++ program and I was wondering if there is a way to print literal strings in C++ withoug having to escape every single special character, 

in Perl this is possible by using single quotes, so i could some something like this:

```
print 'hi there %im a "special#% & character'
```

but in C  I have to do somethign like this:

```
printf(" special character \% and \" and \#") 
```

is there any equivalent of single quotes in C/C++?

regards

Houman

---

### Post by archivator on 2007-10-11
There are single quotes in C but they mean something completely different. Single quotes in C are used to indicate a single character. For example, while "a" is actually two characters (an 'a' and a zero byte), 'a' is a single character.

And no, there is no workaround around escaping special characters. Get used to it.

---

### Post by LaRoza on 2007-10-11
> **Houman said:**
> 

```
printf(" special character \% and \" and \#") 
```



```
printf("%s","special character % and \" and #")
```

Sorry, the "\"" is unavoidable for a literal.

---

### Post by Houman on 2007-10-11
thank you for replies, 
oh well  i guess i have to escape them :(

thanks

---


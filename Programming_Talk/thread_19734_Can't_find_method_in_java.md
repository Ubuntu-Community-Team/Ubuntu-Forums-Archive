---
title: "Can't find method in java"
date: 2005-03-13
forum: Programming Talk
---

### Post by droogie on 2005-03-13
I am trying to use the replace method in a program and I am getting an error saying 

DirectoryInfo.java:142: error: Can't find method `replace(Ljava/lang/String;Ljava/lang/String;)' in type `java.lang.String'.
   		dirStr = temp.replace(trimString, ".:");
                                ^
1 error

I am thinking it has something to do with java and ubuntu because the same code work ok on my windows machine.  I am new to linux and I am not sure if I had to set any environment variables or configure the java installation in any way.  The code also works on Sun Solaris.

-Mike

---

### Post by 0xBulbizarre on 2005-03-13
replace method of String is only applicable to char arguments. [http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#replace(char,%20char](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#replace(char,%20char))

use replaceAll instead !
[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#replaceAll(java.lang.String,%20java.lang.String](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#replaceAll(java.lang.String,%20java.lang.String))

---

### Post by droogie on 2005-03-13
Thanks for the response.  
If I was misusing the replace method, wouldn't I be getting a type mismatch error, not a cannot find the method error?  I think there is something with the java installation that is causing it.
My intention was to use this method

public String replace(CharSequence target,
                      CharSequence replacement)

---

### Post by Viro on 2005-03-13
[QUOTE=droogie]Thanks for the response.  
If I was misusing the replace method, wouldn't I be getting a type mismatch error, not a cannot find the method error?  I think there is something with the java installation that is causing it.
My intention was to use this method

public String replace(CharSequence target,
                      CharSequence replacement)[/QUOTE]
 No, that only happens in languages where overloading isn't allowed. In Java, since there is method overloading methods can have more than one signature, i.e. more than one set of arguments), Java thinks that you're calling a different method.

---


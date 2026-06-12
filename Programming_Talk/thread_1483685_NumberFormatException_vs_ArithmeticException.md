---
title: "NumberFormatException vs ArithmeticException"
date: 2010-05-14
forum: Programming Talk
---

### Post by s3a on 2010-05-14
Could someone please tell me what the difference is between the two?

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by Some Penguin on 2010-05-14
[http://www.lmgtfy.com/?q=numberformatexception+javadoc](http://www.lmgtfy.com/?q=numberformatexception+javadoc)
[http://www.lmgtfy.com/?q=arithmeticexception+javadoc](http://www.lmgtfy.com/?q=arithmeticexception+javadoc)

---

### Post by s3a on 2010-05-15
Ok but for NumberFormatException, I don't get what "appropriate format" means in "Thrown to indicate that the application has attempted to convert a string to one of the numeric types, but that the string does not have the appropriate format." Could you give me a simplistic example please?

([http://java.sun.com/j2se/1.4.2/docs/api/java/lang/NumberFormatException.html](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/NumberFormatException.html))

---

### Post by KdotJ on 2010-05-15
For example

```
String str = "not a number";
int num = Integer.parseInt(str);
```

This will throw a NumberFormatException as the string (str) does not contain a parsable integer. 
Therefore the *format* of the above String variable is not appropriate to be converted into an integer.

---

### Post by s3a on 2010-05-15
I see. Would you also get that same error if you were trying to convert a string with a double value into an int?

> **KdotJ said:**
> For example

```
String str = "not a number";
int num = Integer.parseInt(str);
```

This will throw a NumberFormatException as the string (str) does not contain a parsable integer. 
Therefore the *format* of the above String variable is not appropriate to be converted into an integer.

---

### Post by KdotJ on 2010-05-15
Indeed...
Example here, the following code, will compile:

```

public static void main(String[] args) {

    String d = "9.9";
    int test = Integer.parseInt(d);
    System.out.println(test);    	
}

```

..but give a runtime error of:

```
Exception in thread "main" java.lang.NumberFormatException: For input string: "9.9"
```

---

### Post by s3a on 2010-05-15
Thanks!

---


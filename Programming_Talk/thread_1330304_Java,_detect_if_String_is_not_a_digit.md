---
title: "Java, detect if String is not a digit"
date: 2009-11-18
forum: Programming Talk
---

### Post by andrew222 on 2009-11-18
I wanted to know if there is a mechanism in the Java API that will check a String object and be able to tell if any of the characters are not digits.

I know we can use the Integer (or Long, Short, etc...) and pass the string to the constructor.  However, this will throw a NumberFormatException if the String does not represent a number.

I am looking for a gentler way of checking, which returns a boolean result instead of throwing an exception.

Of course, i could always re-invent the wheel and code my own solution for this, but just wanted to check if there is anything in the API to help with this.

---

### Post by Reiger on 2009-11-18
The Character class will provide what you need.

---

### Post by NovaAesa on 2009-11-18
Your best bet would be to throw an exception I would say. I don't think there is anything 'rough' about using them. Just throw the exception and catch it locally. As far as I know, there is no method to check if a String has all digits.

Maybe you could try doing something with regular expressions? I haven't really used regex with Java before, but a class such as java.util.regex.Matcher might be of use. Just search around in the API.

---

### Post by myrtle1908 on 2009-11-18
Regular expressions are horrible in Java.  You can do it however ...

```
import java.util.regex.Pattern;
import java.util.regex.Matcher;

public class Test {
	public static void main(String[] args) {
		try {
			String s = "123456";
			//String s = "123a456";
			Pattern p = Pattern.compile("^\\d+$");
			Matcher m = p.matcher(s);
			if (m.matches()) {
				System.out.println("Digits only");
			} else {
				System.out.println("Chars other than digits found");
			}
		} catch (Exception e) {
			e.printStackTrace();
		}	
	}
}
```

---

### Post by The Cog on 2009-11-19
This (untested) is the way I would have done it:
```
public static bool onlyHasDigits(String s) {
        for (int i = 0 ; i < s.length() ; i++) {
            if(!Character.isDigit(s.charAt(i))) {
            return false;
        }
    }
    return true
}

```

---

### Post by apmcd47 on 2009-11-19
What about using String.matches(regex)?

eg

[PHP]String mynum;
...
if (mynum.matches("^\d+$")) // one or more digits anchored at both ends
{
   // all digits
} 
else
{
   // not all digits
}[/PHP]
Simple, really.

Andrew

---

### Post by giants_fan on 2009-11-19
Try to apache commons library:

[http://commons.apache.org/lang//api/org/apache/commons/lang/StringUtils.html]("http://commons.apache.org/lang//api/org/apache/commons/lang/StringUtils.html")

---

### Post by myrtle1908 on 2009-11-19
> **apmcd47 said:**
> What about using String.matches(regex)?

Ah yes.  I forgot that String has a matches method.  Much simpler than my use of Matcher and Pattern.

---

### Post by Arndt on 2009-11-20
> **myrtle1908 said:**
> Ah yes.  I forgot that String has a matches method.  Much simpler than my use of Matcher and Pattern.

It's probably worthwhile to run timing tests to see which is best. If the normal occurrence is that the input is in fact a number, and if it is done a lot, then the exception method will be superior to doing a regexp match every time.

---


---
title: "Count the number of occurences of substring in a string in Java"
date: 2008-04-11
forum: Programming Talk
---

### Post by DBQ on 2008-04-11
Does anybody know the simplest and cleanest way of of counting the number of times a substring occurs in a string in Java?

Is there also a way to accomplishing the task using the regular expressions?

---

### Post by slavik on 2008-04-11
I believe that you can, one of the objects returns an array of matches. I don't remember exactly, but it is doable (unless I am not remembering something).

---

### Post by CptPicard on 2008-04-11
Regexps are probably the easiest one... you just call "find" as many times as it returns something, and count those.

---

### Post by ghostdog74 on 2008-04-11
see  [here ]("http://forum.java.sun.com/thread.jspa?threadID=737523&messageID=4235204")for some suggestions

---

### Post by themusicwave on 2008-04-11
You could use String.indexOf(string,start)

Like so:


Where str is the string you are searching in and findStr is what you are looking for.

```

lastIndex = 0;
count =0;

while(lastIndex != -1){

       lastIndex = str.indexOf(findStr,lastIndex);

       if( lastIndex != -1){
             count ++;
      }
}

```

That would do exactly what you need.  There may be more efficient solutions out there like regular expressions though.  This one is decent though.

---

### Post by DBQ on 2008-04-12
Thank you all. Everything was very helpful.  I stuck with the regular expression option.

---

### Post by Balazs_noob on 2008-04-12
[http://java.sun.com/docs/books/tutorial/essential/regex/examples/MatcherDemo.java](http://java.sun.com/docs/books/tutorial/essential/regex/examples/MatcherDemo.java)

---

### Post by sav991 on 2010-08-03
> **themusicwave said:**
> 
```


       lastIndex = str.indexOf(findStr,lastIndex);


```


You would have to change this line to ensure subsequent iterations don't just keep looking at the previous result, but yeah, regular expressions sound like the go since I'm wanting to perform validation tasks.

Thanks.

Update:
Wanting to count the number of commas in a line of CSV text.
```

import java.util.regex.Pattern;

public static Boolean isValid(final String s) {
        String regex = "[^,]*,[^,]*,[^,]*,[^,]*,[^,]*";

        return Pattern.matches(regex, s);
}

```

---

### Post by myrtle1908 on 2010-08-04
> **sav991 said:**
> 
Wanting to count the number of commas in a line of CSV text.



I always liked split for this task ...

```
String s = "a,b,c,d";
System.out.println(s.split(",").length-1);
```

Sure we are creating an array but I don't care :)

Obviously this doesnt cater for quoted commas etc but you can mod the regex to suit.

---

### Post by Some Penguin on 2010-08-04
> **sav991 said:**
> 
Update:
Wanting to count the number of commas in a line of CSV text.


Regexes might be overkill for counting commas.

If you don't care about commas in quoted strings, or any escape characters, you can just loop over the results of stringVariable.toCharArray() incrementing a variable whenever you see a comma.  Linear time, constant space cost.


If you do care, something like

```

boolean escapeMode = false;  // \ = escape next character
boolean quoteMode  = false;  // "foo"
int count = 0;

// note:  below does necessarily not handle all 
// multi-byte Unicode characters; it also does not handle
// quote characters except "
//
// if that is a concern, use String's getCodePointAt() 
// and Character's toChars(), as well as Character's 
// getType() for identifying initial/final quotes... 

for (char c : stringVariable.toCharArray()) {
  if (escapeMode) {
     // Only good for one character.
     escapeMode = false;
  } else if (c == '\\') {
     // next character is treated as normal even if special
     // even if we're in a quote; this allows a quote within
     // a quoted string
     escapeMode = true;
  } else if (c  == '"') {
     quoteMode = !quoteMode;
  } else if ((!quoteMode) && (c == ',')) {
     count++;
  }
}

```

---

### Post by amelie on 2010-12-17
> **sav991 said:**
> You would have to change this line to ensure subsequent iterations don't just keep looking at the previous result


Excuse me, how do you do that, because I have the same problem?
Thanks in advance.

---

### Post by CheetoBandito on 2010-12-17
I like this guy's solution...
[http://timvalenta.wordpress.com/2009/01/06/java-count-substring/](http://timvalenta.wordpress.com/2009/01/06/java-count-substring/)

---


---
title: "java regex replace"
date: 2010-05-16
forum: Programming Talk
---

### Post by Xender1 on 2010-05-16
I am trying to replace all numbers on the line with that number - 10. I thought it would be easy to do but i keep getting 
```

Exception in thread "main" java.lang.IllegalStateException: No match found
        at java.util.regex.Matcher.group(Matcher.java:468)
        at java.util.regex.Matcher.group(Matcher.java:428)
        at javabonus.Main.main(Main.java:29)

```
this is what I am using to capture and replace the digits with on the String line.
```

Pattern num = Pattern.compile("([0-9]+\\.[0-9]+)");
Matcher mnum = grade.matcher(line);
mnum.replaceAll(Integer.toString(Integer.parseInt(mnum.group()) - 10));

```
Should I use a while (mnum.find()) and replace that way ?

---

### Post by Some Penguin on 2010-05-16
Strings are immutable; replaceAll doesn't modify the input string.  You should also realize that you're mnum.group() gets called ONCE, the results parsed ONCE, and then 10 subtracted... and that value is used to replace ALL groups.

---

### Post by soltanis on 2010-05-17
i.e. Instead you should be looping with .replaceFirst():

```

String grade = line;
Pattern num = Pattern.compile("([0-9]+\\.[0-9]+)");
do {
    Matcher matcher = num.matcher(grade);
    grade = matcher.replaceFirst(Integer.toString(Integer.parseInt(matcher.group()) - 10);
} while (matcher.find());

```

No guarantee of working, though; I put that together based on what the javadocs told me, and my Java has been known to be wrong.

---


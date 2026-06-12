---
title: "Java Regex engine vs. Perl's"
date: 2010-09-02
forum: Programming Talk
---

### Post by skytreader on 2010-09-02
Hi. I'm new to Perl but I already have some experiences with regards to regex, through Java. I wonder at this difference I noticed:

Java code:
```
import java.util.regex.*;

public class Test{
	public static void main(String[] args){
		System.out.println(Pattern.matches("[a-z]+", "the quick brown fox"));
	}
}
```

which prints "false" ; and...

Perl code:
```
$s = "the quick brown fox";

if($s =~ /[a-z]+/){
	print "yes\n";
}
```

which prints "yes". I tried to make it possesive but it still prints yes.

So, why the difference? I find it frustrating. My guess is that Perl checks if any substring matches the regex while Java checks for the whole string one shot big shot.

How do I make Perl behave the way Java does?

Thanks.

---

### Post by spjackson on 2010-09-02
One way to force a match against the whole string is to use ^ and $ thus
```

$s = "the quick brown fox";

if($s =~ /^[a-z]+$/){
    print "yes\n";
}

```

---

### Post by Some Penguin on 2010-09-02
Indeed.  Java provides both 'find' and 'matches' methods in java.util.regex.Matcher (and Pattern, but if you're going to be reusing the pattern it's reasonable to compile the Pattern object and use it to produce Matchers); the former behaves like the m// operator in Perl, while the latter is similar to Perl's m/^$/.

---


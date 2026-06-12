---
title: "Java Regex Question"
date: 2008-12-02
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-12-02
In Perl, I can do a regular expression like this:

	if($_ =~ /\s[\d:\d] = \d+/)
	{
	       pinname = $1;
               startindex = $2;
               endindex = $3;
               bitsettings = $4;
	}

So for example, the pinname corresponds to the \s string and is given index 1 ($1) because it was the first subpart of the regular expression match.  The first \d of the index was matched second and was assigned to $2, and so on... Is there a way to do exactly this in Java?  I have looked at Java's Regex and pattern classes, but I don't see anything that can do this.  In fact, for the above example, I don't think Java's regex class will save me much work over the simpler string split method.

---

### Post by Reiger on 2008-12-02
Yes, you can do it (more or less: it's done a bit differently):

```

import javax.regex.*;

public class Test {
  public static Pattern [] my_regexps= new Pattern [] {
         Pattern.compile('/^java$/'/*, optional bit mask containing flags */),
         Pattern.compile('/\\w+/'/*, optional bit mask containing flags */)
         };
  public static void main (String [] args) {
     Matcher m; 
     int i=0;
     for(String s : args) {
       for(Pattern p:  Test.my_regexps) {
          m=p.matcher(s); // evaluate s against m.
          if(m.matches) {
             System.out.println("The pattern \""+p.toString()+"\" matches the argument \""+s+"\"!");
             break;
          }
       }
       if(i==Test.my_regexps.length)
          System.err.println("No pattern matches the argument \""+s+"\"!");
     }
  }
}

```

Then there's things like getting groups/sub expressions, group/sub expression count, etc. etc all embodied within the Matcher class. However if you're looking for simple parsing (does it match or does it not/ split around a regex) you'll find that java.util.Scanner and java.lang.String got a few handy tricks built-in.

---


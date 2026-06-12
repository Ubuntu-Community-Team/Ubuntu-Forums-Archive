---
title: "Java Regular Expressions"
date: 2008-05-23
forum: Programming Talk
---

### Post by DBQ on 2008-05-23
Hi everybody.  My program can take as an input a string which can contain anything.  I need to match a string which contains anything EXCEPT say "hello".  My code needs to be compliant with 1.4 so I cannot use the "?" operator.  Any ideas and examples would be nice.

---

### Post by dwhitney67 on 2008-05-23
[post deleted]

I guess I should have read the thread title a little more closely.

How about this:  [http://www.regular-expressions.info/java.html](http://www.regular-expressions.info/java.html)

---

### Post by DBQ on 2008-05-23
What I mean is that my string can be anything.  For example: "hello world this is me".  Now, want a regular expression which will match ANY string EXCEPT the string that contains the substring "hello".  Thus the example string should not be matched in this case.  If the string is "ubuntu forums" then this string should be matched because it does not contain "hello" substring.  I want to accomplish this using a regular expression, and not some trick such as indexOf.

---

### Post by dwhitney67 on 2008-05-23
Take a look at this "awful" program I wrote.  See if it fits what you need.

The subject string is hard-coded, and the regex string (e.g. "hello") comes from the command line.
[PHP]
import java.util.regex.*;

class JRE
{
  public static void main( String[] args )
  {
    String subject = "Hello, welcome to my world.";
    String regex   = args[0];

    int regexOptions = Pattern.CASE_INSENSITIVE;

    Pattern compiledRegex = Pattern.compile( regex, regexOptions );
    Matcher matcher = compiledRegex.matcher( subject );

    if ( matcher.find() )
    {
      System.out.println( "Subject string '" + subject + "' contains offending pattern string '"
                          + regex + "'" );

    /*
      String textResults = new String("");

      try
      {
        textResults += "Index of the first character in the match: " +
                       Integer.toString(matcher.start()) + "\n";
        textResults += "Index of the first character after the match: " +
                       Integer.toString(matcher.end()) + "\n";
        textResults += "Length of the match: " +
                       Integer.toString(matcher.end() - matcher.start()) + "\n";
        textResults += "Matched text: " + matcher.group() + "\n";

        if (matcher.groupCount() > 0)
        {
          // Capturing parentheses are numbered 1..groupCount()
          // group number zero is the entire regex match
          for (int i = 1; i <= matcher.groupCount(); i++)
          {
            String groupLabel = new String("Group " + Integer.toString(i));

            if (matcher.start(i) < 0)
            {
              textResults += groupLabel + " did not participate in the overall match\n";
            }
            else
            {
              textResults += groupLabel + " start: " +
                             Integer.toString(matcher.start(i)) + "\n";
              textResults += groupLabel + " end: " +
                             Integer.toString(matcher.end(i)) + "\n";
              textResults += groupLabel + " length: " +
                             Integer.toString(matcher.end(i) -
                                              matcher.start(i)) + "\n";
              textResults += groupLabel + " matched text: " + matcher.group(i) + "\n";
            }
          }
        }
      }
      catch (IllegalStateException ex)
      {
        // Querying the results of a Matcher object before calling find()
        // or after a call to find() returned False, throws an IllegalStateException
        // This indicates a bug in our application
        textResults += "Cannot print match results if there aren't any";
      }
      catch (IndexOutOfBoundsException ex)
      {
        // Querying the results of groups (capturing parentheses or backreferences)
        // that do not exist throws an IndexOutOfBoundsException
        // This indicates a bug in our application
        textResults += "Cannot print match results of non-existent groups";
      }

      System.out.println( "textResults = " + textResults );
    */
    }
    else
    {
      System.out.println( "A worthy subject string was given.  Hooray!!!" );
    }
  }
}[/PHP]

---

### Post by fredscripts on 2008-05-24
Maybe what you looking for is the "indexOf" method of class String. 

```
public int indexOf(String str)

    Returns the index within this string of the first occurrence of the specified substring. The integer returned is the smallest value k such that:

         this.startsWith(str, k)
         

    is true.

    Parameters:
        str - any string. 
    Returns:
        if the string argument occurs as a substring within this object, then the index of the first character of the first such substring is returned; if it does not occur as a substring, -1 is returned.
```

So for example an object String s, if you do s.indexOf("Hello"), returns -1 if not found , and the position where it is if found on the string s.

---

### Post by dwhitney67 on 2008-05-24
> **fredscripts said:**
> Maybe what you looking for is the "indexOf" method of class String. 

So for example an object String s, if you do s.indexOf("Hello"), returns -1 if not found , and the position where it is if found on the string s.

This will not work if the sub-string within the string being searched is not the same case as the search string of indexOf().  For instance, indexOf() would return -1 if the word "heLLo" were in the string being searched.  I think the OP wanted to be able to filter variations of the same word.  I think the "Hello" was merely used as an example.

---

### Post by fredscripts on 2008-05-24
> **dwhitney67 said:**
> This will not work if the sub-string within the string being searched is not the same case as the search string of indexOf().  For instance, indexOf() would return -1 if the word "heLLo" were in the string being searched.  I think the OP wanted to be able to filter variations of the same word.  I think the "Hello" was merely used as an example.

Yes, but one can always change the case of all the string at compare-time, I mean:

s.toLowerCase().indexOf("HeLLo".toLowerCase())

---

### Post by dwhitney67 on 2008-05-24
Once again, your example only compares against one variation... "hello".  What if the subject string contained "This is how I spell 'hElLO'".  Then neither "Hello" nor "hello" would be found.  Do you understand now?

-----------------

Nevermind... I see that you lower-cased the subject string too.  Well, in such a case, perhaps you are right... that might just work.  Let's see what the OP thinks.

---

### Post by fredscripts on 2008-05-24
Yep sorry I misunderstood :)

---


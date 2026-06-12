---
title: "Centering output text in Java with BufferedWriter"
date: 2011-06-06
forum: Programming Talk
---

### Post by EarnestLearner on 2011-06-06
I'm trying to create an invoicing system. Each line is 57 characters long and I'm trying to have certain text centred in the output file (which is a .txt). Normally I'd just pad the strings to a certain length, but one of lines is of varying width.

Can anybody offer their expertise on the issue?

---

### Post by r-senior on 2011-06-06
Use a java.util.Formatter or the format() method on java.lang.String? Have the same sort of formatting tokens as C printf (and provide the backing to Java's printf method, which is another alternative).

[http://download.oracle.com/javase/6/docs/api/java/util/Formatter.html](http://download.oracle.com/javase/6/docs/api/java/util/Formatter.html)

[http://download.oracle.com/javase/6/docs/api/java/lang/String.html](http://download.oracle.com/javase/6/docs/api/java/lang/String.html)

[http://download.oracle.com/javase/6/docs/api/java/util/Formatter.html#syntax](http://download.oracle.com/javase/6/docs/api/java/util/Formatter.html#syntax)

---

### Post by stchman on 2011-06-06
Yes, use Formatter.

[PHP]
        Formatter f = new Formatter();
        String sValue = f.format( "%10.4f\n", value ).toString();
[/PHP]

---

### Post by EarnestLearner on 2011-06-06
I've been trying to use String.format() but it only works so far as I explicitly define a number of characters such that it adds white space. Since my strings vary in length I can't just add a static amount of white space as it won't make everything look centred. So far I haven't been able to find an argument in the printf or String.format methods that centre text within a given number of characters. Can you help me out with that?

Whoops. Will try Formatter.

---

### Post by Some Penguin on 2011-06-06
So, why don't you just  check the length of the string and calculate how many spaces you do need to add, and then add them?

---

### Post by EarnestLearner on 2011-06-06
I've tried using Formatter but when converting to string, I hit up a bunch of exceptions. String.format doesn't have that problem, but I can't fix my issue with that either.

```

String title = (headerFormatter.format("%10.4f", "Hello World!")).toString();
bufferedHeaderWriter.write(title);

Exception in thread "main" java.util.IllegalFormatConversionException: f != java.lang.String
    at java.util.Formatter$FormatSpecifier.failConversion(Formatter.java:3999)
    at java.util.Formatter$FormatSpecifier.printFloat(Formatter.java:2722)
    at java.util.Formatter$FormatSpecifier.print(Formatter.java:2667)
    at java.util.Formatter.format(Formatter.java:2433)
    at java.util.Formatter.format(Formatter.java:2367)
    at junk.main(junk.java:17)

```


Some Penguin, thank you! That should work. Certainly didn't think about it that way.

---

### Post by stchman on 2011-06-06
What are you trying to center the text in?  Standard output?  Text areas don't have a fixed width.

If you are developing a swing app and have a fixed width text field, you will need to get the length of the string ( .length() ), get the text field width ( .getColumns() ), then calculate how many spaces you will need to center the text.

Example.  If your text field is 80 columns and your string is 13 characters do the following:

80 (40 is the midpoint) columns.
int( 13 / 2 ) will yield an integer 6

40 - 6 = 34 (spaces you will need to be added to front of string.

Simply make a method.

[PHP]

     public String centerString( String inputString, int totalWidth ) {
        String centeredString = new String();
        String spaceString = new String();

        for( int i = 0; i < ( totalWidth / 2 - inputString.length() / 2 ); i++ ) {
            spaceString += " ";
        }
        
        centeredString = spaceString + inputString;
        return centeredString;
    }


[/PHP]

---


---
title: "Java Errors"
date: 2014-11-24
forum: Programming Talk
---

### Post by lordnam on 2014-11-24
Can anyone help me with these errors I get when I run the code.

Exception in thread "main" java.util.InputMismatchException
    at java.util.Scanner.throwFor(Scanner.java:864)
    at java.util.Scanner.next(Scanner.java:1485)
    at java.util.Scanner.nextInt(Scanner.java:2117)
    at java.util.Scanner.nextInt(Scanner.java:2076)
    at delete.main(delete.java:48)

---

### Post by ofnuts on 2014-11-24
If you google for it:
> 
public class InputMismatchException
extends [NoSuchElementException]("https://docs.oracle.com/javase/7/docs/api/java/util/NoSuchElementException.html") Thrown by a Scanner to indicate that the token  retrieved does not match the pattern for the expected type, or  that the token is out of range for the expected type.
 

Which in clear means that the Scanner cannot really recognize a valid number in what has been read. Check your input.

If, generally, it is  a good idea to split out the code into small functions, opening the file each time is not a good idea because:
[LIST=1]
[*]it's not very good for performance
[*]everything known about the file is lost. This includes how much has been read so far, which is why you end up using nextLine() all over the place. Create the scanner once and pass it as a parameter (and yes, that implies that you call your functions in the right order...).. or don't use these functions, because they become much less necessary.
[/LIST]

---


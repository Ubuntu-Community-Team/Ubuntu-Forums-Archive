---
title: "Questions in Java"
date: 2008-05-25
forum: Programming Talk
---

### Post by samurailink3 on 2008-05-25
I'm trying to read a file into an array... but I'm not quite sure how to go about it. I want to read each new line of the text file into a String array.. then break them down into individual characters.

How would I go about this? I've read some documentation on fileLoad, but this confused me even more...

On a side note... know of any good beginner documentation for Java? Yes, I have read and reviewed the links in the stickys, just wondering about your own personal opinion.

Thanks!!

---

### Post by Balazs_noob on 2008-05-25
hi samurailink3
there is 2 ways to open a text file in Java
with either a BufferedReader or a Scanner
if you wait a few minutes i give you code example ;)

by the way the SUN-s java tutorials are the best although a little long

here
[PHP]
package scan;

import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class Main {
    
    public static void main(String[] args) {
        try {
            Scanner sc = new Scanner(new File("in.txt"));
            String str;
            while (sc.hasNextLine()) {
                str = sc.nextLine();
                System.out.println(str);
            }
        } catch (FileNotFoundException ex) {}
    }
}
[/PHP]

---

### Post by achelis on 2008-05-25
Don't use scanner myself, but shouldn't you close it after reading ?

+1 for Sun's tutorials. Also the Javadoc is a good place to look.

[http://java.sun.com/javase/6/docs/api/]("http://java.sun.com/javase/6/docs/api/")

---

### Post by a9bejo on 2008-05-25
> **samurailink3 said:**
> I'm trying to read a file into an array

The Java SDK itself is not quite complete. There is a set of libraries from the ASF called [apache commons](http://commons.apache.org/) that fills all the gaps, and almost any java program I know makes heavy use of at least one of these components.  For example, the apache.commons.io library has a function to read a file into a list line by line:

[http://commons.apache.org/io/api-release/org/apache/commons/io/FileUtils.html#readLines(java.io.File](http://commons.apache.org/io/api-release/org/apache/commons/io/FileUtils.html#readLines(java.io.File))

So if you don't find some functionality in the JDK, your first step should be to scan the apache commons docs.


> **samurailink3 said:**
> On a side note... know of any good beginner documentation for Java?

[Head First Java](http://www.amazon.com/Head-First-Java-Kathy-Sierra/dp/0596009208) by Kathy Sierra is the easiest way to learn Java, if you are new to programming. 

[Thinking in Java](http://www.amazon.com/Thinking-Java-4th-Bruce-Eckel/dp/0131872486) by Bruce Eckel is the most detailed and complete book about the Language and its APIs.

As for online documentation, the Sun tutorials are the way to go.

---

### Post by Balazs_noob on 2008-05-25
> **achelis said:**
> shouldn't you close it after reading ?
oops yeah :D imagine that there guys ;)

---

### Post by samurailink3 on 2008-05-27
Ah-ha! There is another way of doing it! Sorry about this.. but I researched a while longer and figured it out, but thanks! I guess I should have updated my post, but I was so involved in my code, I guess I just forgot! Thanks!

---


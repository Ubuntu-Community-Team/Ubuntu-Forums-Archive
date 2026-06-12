---
title: "java scanner.nextLine problem"
date: 2006-10-28
forum: Programming Talk
---

### Post by Ramses de Norre on 2006-10-28
Hi,
I have a little problem with java, I use a scanner object to read contents from a file, mostly with the nextLine method.
Now I need to read the file twice (to get different data from it) and the first time goes perfect but when I then use my second method which needs to read the file again I get an error:
```
Exception in thread "main" java.util.NoSuchElementException: No line found
	at java.util.Scanner.nextLine(Scanner.java:1471)
	at create.readDude(create.java:61)
	at fileInputDriver.main(fileInputDriver.java:34)

```

I know that this is because nextLine tries to read past the end of the file but I can't find a method to let it start from the beginning of the file again.. Anyone who knows how to do this?

---

### Post by Tomosaur on 2006-10-28
Most languages require their nextLine function to be enclosed in a while loop which checks whether a line exists. Normally it's of the form:

while (File):
  read nextLine

etc, obviously adapted to your language. I can't remember the exact way of doing it in Java, but it will be similar to that.

---

### Post by Ramses de Norre on 2006-10-28
Yes I do so, but the problem is that java always reads the next line in the file but I can't seem to find a way to start reading from the beginning of the file again.
So I go through the file and indeed I check whether a new line exists with .hasNextLine() but then later in an other method I want to do this again for the whole file but java continues reading the file where my first method stopped and it reaches the end of the file immediately.. So I somehow need to tell java to start reading the file from the beginning again.

---

### Post by Tomosaur on 2006-10-28
Did you remember to close the file? You shouldn't leave files in memory unless they're actively being used. Once you've displayed the contents etc, you should close the file, then re-open it when you need to write or read again. This should move the pointer back to the first line.

---

### Post by Ramses de Norre on 2006-10-28
Ow that worked.
So I need to close the scanner and then make a new one for every time I need to read the file.

Thanks a lot;)

---

### Post by Tomosaur on 2006-10-28
You don't need to create a new scanner instance, just reuse the same one, calling open() and close() when necessary.

---

### Post by Ramses de Norre on 2006-10-29
There doesn't seem to be an open() method..
> The method open() is undefined for the type Scanner.

That's why I didn't try the close() method first, I couldn't find a method to open it again so it looked like a no go.

---

### Post by cggaldes on 2006-11-11
Did you use Scanner to open the file as well as read from it?

---

### Post by Ramses de Norre on 2006-11-12
I don't know what you mean exactly?
I made this method to give me a scanner to read the file:
```
import java.util.Scanner;
import java.io.FileNotFoundException;
import java.io.File;
import java.util.Locale;

/** 
 * 
 * @author Ramses de Norre
 *
 */

public class FileInput 
{
        public static Scanner initiateFile(String file)
        {
            Scanner result=null;
            
            try
            {
                result=new Scanner(new File(file));
                result.useLocale(new Locale("nl","BE"));
            }
            catch(FileNotFoundException e)
            {
                System.out.println("The file " +file+ " was not found!");
            }
            
            return result;
        }
}
```

I could then just use the next, nextLine, nextInt,... methods from Scanner on the file.

---


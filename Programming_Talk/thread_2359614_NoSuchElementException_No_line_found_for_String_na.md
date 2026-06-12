---
title: "NoSuchElementException: No line found for String nameOfPerson = kb.nextLine(). Why?"
date: 2017-04-25
forum: Programming Talk
---

### Post by s3a on 2017-04-25
Hello, everyone. :)

Could someone please help me figure out why this Java syntax
```
import java.util.Scanner;

public class MyClass {

	public static void main(String[] args) {
		
		Scanner kb = new Scanner(System.in);
	      	System.out.print("Enter your name.: ");
	      	String nameOfPerson = kb.nextLine();
	      	System.out.println(nameOfPerson);
	}
}
```

gives me this error
> Enter your name.: Exception in thread "main" java.util.NoSuchElementException: No line found
	at java.util.Scanner.nextLine(Scanner.java:1540)
	at MyClass.main(MyClass.java:10)?

I've been at it for a long time, but I'm having trouble figuring it out.

Any input would be GREATLY appreciated!

---

### Post by spjackson on 2017-04-26
You are supposed to call hasNext() before calling nextLine() to avoid the exception. Nevertheless, your code works for me when System.in is a terminal but throws the exception when it's /dev/null. How are you running your code? Is it from a terminal or an IDE?
```

$ java -version
java version "1.7.0_95"
OpenJDK Runtime Environment (IcedTea 2.6.4) (7u95-2.6.4-1~deb8u1)
OpenJDK 64-Bit Server VM (build 24.95-b01, mixed mode)
$ java MyClass
Enter your name.: fred
fred
$ java MyClass < /dev/null
Enter your name.: Exception in thread "main" java.util.NoSuchElementException: No line found
    at java.util.Scanner.nextLine(Scanner.java:1585)
    at MyClass.main(MyClass.java:10)
$

```

---

### Post by Rocket2DMn on 2017-04-26
It also worked for me at the terminal.  I can force that exception if I send a premature EOF (ctrl-d) before writing anything at the prompt though.  So if you're actually piping in a file to stdio, that could cause a problem if the file is empty.  As always with Java, you should check the "has" functions before trying to get a result, otherwise you'll need to catch the NoSuchElementException and respond appropriately (like maybe prompting again, or exiting gracefully).

---


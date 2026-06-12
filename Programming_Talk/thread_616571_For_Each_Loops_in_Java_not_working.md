---
title: "For Each Loops in Java not working?"
date: 2007-11-18
forum: Programming Talk
---

### Post by zizzdude on 2007-11-18
hey, I'm learning java, and learned about for each loops. but when I compile the code, it gives me an error.

here's the code:

public class ForEachTest
{
	public static void main(String[] args)
	{
		String[] names = {"fred","jane","eric"};
		
		for (String name : names)
		{
			System.out.println(name);
		}
	}
}


here's the output:

ForEachTest.java:7: ';' expected
                for (String name : names)
                                 ^
ForEachTest.java:11: illegal start of expression
        }
        ^
2 errors

---

### Post by Quikee on 2007-11-18
Your example compiles fine for me. Maybe you are using javac version less than 1.5 - as far as I know foreach was introduced in java 5.

Check the version with "javac -version"

---

### Post by Ramses de Norre on 2007-11-18
Search for **update-java-alternatives** on the forums, you'll find enough threads in which they explain how to set up java correctly.

---

### Post by zizzdude on 2007-11-18
> **Quikee said:**
> Your example compiles fine for me. Maybe you are using javac version less than 1.5 - as far as I know foreach was introduced in java 5.

Check the version with "javac -version"

strange, there isn't even a -version option for me on javac. :confused:

---

### Post by xlinuks on 2007-11-18
Here's what I have:
```

fox@fox-desktop:~$ javac -version
javac 1.6.0_03
fox@fox-desktop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

```
You should consider installing the latest version of the JDK from Sun:
```

sudo apt-get install sun-java6-jdk

```

---

### Post by jespdj on 2007-11-20
> **zizzdude said:**
> strange, there isn't even a -version option for me on javac. :confused:
That's because you are using an older Java version. The -version switch on javac (the compiler) only exists in newer versions.

Install a newer version of Java.

---


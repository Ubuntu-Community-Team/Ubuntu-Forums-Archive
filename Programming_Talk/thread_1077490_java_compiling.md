---
title: "java compiling?"
date: 2009-02-22
forum: Programming Talk
---

### Post by abhilashm86 on 2009-02-22
hi i just started java programming using head-first-java book, so i saw an example, how to compile java, take this one

file is jp1.java

> public class jp1
{
   public static void main {String[] args}
        {
        System.out.println("hey,");
        System.out.println("how u doing?");
        }
}



when i compiled, i got these errors,
abhilash@abhi:~$ javac jp1.java
----------
1. ERROR in jp1.java (at line 4)
	public static void main {String[] args} 
	                   ^^^^
Syntax error, insert ";" to complete ClassBodyDeclarations
----------
2. ERROR in jp1.java (at line 4)
	public static void main {String[] args} 
	                   ^^^^
void is an invalid type for the variable main
----------
3. ERROR in jp1.java (at line 4)
	public static void main {String[] args} 
	                                  ^^^^
Syntax error, insert ";" to complete BlockStatements

so do i need to any library functions at top as to c/c++,also should i write main() function?

---

### Post by simeon87 on 2009-02-22
Try the following:

```

public class jp1 {

	public static void main(String[] args) {
		System.out.println("hey,");
		System.out.println("how u doing?");
	}
}

```

You had curly braces instead of parenthesis around String[] args.

---

### Post by CptPicard on 2009-02-22
```

public static void main**(String[] args)** {...

```

---

### Post by abhilashm86 on 2009-02-22
> **simeon87 said:**
> 

You had curly braces instead of parenthesis around String[] args.
abhilash@abhi:~$ java jp1
hey,
how u doing?

yea ur right i compiled it,thanks:) also we are not writing main() function unlike in c/c++/python, i just started java, so bit confused:)

---

### Post by cabalas on 2009-02-22
> **abhilashm86 said:**
> also we are not writing main() function unlike in c/c++/python, i just started java, so bit confused:)

You do still write it, but now it is a static function of a class instead of being off by its own.

---


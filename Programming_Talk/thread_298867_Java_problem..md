---
title: "Java problem."
date: 2006-11-13
forum: Programming Talk
---

### Post by hoagie on 2006-11-13
I just started programing and I wrote my first program today. But! I can't work this out. The program runs fine in eclipse and there are no bugs detected. Although when I try to open the *.class nothing happens.
Heres the code if you need it. ```
public class Hello1 {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		// TODO Auto-generated method stub


	 System.out.println("Hello stupid world!");
	
	}

}

```

---

### Post by Blacktalon on 2006-11-13
I am sorry but I really must ask, why are you trying to open your class file, and where are you trying to open from?

And if its eclipse well, I really don't like eclipse to much but for fixing errors.  You might wanna try doing it in your terminal, and go to your directory(which contains the program and class file) and just do put this into your command line:  vi Hello1.class or if you have emacs do emacs Hello1.class (I prefer emacs myself).

Anyways that should open it....I think, I usually don't mess with it to much myself.

Good Luck,
~BT

---

### Post by hoagie on 2006-11-13
I tried the vi command and got this error message:
```
Êþº¾^@^@^@1^@"^G^@^B^A^@^FHello1^G^@^D^A^@^Pjava/lang/Object^A^@^F<init>^A^@^C()V^A^@^DCode
^@^C^@  ^L^@^E^@^F^A^@^OLineNumberTable^A^@^RLocalVariableTable^A^@^Dthis^A^@^HLHello1;^A^@^Dmain^A^@^V([Ljava/lang/String;)V   ^@^Q^@^S^G^@^R^A^@^Pjava/lang/System^L^@^T^@^U^A^@^Cout^A^@^ULjava/io/PrintStream;^H^@^W^A^@^SHello stupid world!
^@^Y^@^[^G^@^Z^A^@^Sjava/io/PrintStream^L^@^\^@^]^A^@^Gprintln^A^@^U(Ljava/lang/String;)V^A^@^Dargs^A^@^S[Ljava/lang/String;^A^@
SourceFile^A^@^KHello1.java^@!^@^A^@^C^@^@^@^@^@^B^@^A^@^E^@^F^@^A^@^G^@^@^@/^@^A^@^A^@^@^@^E*·^@^H±^@^@^@^B^@
^@^@^@^F^@^A^@^@^@^B^@^K^@^@^@^L^@^A^@^@^@^E^@^L^@^M^@^@^@      ^@^N^@^O^@^A^@^G^@^@^@7^@^B^@^A^@^@^@   ²^@^P^R^V¶^@^X±^@^@^@^B^@
^@^@^@
^@^B^@^@^@
^@^H^@^L^@^K^@^@^@^L^@^A^@^@^@  ^@^^^@^_^@^@^@^A^@ ^@^@^@^B^@!

```
Well the message did actually appear but with all this crap.

---

### Post by hod139 on 2006-11-13
> **hoagie said:**
> I just started programing and I wrote my first program today. But! I can't work this out. The program runs fine in eclipse and there are no bugs detected. Although when I try to open the *.class nothing happens.
You can't open .class files in a text editor.  Those files are the Java byte-code.  You want to open .java files in a text editor.  If you want to run your java program, you use the java command.

```
java Hello1
``` (leave the .class extension off)

---

### Post by Ramses de Norre on 2006-11-13
> **hoagie said:**
> I tried the vi command and got this error message:
```
Êþº¾^@^@^@1^@"^G^@^B^A^@^FHello1^G^@^D^A^@^Pjava/lang/Object^A^@^F<init>^A^@^C()V^A^@^DCode
^@^C^@  ^L^@^E^@^F^A^@^OLineNumberTable^A^@^RLocalVariableTable^A^@^Dthis^A^@^HLHello1;^A^@^Dmain^A^@^V([Ljava/lang/String;)V   ^@^Q^@^S^G^@^R^A^@^Pjava/lang/System^L^@^T^@^U^A^@^Cout^A^@^ULjava/io/PrintStream;^H^@^W^A^@^SHello stupid world!
^@^Y^@^[^G^@^Z^A^@^Sjava/io/PrintStream^L^@^\^@^]^A^@^Gprintln^A^@^U(Ljava/lang/String;)V^A^@^Dargs^A^@^S[Ljava/lang/String;^A^@
SourceFile^A^@^KHello1.java^@!^@^A^@^C^@^@^@^@^@^B^@^A^@^E^@^F^@^A^@^G^@^@^@/^@^A^@^A^@^@^@^E*·^@^H±^@^@^@^B^@
^@^@^@^F^@^A^@^@^@^B^@^K^@^@^@^L^@^A^@^@^@^E^@^L^@^M^@^@^@      ^@^N^@^O^@^A^@^G^@^@^@7^@^B^@^A^@^@^@   ²^@^P^R^V¶^@^X±^@^@^@^B^@
^@^@^@
^@^B^@^@^@
^@^H^@^L^@^K^@^@^@^L^@^A^@^@^@  ^@^^^@^_^@^@^@^A^@ ^@^@^@^B^@!

```
Well the message did actually appear but with all this crap.

That's not an error message, that's binary you're looking at ;)

---

### Post by hoagie on 2006-11-13
Even with java Hello I get: Exception in thread "main" java.lang.NoClassDefFoundError: Hello

---

### Post by sdrubolo on 2006-11-13
you have to issue the command "java Hello1" this because you've called the class Hello1 so that you have to call it from the folder where the all java stuff is stored

---

### Post by hoagie on 2006-11-13
Thanks that solved it.

---


---
title: "[SOLVED] [Java] Problem Compiling first program"
date: 2008-01-17
forum: Programming Talk
---

### Post by TreeFinger on 2008-01-17
I am copying this directly from my book. I don't think I have missed anything..

[php]
public class Lincoln 
{
public static void main (String[] args) 
		{
		System.out.println ("A quote by Abraham Lincoln:");
		
		System.out.println ("Whatever you are, be a good one.");
	}
}
[/php]

```

@home_base:~>javac firstprog.java
firstprog.java:8: error: The public type Lincoln must be defined in its own file
        public class Lincoln 
                     ^^^^^^^
1 problem (1 error)

```

---

### Post by TreeFinger on 2008-01-17
I got it to compile
[php]
class Lincoln 
{

public static void main (String[] args) 
		{
		System.out.println ("A quote by Abraham Lincoln:");
		
		System.out.println ("Whatever you are, be a good one.");
	}
}
[/php]

I guess I shouldn't have ran like a little baby to the forums so quickly. Could anyone tell me why removing Public from line 1 made a difference?

---

### Post by CptPicard on 2008-01-17
Because a "public class X" must be defined in a file called X.java... if the class it's not "public", its visibility is "package" (which is stated by simply leaving the visibility identifier out), and I suppose you can define that in whatever the file is called. Never written a standalone package-visible class though.

---

### Post by geirha on 2008-01-17
In other words, if the code in your first post had been in a file called "Lincoln.java", it would have worked :)

---

### Post by naugiedoggie on 2008-01-17
> **TreeFinger said:**
> I am copying this directly from my book. I don't think I have missed anything..

[php]
public class Lincoln 
{
public static void main (String[] args) 
		{
		System.out.println ("A quote by Abraham Lincoln:");
		
		System.out.println ("Whatever you are, be a good one.");
	}
}
[/php]

```

@home_base:~>javac firstprog.java
firstprog.java:8: error: The public type Lincoln must be defined in its own file
        public class Lincoln 
                     ^^^^^^^
1 problem (1 error)

```

Hello,

Are you taking a class using the Lewis & Lofton book, or are you studying it on your own?  A good self-study resource is _Head First Java_ by Sierra & Bates.  I used to think these books were doofy, but after using this one, I swear by them.  There's no "easy way" to learn Java, but this book does a great job of providing both readable explanations for understanding and drills for practice & retention. 

Thanks.
mp

---


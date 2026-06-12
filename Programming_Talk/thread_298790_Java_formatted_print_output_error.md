---
title: "Java formatted print output error"
date: 2006-11-13
forum: Programming Talk
---

### Post by Kirky_D on 2006-11-13
Hello all!

I am currently learning java, just started. I have come to formatting the output of a print statement. 

This is my code:

```
public class MathExercise2 {
  public static void main(String[] args) {
	
	double speed, distance = 5, time = 3;
	
	speed = distance/time;
	
	System.out.printf("The speed is %4.2f", speed);
  }
}
```

the code compile fine, but it won't run, giving me this error:

Exception in thread "main" java.lang.NoSuchMethodError: method java.io.PrintStream.printf with signature (Ljava.lang.String;[Ljava.lang.Object;)Ljava.io.PrintStream; was not found.
   at MathExercise2.main(MathExercise2.java:11)

I think that maybe i have a class library missing. Does anybody know whats going on?

Cheers all!

---

### Post by ape on 2006-11-13
Your program worked fine for me here.  Off hand, I would say that you are using a Java version less than 1.5 (you can check by executing 'java -version').  The printf statement only appeared in JDK 1.5.

---

### Post by Kirky_D on 2006-11-13
Sorted cheers! I didn't edit /etc/jvm correctly. All is well now!

---


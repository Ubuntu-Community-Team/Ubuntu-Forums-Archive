---
title: "interface pgm in java"
date: 2010-08-05
forum: Programming Talk
---

### Post by navaneethan on 2010-08-05
```
interface First{
	int firstMethod();
	int secondMethod();
	}
interface Second extends First{
	int thirdMethod();
	}
class MyClass implements Second{
	public int thirdMethod()
	{
		System.out.println("THIS IS THE IMPLEMENTED INTERFACE");
	}
}
public class MyMain{
	public static void main(String args[])
	{
		MyClass m = new MyClass();
		m.thirdMethod();
	}
}




```

Here I couldn't get the expected output may i know the problem here and give some suggestion about this

---

### Post by Some Penguin on 2010-08-05
Your problem appears to be that you've not bothered to learn the actual meaning of keywords like 'class', 'interface', and 'extends'.   The code as presented won't compile, because your class lacks implementations for methods belonging to the interface that it supposedly implements.  

Please read the sticky threads for information on learning languages so you can develop a more logical approach to learning than whatever it is that you happen to be doing now.

---

### Post by Queue29 on 2010-08-05
What do you expect to happen when you call firstMethod() and secondMethod()?

You failed to implement them in your base class. The code won't compile, because it's incomplete. 

```

public static void main(String args[])
	{
		MyClass m = new MyClass();
		m.thirdMethod();
                m.firstMethod(); // ???
                m.secondMethod(); // ?????
	}

```

---

### Post by KdotJ on 2010-08-05
> **Some Penguin said:**
> Your problem appears to be that you've not bothered to learn the actual meaning of keywords like 'class', 'interface', and 'extends'.

Lol indeed.
To the OP, is this homework of some sort? How long have you been studying Java (or programming for that matter)?

---

### Post by navaneethan on 2010-08-05
This is not mine homework because i just got the output and while i understand the reason for this output i got stuck thats why sharing here?
i am not a school boy to do homework ;-) as well as i am not the expert like you ;-) just to know the exact reason i stepped here ;-) please mind it ;-)

---

### Post by KdotJ on 2010-08-06
Ok well, do you understand what an interface is? Do you understand how they are used?
Do you know what the keyword 'extends' means?

---

### Post by navaneethan on 2010-08-06
well it was a nice explanation done it :-)

---

### Post by KdotJ on 2010-08-06
I'm very confused but hey.So have you solved your problem?

---

### Post by navaneethan on 2010-08-07
yes done dude I have understood what i want :-) thanks for your participation If anything wrong in my side meant i apologise

---

### Post by KdotJ on 2010-08-07
Well done on the fix

---


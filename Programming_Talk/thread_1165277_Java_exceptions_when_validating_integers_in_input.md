---
title: "Java exceptions when validating integers in input"
date: 2009-05-20
forum: Programming Talk
---

### Post by cdiem on 2009-05-20
There is a simple program I'm doing while learning java, and this method in it:

[PHP]	public static int captureInput() {
		System.out.println("Please enter a number between 0 and 7: ");
		Scanner sc = new Scanner(System.in);
		int i = sc.nextInt();
		if (i < 0 || i > 7) {
			System.err.println("The input is not between 0 and 7; ");
		}
		return i;
	}
[/PHP]

This is supposed to read an integer (between 0 and 7) from the console.
However, when a user enters for instance "cool" instead of "5", this brings out InputMismatchException. When adding an try-catch construct, the method complains, that it should return an 'int' by definition and refuses to compile. Now I know it's pertty easy, but I have searched all over the internet and I was no able to find anything similar to that (the continual entering of digits in my program is in a 'while' loop in the main method, but that's not that important). So, basically, how do I check the input for non-integer input here? I mean, I was not able to try-catch it in a running code. Thanks in advance.

---

### Post by Reiger on 2009-05-20
I suppose you do:
```

try {
 int temp;
 /* code that sets temp but may cause exceptions */
 return temp;
}
catch(Exception e) {
 /* where are you returning an int now? */
}

```

Note that this is not a (general) solution either:
```

int result;
try {
 int temp;
 /* same constructs as before */
 result = temp;
}
catch(Exception e) {
 /* what do you assign to result now? */
}
return result;

```

Instead use a throws clause in the method signature, and let the exception propagate to the caller this way. Then do the error handling in the caller method that knows what to do on errors.

EDIT: You may want to read up on (Java) exceptions if you don't understand my first example immediately.

---

### Post by simeon87 on 2009-05-20
InputMismatchException is a subclass of a RuntimeException which means that you don't explicitly need to write a catch for it (or adding a throws to the method). Basically, this means that it should not occur and in case it does, the application lacks validation code to prevent it from occurring.

In your case, you're writing sc.nextInt() under the assumption that the user will enter correct input. But you can't build an application under that assumption so you'll have to check yourself that the input only contains digits and then you can parse it into an integer.

---

### Post by cdiem on 2009-05-20
@ Reiger - using a 'throws' here seems to make life easier. Thank you  for that. 

@ simeon87 - Would it be a better practice to catch what's entered from the user as a String and then use a regex to filter it? 
I'm sorry if my questions are too basic - I'm just learning on the stuff.

---


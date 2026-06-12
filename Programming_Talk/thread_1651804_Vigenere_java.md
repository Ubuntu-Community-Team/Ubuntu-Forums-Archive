---
title: "Vigenere java"
date: 2010-12-23
forum: Programming Talk
---

### Post by matty-guy on 2010-12-23
Okay, so I'm trying to create a Vigenere encoder, and the program *almost* works. The programs very basic at the moment, as I want the fundamentals to work first, rather than building the fundamentals into the program.

```
import java.util.Scanner;

public class grrrr {
	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);
		String input, key, encrypt="";
		int inputlength;
		
		System.out.println("\nPlease enter the message.");
		input = sc.nextLine();
		
		System.out.println("\nPlease enter the message.");
		key = sc.nextLine();
		
		for (int i = 0; i < input.length(); i++) {
			int hello = key.charAt(i) - 'a';
			int letter = input.charAt(i) - 'a';
		
			int result = (letter + (hello % 26)) ;
			result = result + 'a';
		
			encrypt += (char) result;
		}
	
		System.out.println("\n" + encrypt);
			
		}
	}
```

The problem is, if I use attack as the input and lemonl as the key, the output is lxopv, where it should actually be lxfopv. The problem persists with inputs and keys of longer length as well. Any idea what's wrong? Thanks.

---

### Post by Some Penguin on 2010-12-23
```

(a + (b % c)) != (a+b) % c

```

You have an unused variable inputLength;  don't check whether the input and the key are the same length; should check whether characters are actually lowercase non-multibyte letters before assuming that they are; and should be using StringBuilder instead of string addition.

---

### Post by matty-guy on 2010-12-23
> **Some Penguin said:**
> ```

(a + (b % c)) != (a+b) % c

```

You have an unused variable inputLength;  don't check whether the input and the key are the same length; should check whether characters are actually lowercase non-multibyte letters before assuming that they are; and should be using StringBuilder instead of string addition.

Thanks for the correction. I did say the program was very basic, I wanted to get it right with assumptions before I added the other stuff you'd listed. And I'll check out StringBuilder now, thanks.

---


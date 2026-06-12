---
title: "What is wrong with my calculator program?"
date: 2010-02-07
forum: Programming Talk
---

### Post by thedarklaith on 2010-02-07
Hi, I've just started learning java for fun (yes, I know it's nerdy)and i've been at it for almost a week now and this is a basic program I'm trying to develop:
```

import java.util.Scanner;
public class Calculator {
	public static void main (String [] args){
		Scanner text = new Scanner(System.in);
		double num1, num2, answer;
		String operator;
		System.out.println ("Basic Calculator");
		System.out.println ("Enter the firat number then press return, then enter the operator (+, -, *, /) then press the return key,") ;
		System.out.println ("then enter the second number and press the return key. The result will be displayed on the screen: ");
		num1 = text.nextDouble ();
		operator = text.nextLine();
		
		if (operator.equals("+")){
			num2 = text.nextDouble();
			answer = num1 + num2;
			System.out.println(answer);
		}
		if (operator.equals("-")){
			num2 = text.nextDouble();
			answer = num1 - num2;
			System.out.println(answer);
		}
		if (operator.equals("*")){
			num2 = text.nextDouble();
			answer = num1 * num2;
			System.out.println(answer);
		}
		if (operator.equals("/")){
			num2 = text.nextDouble();
			answer = num1 / num2;
			System.out.println(answer);
		}
	}	
}
```
and for some reason I can't enter the operator. I tried putting "num2 = text.nextDouble();" outside of the if statements but that didn't work either.
Thanks in advance :)

---

### Post by Ferrat on 2010-02-07
well first I would add a check that says what happens if it's not an operator, then I would separate the calculation and input 

first take first number 
then take operator
then second number 

then calculation 

then result.

---

### Post by falconindy on 2010-02-07
You'll want to look at the difference between Scanner.next() and Scanner.nextLine()

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html)

FYI, your code works as you describe with only one minor change. It's far from ideal though. Your multiple if/then constructs should be a single if/then/elseif or a switch/case...

```
if (operator.equals("+")) {
    //add
} elseif (operator.equals("-")) {
    //subtract
} elseif (operator.equals("*")) {
    //multiply
} elseif (operator.equals("/")) {
    //divide
} else {
    //user didn't enter a valid operator. scold them mercilessly.
}
```

---

### Post by thedarklaith on 2010-02-07
Thanks for the answer but could you put some sample code to explain. As I said I've only been using it for about a week so I'm kind of a noob :)

---

### Post by thedarklaith on 2010-02-07
Thanks falconindy, i used this program and it worked:
```

import java.util.*;
public class Calculator {
	public static void main (String [] args){
		Scanner text = new Scanner(System.in);
		double num1, num2, answer;
		String operator;
		System.out.println ("Basic Calculator");
		System.out.println ("Enter the firat number then press return, then enter the operator (+, -, *, /) then press the return key,") ;
		System.out.println ("then enter the second number and press the return key. The result will be displayed on the screen: ");
		num1 = text.nextDouble ();
		operator = text.next();
		num2 = text.nextDouble();
		
		
		if (operator.equals("+")){
			answer = num1 + num2;
			System.out.println(answer);
		}
		if (operator.equals("-")){
			answer = num1 - num2;
			System.out.println(answer);
		}
		if (operator.equals("*")){
			answer = num1 * num2;
			System.out.println(answer);
		}
		if (operator.equals("/")){
			answer = num1 / num2;
			System.out.println(answer);
		}
	}	
}

```
well... I haven't fully tested it yet but it works for multiplication :)
thanks a lot
edit: works fine, I also added an else statement incase someone enters something different

---

### Post by thedarklaith on 2010-02-14
Ok this is my updated calculator working perfectly XD, there is a debug code but Obviously it's off:
```

import java.util.Scanner;

public class CalculatorTwo {
public static void main (String [] args){

System.out.println ("Basic Calculator");

System.out.println ("Enter the firat number, the operator (+, -, *, /) then the second number") ;

System.out.println ("separating them by a space. The result will be displayed on the screen: ");

boolean isDebug=false;

while (true) {

double num1, num2, answer;

String operator = "";

Scanner text = new Scanner(System.in);

num1 = text.nextDouble ();

if (isDebug) System.out.print("\n>>> Debug msg: num1 ="+num1+ "\n");

operator = text.next();

if (isDebug) System.out.print("\n>>> Debug msg: operator ="+operator + "\n");

num2 = text.nextDouble();

if (isDebug) System.out.print("\n>>> Debug msg: num2 ="+num2+ "\n");

if (operator.equals("+")){

answer = num1 + num2;

System.out.println(answer);

num1 = answer;

}

else if (operator.equals("-")){

answer = num1 - num2;

System.out.println(answer);

}

else if (operator.equals("*")){

answer = num1 * num2;

System.out.println(answer);

}

else if (operator.equals("/")){

answer = num1 / num2;

System.out.println(answer);

}else {

System.out.println ("Input is invalid");

}
}
}

} 

```

The codes probably easier to read here:
[http://pastebin.com/f2993653e](http://pastebin.com/f2993653e)
Thanks guys for helping me make it

---


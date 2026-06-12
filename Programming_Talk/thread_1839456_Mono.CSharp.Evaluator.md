---
title: "Mono.CSharp.Evaluator"
date: 2011-09-05
forum: Programming Talk
---

### Post by Dr Belka on 2011-09-05
So I'm using C# and gtk# to write a simple calculator program as a programming exercise.  I'm trying to figure out a way to evaluate string expressions and get the result.  Python has the built in eval() function for this.  

I've been trying to use the Mono.CSharp.Evaluator to accomplish what I need, but I'm getting some errors.  I wrote a simple program to demonstrate what is going on.


```
using System;
using Mono.CSharp;

namespace EvaluatorTest
{
	class MainClass
	{
		public static void Main (string[] args)
		{
			string exp = "5 + 5";
			Evaluator.Run("using System;");
			int answer = (int)Evaluator.Evaluate (exp);
			Console.WriteLine (answer);
		}
	}
}
```

I want "10" to be printed to the screen.

When running this code I get the following error:

> Unhandled Exception: System.ArgumentException: Syntax error on input: partial input
  at Mono.CSharp.Evaluator.Evaluate (System.String input) [0x00000] in <filename unknown>:0 
  at EvaluatorTest.MainClass.Main (System.String[] args) [0x00011] in /home/william/Documents/Development/Mono/EvaluatorTest/EvaluatorTest/Main.cs:32

I have never successfully used the Evaluator class, so this error could be a result of my improper use, but I do not know how to fix it.  

Does anyone know how to fix this/what I am doing wrong?

---

### Post by sundowndk on 2011-11-27
I know its been awhile since this post was made, but others out there may find this post, I did. And the answer is very simple. 

The expression string: "5 + 5" needs to end with ";" like a normal C# code line.

A new example should look like this:'

```
using System;
using Mono.CSharp;

namespace EvaluatorTest
{
	class MainClass
	{
		public static void Main (string[] args)
		{
			string exp = "5 + 5;";
			Evaluator.Run("using System;");
			int answer = (int)Evaluator.Evaluate (exp);
			Console.WriteLine (answer);
		}
	}
}
```

---


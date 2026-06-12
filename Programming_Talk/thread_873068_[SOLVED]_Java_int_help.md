---
title: "[SOLVED] Java int help"
date: 2008-07-28
forum: Programming Talk
---

### Post by bostonaholic on 2008-07-28
*Java 1.4.2_13*
What would I expect to see printed with the following:
```
int x = 3, y = 4;
panel.getTextField().setText("Sum: " + (x + y));
```
Should I see
```
Sum: 7
```
or
```
Sum: 34
```

In a nutshell what I really want to know is...
Does Java do int math inside the ()'s or will it use the + as string concatenation?

Thanks.

---

### Post by mike_g on 2008-07-28
Why dont you try it?

---

### Post by bostonaholic on 2008-07-28
> **mike_g said:**
> Why dont you try it?

I don't have a quick way to setup a new project or integrate it into our current app and run a 70min build.

Just figured asking would be faster.

---

### Post by dribeas on 2008-07-28
> **bostonaholic said:**
> I don't have a quick way to setup a new project or integrate it into our current app and run a 70min build.

Just figured asking would be faster.

Fast answer: String + operator concatenates, while int + operator adds. Now just follow precedence:

```

String txt43 = "txt" + 4 + 3; // precedence from left to right
String txt7 = "txt" + (4+3); // parenthesis override precedence

```

You can make a simple test with just a text editor and a command-line compiler.

David

P.S. I don't quite see how you can end up with 70min compile time in Java... unless you clear la .class files before starting to compile. Use Build instead of Rebuild in your favorite IDE.

---

### Post by bostonaholic on 2008-07-28
> **dribeas said:**
> Fast answer: String + operator concatenates, while int + operator adds. Now just follow precedence:

```

String txt43 = "txt" + 4 + 3; // precedence from left to right
String txt7 = "txt" + (4+3); // parenthesis override precedence

```

You can make a simple test with just a text editor and a command-line compiler.

David

P.S. I don't quite see how you can end up with 70min compile time in Java... unless you clear la .class files before starting to compile. Use Build instead of Rebuild in your favorite IDE.

Thanks.

What I meant about the 70min build time was if I were to insert the code into our application here at work then test from inside there.  And yes, our build time is about 60-70 minutes on a windows machine... which is why I use Linux for development; only a 36min build.

---

### Post by bostonaholic on 2008-07-28
> **dribeas said:**
> Fast answer: String + operator concatenates, while int + operator adds. Now just follow precedence:

```

String txt43 = "txt" + 4 + 3; // precedence from left to right
String txt7 = "txt" + (4+3); // parenthesis override precedence

```

You can make a simple test with just a text editor and a command-line compiler.

David

P.S. I don't quite see how you can end up with 70min compile time in Java... unless you clear la .class files before starting to compile. Use Build instead of Rebuild in your favorite IDE.

Thanks for the command line compiler hint, it's been awhile since I've used this windows machine... let alone using javac... it's been awhile.

I tried it and yes you were right with your answer.

---

### Post by Zugzwang on 2008-07-29
If it takes you >30 minute to compile although you are only making a minor change, you are doing something wrong. Java should only recompile the files in which you actually did changes. However, if you change the methods of a class, you will have to recompile more but that should be done automatically.

BTW: You don't have to possibility to quickly make a new setup? There must be something wrong with your IDE configuration...

---

### Post by drubin on 2008-07-29
> **Zugzwang said:**
> If it takes you >30 minute to compile although you are only making a minor change, you are doing something wrong. Java should only recompile the files in which you actually did changes. However, if you change the methods of a class, you will have to recompile more but that should be done automatically.

BTW: You don't have to possibility to quickly make a new setup? There must be something wrong with your IDE configuration...

I agree even the very very big java projects out there only take about 3mins max to compile that that is maily because of each plugin that gets compiled separately.

---


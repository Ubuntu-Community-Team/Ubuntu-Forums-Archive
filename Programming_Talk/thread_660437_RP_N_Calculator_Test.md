---
title: "RP N Calculator Test"
date: 2008-01-06
forum: Programming Talk
---

### Post by LaRoza on 2008-01-06
Here is an [RPN Calculator]("http://laroza.freehostia.com/home/apps/rpn/default.html") I wrote for the web. I plan on making an Opera widget out of it, but would like your opinions/criticism of the script.

Just type the expression in the first text field and press enter.

---

### Post by AlexThomson_NZ on 2008-01-06
Pretty nice- tried to stump it but seems pretty robust- even differentiates between +ve and -vi infinity.

Out of curiosity what do you use RPN for so much you would make a widget from it?

---

### Post by LaRoza on 2008-01-06
> **AlexThomson_NZ said:**
> Pretty nice- tried to stump it but seems pretty robust- even differentiates between +ve and -vi infinity.

Out of curiosity what do you use RPN for so much you would make a widget from it?

I like postfix notation over infix, and wanted an app I can use when browsing. You can see [http://laroza.freehostia.com](http://laroza.freehostia.com) under "Web Applications" for little programs I wrote. 

I mainly wanted to write the script, which is very simple:

[php]
window.onload = function()
{
    var rpn = document.getElementById("rpn");
    document.getElementById("inpu").focus();
    rpn.onsubmit = function()
    {
        var inpu = document.getElementById("inpu").value.split(" ");
        var stack = new Array();
        var total;
        for (var i = 0; i < inpu.length; i++)
        {
            if (inpu[i] == '+')
            {
                    total = stack.pop() + stack.pop();
                    stack.push(total);
            }
            else if (inpu[i] == '*')
            {
                total = stack.pop() * stack.pop();
                stack.push(total);
            }
            else if (inpu[i] == '-')
            {
                total = -stack.pop() + stack.pop();
                stack.push(total);
            }
            else if (inpu[i] == '/')
            {
                var first = stack.pop();
                total = stack.pop() / first;
                stack.push(total);
            }
            else if (inpu[i] == '^')
            {
                var first = stack.pop();
                total = Math.pow(stack.pop(),first); 
            }
            else
            {
                stack.push(parseFloat(inpu[i]));
            }            
        }
        document.getElementById("outpu").value = total;
        return false;
    }


}

[/php]

Any error messages come from the JavaScript engine, not from me.

---

### Post by Wybiral on 2008-01-06
Not bad, but can you write an infix-to-postfix compiler so it can evaluate infix expressions? :)

---

### Post by Compyx on 2008-01-07
> **Wybiral said:**
> Not bad, but can you write an infix-to-postfix compiler so it can evaluate infix expressions? :)

Yes, that is a much more interesting problem, I personally use Dijkstra's "shunting yard" algorithm for that, but there are other approaches.

By the way, doesn't Javascript have switch statements?

---

### Post by popch on 2008-01-07
I did a short spot check. It runs fine in Windows XP and Firefox 1.5.0.1.

I would differentiate the input tokens into three cases: 
[LIST=1]
[*]recognized operation
[*]recognized number
[*]anything else (such as 'foo' or //)[/LIST]Reasons: leaves your virtual calculator under all circumstancces in a defined state; makes later addition of more functions easier; makes implementation of the following suggestion simpler; allow later extensions such as converting between numbers of different bases.

I also would place the handling of the stack in a central location such that the code appears once and only once in the program, and make only the execution of the recognized operation dependent on the operation code.

Reasons: makes any kind of enhancements easier, such as adding new operations. Also makes it possible to add features such as 'history' which would require additional sttements to be executed before or after each operation.

I would introduce a 'table' which states for each op code the number of arguments it takes off the stack, even if at the moment that number is 'one' for every op code supported. 

Reason: makes it much easier to introduce operations at a later time which affect more or less than two operands in the stack (such as 'reverse sign' or 'pi')

As you can see, all my suggestions point towards later extensions which - in my experience - are certain to come.

---

### Post by LaRoza on 2008-01-07
> **popch said:**
> I did a short spot check. It runs fine in Windows XP and Firefox 1.5.0.1.

I would differentiate the input tokens into three cases: 
[LIST=1]
[*]recognized operation
[*]recognized number
[*]anything else (such as 'foo' or //)[/LIST]Reasons: leaves your virtual calculator under all circumstancces in a defined state; makes later addition of more functions easier; makes implementation of the following suggestion simpler; allow later extensions such as converting between numbers of different bases.

I also would place the handling of the stack in a central location such that the code appears once and only once in the program, and make only the execution of the recognized operation dependent on the operation code.

Reasons: makes any kind of enhancements easier, such as adding new operations. Also makes it possible to add features such as 'history' which would require additional sttements to be executed before or after each operation.

I would introduce a 'table' which states for each op code the number of arguments it takes off the stack, even if at the moment that number is 'one' for every op code supported. 

Reason: makes it much easier to introduce operations at a later time which affect more or less than two operands in the stack (such as 'reverse sign' or 'pi')

As you can see, all my suggestions point towards later extensions which - in my experience - are certain to come.

Very good advice, in fact, it is similar to the RPN calculator I once I wrote in C. However, this is in ECMAScript, and is only going to be a simple Opera Widget in the future.

---

### Post by LaRoza on 2008-01-07
> **Compyx said:**
> Yes, that is a much more interesting problem, I personally use Dijkstra's "shunting yard" algorithm for that, but there are other approaches.

By the way, doesn't Javascript have switch statements?

Yes it does. 

Why don't I use them? Good question, I wrote this late at night, and actually only wrote it for only one operator (+) to test it. Then I added the others, copy and paste and a little edit.

Why don't I make it convert infix to post fix? Because that wasn't the point of the app, and ECMAScript has an "eval" function and ECMAScript uses infix so it would be pointless in this language and for my purpose which was to prototype an RPN calculator for an Opera Widget for my personal use.

---

### Post by Wybiral on 2008-01-07
> **LaRoza said:**
> Yes it does. 

Why don't I use them? Good question, I wrote this late at night, and actually only wrote it for only one operator (+) to test it. Then I added the others, copy and paste and a little edit.

Why don't I make it convert infix to post fix? Because that wasn't the point of the app, and ECMAScript has an "eval" function and ECMAScript uses infix so it would be pointless in this language and for my purpose which was to prototype an RPN calculator for an Opera Widget for my personal use.

I don't like using the switch case these days. It's too cluttered having to type all of that case/break crap. I think the else/if way looks cleaner. As for the RPN not having an infix compiler, it may not serve an immediate purpose, but it's a common learning exercise (plus, it's fun). You could write an entire C compiler in ECMAScript if you wanted to, and then there would be a purpose for the infix-to-postfix converter! :)

---

### Post by LaRoza on 2008-01-07
> **Wybiral said:**
> I don't like using the switch case these days. It's too cluttered having to type all of that case/break crap. I think the else/if way looks cleaner. As for the RPN not having an infix compiler, it may not serve an immediate purpose, but it's a common learning exercise (plus, it's fun). You could write an entire C compiler in ECMAScript if you wanted to, and then there would be a purpose for the infix-to-postfix converter! :)

I avoid switches usually also, mainly because they are not consistant across languages.

It would be a very good learning exericise, but my next step is making the Opera Widget.

It would be fun, and I will be doing it soon because of this.

I think I will skip on writing a C compiler in ECMAScript....

---

### Post by popch on 2008-01-07
Slightly off topic, but I just remembered that practically my first application in a language similar to ECMAscript was an RPN calculator. The language was NewtonScript, the language built into Apple's first PdA. The calculator supported one (1) operation, which was '+'.

Have fun.

---

### Post by LaRoza on 2008-01-07
> **popch said:**
> Slightly off topic, but I just remembered that practically my first application in a language similar to ECMAscript was an RPN calculator. The language was NewtonScript, the language built into Apple's first PdA. The calculator supported one (1) operation, which was '+'.

Have fun.

Why didn't you add the others?

---

### Post by popch on 2008-01-07
> **LaRoza said:**
> Why didn't you add the others?

I wasn't interested in having a calculator, I just wanted to test if I understood the IDE and language. It worked fine, so I dropped the exercise.

---

### Post by LaRoza on 2008-01-07
> **popch said:**
> I wasn't interested in having a calculator, I just wanted to test if I understood the IDE and language. It worked fine, so I dropped the exercise.

I did the same for my C calculator...

When I wrote this one, it was only for addition to test it, then I added the others.

---


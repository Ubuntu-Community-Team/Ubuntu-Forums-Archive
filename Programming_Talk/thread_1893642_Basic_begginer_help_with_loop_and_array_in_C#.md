---
title: "Basic begginer help with loop and array in C#"
date: 2011-12-10
forum: Programming Talk
---

### Post by Tarast on 2011-12-10
Hi guys, I need help, basically I am writing a program in which I can enter 5 numbers and  calculate the average value. I know I have to use a for loop, do I need to use array? If so how can I read array from the user input?

---

### Post by ve4cib on 2011-12-10
> **Tarast said:**
> Hi guys, I need help, basically I am writing a program in which I can enter 5 numbers and  calculate the average value. I know I have to use a for loop, do I need to use array? If so how can I read array from the user input?

You could use an array, but if you're simply calculating the average you don't have to:

```

const int max_times = 5;
double total = 0;
double average;
int input;
for(int i=0; i<max_times; i++)
{
    input = readUserInput();
    total += input;
}
average = total/max_times;

```

Basically you keep a running total of the inputs, and divide by the number of inputs entered.

If you wanted to use an array you could do it like this:

```

const int max_times = 5;
double total = 0;
double average;
int inputs[max_times];
for(int i=0; i<max_times; i++)
{
    inputs[i] = readUserInput();
}

for(int i=0; i<max_times; i++)
{
    total += inputs[i];
}
average = total/max_times;

```

Same process as before, but you read in values to the array, and then calculate the total from the array instead of from the user input directly.

---

### Post by Tarast on 2011-12-14
awww thanks mate

---

### Post by Tony Flury on 2011-12-14
This smells of homework - if so what have you learned by someone giving you the full answer - unless you understand why the answer is right you don't learn much other than copy and paste.

In general people shouldn't give you answers to your homework. What they will do is help you on specific issues (compiler errors/crashes etc), or specific problems that arise when you have already written some code but cannot get it to work.

---


---
title: "[Java] Returning Values From A Vector"
date: 2009-03-25
forum: Programming Talk
---

### Post by Sinkingships7 on 2009-03-25
I'm writing this program for school. It takes 10 doubles as input, adds them within a function, and returns the average.

I have only one question: **how do I get a value from within the vector?**

I was under the impression that the **get(int)** method of the Vector class would do this for me, but apparently I'm wrong. I get this error:

[I]H:\Adv Programming\NetBeansProjects\Project 9-2\src\project92\Main.java:11: operator + cannot be applied to int,java.lang.Object
[/I]

```
[color=#008000]**package**[/color] project92[color=#666666];[/color] 

[color=#008000]**import**[/color] [color=#0000FF]**java.util.Scanner**[/color][color=#666666];[/color] 
[color=#008000]**import**[/color] [color=#0000FF]**java.util.Vector**[/color][color=#666666];[/color] 

[color=#008000]**public**[/color] [color=#008000]**class**[/color] [color=#0000FF]**Main**[/color][color=#666666]{[/color] 
    [color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]double[/color] [color=#0000FF]average[/color][color=#666666]([/color]Vector V[color=#666666]){[/color] 
        [color=#B00040]int[/color] sum [color=#666666]=[/color] [color=#666666]0[/color][color=#666666];[/color] 
        System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color]V[color=#666666].[/color][color=#7D9029]size[/color][color=#666666]());[/color] 
        [color=#008000]**for**[/color] [color=#666666]([/color][color=#B00040]int[/color] i [color=#666666]=[/color] [color=#666666]0[/color][color=#666666];[/color] i [color=#666666]<=[/color] V[color=#666666].[/color][color=#7D9029]size[/color][color=#666666]();[/color] i[color=#666666]++){[/color] 
            sum [color=#666666]+=[/color] V[color=#666666].[/color][color=#7D9029]get[/color][color=#666666]([/color]i[color=#666666]);[/color] 
        [color=#666666]}[/color] 
        [color=#008000]**return**[/color] [color=#666666]([/color]sum [color=#666666]/[/color] V[color=#666666].[/color][color=#7D9029]size[/color][color=#666666]());[/color] 
    [color=#666666]}[/color] 
     
    [color=#008000]**public**[/color] [color=#008000]**static**[/color] [color=#B00040]void[/color] [color=#0000FF]main[/color][color=#666666]([/color]String[color=#666666][][/color] args[color=#666666]){[/color] 
        Scanner input [color=#666666]=[/color] [color=#008000]**new**[/color] Scanner[color=#666666]([/color]System[color=#666666].[/color][color=#7D9029]in[/color][color=#666666]);[/color] 
        Vector list [color=#666666]=[/color] [color=#008000]**new**[/color] Vector[color=#666666]();[/color] 
        [color=#B00040]double[/color] num[color=#666666];[/color] 
         
        [color=#008000]**for**[/color] [color=#666666]([/color][color=#B00040]int[/color] i [color=#666666]=[/color] [color=#666666]1[/color][color=#666666];[/color] i [color=#666666]<=[/color] [color=#666666]10[/color][color=#666666];[/color] i[color=#666666]++){[/color] 
            [color=#008000]**try**[/color][color=#666666]{[/color] 
                System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]print[/color][color=#666666]([/color][color=#BA2121]"Enter a decimal value: "[/color][color=#666666]);[/color] 
                num [color=#666666]=[/color] input[color=#666666].[/color][color=#7D9029]nextDouble[/color][color=#666666]();[/color] 
            [color=#666666]}[/color][color=#008000]**catch**[/color] [color=#666666]([/color]Exception e[color=#666666]){[/color] 
                System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color][color=#BA2121]"Invalid Input. Try Again."[/color][color=#666666]);[/color] 
                i[color=#666666]--;[/color] 
                [color=#008000]**continue**[/color][color=#666666];[/color] 
            [color=#666666]}[/color] 
             
            list[color=#666666].[/color][color=#7D9029]add[/color][color=#666666]([/color]num[color=#666666]);[/color]             
        [color=#666666]}[/color] 
         
        System[color=#666666].[/color][color=#7D9029]out[/color][color=#666666].[/color][color=#7D9029]println[/color][color=#666666]([/color][color=#BA2121]"The average of the doubles is "[/color] [color=#666666]+[/color] average[color=#666666]([/color]list[color=#666666]));[/color] 
    [color=#666666]}[/color] 
[color=#666666]}[/color]  

```

---

### Post by jespdj on 2009-03-25
Do you understand what the error message means?

It means you are trying to add an int and an Object together. That doesn't work. Your Vector contains objects (in your case, instances of class Double). But you're not using generics, so the compiler doesn't know that in your method 'average'.

First of all, you probably should make 'sum' a **double**, not an **int**.

You could either use generics:
```
public static double average(Vector<Double> V) {
    double sum = 0.0;
    // ...
}

public static void main(String[] args) {
    // ...
    Vector<Double> list = new Vector<Double>();
    // ...
}
```

Or you could cast the Object that you get out of the Vector to a Double:
```
public static double average(Vector V) {
    double sum = 0.0;
    System.out.println(V.size()); 
    for (int i = 0; i <= V.size(); i++){ 
        sum += (Double) V.get(i); 
    } 
    return (sum / V.size()); 
}
```

---

### Post by davetv on 2009-03-25
forgive me as a java noob here ... I am a Delphi/c/c++ programmer. 

A question ... V.size ... shouldn't the for loop conditional be "i<V.size()" rather than "i<=V.Size()". It seems to make more sense to me in the context of working out the average as sum/V.size()

---

### Post by Sinkingships7 on 2009-03-25
jespdj: Thank you! I didn't realize that there was a difference between the double primitive and the Double object. Java's my most recent language.

I just casted the sum statement and that fixed my problem. Thanks!

---

### Post by simeon87 on 2009-03-25
> **davetv said:**
> forgive me as a java noob here ... I am a Delphi/c/c++ programmer. 

A question ... V.size ... shouldn't the for loop conditional be "i<V.size()" rather than "i<=V.Size()". It seems to make more sense to me in the context of working out the average as sum/V.size()

It should indeed be i < V.size() because there's no element at index V.size() as indices start at 0.

---


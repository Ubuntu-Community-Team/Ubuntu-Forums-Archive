---
title: "need help java : how to format the output?"
date: 2008-02-18
forum: Programming Talk
---

### Post by AlexenderReez on 2008-02-18
i have done simple java program that should display price for food selected.i wonder,how to format/synchronize the out so that it give price output accurately like

> 12.45

instead of

> 12.450000001  //-->i don't want this output...

i google around and i try to change code from

[PHP] System.out.println("Total Prices need to pay RM= " +overallTotal));[/PHP]

to

[PHP]System.out.println("Total Prices need to pay RM= "+ String.format("%0.2f",overallTotal));[/PHP]

but it display = --

[PHP]reez@alexenderreez:~/Desktop/assignment$ java MacDollah
1. Mac Beef = 2.7
2. Mac Fish = 3.5
3. Cheesy Beef Burger = 3.5
4. Mac Chicken = 3.0
5. Mengelembu Fries = 2.0
6. Combo Meal A = 5.0
7. Combo Meal B = 6.5
8. Combo Meal C = 8.0
9. SoftDrink = 2.0
10. Ais CreaM = 1.0
Please enter your number selection(Enter 0 to end selection)
2
 RM=3.5
Please enter your number selection(Enter 0 to end selection)
4
 RM=3.0
Please enter your number selection(Enter 0 to end selection)
0
Exception in thread "main" java.util.MissingFormatWidthException: 0.2f
        at java.util.Formatter$FormatSpecifier.checkNumeric(Formatter.java:2929)
        at java.util.Formatter$FormatSpecifier.checkFloat(Formatter.java:2908)
        at java.util.Formatter$FormatSpecifier.<init>(Formatter.java:2644)
        at java.util.Formatter.parse(Formatter.java:2479)
        at java.util.Formatter.format(Formatter.java:2413)
        at java.util.Formatter.format(Formatter.java:2366)
        at java.lang.String.format(String.java:2770)
        at order.displayPrice(order.java:25)
        at MacDollah.main(MacDollah.java:16)
[/PHP]

which is give error there....nay help...how should i write to format the output..?

---

### Post by Geekkit on 2008-02-18
> **AlexenderReez said:**
> i have done simple java program that should display price for food selected.i wonder,how to format/synchronize the out so that it give price output

To format a price use the NumberFormat class like this:

```
    // Format
    locale = Locale.CANADA;
    string = NumberFormat.getCurrencyInstance(locale).format(123.45);
    // $123.45
```

If you want quick and dirty (i.e., C-Style)  then use the printf statement:

```
double x = 27.5;
System.out.printf("x = %15.2f", x);
```

---

### Post by AlexenderReez on 2008-02-18
thanks:KS

---

### Post by Geekkit on 2008-02-18
> **AlexenderReez said:**
> thanks:KS

Welcome. :)

---

